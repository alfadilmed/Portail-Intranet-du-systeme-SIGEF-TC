```markdown
# Fiche Module : Annuaire et Profils Utilisateurs

**Identifiant du Module :** M-USERPROF
**Version :** 1.0
**Date de création :** 2023-10-27
**Auteur :** Jules AI – Agent IA Senior

## 1. Objectif

Le module "Annuaire et Profils Utilisateurs" a pour objectif de fournir une interface centralisée pour rechercher et consulter les informations des collaborateurs de la Cour des Comptes. Il permet également à chaque utilisateur de visualiser et, dans une certaine mesure, de personnaliser son propre profil professionnel. Ce module vise à faciliter la prise de contact, l'identification des compétences et la connaissance de l'organisation interne.

## 2. Description Détaillée

Ce module s'appuie en grande partie sur les données issues de l'annuaire d'entreprise (LDAP/AD) et les enrichit potentiellement avec des informations gérées directement dans le portail. Il offre des fonctionnalités de recherche et de filtrage pour trouver des collègues, ainsi qu'une page de profil détaillée pour chaque utilisateur.

Fonctionnalités clés :
*   **Synchronisation avec l'annuaire d'entreprise (LDAP/AD) :**
    *   Récupération automatique des informations de base : nom, prénom, email, numéro de téléphone professionnel, département, fonction/poste, responsable hiérarchique.
    *   Mise à jour régulière des informations synchronisées.
*   **Annuaire des collaborateurs :**
    *   Liste consultable et paginée de tous les collaborateurs.
    *   Recherche par nom, prénom, email.
    *   Filtres avancés : par département, par fonction, par localisation (si disponible).
    *   Affichage des résultats sous forme de liste ou de cartes de visite.
*   **Page de Profil Utilisateur :**
    *   Affichage des informations synchronisées depuis l'annuaire (non modifiables par l'utilisateur directement dans le portail, sauf si politique spécifique).
    *   **Champs personnalisables par l'utilisateur (gérés par le portail) :**
        *   Photo de profil (upload).
        *   Biographie courte / Présentation.
        *   Compétences / Domaines d'expertise (via tags ou saisie libre).
        *   Projets en cours ou significatifs.
        *   Liens vers des profils professionnels externes (ex: LinkedIn, si autorisé par la politique interne).
        *   Préférences de communication (ex: "Préfère être contacté par email").
    *   Affichage de l'organigramme simplifié (position, responsable, collaborateurs directs) si les données sont disponibles et que la fonctionnalité est implémentée.
    *   Raccourcis pour contacter l'utilisateur (ex: lien `mailto:`, `tel:`).
*   **Confidentialité du Profil :**
    *   Certaines informations du profil (synchronisées ou ajoutées) peuvent avoir des niveaux de visibilité configurables (ex: visible par tous, visible par mon département, visible uniquement par moi). Par défaut, les informations professionnelles sont visibles par tous les utilisateurs connectés.
*   **Organigramme (fonctionnalité optionnelle/avancée) :**
    *   Représentation graphique navigable de la structure hiérarchique de l'organisation, basée sur les données de l'annuaire.

## 3. Interfaces Utilisateur (Mockups Légers ou Wireframes - Description Textuelle)

### 3.1. Page Annuaire des Collaborateurs
*   **En-tête :** Titre "Annuaire des Collaborateurs".
*   **Zone de Recherche et Filtres :**
    *   Champ de recherche principal (nom, prénom, email).
    *   Bouton/Lien "Filtres avancés" ouvrant une modale ou une section avec :
        *   Liste déroulante "Département".
        *   Champ "Fonction/Poste".
        *   Liste déroulante "Localisation" (si pertinent).
    *   Bouton "Appliquer les filtres".
*   **Zone d'Affichage des Résultats :**
    *   Liste des collaborateurs correspondants aux critères. Chaque entrée affiche :
        *   Photo miniature.
        *   Nom complet (cliquable, mène à la page de profil).
        *   Fonction/Poste principal.
        *   Département.
        *   Email et numéro de téléphone (visibles directement ou au survol).
    *   Pagination si grand nombre de résultats.
    *   Option pour changer la vue (liste compacte / cartes de visite).

### 3.2. Page de Profil Utilisateur (Vue Publique par un autre collaborateur)
*   **Section Principale :**
    *   Grande photo de profil.
    *   Nom complet.
    *   Fonction/Poste.
    *   Département.
    *   Coordonnées : Email, Téléphone pro, Bureau (si applicable). Liens cliquables.
    *   Responsable hiérarchique (Nom, cliquable vers son profil).
*   **Onglets ou Sections Secondaires :**
    *   **Informations :**
        *   Biographie / Présentation.
        *   Compétences (liste de tags).
        *   Projets.
        *   Liens externes.
    *   **Activité récente (optionnel) :** Dernières contributions sur le portail (actualités publiées, messages de forum pertinents - soumis à confidentialité).
    *   **Organigramme (si l'utilisateur est un manager) :** Liste de ses collaborateurs directs.

### 3.3. Page de Profil Utilisateur (Vue Édition par l'utilisateur concerné)
*   Même structure que la vue publique, mais avec des icônes "Modifier" à côté des champs personnalisables.
*   **Champs modifiables :**
    *   Zone pour uploader/changer la photo de profil.
    *   Éditeur de texte pour la biographie.
    *   Interface pour ajouter/supprimer des compétences (champ de saisie avec autocomplétion de tags existants ou création de nouveaux).
    *   Interface pour lister les projets (titre, description courte, lien optionnel).
    *   Champs pour les liens externes.
*   Bouton "Enregistrer les modifications".
*   Accès aux paramètres de confidentialité de certaines informations du profil (si cette granularité est implémentée).

## 4. Règles de Gestion

*   RG-USERP-001 : Les informations de base (nom, prénom, email, téléphone pro, département, fonction, responsable) sont synchronisées depuis l'annuaire d'entreprise et ne sont pas modifiables directement dans le portail par l'utilisateur standard.
*   RG-USERP-002 : La modification des informations synchronisées doit se faire à la source (dans l'annuaire d'entreprise, via les processus RH/IT).
*   RG-USERP-003 : Chaque utilisateur peut modifier les champs personnalisables de son propre profil (photo, biographie, compétences, etc.).
*   RG-USERP-004 : L'upload de photo de profil est soumis à des restrictions de taille et de format. Une photo par défaut est affichée si aucune photo n'est uploadée.
*   RG-USERP-005 : Toutes les informations de profil à caractère professionnel sont visibles par défaut par tous les utilisateurs authentifiés du portail.
*   RG-USERP-006 : Des politiques de modération peuvent s'appliquer sur les contenus ajoutés par les utilisateurs (biographie, photo) si jugé nécessaire.
*   RG-USERP-007 : La recherche dans l'annuaire porte sur les champs indexés (nom, prénom, email, département, fonction, compétences).
*   RG-USERP-008 : Les informations de contact (email, téléphone) doivent être à jour et fonctionnelles.
*   RG-USERP-009 : L'affichage du responsable hiérarchique et des collaborateurs directs dépend de la disponibilité et de la fiabilité de ces données dans l'annuaire source.

## 5. Dépendances Éventuelles

*   **Annuaire d'Entreprise (LDAP/Active Directory) :** Source principale des données. Une connexion fiable et des droits de lecture sont indispensables.
*   **Module d'Authentification (M-AUTH/IDP) :** Pour identifier l'utilisateur connecté et gérer les droits d'accès à son propre profil en mode édition.
*   **Service de Stockage (interne au portail ou GED) :** Pour stocker les photos de profil uploadées.
*   **Module Moteur de Recherche (M-SEARCH) :** Pour l'indexation des profils et la recherche avancée.
*   **Module Notifications (M-NOTIF) (optionnel) :** Pour notifier des mises à jour de profil importantes si nécessaire (rarement utilisé pour ce module).

## 6. Données en Entrée/Sortie

### 6.1. Données en Entrée (pour la modification du profil par l'utilisateur)
*   ID Utilisateur (implicite, l'utilisateur connecté)
*   Fichier Photo (binaire)
*   Texte Biographie
*   Liste de Compétences (tableau de chaînes)
*   Liste de Projets (tableau d'objets {titre, description, lien})
*   Liste de Liens externes (tableau d'objets {libellé, url})

### 6.2. Données en Sortie (pour l'affichage d'un profil ou d'une liste annuaire)
*   ID Utilisateur (identifiant unique)
*   Nom, Prénom
*   Email
*   Téléphone professionnel
*   Département
*   Fonction/Poste
*   ID/Nom du Responsable hiérarchique
*   URL Photo de profil
*   Biographie
*   Liste de Compétences
*   Liste de Projets
*   Liste de Liens externes
*   Date de dernière mise à jour du profil (partie portail)

### 6.3. Données Stockées (Persistance - pour la partie gérée par le portail)
*   Table Profils_Utilisateurs_Portail : id_utilisateur (clé étrangère vers l'identifiant unique de l'utilisateur, souvent le `objectGUID` ou `sAMAccountName` de LDAP/AD), url_photo, biographie_texte, competences_json (ou table séparée), projets_json (ou table séparée), liens_externes_json (ou table séparée), date_derniere_maj_portail.
    *   Les données synchronisées de LDAP/AD sont généralement mises en cache ou requêtées à la volée, mais une copie peut être stockée pour des raisons de performance de recherche, avec un mécanisme de mise à jour.
    (Structure indicative)

---
*Document préparé par : Primex Software*
*Rédigé par : Jules AI – Agent IA Senior*
*Date : 2023-10-27*
*URL : https://primex-software.com*
```
