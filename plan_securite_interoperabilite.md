# Plan de Sécurité & Interopérabilité - Projet SIGEF-TC

## Introduction
Ce document décrit les stratégies et mesures de sécurité ainsi que les principes d'interopérabilité pour le Système Intégré de Gestion et de Contrôle de la Cour des Comptes (SIGEF-TC). La sécurité et l'interopérabilité sont des piliers fondamentaux pour garantir la confidentialité, l'intégrité, la disponibilité des données et la communication efficace avec les systèmes externes.

## 1. Sécurité

### 1.1. Authentification et Gestion des Rôles
*   **Module Centralisé :** La "Plateforme d’Authentification et Gestion des Entités" sera le seul service responsable de l'authentification et de la gestion des habilitations pour l'ensemble du SIGEF-TC.
*   **Authentification Unique (SSO) :** Les agents de la Cour utiliseront un seul jeu d'identifiants pour accéder à tous les modules auxquels ils ont droit (basé sur OpenID Connect/OAuth 2.0).
*   **Politique de Mots de Passe Robuste :**
    *   Complexité minimale (longueur, types de caractères).
    *   Historique des mots de passe pour éviter la réutilisation.
    *   Expiration régulière et mécanisme de réinitialisation sécurisé.
    *   Stockage sécurisé des mots de passe (hachage fort avec sel, ex: Argon2, bcrypt).
*   **Authentification Multi-Facteurs (MFA/2FA) :**
    *   Obligatoire pour les administrateurs et les rôles à privilèges élevés.
    *   Fortement recommandée et configurable pour tous les utilisateurs.
    *   Méthodes supportées : TOTP (Google Authenticator, Authy), SMS, Email (moins sécurisé, pour récupération).
*   **Gestion des Rôles et Permissions (RBAC) :**
    *   Principe du moindre privilège : les utilisateurs n'ont accès qu'aux fonctionnalités et données strictement nécessaires à leur mission.
    *   Permissions granulaires définies par module et par type d'action (Créer, Lire, Mettre à jour, Supprimer, Valider, etc.).
    *   Les rôles seront définis en collaboration avec la Cour des Comptes pour refléter l'organisation et les responsabilités.
    *   Audit régulier des rôles et permissions attribués.
*   **Verrouillage de Compte :** Après un nombre défini de tentatives de connexion échouées.
*   **Gestion des Sessions :** Expiration automatique des sessions inactives, déconnexion unique (SLO).

### 1.2. Sécurité des Accès aux Modules Sensibles
*   **Modules prioritaires :** E-Comptes / Traitement procédural, Gestion Financière, Gestion des RH (surtout paie), Suivi Budgétaire (Comptes de l’État), Plateforme d'Authentification elle-même.
*   **Contrôles d'accès renforcés :**
    *   MFA obligatoire pour l'accès à ces modules ou à leurs fonctionnalités les plus critiques.
    *   Filtrage IP (optionnel, si applicable) pour restreindre l'accès depuis des réseaux non autorisés.
    *   Surveillance accrue des logs d'accès à ces modules.
*   **Chiffrement des Données Sensibles :**
    *   **En transit :** HTTPS/TLS systématique pour toutes les communications entre le client et le serveur, et entre les modules. Utilisation de certificats SSL/TLS valides et robustes.
    *   **Au repos :** Chiffrement des bases de données (TDE) ou de champs spécifiques contenant des informations hautement confidentielles (ex: données personnelles sensibles, informations financières critiques) en utilisant des algorithmes de chiffrement forts (AES-256). La gestion des clés de chiffrement sera centralisée et sécurisée.

### 1.3. Journalisation et Traçabilité (Audit Logs)
*   **Journalisation Complète :**
    *   Tentatives d'authentification (réussies, échouées) avec adresse IP, timestamp.
    *   Accès aux modules et aux fonctionnalités clés.
    *   Opérations de création, modification, suppression de données importantes (ex: écritures comptables, dossiers de procédure, droits utilisateurs).
    *   Actions d'administration du système.
    *   Erreurs système et applicatives.
*   **Contenu des Logs :** Timestamp, ID utilisateur, action effectuée, ressource affectée, résultat de l'action, adresse IP source.
*   **Protection des Logs :**
    *   Inaltérabilité : les logs seront stockés de manière à empêcher leur modification ou suppression non autorisée (ex: écriture seule, envoi vers un système de centralisation des logs).
    *   Conservation : Durée de conservation définie selon les exigences légales et les besoins d'audit.
    *   Accès restreint : Seuls les administrateurs habilités pourront consulter les logs.
