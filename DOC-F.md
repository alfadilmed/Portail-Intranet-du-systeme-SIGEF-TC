```markdown
# Documentation Fonctionnelle (DOC-F) - Portail Intranet SIGEF-TC

## 1. Introduction

Cette documentation fonctionnelle décrit les modules, les fonctionnalités, les interactions utilisateurs et les règles de gestion du Portail Intranet SIGEF-TC. Elle sert de référence pour l'équipe de développement, les testeurs et le comité de pilotage.

## 2. Détail des Modules

### 2.1. Tableau de Bord Personnalisé
*   **Objectif :** Fournir une page d'accueil centralisée et personnalisable, offrant un aperçu des informations les plus pertinentes pour l'utilisateur connecté.
*   **Fonctionnalités :**
    *   Affichage de widgets configurables par l'utilisateur (glisser-déposer).
    *   Widgets disponibles : Mes dernières actualités, Mes tâches, Prochains événements du calendrier, Documents récents, Notifications non lues, Liens rapides.
    *   Possibilité pour l'administrateur de définir des widgets par défaut par rôle.
    *   Mise en page responsive.

### 2.2. Actualités et Annonces
*   **Objectif :** Diffuser les informations officielles, les nouvelles de l'organisation et les événements importants à l'ensemble des collaborateurs ou à des groupes ciblés.
*   **Fonctionnalités :**
    *   Création d'actualités avec un éditeur de texte riche (WYSIWYG).
    *   Possibilité d'ajouter des images, vidéos, et pièces jointes.
    *   Catégorisation des actualités (ex: Direction, RH, IT, Projets).
    *   Ciblage de la diffusion par département, rôle ou groupe d'utilisateurs.
    *   Gestion des dates de publication et d'expiration.
    *   Système de commentaires (activable par actualité).
    *   Marquage des actualités importantes/urgentes.
    *   Flux RSS des actualités.

### 2.3. Calendrier Partagé
*   **Objectif :** Permettre la gestion et la visualisation des événements, réunions, et échéances pour l'ensemble de l'organisation ou pour des équipes spécifiques.
*   **Fonctionnalités :**
    *   Affichage mensuel, hebdomadaire, journalier.
    *   Création d'événements avec titre, description, date/heure de début et fin, lieu.
    *   Invitation de participants (individus ou groupes).
    *   Gestion des rappels et notifications.
    *   Possibilité de créer des calendriers multiples (ex: Calendrier Général, Calendrier RH, Calendrier Projet X).
    *   Superposition de calendriers.
    *   Gestion des événements récurrents.
    *   Intégration possible avec des calendriers externes (ex: via iCal).

### 2.4. Forums de Discussion
*   **Objectif :** Créer des espaces d'échange thématiques pour faciliter la collaboration, le partage de connaissances et la résolution de problèmes.
*   **Fonctionnalités :**
    *   Création de catégories de forums et de forums.
    *   Création de sujets de discussion (posts) avec un éditeur de texte riche.
    *   Réponse aux sujets et aux messages.
    *   Système de modération (par les administrateurs de forum).
    *   Abonnement aux forums ou sujets pour recevoir des notifications.
    *   Recherche dans les forums.
    *   Marquage des sujets comme résolus.

### 2.5. Gestion Électronique de Documents (GED)
*   **Objectif :** Fournir un système centralisé pour stocker, organiser, rechercher, partager et gérer les versions des documents de l'organisation.
*   **Fonctionnalités :**
    *   Structure de dossiers et sous-dossiers.
    *   Upload de fichiers (divers formats supportés : PDF, Docx, Xlsx, Pptx, images, etc.).
    *   Gestion des versions des documents (versioning).
    *   Attribution de métadonnées aux documents (auteur, date, mots-clés, catégorie).
    *   Contrôle d'accès fin par dossier et par document (lecture, écriture, suppression, partage).
    *   Fonction de check-in / check-out pour éviter les conflits d'édition.
    *   Moteur de recherche puissant (recherche full-text et par métadonnées).
    *   Corbeille pour les documents supprimés (avec restauration possible).
    *   Prévisualisation de certains types de documents directement dans le navigateur.
    *   Workflow de validation de documents (optionnel).

### 2.6. Annuaire des Collaborateurs et Profils Utilisateurs
*   **Objectif :** Faciliter la recherche et la prise de contact avec les collaborateurs, et permettre à chacun de gérer son profil.
*   **Fonctionnalités :**
    *   Liste des collaborateurs avec recherche par nom, prénom, département, poste, compétences.
    *   Fiche profil détaillée : photo, nom, prénom, poste, département, responsable hiérarchique, coordonnées (téléphone, email), compétences, projets en cours, biographie courte.
    *   Synchronisation des informations de base depuis l'annuaire LDAP/AD.
    *   Possibilité pour l'utilisateur de modifier certaines informations de son profil (photo, biographie, compétences).
    *   Organigramme navigable (optionnel).

### 2.7. Moteur de Recherche Global
*   **Objectif :** Permettre une recherche transversale et efficace sur l'ensemble des contenus du portail.
*   **Fonctionnalités :**
    *   Champ de recherche unique accessible depuis toutes les pages.
    *   Indexation des actualités, pages de contenu, documents de la GED, messages des forums, profils utilisateurs.
    *   Filtrage des résultats par type de contenu, date, auteur, catégorie.
    *   Pertinence des résultats (algorithme de scoring).
    *   Suggestions de recherche (auto-complétion).

### 2.8. Notifications
*   **Objectif :** Informer les utilisateurs des événements importants et des actions requérant leur attention.
*   **Fonctionnalités :**
    *   Centre de notifications accessible depuis l'en-tête du portail.
    *   Notifications en temps réel (push si possible) et par email (configurable par l'utilisateur).
    *   Types de notifications : nouvelle actualité ciblée, invitation à un événement, nouveau message dans un forum suivi, mention dans une discussion, tâche assignée, document partagé, etc.
    *   Marquage des notifications comme lues/non lues.
    *   Paramètres de notification personnalisables par l'utilisateur.

### 2.9. Espaces Collaboratifs
*   **Objectif :** Fournir des environnements de travail dédiés à des projets, des équipes ou des groupes d'intérêt.
*   **Fonctionnalités (par espace) :**
    *   Membres de l'espace (avec rôles spécifiques à l'espace).
    *   Module d'actualités/annonces spécifique à l'espace.
    *   Module de calendrier spécifique à l'espace.
    *   Module de discussion/forum spécifique à l'espace.
    *   Module de gestion de documents spécifique à l'espace (sous-ensemble de la GED principale ou GED dédiée).
    *   Outil de gestion de tâches simple (liste de tâches, assignation, statut, échéance).
    *   Wiki simple pour la documentation collaborative.
    *   Paramétrage de la visibilité de l'espace (public, privé sur invitation, restreint).

## 3. Diagramme des Cas d’Usage (UML)

*(Représentation textuelle simplifiée. Un diagramme graphique sera produit avec un outil UML dédié.)*

**Acteurs principaux :**
*   Collaborateur (Utilisateur Standard)
*   Contributeur (Utilisateur pouvant publier du contenu)
*   Modérateur (Utilisateur gérant les forums/contenus)
*   Administrateur du Portail

**Cas d'usage principaux pour le Collaborateur :**
*   Se connecter / Se déconnecter
*   Consulter son tableau de bord
*   Lire les actualités et annonces
*   Consulter le calendrier
*   Participer aux forums (lire, répondre)
*   Rechercher des documents dans la GED
*   Consulter l'annuaire des collaborateurs
*   Rechercher des informations (moteur global)
*   Gérer ses notifications
*   Consulter/Participer à un espace collaboratif
*   Modifier son profil (informations autorisées)

**Cas d'usage principaux pour le Contributeur (en plus de ceux du Collaborateur) :**
*   Créer/Modifier une actualité
*   Créer/Modifier un événement au calendrier (si droits)
*   Créer un sujet de forum
*   Uploader/Modifier un document dans la GED (si droits)
*   Créer/Gérer un espace collaboratif (si créateur)

**Cas d'usage principaux pour le Modérateur (en plus de ceux du Contributeur) :**
*   Modérer les messages des forums
*   Gérer les contenus signalés
*   Valider/Rejeter des actualités (si workflow)

**Cas d'usage principaux pour l'Administrateur du Portail :**
*   Gérer les utilisateurs et les rôles
*   Configurer les modules du portail
*   Gérer les catégories d'actualités et de forums
*   Gérer la structure de la GED (dossiers racine)
*   Paramétrer les aspects globaux du portail (logo, thèmes)
*   Consulter les logs d'audit
*   Gérer les sauvegardes (via interface ou scripts)

## 4. Diagrammes de Navigation (UX Wireflows)

*(Description textuelle des flux de navigation principaux. Des wireframes détaillés seront produits lors de la phase de conception UX/UI.)*

**Flux 1 : Consultation d'une actualité**
1.  Page d'accueil (Tableau de Bord) -> Clic sur widget "Dernières Actualités" OU Menu "Actualités"
2.  Page Liste des Actualités (avec filtres et pagination) -> Clic sur le titre d'une actualité
3.  Page Détail de l'Actualité (contenu, auteur, date, commentaires)

**Flux 2 : Ajout d'un document à la GED**
1.  Menu "GED" -> Navigation dans l'arborescence des dossiers
2.  Page Dossier Spécifique -> Clic sur bouton "Ajouter un document"
3.  Formulaire d'upload (sélection fichier, saisie métadonnées) -> Clic sur "Valider"
4.  Retour Page Dossier Spécifique (avec document visible)

**Flux 3 : Recherche d'un collaborateur**
1.  Menu "Annuaire" OU Champ de recherche global
2.  Page Annuaire (avec filtres) -> Saisie nom/prénom/critère -> Clic sur "Rechercher" OU Sélection dans la liste
3.  Page de résultats de recherche de l'annuaire -> Clic sur un nom
4.  Page Profil du Collaborateur

**Flux 4 : Participation à un forum**
1.  Menu "Forums" -> Page Liste des Catégories de Forums
2.  Clic sur une Catégorie -> Page Liste des Forums de la catégorie
3.  Clic sur un Forum -> Page Liste des Sujets du forum
4.  Clic sur un Sujet -> Page de discussion du Sujet
5.  Champ "Répondre" -> Saisie message -> Clic "Envoyer"

## 5. Gestion des Rôles & Droits

Un système de Rôles et Permissions (RBAC - Role-Based Access Control) sera implémenté.

**Rôles types (liste non exhaustive, à affiner) :**
*   **Utilisateur Standard (Collaborateur) :**
    *   Droits de lecture sur la majorité des contenus (actualités, calendrier général, forums publics, GED publique).
    *   Peut modifier son propre profil (partiellement).
    *   Peut participer aux forums (poster des réponses).
*   **Contributeur Actualités :**
    *   Peut créer, modifier, soumettre à publication ses propres actualités.
*   **Éditeur Actualités :**
    *   Peut publier/dépublier, modifier toutes les actualités dans ses catégories.
*   **Gestionnaire Calendrier :**
    *   Peut créer/modifier des événements dans les calendriers dont il a la charge.
*   **Modérateur Forum :**
    *   Peut modérer les messages, sujets, et utilisateurs dans les forums assignés.
*   **Gestionnaire GED (par dossier/espace) :**
    *   Peut gérer les droits d'accès, uploader, modifier, supprimer des documents dans les zones de la GED qui lui sont attribuées.
*   **Créateur d'Espace Collaboratif :**
    *   Peut créer un espace, inviter des membres, configurer les outils de l'espace.
    *   Administrateur de son propre espace.
*   **Administrateur Technique :**
    *   Accès complet à la configuration technique du portail, gestion des utilisateurs, rôles globaux, logs, maintenance. Ne gère pas le contenu fonctionnel par défaut.
*   **Super Administrateur (Fonctionnel) :**
    *   Accès à toutes les fonctionnalités d'administration fonctionnelle, y compris la gestion de contenu global, la configuration des modules, etc.

**Permissions granulaires :**
Chaque action significative dans le système sera associée à une permission (ex: `actualite.creer`, `document.telecharger`, `forum.repondre`, `utilisateur.modifier_profil`). Les rôles seront des ensembles de permissions.

## 6. Parcours Utilisateurs Types (Scénarios)

**Scénario 1 : Un nouveau collaborateur, Jean Dupont, rejoint l'organisation.**
1.  **RH/Admin IT :** Crée le compte de Jean dans l'AD/LDAP. Le portail synchronise le compte. L'admin du portail assigne le rôle "Collaborateur" à Jean.
2.  **Jean :** Reçoit ses identifiants.
3.  **Jean :** Se connecte pour la première fois au portail.
4.  **Jean :** Atterrit sur le Tableau de Bord (avec widgets par défaut).
5.  **Jean :** Explore le menu "Actualités" et lit les dernières nouvelles de l'entreprise.
6.  **Jean :** Consulte le module "Annuaire" pour trouver ses collègues de département. Il clique sur le profil de sa responsable, Marie Durand, pour voir ses informations de contact.
7.  **Jean :** Modifie son propre profil pour ajouter une photo et quelques compétences.
8.  **Jean :** Reçoit une notification pour un événement "Réunion d'intégration" dans son calendrier.

**Scénario 2 : Sophie Martin, Chef de Projet, veut partager un document important avec son équipe.**
1.  **Sophie :** Se connecte au portail. Elle a le rôle "Créateur d'Espace Collaboratif" et "Gestionnaire GED" pour son projet.
2.  **Sophie :** Navigue vers l'Espace Collaboratif de son "Projet Alpha".
3.  **Sophie :** Ouvre le module "Documents" de l'espace.
4.  **Sophie :** Clique sur "Ajouter un document", uploade le "Cahier des Charges v2.pdf".
5.  **Sophie :** Ajoute des métadonnées : version "2.0", statut "Validé".
6.  **Sophie :** Vérifie que les droits d'accès pour les membres de son équipe sont corrects (lecture seule pour certains, écriture pour d'autres).
7.  **Sophie :** Publie une annonce dans le module "Actualités" de l'espace projet pour informer l'équipe de la disponibilité du document, avec un lien direct vers celui-ci.
8.  **Membres de l'équipe :** Reçoivent une notification. Ils peuvent accéder et consulter le document.

**Scénario 3 : Paul Lefevre, du service Communication, doit publier une annonce urgente.**
1.  **Paul :** Se connecte au portail. Il a le rôle "Éditeur Actualités".
2.  **Paul :** Navigue vers le module "Actualités" (section administration).
3.  **Paul :** Clique sur "Créer une nouvelle actualité".
4.  **Paul :** Rédige le titre et le contenu de l'annonce urgente, y insère une image.
5.  **Paul :** Coche l'option "Actualité Importante/Urgente" pour qu'elle apparaisse en évidence.
6.  **Paul :** Cible la diffusion à "Tous les collaborateurs".
7.  **Paul :** Publie l'actualité immédiatement.
8.  **Collaborateurs :** Voient l'actualité urgente sur leur tableau de bord et/ou reçoivent une notification.

---
*Document préparé par : Primex Software*
*Rédigé par : Jules AI – Agent IA Senior*
*Date : 2023-10-27*
*URL : https://primex-software.com*
```
