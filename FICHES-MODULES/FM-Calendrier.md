```markdown
# Fiche Module : Calendrier Partagé

**Identifiant du Module :** M-CAL
**Version :** 1.0
**Date de création :** 2023-10-27
**Auteur :** Jules AI – Agent IA Senior

## 1. Objectif

Le module "Calendrier Partagé" a pour objectif de fournir aux collaborateurs de la Cour des Comptes un outil centralisé pour la gestion, la visualisation et le partage d'événements, de réunions, d'échéances importantes et de disponibilités. Il vise à améliorer l'organisation, la coordination et la communication des activités temporelles au sein de l'institution.

## 2. Description Détaillée

Ce module permet aux utilisateurs de créer des événements personnels ou de groupe, d'inviter des participants, de définir des rappels et de visualiser plusieurs calendriers (personnel, équipe, général) de manière superposée ou distincte. Il offre des vues mensuelle, hebdomadaire et journalière pour une meilleure lisibilité.

Fonctionnalités clés :
*   Création d'événements avec titre, description, date/heure de début et de fin, lieu.
*   Gestion des événements sur une journée entière ou récurrents (quotidien, hebdomadaire, mensuel, annuel, personnalisé).
*   Invitation de participants (collaborateurs individuels ou groupes issus de l'annuaire).
*   Gestion du statut des participants (Accepté, Refusé, Peut-être).
*   Définition de rappels pour les événements (notifications in-app, email).
*   Création et gestion de calendriers multiples :
    *   Calendrier personnel (privé par défaut).
    *   Calendriers d'équipe/projet (partagés avec les membres).
    *   Calendriers thématiques ou institutionnels (ex: "Jours Fériés", "Événements RH").
*   Partage de calendriers avec des droits spécifiques (lecture seule, ajout d'événements, gestion complète).
*   Affichage des calendriers en superposition avec codes couleurs distincts.
*   Vues : mensuelle, hebdomadaire (grille), journalière (agenda), liste d'événements.
*   Navigation aisée entre les jours, semaines, mois.
*   Intégration possible pour synchronisation avec des clients de messagerie (ex: via export/import iCalendar `.ics`).
*   Recherche d'événements par mots-clés, dates, participants.

## 3. Interfaces Utilisateur (Mockups Légers ou Wireframes - Description Textuelle)

### 3.1. Vue Principale du Calendrier
*   **En-tête :** Titre "Calendrier". Boutons de navigation (Précédent, Suivant, Aujourd'hui). Sélecteur de vue (Mois, Semaine, Jour, Liste). Bouton "Créer un événement".
*   **Panneau Latéral Gauche (ou menu déroulant) :**
    *   Mini-calendrier pour navigation rapide.
    *   Liste des calendriers disponibles pour l'utilisateur (avec cases à cocher pour afficher/masquer et codes couleurs) :
        *   Mon Calendrier (personnel)
        *   Calendriers partagés avec moi
        *   Calendriers d'équipe/institutionnels auxquels je suis abonné.
    *   Option "Gérer mes calendriers" / "Créer un nouveau calendrier".
*   **Zone Centrale d'Affichage :**
    *   **Vue Mois :** Grille mensuelle. Les jours affichent un résumé des événements (ex: "10:00 Réunion X"). Clic sur un jour pour voir détails ou sur un événement pour l'ouvrir.
    *   **Vue Semaine :** Grille hebdomadaire (jours en colonnes, heures en lignes). Les événements sont des blocs positionnés selon leur durée.
    *   **Vue Jour :** Grille horaire pour la journée sélectionnée.
    *   **Vue Liste :** Liste chronologique des prochains événements.
*   **Interaction :** Clic sur un créneau vide pour créer un événement. Glisser-déposer pour déplacer/redimensionner un événement (si droits).

### 3.2. Fenêtre Modale/Page de Création/Édition d'Événement
*   Champ "Titre de l'événement" (obligatoire).
*   Sélecteur de "Calendrier" (dans lequel enregistrer l'événement, parmi ceux où l'utilisateur a les droits d'écriture).
*   Sélecteurs Date/Heure de "Début" et "Fin".
*   Case à cocher "Journée entière".
*   Champ "Lieu" (texte libre, potentiellement intégrable avec un système de réservation de salles).
*   Champ "Description" (éditeur de texte simple ou riche).
*   **Participants :**
    *   Champ de recherche pour ajouter des participants (autocomplétion depuis l'annuaire).
    *   Liste des participants invités (avec leur statut de réponse).
    *   Option "Rendre la liste des participants visible à tous les invités".
*   **Récurrence :**
    *   Options : "Ne se répète pas", "Tous les jours", "Toutes les semaines le [jour]", "Tous les mois le [jour]", "Tous les ans le [jour]", "Personnalisé..." (ouvre des options avancées).
*   **Rappels :**
    *   Options : "Aucun", "10 minutes avant", "30 minutes avant", "1 heure avant", "1 jour avant", "Personnalisé..." (permettant plusieurs rappels par email/notification).
*   **Visibilité/Confidentialité de l'événement :** "Public" (visible par ceux qui ont accès au calendrier), "Privé" (seul le titre ou "Occupé" est visible par les autres).
*   Boutons : "Enregistrer", "Annuler", "Supprimer" (si édition).

### 3.3. Interface de Gestion des Calendriers (accessible via le panneau latéral)
*   Liste des calendriers créés par l'utilisateur ou dont il est propriétaire.
*   Pour chaque calendrier : Nom, Description, Couleur, Actions (Modifier, Partager, Supprimer, Exporter en .ics).
*   Bouton "Créer un nouveau calendrier" :
    *   Formulaire : Nom du calendrier, Description, Couleur par défaut.
*   Interface de partage d'un calendrier :
    *   Ajouter des utilisateurs/groupes.
    *   Définir leurs permissions (Voir tous les détails des événements, Voir uniquement disponible/occupé, Apporter des modifications aux événements, Gérer les options de partage).

## 4. Règles de Gestion

*   RG-CAL-001 : Un titre, une date et une heure de début sont obligatoires pour chaque événement.
*   RG-CAL-002 : La date/heure de fin doit être postérieure à la date/heure de début.
*   RG-CAL-003 : Tout utilisateur peut créer des événements dans son calendrier personnel.
*   RG-CAL-004 : La création d'événements dans des calendriers partagés dépend des droits accordés à l'utilisateur sur ce calendrier.
*   RG-CAL-005 : Les invitations envoyées aux participants génèrent des notifications.
*   RG-CAL-006 : Les participants peuvent accepter, refuser ou proposer un nouvel horaire (optionnel) pour un événement auquel ils sont invités. Leur réponse met à jour le statut dans les détails de l'événement pour l'organisateur.
*   RG-CAL-007 : Les rappels génèrent des notifications in-app et/ou par email selon les préférences de l'utilisateur et la configuration du rappel.
*   RG-CAL-008 : La suppression d'un événement récurrent peut s'appliquer à une occurrence unique, à toutes les occurrences futures, ou à toutes les occurrences.
*   RG-CAL-009 : Les conflits d'horaires pour un même utilisateur peuvent être signalés visuellement mais ne bloquent pas nécessairement la création (sauf si configuré).
*   RG-CAL-010 : Les administrateurs du portail peuvent gérer tous les calendriers institutionnels.
*   RG-CAL-011 : Les données des événements privés d'un utilisateur ne sont pas visibles par les autres, sauf si l'utilisateur choisit de partager explicitement son calendrier avec des droits de lecture. L'option "Occupé" peut être affichée.

## 5. Dépendances Éventuelles

*   **Module Utilisateurs & Profils (M-USER) :** Pour l'identification de l'organisateur, des participants, et la gestion des groupes.
*   **Module Notifications (M-NOTIF) :** Pour les invitations, les réponses, les rappels d'événements.
*   **Annuaire LDAP/AD :** Pour la recherche et l'invitation de participants.
*   **Service Email :** Pour l'envoi de notifications et de rappels par email.
*   **Module Espaces Collaboratifs (M-ESPACE) :** Un espace pourrait avoir son propre calendrier d'équipe.

## 6. Données en Entrée/Sortie

### 6.1. Données en Entrée (pour la création/édition d'événement)
*   Titre (texte)
*   ID Calendrier (référence)
*   Date/heure de début (datetime)
*   Date/heure de fin (datetime)
*   Flag "Journée entière" (booléen)
*   Lieu (texte)
*   Description (texte/HTML)
*   Liste des ID Participants (références)
*   Paramètres de récurrence (objet/JSON)
*   Paramètres de rappels (liste d'objets/JSON)
*   Visibilité (public/privé)

### 6.2. Données en Sortie (pour l'affichage d'un événement)
*   ID Événement
*   Titre
*   Nom du Calendrier
*   Date/heure de début
*   Date/heure de fin
*   Lieu
*   Description
*   Nom de l'Organisateur
*   Liste des Participants (avec nom et statut de réponse)
*   Détails de la récurrence
*   Détails des rappels

### 6.3. Données Stockées (Persistance)
*   Table Calendriers : id, nom, description, id_proprietaire, couleur, type (personnel, equipe, institutionnel).
*   Table Calendriers_Partages : id_calendrier, id_utilisateur_partage, id_groupe_partage, permission (lecture_seule, lecture_ecriture, gestion).
*   Table Evenements : id, id_calendrier, titre, description, lieu, date_debut, date_fin, flag_journee_entiere, id_organisateur, regle_recurrence (ex: RRULE string), visibilite.
*   Table Evenements_Participants : id_evenement, id_utilisateur, statut_reponse (accepte, refuse, peut-etre, pas_repondu).
*   Table Evenements_Rappels : id_evenement, type_rappel (notification, email), delai_avant_rappel (ex: '10 minutes').
*   Table Evenements_Occurrences_Exclues (pour les exceptions de récurrence) : id_evenement_parent, date_occurrence_originale.
    (Structure indicative, à affiner)

---
*Document préparé par : Primex Software*
*Rédigé par : Jules AI – Agent IA Senior*
*Date : 2023-10-27*
*URL : https://primex-software.com*
```