*   **Revue des Logs :** Processus de revue régulière des logs pour détecter les activités suspectes ou les anomalies. Alertes automatiques pour les événements critiques.

### 1.4. Sécurité Applicative
*   **Prévention des failles OWASP Top 10 :**
    *   Validation systématique des entrées utilisateurs (côté client et serveur) pour prévenir les injections (SQL, XSS, etc.).
    *   Utilisation de requêtes paramétrées / ORM pour l'accès aux bases de données.
    *   Protection contre CSRF (jetons anti-CSRF).
    *   Configuration correcte des en-têtes de sécurité HTTP (CSP, HSTS, X-Frame-Options, etc.).
*   **Mises à jour régulières :** Application des correctifs de sécurité pour le système d'exploitation, les serveurs web, les bases de données, les frameworks et les bibliothèques utilisées.
*   **Tests de Sécurité :**
    *   Scans de vulnérabilités automatisés réguliers.
    *   Tests d'intrusion (pentests) réalisés par des experts externes avant la mise en production majeure et périodiquement ensuite.
*   **Sécurité des API :** Toutes les API exposées (internes ou externes) seront sécurisées via la Plateforme d'Authentification (OAuth 2.0).

### 1.5. Sécurité de l'Infrastructure
*   **Hébergement Sécurisé :** Choix d'un hébergeur respectant les normes de sécurité reconnues (ex: ISO 27001, HDS si données de santé, etc.).
*   **Segmentation Réseau :** Isolation des différents environnements (développement, test, production) et des composants critiques (ex: base de données).
*   **Pare-feu :** Configuration stricte des pare-feu pour ne autoriser que les flux nécessaires.
*   **Protection Anti-DDoS.**
*   **Systèmes de Détection et de Prévention d'Intrusion (IDS/IPS).**

## 2. Interopérabilité

### 2.1. Principes Généraux
*   **Module Centralisé :** Le module "Interopérabilité" servira de hub pour la majorité des échanges de données avec les systèmes externes.
*   **Standardisation :** Utilisation de standards ouverts et reconnus chaque fois que possible (RESTful APIs avec JSON, XML, SFTP).
*   **Sécurité des Échanges :**
    *   Authentification mutuelle lorsque possible (ex: mTLS pour les API).
    *   Chiffrement des données en transit (TLS/HTTPS, SFTP).
    *   Signature des messages pour garantir l'intégrité et la non-répudiation (si nécessaire).
    *   Gestion sécurisée des clés API et des credentials pour l'accès aux systèmes externes (via un coffre-fort de secrets).
*   **Traçabilité :** Journalisation de tous les échanges de données (succès, échecs, volumes).
*   **Gouvernance des Données :** Définition claire des propriétaires de données, des formats, des fréquences d'échange et des responsabilités en cas d'incident pour chaque flux d'interopérabilité.

### 2.2. Interopérabilité avec Systèmes Externes Spécifiques
*   **DGCI (Direction Générale des Impôts et des Domaines) :**
    *   **Flux :** Récupération de données fiscales pour audit/contrôle.
    *   **Méthode :** API REST sécurisée (si disponible) ou transfert de fichiers SFTP chiffrés. Des formats structurés (XML, JSON) seront privilégiés.
