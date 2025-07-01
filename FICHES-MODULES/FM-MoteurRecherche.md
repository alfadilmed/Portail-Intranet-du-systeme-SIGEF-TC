```markdown
# Fiche Module : Moteur de Recherche Global

**Identifiant du Module :** M-SEARCH
**Version :** 1.0
**Date de création :** 2023-10-27
**Auteur :** Jules AI – Agent IA Senior

## 1. Objectif

Le module "Moteur de Recherche Global" a pour objectif de fournir une fonctionnalité de recherche transversale puissante et intuitive, permettant aux utilisateurs de trouver rapidement des informations pertinentes à travers l'ensemble des contenus et modules du Portail Intranet SIGEF-TC. Il vise à améliorer l'accessibilité de l'information et à faire gagner du temps aux collaborateurs.

## 2. Description Détaillée

Ce module s'interface avec un moteur d'indexation et de recherche dédié (ex: OpenSearch, Elasticsearch). Il est responsable de collecter les informations depuis les différents modules du portail (Actualités, GED, Profils Utilisateurs, Forums, etc.), de les préparer pour l'indexation, de présenter une interface de recherche à l'utilisateur, et d'afficher les résultats de manière claire et organisée.

Fonctionnalités clés :
*   **Champ de recherche unique et omniprésent :** Un champ de recherche global est accessible depuis l'en-tête de toutes les pages du portail.
*   **Indexation des contenus :**
    *   Actualités et Annonces : Titre, contenu, auteur, catégorie, tags.
    *   Documents de la GED : Contenu des fichiers (pour les formats supportés comme PDF, DOCX, TXT), nom du fichier, métadonnées (auteur, mots-clés, description).
    *   Profils Utilisateurs : Nom, prénom, fonction, département, compétences, biographie.
    *   Forums de Discussion : Titre des sujets, contenu des messages, auteur.
    *   Pages de contenu statique (si applicable).
    *   Calendrier : Titre des événements, description (selon politique de confidentialité).
*   **Interface de résultats de recherche :**
    *   Affichage des résultats paginés, classés par pertinence par défaut.
    *   Pour chaque résultat : Titre (lien vers la ressource), extrait pertinent avec les termes recherchés mis en évidence, source (module d'origine, ex: "Actualité", "Document GED"), date, auteur.
*   **Filtrage et Facettes :**
    *   Filtres pour affiner les résultats par :
        *   Type de contenu (Actualité, Document, Utilisateur, Forum, etc.).
        *   Date de publication/modification (ex: "Dernière semaine", "Dernier mois", plage de dates).
        *   Auteur/Contributeur.
        *   Catégorie (pour les actualités, forums).
        *   Type de fichier (pour les documents).
    *   Les facettes affichent le nombre de résultats pour chaque valeur de filtre possible.
*   **Suggestions de recherche (Auto-complétion) :** Pendant que l'utilisateur tape dans le champ de recherche, des suggestions basées sur les recherches populaires ou les titres de contenu peuvent apparaître.
*   **Correction orthographique ("Did you mean...?") :** Suggestion de termes corrigés si une faute de frappe est probable.
*   **Recherche avancée :** Une page de recherche avancée peut permettre des requêtes plus complexes (opérateurs booléens AND/OR/NOT, recherche exacte de phrase, exclusion de mots).
*   **Prise en compte des permissions :** Les résultats de recherche ne doivent afficher que les contenus auxquels l'utilisateur connecté a le droit d'accéder. Le filtrage de sécurité est primordial.
*   **Personnalisation de la pertinence (optionnel) :** Possibilité d'ajuster l'algorithme de scoring pour donner plus de poids à certains champs ou types de contenu.

## 3. Interfaces Utilisateur (Mockups Légers ou Wireframes - Description Textuelle)

### 3.1. Champ de Recherche Global (dans l'en-tête du portail)
*   Champ de saisie texte simple avec une icône loupe.
*   En tapant, une liste déroulante de suggestions (auto-complétion) peut apparaître sous le champ.
*   Valider la recherche (Entrée ou clic sur l'icône) mène à la page de résultats.

### 3.2. Page de Résultats de Recherche
*   **En-tête :** Rappel du terme recherché. Nombre total de résultats.
*   **Panneau Latéral Gauche (Filtres et Facettes) :**
    *   Section "Type de contenu" : Liens/cases à cocher (Actualité (xx), Document (yy), Utilisateur (zz), ...).
    *   Section "Date" : Options (Toute date, Dernière semaine, Dernier mois, Plage personnalisée).
    *   Autres sections de filtres contextuels selon les types de résultats (Catégorie, Auteur, etc.).
*   **Zone Principale (Liste des Résultats) :**
    *   Pour chaque résultat :
        *   Titre de la ressource (lien cliquable).
        *   Extrait du contenu avec les mots-clés en surbrillance.
        *   Informations contextuelles : Source (ex: "Document GED"), Auteur, Date de modification.
        *   Icône représentant le type de contenu.
    *   Pagination en bas de la liste.
    *   Options de tri (par pertinence, par date).
*   **Si aucun résultat :** Message "Aucun résultat trouvé pour '[terme recherché]'". Suggestion de vérifier l'orthographe ou d'essayer d'autres mots-clés. Lien vers la recherche avancée.

### 3.3. Page de Recherche Avancée (optionnel)
*   Formulaire avec plusieurs champs :
    *   "Tous ces mots" (AND).
    *   "Cette expression exacte".
    *   "Un de ces mots" (OR).
    *   "Aucun de ces mots" (NOT).
    *   Filtres spécifiques par type de contenu sélectionnable.
*   Bouton "Lancer la recherche avancée".

## 4. Règles de Gestion

*   RG-SRCH-001 : La recherche est effectuée sur un index mis à jour régulièrement (quasi temps réel ou batch fréquent).
*   RG-SRCH-002 : Les résultats de recherche respectent scrupuleusement les droits d'accès de l'utilisateur effectuant la recherche. Un contenu non accessible à l'utilisateur ne doit jamais apparaître.
*   RG-SRCH-003 : La pertinence des résultats est calculée par le moteur de recherche sous-jacent (ex: TF-IDF, BM25).
*   RG-SRCH-004 : L'indexation du contenu des fichiers de la GED ne concerne que les formats pris en charge (ex: PDF, DOCX, ODT, TXT). Pour les autres (images, vidéos), seuls les métadonnées et le nom de fichier sont indexés.
*   RG-SRCH-005 : Les termes de recherche sont nettoyés (ex: suppression des stop words communs, normalisation de la casse) avant d'être soumis au moteur de recherche.
*   RG-SRCH-006 : Les administrateurs du portail peuvent avoir accès à des statistiques de recherche (termes les plus recherchés, recherches sans résultats) pour améliorer le contenu ou la configuration du moteur.
*   RG-SRCH-007 : La profondeur d'indexation des forums peut être limitée (ex: ne pas indexer les messages très anciens ou les forums archivés, sauf si spécifié).
*   RG-SRCH-008 : Les suggestions de recherche et la correction orthographique s'appuient sur les capacités du moteur de recherche ou des bibliothèques dédiées.

## 5. Dépendances Éventuelles

*   **Moteur d'Indexation et de Recherche (Ex: OpenSearch/Elasticsearch) :** Composant central indispensable. Ce module est une interface vers ce moteur.
*   **Tous les modules produisant du contenu :**
    *   Module Actualités (M-ACTU)
    *   Module GED (M-GED)
    *   Module Profils Utilisateurs (M-USERPROF)
    *   Module Forums (M-FORUM)
    *   Module Calendrier (M-CAL) (pour les événements publics)
*   **Bus de Messages (optionnel mais recommandé) :** Pour notifier le service d'indexation des créations/modifications/suppressions de contenu dans les autres modules, afin de maintenir l'index à jour.
*   **Module d'Authentification/Gestion des Droits :** Pour assurer le filtrage sécurisé des résultats.

## 6. Données en Entrée/Sortie

### 6.1. Données en Entrée (pour une requête de recherche)
*   Termes de recherche (chaîne de caractères).
*   Filtres sélectionnés (objet/JSON : ex: `{ type: "Document", date_range: "last_month" }`).
*   Informations de pagination (numéro de page, nombre d'items par page).
*   Critères de tri (ex: "pertinence", "date_desc").
*   Contexte utilisateur (ID utilisateur pour le filtrage des droits).

### 6.2. Données en Sortie (résultats de recherche)
*   Liste d'objets "Résultat", chaque objet contenant :
    *   ID unique de la ressource.
    *   Titre.
    *   URL vers la ressource.
    *   Extrait pertinent (snippet).
    *   Type de contenu (source).
    *   Date de publication/modification.
    *   Auteur/Propriétaire.
    *   Score de pertinence.
    *   Autres métadonnées utiles pour l'affichage.
*   Informations de pagination (nombre total de résultats, page actuelle, nombre total de pages).
*   Liste des facettes disponibles avec leur nombre d'occurrences.

### 6.3. Données Stockées (au niveau du moteur d'indexation - ex: OpenSearch)
*   **Index :** Un ou plusieurs index contenant les documents préparés pour la recherche.
*   **Format d'un document dans l'index (exemple simplifié) :**
    ```json
    {
      "id_ressource": "uuid-actualite-123",
      "type_contenu": "Actualité",
      "titre": "Lancement du nouveau portail intranet",
      "contenu_texte": "Le texte complet de l'actualité...", // pour full-text search
      "auteur_nom": "Service Communication",
      "auteur_id": "grp-com",
      "date_publication": "2023-10-26T10:00:00Z",
      "categories": ["Interne", "Projet SIGEF-TC"],
      "tags": ["intranet", "nouveau", "communication"],
      "permissions_lecture": ["role_collaborateur", "user_admin1"] // IDs utilisateurs/groupes/rôles ayant le droit de lire
    }
    ```
    Chaque module est responsable de "pousser" ses données dans ce format (ou un format similaire adapté) vers le service d'indexation.

---
*Document préparé par : Primex Software*
*Rédigé par : Jules AI – Agent IA Senior*
*Date : 2023-10-27*
*URL : https://primex-software.com*
```
