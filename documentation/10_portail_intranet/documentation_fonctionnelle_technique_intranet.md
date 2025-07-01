# Documentation Fonctionnelle & Technique : Portail Intranet

## Objectif du module

Le Portail Intranet SIGEF-TC a pour objectif de servir de point d'entrée unique et centralisé pour les agents de la Cour des Comptes, leur donnant accès aux différents modules du SIGEF-TC, à des informations internes, des actualités, des outils de collaboration et des ressources utiles à leur travail quotidien. Il vise à améliorer la communication interne et la productivité.

## Acteurs concernés

*   Tous les agents de la Cour des Comptes (utilisateurs principaux).
*   Service de communication interne / RH (contributeurs de contenu).
*   Administrateurs de l'intranet.

## Cas d’usage

*   **Page d'accueil personnalisée :** Affichage de widgets pertinents (notifications, tâches en attente, actualités, calendrier).
*   **Accès centralisé aux modules SIGEF-TC :** Liens directs vers les différents modules (RH, Financier, GND, E-Comptes, etc.).
*   **Diffusion d'actualités et d'annonces internes.**
*   **Annuaire des employés :** Recherche de contacts, informations de base.
*   **Partage de documents d'intérêt général** (non gérés par la GND, ex: manuels, procédures internes, chartes).
*   **Espaces collaboratifs simples** (forums de discussion, groupes de travail par projet/département - optionnel).
*   **Gestion de contenu (CMS) :** Publication d'articles, de pages d'information.
*   **Calendrier des événements internes.**
*   **Liens utiles** vers des ressources externes ou internes.
*   **Sondages et enquêtes rapides.**

## Fonctionnalités clés

*   **Authentification unique (SSO)** avec la Plateforme d’Authentification.
*   **Tableau de bord personnalisable** par l'utilisateur ou par rôle.
*   **Moteur de recherche global** (recherche dans l'intranet et potentiellement fédérée avec d'autres modules comme la GND ou la Bibliothèque Numérique).
*   **Système de gestion de contenu (CMS) intégré** pour la création et la gestion des pages et des actualités.
*   **Gestion des droits de publication et de consultation** du contenu.
*   **Annuaire du personnel intégré** (synchronisé avec le module RH).
*   **Notifications agrégées** provenant des différents modules SIGEF-TC.
*   **Design responsive** pour accès sur différents appareils.
*   **Gestion des widgets** sur la page d'accueil.
*   **Fonctionnalités de type "social" (optionnel) :** Commentaires sur les actualités, "j'aime".
*   **Intégration avec des outils de communication existants** (ex: messagerie instantanée, si pertinent).
*   **Multilinguisme (si nécessaire).**

## Interfaces attendues

*   **Interface utilisateur web principale** accessible via un navigateur.
*   **Interface d'administration du contenu** pour les contributeurs et administrateurs.
*   **API** pour récupérer des informations des autres modules (notifications, tâches) et pour le moteur de recherche global.

## Diagramme fonctionnel simplifié (UML si possible)

```mermaid
graph TD
    A[Agent Cour] -- S'authentifie (SSO) --> B(Portail Intranet);
    B -- Affiche Tableau de Bord Personnalisé --> A;
    B -- Fournit Accès aux Modules --> C[Modules SIGEF-TC (RH, GND, E-Comptes, etc.)];
    D[Service Communication/RH/Admin] -- Publie Contenu via CMS --> E[Base de Contenu Intranet (Actualités, Pages)];
    B -- Affiche Contenu de --> E;
    F[Moteur de Recherche Global] -- Indexe --> E;
    F -- Peut interroger (via API) --> C;
    B -- Utilise --> F;
    G[Module RH] -- Synchronise Données Annuaire --> H[Annuaire Intranet];
    B -- Affiche Données de --> H;
    I[Plateforme d'Authentification] -- Gère SSO --> B;
    J[API Gateway/Modules SIGEF-TC] -- Envoient Notifications/Données pour Widgets --> B;
```

## Contraintes techniques ou juridiques

*   **Sécurité des accès** et protection contre les accès non autorisés.
*   **Performance et disponibilité** du portail.
*   **Facilité d'utilisation et d'administration** du contenu.
*   **Intégration fluide avec la solution SSO.**
*   **Scalabilité** pour supporter tous les utilisateurs connectés.
*   **Respect de la charte graphique et de l'image de la Cour des Comptes.**

## Dépendances avec d’autres modules

*   **Plateforme d’Authentification et Gestion des Entités :** Essentielle pour le SSO et la gestion des profils utilisateurs qui peuvent influencer la personnalisation.
*   **Gestion des Ressources Humaines (RH) :** Pour l'annuaire du personnel et potentiellement pour la diffusion d'informations RH.
*   **Tous les modules applicatifs SIGEF-TC :** L'intranet sert de point d'accès et peut agréger des notifications ou des données synthétiques de ces modules.
*   **Gestion Numérique des Documents (GND) :** Le moteur de recherche de l'intranet pourrait étendre sa recherche à la GND. Des documents de la GND pourraient être mis en avant sur l'intranet.
*   **Bibliothèque Numérique :** Accès facilité via l'intranet.
*   **Application Mobile :** Peut afficher certaines actualités ou notifications de l'intranet.

## Spécifications API (si applicables)

L'intranet consommera principalement des API fournies par d'autres modules. Il pourrait exposer une API limitée pour :
*   Permettre à d'autres outils de publier des actualités (rare).
*   Fournir un flux RSS des actualités.
*   **API internes pour les composants front-end (si architecture découplée type SPA) :**
    *   `/intranet/api/news` : Gestion des actualités.
    *   `/intranet/api/pages` : Gestion des pages de contenu.
    *   `/intranet/api/widgets` : Configuration et données des widgets.
    *   `/intranet/api/search` : Endpoint pour le moteur de recherche.
    *   `/intranet/api/notifications` : Agrégation des notifications.
*   **Authentification via le SSO existant (transmission de jeton).**
*   **Formats de données :** JSON.

**Technologies possibles pour le CMS :**
*   Solutions open-source éprouvées (ex: WordPress avec sécurisation renforcée, Drupal, Joomla) si les fonctionnalités correspondent et que l'intégration SSO est possible.
*   Framework CMS headless (ex: Strapi, Directus) si une approche découplée est préférée, avec un front-end sur mesure (React, Vue.js).
*   Développement sur mesure basé sur le framework backend principal (Node.js/Express, Laravel) si les besoins sont très spécifiques et que les solutions existantes ne conviennent pas.

---
Document préparé par : Primex Software
Rédigé par : Team Primex Software
URL : https://primex-software.com
Date : 2024-07-26
