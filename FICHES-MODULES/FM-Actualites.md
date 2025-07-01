```markdown
# Fiche Module : Actualités et Annonces

**Identifiant du Module :** M-ACTU
**Version :** 1.0
**Date de création :** 2023-10-27
**Auteur :** Jules AI – Agent IA Senior

## 1. Objectif

Le module "Actualités et Annonces" a pour objectif de permettre la création, la gestion, la diffusion et la consultation d'informations pertinentes (nouvelles de l'organisation, événements, communications officielles, etc.) à destination de l'ensemble des collaborateurs ou de groupes ciblés au sein de la Cour des Comptes. Il vise à remplacer ou compléter les canaux de communication traditionnels (emails, affichage papier) par un outil centralisé, dynamique et accessible.

## 2. Description Détaillée

Ce module permet aux utilisateurs habilités (Contributeurs, Éditeurs) de rédiger des articles informatifs, de les catégoriser, de définir leur audience et de les publier sur le portail intranet. Les collaborateurs peuvent ensuite consulter ces actualités via une page dédiée, des widgets sur leur tableau de bord, et recevoir des notifications pour les informations importantes.

Fonctionnalités clés :
*   Création et édition d'actualités via un éditeur de texte riche (WYSIWYG).
*   Ajout de médias (images, vidéos embarquées) et de pièces jointes.
*   Catégorisation des actualités (ex: Direction, RH, IT, Projets, Social).
*   Ciblage de la diffusion (tous les collaborateurs, par département, par rôle, par groupe spécifique).
*   Planification de la publication (date/heure de début) et de l'archivage/dépublication (date/heure de fin).
*   Marquage des actualités comme "Importantes" ou "Urgentes" pour une mise en évidence visuelle.
*   Gestion d'un workflow de publication simple (Brouillon -> Soumis pour relecture -> Publié -> Archivé) - optionnel, selon complexité souhaitée.
*   Système de commentaires sous les actualités (activable/désactivable par actualité, avec modération).
*   Affichage chronologique ou par pertinence des actualités.
*   Filtrage des actualités par catégorie, date, mots-clés.
*   Flux RSS des actualités.

## 3. Interfaces Utilisateur (Mockups Légers ou Wireframes - Description Textuelle)

### 3.1. Page Liste des Actualités (Vue Collaborateur)
*   **En-tête :** Titre "Actualités et Annonces".
*   **Zone de Filtres (latérale ou en haut) :**
    *   Liste déroulante "Catégories".
    *   Sélecteur de date (ex: "Ce mois-ci", "Mois dernier", "Plage de dates").
    *   Champ de recherche par mots-clés.
*   **Zone Principale :**
    *   Liste des actualités sous forme de "cartes" ou de lignes. Chaque actualité affiche :
        *   Titre (cliquable).
        *   Extrait du contenu ( premières lignes).
        *   Image principale (si présente).
        *   Catégorie.
        *   Date de publication.
        *   Auteur (optionnel).
        *   Indicateur "Important" / "Urgent" (si applicable).
    *   Pagination si le nombre d'actualités est important.
*   **Actions :**
    *   Lien vers le flux RSS.

### 3.2. Page Détail d'une Actualité (Vue Collaborateur)
*   **En-tête :** Titre de l'actualité.
*   **Informations Méta :** Catégorie, date de publication, auteur.
*   **Contenu Principal :** Corps de l'actualité (texte formaté, images, vidéos).
*   **Pièces Jointes :** Liste des fichiers attachés avec liens de téléchargement.
*   **Section Commentaires (si activée) :**
    *   Champ pour ajouter un nouveau commentaire.
    *   Liste des commentaires existants (avec nom de l'auteur, date, contenu).
*   **Actions :**
    *   Bouton "Retour à la liste".
    *   Options de partage (ex: par email, vers un espace collaboratif) - optionnel.

### 3.3. Interface de Création/Édition d'Actualité (Vue Contributeur/Éditeur)
*   **Formulaire :**
    *   Champ "Titre" (obligatoire).
    *   Éditeur WYSIWYG pour le "Contenu" (avec options de formatage, insertion d'images/liens/vidéos).
    *   Sélecteur de "Catégorie" (liste déroulante, obligatoire).
    *   Champ "Extrait" (pour la prévisualisation sur la liste).
    *   Option "Image principale" (upload).
    *   Option "Pièces jointes" (upload multiple).
    *   **Paramètres de Publication :**
        *   Sélecteur "Ciblage de l'audience" (ex: Tous, Département X, Rôle Y).
        *   Sélecteur de date/heure de "Début de publication".
        *   Sélecteur de date/heure de "Fin de publication".
        *   Case à cocher "Marquer comme Important/Urgent".
        *   Case à cocher "Activer les commentaires".
    *   **Workflow (si applicable) :**
        *   Boutons "Enregistrer comme brouillon", "Soumettre pour relecture", "Publier".
*   **Prévisualisation :** Option pour voir un aperçu de l'actualité avant publication.

### 3.4. Interface de Gestion des Actualités (Vue Éditeur/Admin)
*   **Tableau listant toutes les actualités avec colonnes :** Titre, Catégorie, Statut (Brouillon, Publié, Archivé), Date de publication, Auteur, Actions.
*   **Filtres :** Par statut, catégorie, auteur.
*   **Actions par actualité :** Modifier, Supprimer, Archiver, Publier/Dépublier.
*   **Actions globales :** "Créer une nouvelle actualité".

## 4. Règles de Gestion

*   RG-ACTU-001 : Un titre est obligatoire pour chaque actualité.
*   RG-ACTU-002 : Une catégorie est obligatoire pour chaque actualité.
*   RG-ACTU-003 : Seuls les utilisateurs avec le rôle "ContributeurActualites" ou "EditeurActualites" peuvent créer des actualités.
*   RG-ACTU-004 : Les "EditeurActualites" peuvent modifier/supprimer/publier/dépublier n'importe quelle actualité dans leurs catégories de responsabilité. Les "ContributeurActualites" ne peuvent modifier/supprimer que leurs propres brouillons ou actualités soumises.
*   RG-ACTU-005 : Une actualité n'est visible par les collaborateurs que si son statut est "Publié" et que la date actuelle est dans l'intervalle [Date de début de publication, Date de fin de publication].
*   RG-ACTU-006 : Les actualités marquées "Importantes/Urgentes" sont affichées de manière proéminente (ex: en haut de la liste, avec un style distinctif).
*   RG-ACTU-007 : Le ciblage d'audience restreint la visibilité d'une actualité aux utilisateurs appartenant aux groupes/départements/rôles spécifiés. Si aucun ciblage n'est spécifié, l'actualité est visible par tous.
*   RG-ACTU-008 : Les commentaires, s'ils sont activés, sont soumis à une politique de modération (a posteriori par défaut, ou a priori si requis).
*   RG-ACTU-009 : Les pièces jointes sont soumises à des restrictions de taille et de type de fichier (à définir).
*   RG-ACTU-010 : Les actualités archivées ne sont plus visibles sur la page principale des actualités mais restent accessibles via l'interface de gestion pour les administrateurs/éditeurs.

## 5. Dépendances Éventuelles

*   **Module Utilisateurs & Profils (M-USER) :** Pour l'identification de l'auteur et le ciblage d'audience.
*   **Module Notifications (M-NOTIF) :** Pour notifier les utilisateurs de nouvelles actualités importantes ou ciblées.
*   **Module Moteur de Recherche (M-SEARCH) :** Pour l'indexation et la recherche des actualités.
*   **Service de Stockage (GED ou stockage dédié) :** Pour les images et pièces jointes.
*   **Annuaire LDAP/AD :** Pour la résolution des groupes/départements lors du ciblage.

## 6. Données en Entrée/Sortie

### 6.1. Données en Entrée (pour la création/édition)
*   Titre (texte)
*   Contenu (HTML/texte riche)
*   ID Catégorie (référence)
*   Liste des ID Cibles (utilisateurs, groupes, rôles - références)
*   Date/heure de début de publication (datetime)
*   Date/heure de fin de publication (datetime)
*   Flag "Important/Urgent" (booléen)
*   Flag "Activer commentaires" (booléen)
*   Fichiers images (binaires)
*   Fichiers pièces jointes (binaires)
*   Statut (si workflow)

### 6.2. Données en Sortie (pour l'affichage)
*   ID Actualité
*   Titre
*   Contenu
*   Nom Catégorie
*   Date de publication
*   Nom Auteur
*   Liste des URLs/Noms des pièces jointes
*   Flag "Important/Urgent"
*   Liste des commentaires (ID Commentaire, Auteur Commentaire, Texte Commentaire, Date Commentaire)
*   URL image principale

### 6.3. Données Stockées (Persistance)
*   Table Actualites : id, titre, contenu, id_auteur, id_categorie, date_creation, date_publication, date_fin_publication, statut, flag_important, flag_commentaires_actives.
*   Table Actualites_Cibles : id_actualite, id_groupe_cible (ou type_cible, id_cible).
*   Table Actualites_PiecesJointes : id, id_actualite, nom_fichier, chemin_stockage, type_mime, taille.
*   Table Commentaires_Actualites : id, id_actualite, id_auteur_commentaire, texte, date_commentaire, statut_moderation.
    (Structure indicative, à affiner selon la base de données choisie)

---
*Document préparé par : Primex Software*
*Rédigé par : Jules AI – Agent IA Senior*
*Date : 2023-10-27*
*URL : https://primex-software.com*
```