*   **SIGRH (Système Intégré de Gestion des Ressources Humaines de l'État) :**
    *   **Flux :** Synchronisation des données des agents de la Cour (état civil, position administrative). Potentiellement, export des données de paie agrégées si la paie est gérée en externe.
    *   **Méthode :** API REST ou SOAP si disponible, sinon SFTP.
*   **SIDONIA (Système Douanier) / GAINDE (Plateforme de dématérialisation des formalités du commerce extérieur) :**
    *   **Flux :** Récupération de données sur les opérations douanières pour contrôle.
    *   **Méthode :** API ou SFTP, selon les capacités des systèmes sources.
*   **Systèmes Bancaires :**
    *   **Flux :** Confirmation de transactions, récupération de relevés pour la Gestion Financière interne de la Cour.
    *   **Méthode :** Protocoles spécifiques bancaires (Ebics si applicable en local) ou API sécurisées si les banques les proposent. SFTP pour les relevés.
*   **Autres Administrations :** Définition au cas par cas en fonction des besoins et des capacités des systèmes partenaires, en privilégiant toujours les API sécurisées.

### 2.3. Exposition de Services par SIGEF-TC (si applicable)
*   Si SIGEF-TC doit exposer des données à des tiers autorisés (ex: portail de données ouvertes pour des statistiques anonymisées), cela se fera via une API Gateway.
*   Les API exposées seront conformes aux principes RESTful, utiliseront JSON et seront sécurisées par la Plateforme d'Authentification (OAuth 2.0, clés API).
*   Une documentation claire (Swagger/OpenAPI) sera fournie pour chaque API exposée.

## 3. Conformité RGPD (et autres réglementations locales)
*   **Cartographie des Données Personnelles :** Identifier toutes les données personnelles traitées par SIGEF-TC, leur finalité, leur durée de conservation.
*   **Minimisation des Données :** Ne collecter et traiter que les données strictement nécessaires.
*   **Droits des Personnes :** Mettre en place des mécanismes pour permettre aux individus d'exercer leurs droits (accès, rectification, suppression, portabilité) si applicable.
*   **Privacy by Design & by Default :** Intégrer les principes de protection de la vie privée dès la conception des modules.
*   **Analyse d'Impact sur la Protection des Données (AIPD/PIA) :** Réaliser une AIPD pour les traitements susceptibles d'engendrer un risque élevé pour les droits et libertés des personnes.
*   **Sécurité des Données Personnelles :** Toutes les mesures de sécurité décrites dans ce plan contribuent à la conformité RGPD.
*   **Registre des Traitements :** Maintenir un registre des activités de traitement des données personnelles.
*   **Notification des Violations de Données :** Mettre en place une procédure pour détecter et notifier les violations de données à l'autorité de contrôle et aux personnes concernées, conformément à la réglementation.

## 4. Stratégies de Sauvegarde et de Continuité de Service (PCA/PRA)

### 4.1. Sauvegardes
*   **Périmètre :** Sauvegarde complète des bases de données, des fichiers de configuration, des logs importants, et des données stockées dans le module Gestion des Fichiers et la GND.
*   **Fréquence :**
    *   Sauvegardes complètes hebdomadaires.
    *   Sauvegardes incrémentielles ou différentielles quotidiennes.
    *   Sauvegarde des logs de transaction des bases de données en continu ou très fréquemment.
*   **Rétention :** Politiques de rétention adaptées aux besoins (ex: 30 jours pour les sauvegardes quotidiennes, plusieurs mois pour les hebdomadaires, archivage annuel).
*   **Stockage des Sauvegardes :**
    *   Sur un site distant géographiquement du site de production.
    *   Chiffrement des sauvegardes.
*   **Tests de Restauration :** Réaliser des tests de restauration réguliers pour s'assurer de la validité des sauvegardes et de la maîtrise du processus.

### 4.2. Plan de Continuité d'Activité (PCA) / Plan de Reprise d'Activité (PRA)
*   **Analyse des Besoins de Continuité (BIA) :** Identifier les processus critiques du SIGEF-TC et les RTO (Recovery Time Objective) / RPO (Recovery Point Objective) associés.
*   **Infrastructure de Secours :**
    *   Mise en place d'une infrastructure de secours (physique ou cloud) capable de prendre le relais en cas d'incident majeur sur le site principal.
    *   Réplication des données critiques vers le site de secours (synchrone ou asynchrone selon RPO).
*   **Procédures de Basculement et de Retour :** Documenter et tester les procédures de basculement vers le site de secours et de retour à la normale.
*   **Tests Réguliers :** Effectuer des exercices de PRA périodiques pour s'assurer de son efficacité et former les équipes.
*   **Communication de Crise :** Plan de communication en cas d'activation du PRA.

## Conclusion
La sécurité et l'interopérabilité sont des chantiers continus. Ce plan fournit une base solide qui devra être régulièrement revue, mise à jour et testée en fonction de l'évolution des menaces, des technologies et des besoins du SIGEF-TC. Une culture de la sécurité doit être promue au sein de toutes les équipes impliquées dans le projet.

---
Document préparé par : Primex Software
Rédigé par : Team Primex Software
URL : https://primex-software.com
Date : 2024-07-26
