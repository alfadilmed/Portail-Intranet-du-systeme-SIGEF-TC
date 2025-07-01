```markdown
# Documentation Technique (DOC-T) - Portail Intranet SIGEF-TC

## 1. Introduction

Cette documentation technique détaille l'architecture logicielle, les composants techniques, les aspects de sécurité, les intégrations et les API du Portail Intranet SIGEF-TC. Elle est destinée aux équipes de développement, d'exploitation et d'architecture. Elle complète les informations fournies dans le `README.md`.

## 2. Architecture Logicielle

### 2.1. Choix d'Architecture : Microservices
L'architecture retenue est une **architecture microservices**. Ce choix est motivé par :
*   **Modularité :** Chaque fonctionnalité métier clé (GED, Actualités, Calendrier, etc.) est encapsulée dans un service indépendant.
*   **Scalabilité :** Permet de dimensionner indépendamment chaque service en fonction de sa charge.
*   **Résilience :** La défaillance d'un service a un impact limité sur le reste du portail.
*   **Flexibilité Technologique :** Possibilité de choisir la technologie la plus adaptée pour chaque microservice (bien que nous recommandions une certaine homogénéité pour simplifier la maintenance).
*   **Déploiement Indépendant :** Les mises à jour et les nouvelles versions de chaque service peuvent être déployées sans impacter les autres.

### 2.2. Vue d'Ensemble des Composants

Le système sera composé des éléments suivants :

*   **Client Frontend (SPA) :** Application web monopage (React ou Vue.js) s'exécutant dans le navigateur de l'utilisateur.
*   **Passerelle API (API Gateway) :** Point d'entrée unique pour toutes les requêtes du client. Elle gère :
    *   Authentification et autorisation des requêtes (via le Service d'Identité).
    *   Routage des requêtes vers les microservices appropriés.
    *   Limitation de débit (rate limiting) et protection contre les abus.
    *   Agrégation de réponses (potentiellement).
    *   Terminaison SSL.
*   **Microservices Backend :**
    *   **Service Utilisateurs & Profils :** Gestion des données utilisateurs, profils, préférences, synchronisation avec LDAP/AD.
    *   **Service Actualités :** Gestion de la création, publication, stockage des actualités et annonces.
    *   **Service Calendrier :** Gestion des événements, invitations, rappels.
    *   **Service GED :** Gestion du stockage des fichiers, métadonnées, versioning, droits d'accès aux documents.
    *   **Service Forums :** Gestion des catégories, forums, sujets, messages, modération.
    *   **Service Notifications :** Gestion de la création et de l'envoi des notifications (in-app, email).
    *   **Service Recherche :** Interface avec le moteur de recherche (OpenSearch/Elasticsearch) pour l'indexation et la recherche.
    *   **Service Espaces Collaboratifs :** Gestion de la création et de la configuration des espaces, de leurs membres et des liens vers les fonctionnalités dédiées.
*   **Service d'Identité (Identity Provider / IDP) :**
    *   Gestion centralisée de l'authentification (OAuth2 / OpenID Connect).
    *   Gestion des sessions utilisateurs.
    *   Intégration avec l'annuaire d'entreprise (LDAP/AD) pour le Single Sign-On (SSO).
    *   Gestion des rôles et permissions (peut être un service à part ou intégré à l'IDP).
*   **Bases de Données :**
    *   **PostgreSQL :** Pour les données structurées et relationnelles (utilisateurs, rôles, métadonnées des actualités, événements du calendrier, structure de la GED, forums). Chaque microservice pourrait avoir son propre schéma ou sa propre base de données pour une isolation maximale.
    *   **MongoDB / MinIO :** MongoDB pour les contenus flexibles (ex: contenu des actualités, certains logs) ou MinIO (compatible S3) pour le stockage binaire des fichiers de la GED.
*   **Moteur de Recherche :**
    *   **OpenSearch/Elasticsearch :** Pour l'indexation full-text de tous les contenus pertinents et la fourniture de capacités de recherche avancées.
*   **Bus de Messages (Message Broker) :**
    *   **RabbitMQ / NATS :** Pour la communication asynchrone entre les microservices (ex: un nouveau document dans la GED déclenche un événement pour le service de recherche afin de l'indexer, une nouvelle actualité déclenche une notification).
*   **Cache Distribué :**
    *   **Redis :** Pour la mise en cache des sessions, des configurations, des données fréquemment accédées afin d'améliorer les performances et de réduire la charge sur les bases de données.

### 2.3. Diagrammes d'Architecture

#### 2.3.1. Diagramme de Composants Logiques
*(Description textuelle. Un diagramme formel sera créé avec un outil de modélisation.)*

```
[Client Navigateur (SPA)] <--(HTTPS)--> [Passerelle API]

