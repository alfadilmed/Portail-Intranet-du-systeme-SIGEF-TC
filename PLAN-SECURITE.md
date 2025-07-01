```markdown
# Plan de Sécurité & Confidentialité - Portail Intranet SIGEF-TC

## 1. Introduction

Ce document décrit les mesures de sécurité et de confidentialité qui seront mises en œuvre pour le Portail Intranet SIGEF-TC. L'objectif est de garantir l'intégrité, la confidentialité, la disponibilité des données et des services du portail, et de protéger les informations personnelles des collaborateurs de la Cour des Comptes, conformément aux réglementations en vigueur et aux politiques internes de l'organisation.

## 2. Accès Restreint au Portail (Authentification Forte)

### 2.1. Authentification Unique (SSO)
*   **Principe :** Les utilisateurs accéderont au portail en utilisant leurs identifiants d'entreprise existants.
*   **Technologie :** Intégration avec l'annuaire d'entreprise (LDAP/Active Directory) via un Service d'Identité (IDP) supportant les protocoles OAuth 2.0 et OpenID Connect (OIDC). Keycloak est la solution préconisée.
*   **Flux :** L'utilisateur est redirigé vers la page de connexion de l'IDP. Après authentification réussie auprès de l'annuaire, l'IDP émet des tokens (Access Token, Refresh Token) que le portail utilise pour gérer la session et autoriser l'accès aux API.

### 2.2. Authentification Multi-Facteurs (MFA)
*   **Recommandation :** Activation de la MFA au niveau de l'IDP, au minimum pour les comptes administrateurs et les utilisateurs ayant accès à des données sensibles.
*   **Méthodes Supportées :** L'IDP (Keycloak) doit supporter diverses méthodes de MFA (TOTP via application d'authentification, SMS, FIDO U2F/WebAuthn). Le choix de la méthode sera aligné sur la politique de sécurité de la Cour des Comptes.

### 2.3. Politique de Mots de Passe
*   Gérée par l'annuaire d'entreprise (LDAP/AD). Le portail ne stocke ni ne gère directement les mots de passe des utilisateurs.
*   Les politiques de complexité, d'expiration, et de verrouillage de compte de l'annuaire s'appliquent.

### 2.4. Gestion des Sessions
*   **Durée de vie des sessions :** Configurable au niveau de l'IDP et du portail. Sessions avec expiration automatique après une période d'inactivité.
*   **Sécurité des tokens :**
    *   Access Tokens (JWT) : Courte durée de vie (ex: 15-60 minutes), transmis via Header HTTP `Authorization: Bearer`.
    *   Refresh Tokens : Durée de vie plus longue (ex: plusieurs heures/jours), stockés de manière sécurisée (HttpOnly, Secure cookie pour le frontend SPA si l'IDP et le SPA sont sur le même domaine principal, sinon backend-for-frontend pattern pour gérer les refresh tokens). Rotation des refresh tokens.
*   **Déconnexion :** La déconnexion du portail doit invalider la session au niveau du portail et initier une déconnexion de l'IDP (Single Log-Out - SLO) si possible.

## 3. Protection des Données Personnelles et Institutionnelles

### 3.1. Classification des Données
*   Les données gérées par le portail seront classifiées selon leur sensibilité (ex: publiques, internes, confidentielles, personnelles).
*   Cette classification guidera les mesures de protection et les droits d'accès.

### 3.2. Chiffrement
*   **Chiffrement en Transit :**
    *   TLS 1.2 minimum (TLS 1.3 recommandé) pour toutes les communications HTTP (navigateur client vers Passerelle API, Passerelle API vers microservices, microservices entre eux, microservices vers bases de données et autres services backends).
    *   Utilisation de certificats SSL/TLS émis par une autorité de certification reconnue ou par la PKI interne de la Cour des Comptes.
    *   Configuration des serveurs pour utiliser des suites cryptographiques fortes.
*   **Chiffrement au Repos :**
    *   **Bases de Données :** Activation du chiffrement transparent des données (TDE) pour PostgreSQL et MongoDB si supporté et jugé nécessaire, ou chiffrement au niveau du système de fichiers des serveurs de base de données.
    *   **Stockage des Fichiers (GED) :** Chiffrement côté serveur pour les fichiers stockés sur MinIO/S3 (ex: AES-256).
    *   **Sauvegardes :** Les sauvegardes des bases de données et des fichiers seront chiffrées.
*   **Chiffrement des Données Sensibles :** Les champs contenant des données personnelles particulièrement sensibles (si applicable et au-delà des informations de profil de base) pourraient faire l'objet d'un chiffrement applicatif supplémentaire (rarement nécessaire pour un intranet standard, mais à évaluer).

### 3.3. Contrôle d'Accès Basé sur les Rôles (RBAC)
*   **Principe du moindre privilège :** Les utilisateurs n'auront accès qu'aux données et fonctionnalités strictement nécessaires à l'exercice de leurs fonctions.
*   **Définition des Rôles :** Des rôles clairs (Collaborateur, Contributeur, Éditeur, Administrateur de module, Administrateur Portail, etc.) seront définis avec des ensembles de permissions spécifiques.
*   **Application :** Les permissions seront vérifiées à plusieurs niveaux :
    *   Passerelle API (pour les accès généraux aux services).
    *   Chaque microservice (pour les opérations fines sur ses propres ressources).
*   **Gestion des Droits :** Interface d'administration pour gérer l'attribution des rôles aux utilisateurs ou aux groupes (synchronisés depuis LDAP/AD).

### 3.4. Anonymisation/Pseudonymisation
*   Pour les statistiques d'utilisation ou les logs d'analyse, les données personnelles identifiables seront anonymisées ou pseudonymisées lorsque cela est possible et approprié.

### 3.5. Conformité Réglementaire
*   Le portail sera développé en tenant compte des exigences du Règlement Général sur la Protection des Données (RGPD) si applicable, et des lois nationales relatives à la protection des données personnelles.
*   Une analyse d'impact sur la protection des données (AIPD/PIA) pourra être menée si le traitement de données sensibles le justifie.

## 4. Stratégie de Sauvegarde et Continuité de Service

### 4.1. Sauvegardes (Backups)
*   **Périmètre :**
    *   Bases de données (PostgreSQL, MongoDB).
    *   Stockage des fichiers de la GED (MinIO/S3).
    *   Configurations des applications et des serveurs.
    *   Images Docker des applications (stockées dans un registre privé).
*   **Fréquence :**
    *   Sauvegardes complètes : Hebdomadaires.
    *   Sauvegardes incrémentielles/différentielles : Quotidiennes pour les bases de données et les fichiers.
    *   Transaction logs (pour PostgreSQL) : Sauvegardés en continu ou très fréquemment pour permettre une restauration à un point précis dans le temps (PITR).
*   **Rétention :** Politique de rétention à définir avec la Cour des Comptes (ex: 30 jours pour les sauvegardes quotidiennes, 3 mois pour les hebdomadaires, 1 an pour les mensuelles).
*   **Stockage des Sauvegardes :**
    *   Sur un support/serveur distinct de l'infrastructure de production.
    *   Idéalement, une copie hors site (ou dans une zone de disponibilité différente).
    *   Chiffrement des sauvegardes.
*   **Tests de Restauration :** Des tests de restauration réguliers (ex: trimestriels) seront effectués pour vérifier l'intégrité des sauvegardes et la validité de la procédure de restauration.

### 4.2. Plan de Continuité d'Activité (PCA) / Plan de Reprise d'Activité (PRA)
*   **Objectifs de Temps de Reprise (RTO) et Objectifs de Perte de Données Maximale Admissible (RPO) :** À définir en collaboration avec la Cour des Comptes en fonction de la criticité du portail.
*   **Haute Disponibilité (HA) :**
    *   Pour les composants critiques (Passerelle API, Service d'Identité, Bases de données), mise en place de solutions de clustering et de redondance.
    *   Utilisation d'un orchestrateur de conteneurs (Kubernetes) pour assurer le redémarrage automatique des services défaillants.
    *   Load balancing pour répartir la charge et éviter les points uniques de défaillance.
*   **Procédure de Reprise :** Documentation claire des étapes de restauration des services et des données en cas d'incident majeur.
*   **Infrastructure de Secours (si RTO/RPO stricts) :** Mise en place d'une infrastructure de secours (dormante ou active) dans un autre site/datacenter.

## 5. Journalisation et Audit (Logging & Monitoring)

### 5.1. Journalisation des Événements
*   **Collecte Centralisée :** Utilisation d'une stack EFK (Elasticsearch/OpenSearch, Fluentd, Kibana) ou similaire pour collecter, stocker et analyser les logs de tous les composants.
*   **Types de Logs :**
    *   **Logs Applicatifs :** Activités des microservices (requêtes reçues, erreurs, avertissements, informations de débogage).
    *   **Logs d'Accès :** Requêtes HTTP vers la Passerelle API et les serveurs web (IP source, URL, statut, user agent).
    *   **Logs de Sécurité :**
        *   Tentatives d'authentification (réussies et échouées).
        *   Modifications des droits d'accès.
        *   Accès refusés.
        *   Alertes de sécurité potentielles (détectées par des IDS/IPS si en place).
    *   **Logs d'Audit :** Actions critiques effectuées par les utilisateurs et les administrateurs (création/modification/suppression de contenus sensibles, modifications de configuration majeures, accès aux données personnelles). Ces logs doivent être immuables ou protégés contre la falsification.
*   **Format des Logs :** Structuré (ex: JSON) pour faciliter l'analyse et la corrélation.
*   **Rétention des Logs :** Politique de rétention à définir (ex: 3 à 12 mois pour les logs applicatifs, plus longtemps pour les logs d'audit et de sécurité selon les exigences légales).

### 5.2. Surveillance (Monitoring)
*   **Indicateurs Clés :**
    *   Disponibilité des services (uptime).
    *   Performance (temps de réponse, latence).
    *   Utilisation des ressources (CPU, RAM, disque, réseau).
    *   Taux d'erreur.
*   **Outils :** Prometheus pour la collecte de métriques, Grafana pour la visualisation et les tableaux de bord. Alertmanager pour les alertes.
*   **Alertes :** Configuration d'alertes en temps réel pour les incidents critiques (service indisponible, taux d'erreur élevé, ressources saturées, tentatives d'intrusion suspectes).

## 6. Sécurité Applicative et Infrastructurelle

### 6.1. Bonnes Pratiques de Développement Sécurisé (DevSecOps)
*   **OWASP Top 10 :** Prise en compte systématique des risques (injection, XSS, CSRF, authentification cassée, etc.) lors du développement.
*   **Validation des Entrées :** Validation et sanitation de toutes les données provenant des utilisateurs ou de sources externes (côté client et serveur).
*   **Requêtes Préparées / ORM :** Utilisation systématique pour prévenir les injections SQL/NoSQL.
*   **Encodage des Sorties :** Encodage approprié des données affichées pour prévenir les attaques XSS.
*   **Headers de Sécurité HTTP :** Implémentation des headers recommandés (Content Security Policy (CSP), HTTP Strict Transport Security (HSTS), X-Content-Type-Options, X-Frame-Options, Referrer-Policy).
*   **Gestion des Dépendances :** Scan régulier des bibliothèques et frameworks tiers pour identifier et corriger les vulnérabilités connues (outils type npm audit, Snyk, OWASP Dependency-Check).
*   **Secrets Management :** Utilisation d'un gestionnaire de secrets (ex: HashiCorp Vault, secrets Kubernetes) pour les clés API, mots de passe de bases de données, certificats. Aucun secret en dur dans le code ou les fichiers de configuration versionnés.
*   **Revues de Code :** Revues de code axées sur la sécurité.
*   **Tests de Sécurité :**
    *   Tests d'intrusion (pentests) planifiés avant la mise en production et régulièrement par la suite.
    *   Scans de vulnérabilités automatisés (SAST/DAST) intégrés dans le pipeline CI/CD.

### 6.2. Sécurisation de l'Infrastructure
*   **Hardening des Systèmes :** Configuration sécurisée des systèmes d'exploitation, des serveurs web, des bases de données (désactivation des services inutiles, application des patchs de sécurité, etc.).
*   **Pare-feu Réseau :** Filtrage des flux entrants et sortants. Segmentation du réseau (DMZ, zone applicative, zone données).
*   **Protection Anti-DDoS (si exposé sur internet, moins critique pour un intranet pur) :** Solutions de mitigation DDoS.
*   **Mises à Jour et Patch Management :** Processus rigoureux pour l'application des correctifs de sécurité sur tous les composants logiciels et systèmes.

## 7. Formation et Sensibilisation
*   Formation des administrateurs du portail aux aspects de sécurité et à la gestion des incidents.
*   Sensibilisation des utilisateurs aux bonnes pratiques de sécurité (choix de mots de passe robustes si non SSO, vigilance face au phishing, signalement d'activités suspectes).

---
*Document préparé par : Primex Software*
*Rédigé par : Jules AI – Agent IA Senior*
*Date : 2023-10-27*
*URL : https://primex-software.com*
```
