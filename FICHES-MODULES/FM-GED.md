```markdown
# Fiche Module : Gestion Électronique de Documents (GED)

**Identifiant du Module :** M-GED
**Version :** 1.0
**Date de création :** 2023-10-27
**Auteur :** Jules AI – Agent IA Senior

## 1. Objectif

Le module "Gestion Électronique de Documents (GED)" a pour objectif de fournir un système centralisé, sécurisé et efficace pour le stockage, l'organisation, le versioning, le partage et la recherche de documents au sein de la Cour des Comptes. Il vise à faciliter l'accès à l'information, à améliorer la collaboration autour des documents et à assurer la traçabilité et la pérennité du patrimoine documentaire de l'institution.

## 2. Description Détaillée

Ce module permet aux utilisateurs de naviguer dans une arborescence de dossiers, d'uploader des fichiers, de gérer leurs versions, d'attribuer des métadonnées, de contrôler les accès et de rechercher des documents par leur contenu ou leurs propriétés.

Fonctionnalités clés :
*   **Arborescence de dossiers et sous-dossiers :** Organisation hiérarchique des documents.
*   **Upload de fichiers :** Prise en charge de multiples formats de fichiers (PDF, DOCX, XLSX, PPTX, ODT, ODS, ODP, TXT, images JPG/PNG, etc.). Limites de taille configurables.
*   **Gestion des versions (Versioning) :**
    *   Archivage automatique des versions précédentes lors de la modification ou du remplacement d'un fichier.
    *   Possibilité de consulter, restaurer ou télécharger les versions antérieures.
    *   Commentaires de version.
*   **Métadonnées :**
    *   Métadonnées système (nom du fichier, taille, type, date de création/modification, auteur de l'upload).
    *   Métadonnées personnalisables (ex: catégorie, mots-clés, statut du document, date d'expiration, service responsable). Champs de métadonnées configurables par type de document ou par dossier.
*   **Contrôle d'accès granulaire :**
    *   Permissions par dossier et/ou par document.
    *   Permissions types : Lecture, Téléchargement, Contribution (ajout/modification de documents), Gestion des permissions (pour les propriétaires de dossiers/documents).
    *   Attribution des permissions à des utilisateurs individuels ou à des groupes. Héritage des permissions.
*   **Fonction de Check-in / Check-out :** Verrouillage d'un document pour modification afin d'éviter les conflits d'édition simultanée.
*   **Moteur de recherche puissant :**
    *   Recherche full-text dans le contenu des documents (pour les formats indexables comme PDF, DOCX, TXT).
    *   Recherche par métadonnées (nom, auteur, date, catégorie, mots-clés, etc.).
    *   Filtres de recherche avancée.
*   **Corbeille :** Les documents supprimés sont déplacés vers une corbeille avec possibilité de restauration par les utilisateurs autorisés (ou vidage définitif).
*   **Prévisualisation :** Affichage d'aperçus de certains types de documents (PDF, images, documents Office via conversion) directement dans le navigateur.
*   **Partage de documents/dossiers :**
    *   Partage interne avec d'autres utilisateurs/groupes du portail.
    *   Partage externe sécurisé via lien (avec mot de passe et date d'expiration) - optionnel et soumis à politique de sécurité stricte.
*   **Workflows de validation (optionnel, plus complexe) :** Possibilité de soumettre des documents à un circuit d'approbation.
*   **Audit Trail :** Journalisation des actions importantes (upload, téléchargement, modification, suppression, changement de permissions).

## 3. Interfaces Utilisateur (Mockups Légers ou Wireframes - Description Textuelle)

### 3.1. Vue Principale de la GED (Explorateur de fichiers)
*   **En-tête :** Titre "Gestion des Documents". Chemin de navigation (Breadcrumb) indiquant le dossier courant. Champ de recherche rapide dans le dossier courant. Bouton "Uploader un fichier", "Créer un dossier".
*   **Panneau Latéral Gauche (optionnel) :**
    *   Arborescence des dossiers principaux (favoris, mes documents, partagés avec moi, dossiers d'équipe).
    *   Filtres rapides (par type de fichier, date de modification).
*   **Zone Centrale :**
    *   Liste des dossiers et fichiers du répertoire courant (affichage en liste ou en icônes).
    *   Pour chaque item : Icône de type, Nom, Date de modification, Taille, Auteur.
    *   Actions contextuelles (clic droit ou icône "...") : Ouvrir/Prévisualiser, Télécharger, Modifier (check-out), Gérer les versions, Modifier les métadonnées, Partager, Déplacer, Renommer, Supprimer, Gérer les permissions.
*   **Barre d'informations (en bas ou latérale droite si un item est sélectionné) :**
    *   Aperçu (si disponible), Métadonnées principales, Versions, Activité récente.

### 3.2. Fenêtre Modale/Page d'Upload de Fichiers
*   Zone de glisser-déposer (Drag & Drop) ou bouton "Sélectionner des fichiers".
*   Liste des fichiers en cours d'upload avec barre de progression.
*   Options pour chaque fichier (ou pour le lot) :
    *   Ajouter des commentaires de version (pour les nouvelles versions).
    *   Attribuer des métadonnées initiales (si champs communs).
*   Bouton "Démarrer l'upload".

### 3.3. Fenêtre Modale/Page des Propriétés/Métadonnées d'un Document
*   **Onglets :** Général, Versions, Permissions, Activité.
*   **Onglet Général :**
    *   Nom du fichier (modifiable si droits).
    *   Champs de métadonnées système (non modifiables).
    *   Champs de métadonnées personnalisés (modifiables si droits).
    *   Bouton "Enregistrer les modifications".
*   **Onglet Versions :**
    *   Liste des versions avec numéro, date, auteur, commentaire.
    *   Actions par version : Prévisualiser, Télécharger, Restaurer cette version (crée une nouvelle version basée sur l'ancienne).
    *   Bouton "Uploader une nouvelle version".
*   **Onglet Permissions :**
    *   Liste des utilisateurs/groupes ayant accès, avec leurs niveaux de permission.
    *   Boutons "Ajouter un utilisateur/groupe", "Modifier la permission", "Retirer l'accès".
*   **Onglet Activité :** Journal des actions sur le document.

### 3.4. Fenêtre Modale de Check-in / Check-out
*   **Check-out :** Bouton "Réserver et télécharger" ou "Réserver". Indique que le document est verrouillé par l'utilisateur.
*   **Check-in :** Formulaire pour uploader la nouvelle version du document réservé. Champ pour commentaire de version. Bouton "Enregistrer et libérer". Option "Annuler la réservation".

### 3.5. Page de Recherche Avancée
*   Champs de recherche : Mots-clés (contenu), Titre, Auteur, Type de fichier, Plage de dates, Catégorie, autres métadonnées personnalisées.
*   Bouton "Rechercher".
*   Affichage des résultats similaire à l'explorateur de fichiers, avec pertinence et extraits.

## 4. Règles de Gestion

*   RG-GED-001 : La structure des dossiers racine est définie par les administrateurs. Les utilisateurs peuvent créer des sous-dossiers selon leurs droits.
*   RG-GED-002 : L'upload de fichiers est soumis à des quotas de taille par fichier et potentiellement par utilisateur/dossier.
*   RG-GED-003 : Les types de fichiers autorisés sont définis par une liste blanche.
*   RG-GED-004 : Lors de l'upload d'un fichier avec un nom existant dans le même dossier, le système propose de créer une nouvelle version ou de renommer.
*   RG-GED-005 : Le check-out d'un document le verrouille en écriture pour les autres utilisateurs. Seul l'utilisateur ayant fait le check-out ou un administrateur peut le libérer.
*   RG-GED-006 : La suppression d'un document le déplace vers la corbeille. La durée de rétention dans la corbeille est configurable.
*   RG-GED-007 : Les permissions sont héritées des dossiers parents par défaut, mais peuvent être surchargées au niveau d'un sous-dossier ou d'un fichier.
*   RG-GED-008 : La recherche full-text n'est disponible que pour les formats de fichiers pris en charge par le moteur d'indexation.
*   RG-GED-009 : Les métadonnées obligatoires (si définies pour un type de document/dossier) doivent être renseignées avant de finaliser l'upload ou la modification.
*   RG-GED-010 : L'accès aux versions antérieures est soumis aux mêmes droits que l'accès à la version courante du document.
*   RG-GED-011 : Le partage externe (si activé) doit imposer des mesures de sécurité (mot de passe, expiration, journalisation des accès).

## 5. Dépendances Éventuelles

*   **Module Utilisateurs & Profils (M-USER) :** Pour l'identification de l'auteur, du modificateur, et la gestion des droits via utilisateurs/groupes.
*   **Module Notifications (M-NOTIF) :** Pour notifier les utilisateurs lors de partages de documents, de commentaires sur des documents suivis, ou d'actions de workflow.
*   **Module Moteur de Recherche (M-SEARCH) :** La GED s'appuie sur ce module (ou son instance dédiée) pour l'indexation et la recherche.
*   **Service de Stockage Objet (MinIO/S3) :** Pour le stockage physique des fichiers.
*   **Service de Conversion de Documents (optionnel) :** Pour la prévisualisation (ex: LibreOffice pour convertir les documents Office en PDF).
*   **Annuaire LDAP/AD :** Pour la résolution des groupes dans la gestion des permissions.
*   **Module Espaces Collaboratifs (M-ESPACE) :** Chaque espace peut avoir sa propre section GED.

## 6. Données en Entrée/Sortie

### 6.1. Données en Entrée (pour l'upload/modification)
*   Fichier binaire.
*   Nom du fichier (texte).
*   ID Dossier parent (référence).
*   Métadonnées (objet/JSON : clé/valeur).
*   Commentaire de version (texte).
*   ID Utilisateur (auteur de l'action).

### 6.2. Données en Sortie (pour l'affichage/recherche)
*   Liste de Fichiers/Dossiers :
    *   ID Document/Dossier
    *   Nom
    *   Type (fichier/dossier)
    *   Taille
    *   Date de modification
    *   Auteur
    *   Version actuelle
    *   Métadonnées principales
    *   Permissions de l'utilisateur courant sur l'item.
*   Détails d'un document : Toutes les métadonnées, liste des versions, informations de partage.

### 6.3. Données Stockées (Persistance - indicative)
*   Table Dossiers : id, nom, id_parent, id_createur, date_creation, date_modification.
*   Table Documents : id, id_dossier, nom_initial, id_createur, date_creation.
*   Table Versions_Documents : id, id_document, numero_version, nom_fichier_stockage, chemin_stockage, taille, type_mime, hash_contenu, id_uploader, date_upload, commentaire_version, est_version_actuelle (bool).
*   Table Metadonnees_Documents : id, id_version_document (ou id_document si métadonnées au niveau doc), nom_champ_meta, valeur_meta.
*   Table Permissions_GED : id, id_item (document ou dossier), type_item (doc/folder), id_utilisateur, id_groupe, type_permission (lecture, ecriture, gestion, etc.).
*   Table Corbeille_GED : id, id_item_origine, type_item_origine, date_suppression, id_utilisateur_suppresseur, données_originales (JSON).
*   Table Verrouillages_GED (Check-out) : id_document, id_utilisateur, date_verrouillage.
    (Structure à affiner, notamment pour le stockage des fichiers qui sera sur un système de fichiers ou un stockage objet type S3/MinIO, la base de données ne contenant que les métadonnées et pointeurs).

---
*Document préparé par : Primex Software*
*Rédigé par : Jules AI – Agent IA Senior*
*Date : 2023-10-27*
*URL : https://primex-software.com*
```