[Passerelle API] --(routage + auth)--> [Service Utilisateurs]
[Passerelle API] --(routage + auth)--> [Service Actualités]
[Passerelle API] --(routage + auth)--> [Service GED]
[Passerelle API] --(routage + auth)--> [Service Calendrier]
[Passerelle API] --(routage + auth)--> [Service Forums]
[Passerelle API] --(routage + auth)--> [Service Espaces Collab.]
[Passerelle API] --(routage + auth)--> [Service Recherche]

[Service Utilisateurs] <--(JDBC/TCP)--> [PostgreSQL (Base Utilisateurs)]
[Service Utilisateurs] <--(LDAPS)-----> [Annuaire LDAP/AD]

[Service Actualités]  <--(JDBC/TCP)--> [PostgreSQL (Base Actualités)]
[Service Actualités]  --(event)------> [Bus de Messages]

[Service GED]         <--(JDBC/TCP)--> [PostgreSQL (Métadonnées GED)]
[Service GED]         <--(S3 API)----> [MinIO / Stockage Fichiers]
[Service GED]         --(event)------> [Bus de Messages]

[Service Calendrier]  <--(JDBC/TCP)--> [PostgreSQL (Base Calendrier)]
[Service Calendrier]  --(event)------> [Bus de Messages]

[Service Forums]      <--(JDBC/TCP)--> [PostgreSQL (Base Forums)]
[Service Forums]      --(event)------> [Bus de Messages]

[Service Espaces Collab.] <--(JDBC/TCP)--> [PostgreSQL (Base Espaces)]

[Service Recherche]   <--(HTTP API)--> [OpenSearch/Elasticsearch Cluster]
[Service Recherche]   <--(consomme)--- [Bus de Messages]

