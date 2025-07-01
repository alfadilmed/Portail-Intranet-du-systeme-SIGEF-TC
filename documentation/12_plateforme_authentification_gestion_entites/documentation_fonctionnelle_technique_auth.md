# Documentation Fonctionnelle & Technique : Plateforme d’Authentification et Gestion des Entités

## Objectif du module

Ce module est une composante transversale et critique du SIGEF-TC. Son objectif est double :
1.  **Authentification :** Fournir un service centralisé et sécurisé d'authentification unique (Single Sign-On, SSO) pour tous les utilisateurs (agents de la Cour, et potentiellement usagers externes) accédant aux différents modules du SIGEF-TC. Gérer les identités numériques.
2.  **Gestion des Entités et Habilitations :** Gérer les profils utilisateurs, les rôles, les groupes et les permissions (habilitations) qui déterminent les accès et les droits des utilisateurs sur les différents modules et leurs fonctionnalités/données. Il ne s'agit pas ici des "entités contrôlées" (qui sont dans le module "Gestion des Entités et Plaintes") mais des entités utilisateurs du système SIGEF-TC lui-même (personnes, rôles, groupes).

## Acteurs concernés

*   **Tous les utilisateurs du SIGEF-TC** (agents internes, usagers externes le cas échéant).
*   **Administrateurs de sécurité / Administrateurs du SIGEF-TC** (pour la gestion des utilisateurs, rôles, permissions).
*   **Développeurs des autres modules SIGEF-TC** (qui intégreront leurs modules avec cette plateforme).

## Cas d’usage

**Authentification :**
*   Connexion unique (SSO) des agents de la Cour à l'ensemble des modules SIGEF-TC.
*   Authentification des usagers externes pour l'accès aux portails dédiés (ex: soumission de plainte, portail justiciable E-Comptes).
*   Gestion des mots de passe (politiques de complexité, renouvellement, récupération).
*   Authentification multi-facteurs (MFA/2FA) pour renforcer la sécurité, notamment pour les accès sensibles.
*   Gestion des sessions utilisateurs.
*   Déconnexion unique (Single Log-Out, SLO).

**Gestion des Entités (Utilisateurs/Rôles/Permissions) :**
*   Création, modification, suppression des comptes utilisateurs.
*   Définition et gestion des rôles (ex: "Magistrat", "Greffier", "Agent RH", "Comptable").
*   Assignation des utilisateurs à des rôles et/ou des groupes.
*   Définition des permissions granulaires associées aux rôles ou directement aux utilisateurs pour chaque module (ex: "peut créer facture", "peut lire dossier X", "peut valider congé").
*   Audit des changements de droits et d'accès.
*   Synchronisation avec un annuaire d'entreprise existant (ex: LDAP, Active Directory) si applicable.

## Fonctionnalités clés

**Authentification :**
*   Support des protocoles standards d'authentification et d'autorisation (OAuth 2.0, OpenID Connect).
*   Interface de connexion unique.
*   Politiques de mot de passe configurables.
*   Support MFA (TOTP, SMS, email, FIDO U2F/WebAuthn).
*   Gestion des jetons (JWT).
*   Journalisation des tentatives d'accès (réussies et échouées).
*   Verrouillage de compte après tentatives échouées.

**Gestion des Entités (Utilisateurs/Rôles/Permissions) :**
*   Interface d'administration centralisée pour la gestion des utilisateurs, rôles et permissions.
*   Modèle de contrôle d'accès basé sur les rôles (RBAC) extensible.
*   Possibilité de définir des permissions basées sur les attributs (ABAC) pour des scénarios plus complexes (optionnel).
*   Hiérarchie des rôles (optionnel).
*   Gestion des groupes d'utilisateurs.
*   API sécurisée pour que les modules puissent vérifier les permissions.
*   Historique des affectations de rôles et permissions.

## Interfaces attendues

*   **Interface de connexion web unique** pour les utilisateurs.
*   **Interface d'administration web** pour les administrateurs de sécurité.
*   **API RESTful/GraphQL** pour l'intégration avec les autres modules SIGEF-TC :
    *   Pour rediriger vers la page de connexion (flux OAuth2/OIDC).
    *   Pour valider les jetons d'accès.
    *   Pour obtenir les informations de profil utilisateur.
    *   Pour vérifier les permissions d'un utilisateur sur une ressource ou une action spécifique.

## Diagramme fonctionnel simplifié (UML si possible)

