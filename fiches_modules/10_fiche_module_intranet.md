# Fiche Module : Portail Intranet

## Nom du module (officiel)
Portail Intranet

## Objectif
Servir de point d'entrée unique et centralisé pour les agents de la Cour, donnant accès aux modules SIGEF-TC, informations internes, actualités, outils de collaboration et ressources utiles.

## Fonctionnalités
*   Authentification unique (SSO).
*   Tableau de bord personnalisable (widgets : notifications, tâches, actualités).
*   Accès centralisé (liens) aux modules SIGEF-TC.
*   Diffusion d'actualités et annonces internes (CMS).
*   Annuaire des employés (synchronisé avec RH).
*   Partage de documents d'intérêt général (non GND).
*   Espaces collaboratifs simples (forums, groupes - optionnel).
*   Calendrier d'événements internes.
*   Moteur de recherche global (intranet, et potentiellement fédéré GND/Bibliothèque).
*   Sondages rapides.

## Données en entrée
*   Contenu publié par les contributeurs (actualités, pages d'information).
*   Informations de l'annuaire (depuis RH).
*   Notifications et données synthétiques des autres modules (pour widgets).
*   Liens vers les modules SIGEF-TC.
*   Événements du calendrier.

## Données en sortie
*   Pages web de l'intranet (actualités, informations).
*   Résultats de recherche.
*   Notifications agrégées.
*   Affichage de l'annuaire.
*   Tableaux de bord personnalisés.

## Règles de gestion spécifiques
*   Politique éditoriale pour la publication de contenu.
*   Gestion des droits de publication et de consultation du contenu.
*   Règles de personnalisation du tableau de bord par rôle/utilisateur.
*   Fréquence de synchronisation de l'annuaire.

## UI/UX wireframe simplifié (si pertinent)
*   **Page d'accueil Intranet (connecté) :** Logo, barre de navigation (Actualités, Annuaire, Modules, Mon Espace), zone principale avec widgets configurables (Mes dernières notifications SIGEF-TC, Prochains événements, Actualités récentes de la Cour, Mes tâches en attente).
*   **Page Actualité :** Titre, date, auteur, contenu de l'article, commentaires (si activés).
*   **Page Annuaire :** Champ de recherche, liste des employés avec photo, nom, fonction, service, contact.

## Critères d’acceptation
*   Un agent peut se connecter à l'intranet via SSO.
*   La page d'accueil affiche des actualités récentes et des notifications pertinentes pour l'agent.
*   L'agent peut accéder au module RH en cliquant sur un lien depuis l'intranet.
*   Une recherche dans l'annuaire par nom retourne les bonnes informations de contact.
*   Un contributeur autorisé peut publier une nouvelle actualité.

## Points de vigilance
*   Qualité et pertinence du contenu publié (éviter que l'intranet devienne obsolète).
*   Performance du portail, surtout avec de nombreux widgets et appels API.
*   Complexité du moteur de recherche global s'il doit interroger plusieurs modules.
*   Intégration fluide avec le SSO et les autres modules pour l'agrégation d'informations.
*   Adoption par les utilisateurs comme point d'entrée principal.

## Technologies envisagées
*   **CMS/Backend :** Solution CMS (WordPress sécurisé, Drupal, Strapi/Directus + front dédié) ou développement sur mesure avec Node.js/Laravel.
*   **Frontend :** React.js ou Vue.js.
*   **Base de données :** PostgreSQL.
*   **API :** RESTful (pour consommer les données des autres modules et pour ses propres besoins si architecture découplée).
*   **Moteur de recherche :** Elasticsearch (si recherche fédérée).

---
Document préparé par : Primex Software
Rédigé par : Team Primex Software
URL : https://primex-software.com
Date : 2024-07-26