[Tous les Microservices] --(authZ req)--> [Service d'Identité / Droits]
[Tous les Microservices] --(read/write)--> [Redis (Cache)]
[Tous les Microservices] --(publish/log)--> [Bus de Messages (pour Logs vers EFK)]

[Service Notifications] <--(consomme)--- [Bus de Messages]
[Service Notifications] --(SMTP)-------> [Serveur Email]
[Service Notifications] --(WebSockets?)-> [Client Navigateur (via Passerelle)]

[Service d'Identité]  <--(JDBC/TCP)--> [PostgreSQL (Base Identités/Tokens)]
[Service d'Identité]  <--(LDAPS)-----> [Annuaire LDAP/AD]
```

#### 2.3.2. Diagramme de Déploiement (Conceptuel)
*(Description textuelle. Un diagramme formel sera créé avec un outil de modélisation.)*

*   **Zone DMZ (ou Proxy Inverse) :**
    *   Serveur(s) hébergeant la Passerelle API.
    *   Potentiellement un Load Balancer en amont.
*   **Zone Applicative Sécurisée :**
    *   Cluster Kubernetes (ou serveurs Docker) hébergeant les conteneurs des différents microservices (Frontend SPA servi par un conteneur Nginx/Node.js, services backend).
    *   Service d'Identité.
    *   Serveur(s) pour le Bus de Messages (RabbitMQ/NATS).
    *   Serveur(s) pour le Cache Distribué (Redis).
*   **Zone Données Sécurisée :**
    *   Cluster(s) de bases de données PostgreSQL.
    *   Cluster MongoDB (si utilisé).
    *   Cluster MinIO (stockage objet).
    *   Cluster OpenSearch/Elasticsearch.
*   **Zone Services d'Infrastructure :**
    *   Serveur(s) LDAP/AD (existant).
    *   Serveur SMTP (existant ou dédié).
    *   Serveur(s) de monitoring (Prometheus, Grafana).
    *   Serveur(s) de logging (EFK Stack).
    *   Serveur(s) CI/CD (GitLab CI, Jenkins).

Toutes les communications entre zones et entre serveurs doivent être sécurisées (TLS).

### 2.4. Technologies Spécifiques par Composant

*   **Frontend SPA :**
    *   Langage : TypeScript
    *   Framework : React avec Next.js (pour SSR/SSG et routing) ou Vue.js avec Nuxt.js.
    *   Gestion d'état : Redux Toolkit (React) / Pinia (Vue).
    *   Client HTTP : Axios ou Fetch API.
    *   UI Kit : Material-UI, Ant Design, ou Tailwind CSS avec Headless UI.
*   **Passerelle API :**
    *   Kong API Gateway, Traefik, ou un développement custom avec NestJS (module Gateway).
*   **Microservices Backend (exemple pour un service type) :**
    *   Langage : TypeScript avec Node.js.
    *   Framework : NestJS (structure modulaire, DI, support pour microservices, OpenAPI).
    *   ORM : TypeORM ou Prisma pour l'interaction avec PostgreSQL.
    *   Communication inter-services : REST/HTTP synchrone, et événements via RabbitMQ/NATS pour l'asynchrone.
    *   Validation des données : `class-validator` avec NestJS.
*   **Service d'Identité :**
    *   Keycloak (solution open-source robuste supportant OAuth2, OpenID Connect, SAML, intégration LDAP).
    *   Ou développement custom avec NestJS et Passport.js si les besoins sont plus simples et un contrôle total est requis.
*   **Conteneurisation et Orchestration :**
    *   Docker pour la conteneurisation.
    *   Kubernetes pour l'orchestration, la gestion des déploiements, la scalabilité et la résilience. `Helm` pour la gestion des packages Kubernetes.

## 3. Sécurité

### 3.1. Authentification
*   **Mécanisme :** OAuth 2.0 avec le flux Authorization Code Grant (PKCE recommandé pour les SPA). OpenID Connect (OIDC) sera utilisé par-dessus OAuth 2.0 pour la fédération d'identité.
*   **Fournisseur d'Identité (IDP) :** Un service d'identité dédié (ex: Keycloak) sera utilisé.
*   **Intégration SSO :** L'IDP sera configuré pour s'intégrer avec l'annuaire LDAP/Active Directory de la Cour des Comptes pour permettre le Single Sign-On. Les utilisateurs se connecteront avec leurs identifiants d'entreprise.
*   **Authentification Multi-Facteurs (MFA) :** L'IDP devra supporter la MFA (TOTP, SMS, etc.). Son activation sera recommandée, notamment pour les comptes à privilèges.
*   **Gestion des Tokens :**
    *   Access Tokens (JWT) : Courte durée de vie, utilisés pour accéder aux API des microservices. Signés par l'IDP.
    *   Refresh Tokens : Longue durée de vie, stockés de manière sécurisée (HttpOnly cookie pour le frontend), utilisés pour obtenir de nouveaux access tokens sans re-authentification.
*   **Sécurité des API :** Chaque microservice validera la signature et les scopes des JWT reçus.

### 3.2. Gestion des Accès (Autorisation)
*   **Modèle :** RBAC (Role-Based Access Control) sera implémenté.
*   **Définition :** Les rôles et permissions seront définis centralement (potentiellement gérés par l'IDP ou un service d'autorisation dédié) et/ou localement par certains microservices pour des contrôles plus fins.
*   **Application :** La Passerelle API pourra effectuer une première vérification des rôles/scopes. Chaque microservice sera responsable de l'application fine des permissions pour ses propres ressources.
*   **Exemple :** Un utilisateur avec le rôle "ContributeurActualites" aura la permission de créer des actualités. Le service Actualités vérifiera cette permission.

### 3.3. Journalisation (Logging)
*   **Stratégie :** Tous les microservices et composants d'infrastructure devront produire des logs structurés (ex: JSON).
*   **Contenu des Logs :**
    *   Requêtes reçues et traitées (avec anonymisation des données sensibles).
    *   Erreurs et exceptions.
    *   Événements de sécurité (tentatives de connexion échouées, accès non autorisés, modifications de droits).
    *   Actions métier importantes (création de contenu, suppression).
*   **Centralisation :** Les logs seront centralisés à l'aide d'une stack EFK (Elasticsearch/OpenSearch, Fluentd, Kibana) ou ELK.
    *   Fluentd (ou Filebeat/Logstash) collectera les logs des conteneurs et des serveurs.
    *   Elasticsearch/OpenSearch stockera et indexera les logs.
    *   Kibana fournira une interface pour la recherche, la visualisation et l'analyse des logs.
*   **Audit :** Des logs d'audit spécifiques seront générés pour les actions critiques (changements de configuration, gestion des droits, accès aux données sensibles).

### 3.4. Protection des Données
*   **Chiffrement en Transit :** TLS/HTTPS obligatoire pour toutes les communications (clients vers passerelle, passerelle vers microservices, microservices entre eux, services vers bases de données). Utilisation de certificats SSL/TLS valides.
*   **Chiffrement au Repos :**
    *   Les bases de données (PostgreSQL, MongoDB) devront être configurées pour le chiffrement au repos (TDE - Transparent Data Encryption si supporté, ou chiffrement au niveau du système de fichiers).
    *   Les fichiers stockés dans la GED (MinIO/S3) seront chiffrés côté serveur.
    *   Les sauvegardes seront chiffrées.
*   **Données Sensibles :** Les mots de passe ne seront jamais stockés en clair (gérés par l'IDP, qui utilise des algorithmes de hachage forts comme bcrypt ou Argon2). Les autres données personnelles identifiables (PII) seront traitées avec soin, en limitant leur accès et leur journalisation.
*   **Sécurisation des Backups :** Les sauvegardes seront stockées dans un emplacement sécurisé, chiffrées, et testées régulièrement.

### 3.5. Sécurité Applicative
*   **OWASP Top 10 :** Les développements suivront les recommandations pour prévenir les vulnérabilités courantes (Injections SQL/NoSQL, XSS, CSRF, Broken Authentication, etc.).
    *   Utilisation d'ORM/requêtes préparées.
    *   Validation et sanitation systématique des entrées utilisateurs (côté client et serveur).
    *   Encodage des sorties pour prévenir XSS.
    *   Utilisation de tokens anti-CSRF pour les opérations sensibles modifiant l'état.
    *   Headers de sécurité HTTP (Content Security Policy, Strict-Transport-Security, X-Content-Type-Options, X-Frame-Options).
*   **Dépendances :** Analyse régulière des dépendances logicielles (npm audit, composer audit, etc.) pour identifier et corriger les vulnérabilités connues.
*   **Secrets Management :** Utilisation d'un gestionnaire de secrets (ex: HashiCorp Vault, secrets Kubernetes) pour stocker les clés API, mots de passe de bases de données, certificats. Ne pas stocker de secrets dans le code source.

## 4. Intégrations Possibles

*   **Annuaire d'Entreprise (LDAP / Active Directory) :**
    *   **Objectif :** Authentification centralisée (SSO), synchronisation des informations de base des utilisateurs (nom, email, département).
    *   **Méthode :** Le Service d'Identité (Keycloak) se connectera en tant que client LDAP/AD.
*   **Système de Gestion Électronique de Documents (GED) Existant :**
    *   **Objectif :** Si une GED existante doit être intégrée plutôt que remplacée.
    *   **Méthode :** Via API si la GED existante en expose une. Développement d'un connecteur spécifique. Le module GED du portail agirait alors comme une surcouche ou un point d'accès.
*   **Outils RH (SIRH) :**
    *   **Objectif :** Synchroniser des informations de profil plus riches (poste, manager, etc.), gérer les arrivées/départs.
    *   **Méthode :** Via API du SIRH si disponible, ou par import/export de fichiers plats (moins idéal).
*   **Système d'Email Interne (Exchange, etc.) :**
    *   **Objectif :** Envoi de notifications par email, potentiellement intégration de fonctionnalités de calendrier.
    *   **Méthode :** Via SMTP pour l'envoi. Pour l'intégration de calendrier, via EWS (Exchange Web Services) ou Microsoft Graph API si applicable.
*   **Autres Modules SIGEF-TC :**
    *   **Objectif :** Permettre une navigation fluide et un échange de données entre le portail et d'autres applications du SIGEF-TC.
    *   **Méthode :** Via des liens profonds (deep linking) et/ou des API REST spécifiques si des échanges de données sont nécessaires. Un système de SSO entre les modules est fortement recommandé.

## 5. API d’Interopérabilité (Vers autres modules SIGEF-TC)

Le portail intranet pourra exposer des API REST sécurisées pour permettre à d'autres modules du SIGEF-TC d'interagir avec lui.

*   **Principes :**
    *   Sécurisation via OAuth2 (client credentials grant pour les appels serveur-à-serveur).
    *   Documentation OpenAPI (Swagger) pour chaque API exposée.
    *   Versioning des API.
*   **Exemples d'API que le portail pourrait exposer :**
    *   `GET /api/v1/users/{userId}` : Récupérer des informations de profil utilisateur.
    *   `GET /api/v1/news?filter=...` : Récupérer une liste d'actualités filtrées.
    *   `POST /api/v1/notifications` : Permettre à un autre module de pousser une notification à un utilisateur du portail.
    *   `GET /api/v1/documents/{documentId}` : Accéder à un document de la GED (avec vérification des droits).
*   **Consommation d'API externes :**
    *   Le portail pourra également consommer des API exposées par d'autres modules SIGEF-TC pour afficher des informations consolidées ou déclencher des actions.

---
*Document préparé par : Primex Software*
*Rédigé par : Jules AI – Agent IA Senior*
*Date : 2023-10-27*
*URL : https://primex-software.com*
```