```mermaid
graph TD
    A[Utilisateur] -- Tente d'accéder à --> M[Module Applicatif SIGEF-TC];
    M -- Redirige pour authentification --> AUTH_UI[Interface de Connexion (Plateforme Auth)];
    A -- Saisit identifiants --> AUTH_UI;
    AUTH_UI -- Vérifie identifiants/MFA --> IDP[Identity Provider (Coeur Plateforme Auth)];
    IDP -- Génère Jetons (Accès, ID) --> A;
    A -- Présente Jeton d'Accès --> M;
    M -- Valide Jeton (via API Plateforme Auth) --> IDP;
    IDP -- Confirme validité --> M;
    M -- Vérifie Permissions (via API Plateforme Auth) --> PERM[Service de Permissions (Plateforme Auth)];
    PERM -- Retourne Droits --> M;
    M -- Accorde/Refuse Accès --> A;

    ADMIN[Admin Sécurité] -- Gère Utilisateurs/Rôles/Permissions --> ADMIN_UI[Interface d'Admin (Plateforme Auth)];
    ADMIN_UI -- Met à jour --> IDP_DB[Base de Données Utilisateurs/Rôles];
    ADMIN_UI -- Met à jour --> PERM_DB[Base de Données Permissions];
    IDP -- Lit --> IDP_DB;
    PERM -- Lit --> PERM_DB;
```

## Contraintes techniques ou juridiques

*   **Sécurité maximale :** Ce module est la pierre angulaire de la sécurité du SIGEF-TC. Doit être protégé contre les attaques courantes (injection SQL, XSS, CSRF, credential stuffing, etc.).
*   **Haute disponibilité :** Une panne de ce module rendrait l'ensemble du SIGEF-TC inaccessible.
*   **Performance :** Les processus d'authentification et de vérification des permissions doivent être rapides pour ne pas impacter l'expérience utilisateur.
*   **Scalabilité :** Doit pouvoir gérer tous les utilisateurs du système.
*   **Conformité aux réglementations sur la protection des données personnelles** (gestion des identités).
*   **Utilisation de chiffrements robustes** pour les mots de passe et les données sensibles.
*   **Auditabilité complète** des actions d'administration et des événements d'authentification.

## Dépendances avec d’autres modules

*   **Tous les modules du SIGEF-TC** dépendent de cette plateforme pour l'authentification de leurs utilisateurs et la vérification de leurs droits d'accès. Chaque module devra intégrer un client OAuth2/OIDC et appeler les API de cette plateforme pour la gestion des permissions.
*   **Peut s'interfacer avec un annuaire d'entreprise existant (LDAP/AD)** pour provisionner les utilisateurs internes.

## Spécifications API (si applicables)

Basé sur **OAuth 2.0** et **OpenID Connect (OIDC)** :
*   **Endpoints OIDC standard :**
    *   `/oauth2/authorize` : Pour initier le flux d'authentification.
    *   `/oauth2/token` : Pour échanger un code d'autorisation contre des jetons.
    *   `/oauth2/userinfo` : Pour obtenir les informations du profil utilisateur.
    *   `/oauth2/jwks` : Pour fournir les clés publiques de signature des jetons.
    *   `/oauth2/revoke` : Pour révoquer des jetons.
    *   `/oauth2/logout` : Pour la déconnexion.
*   **API de gestion des permissions (interne aux modules) :**
    *   `/api/permissions/check` : Pour vérifier si un utilisateur (identifié par son jeton) a une permission spécifique sur une ressource.
    *   `/api/users/{userId}/permissions` : Pour lister les permissions d'un utilisateur.
*   **API d'administration (pour l'interface d'admin ou des scripts) :**
    *   `/api/admin/users` : CRUD pour les utilisateurs.
    *   `/api/admin/roles` : CRUD pour les rôles.
    *   `/api/admin/permissions` : CRUD pour les permissions.
    *   `/api/admin/users/{userId}/roles` : Assignation des rôles aux utilisateurs.
*   **Formats de données :** JSON.
*   **Jetons :** JWT (JSON Web Tokens).

**Technologies recommandées :**
*   Des solutions open-source robustes et éprouvées comme Keycloak, IdentityServer, ou des services cloud (AWS Cognito, Azure AD B2C, Auth0) peuvent être envisagées pour accélérer le développement et bénéficier de fonctionnalités de sécurité avancées. Si un développement sur mesure est choisi, il doit être basé sur des bibliothèques de sécurité auditées.

---
Document préparé par : Primex Software
Rédigé par : Team Primex Software
URL : https://primex-software.com
Date : 2024-07-26
