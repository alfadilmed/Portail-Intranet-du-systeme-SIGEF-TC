```markdown
# Checklists et Livrables de Tests - Portail Intranet SIGEF-TC

## 1. Introduction

Ce document présente les différentes checklists et les types de tests qui seront effectués tout au long du cycle de vie du projet Portail Intranet SIGEF-TC. L'objectif est d'assurer la qualité, la conformité fonctionnelle, la performance, la sécurité et l'utilisabilité du portail avant sa mise en production.

## 2. Stratégie de Test Globale

*   **Tests Continus :** Les tests seront intégrés dès le début du cycle de développement (Shift-Left Testing).
*   **Niveaux de Test :**
    *   Tests Unitaires (TU)
    *   Tests d'Intégration (TI)
    *   Tests Fonctionnels (TF) / Tests Système
    *   Tests d'Acceptation Utilisateur (UAT) / Recette
    *   Tests Non Fonctionnels (Performance, Sécurité, Utilisabilité, Compatibilité)
*   **Automatisation :** Un maximum de tests (unitaires, intégration, certains fonctionnels) seront automatisés et intégrés dans le pipeline CI/CD.
*   **Gestion des Anomalies :** Utilisation d'un outil de suivi des anomalies (ex: Jira) pour enregistrer, prioriser et suivre la correction des bugs.

## 3. Checklists et Cas de Test par Type

### 3.1. Tests Fonctionnels (Cas de Test)

Des cas de test détaillés seront écrits pour chaque fonctionnalité décrite dans la Documentation Fonctionnelle (DOC-F.md) et les Fiches Modules. Ces cas de test suivront un format standard :
*   **ID du Cas de Test :** Identifiant unique (ex: TF-ACTU-001)
*   **Module Concerné :** (ex: Actualités)
*   **Fonctionnalité Testée :** (ex: Création d'une nouvelle actualité)
*   **Prérequis :** Conditions nécessaires avant d'exécuter le test (ex: Utilisateur connecté avec le rôle "ContributeurActualites").
*   **Étapes de Test :** Séquence d'actions à effectuer.
*   **Données d'Entrée :** Valeurs spécifiques à utiliser.
*   **Résultat Attendu :** Comportement attendu du système.
*   **Résultat Obtenu :** (À remplir lors de l'exécution)
*   **Statut :** (Réussi, Échoué, Bloqué, Non testé)
*   **Criticité :** (Bloquant, Majeur, Mineur, Cosmétique)
*   **Commentaires :**

**Exemples de domaines fonctionnels à couvrir (liste non exhaustive) :**

*   **Authentification et Gestion des Utilisateurs :**
    *   Connexion/Déconnexion (SSO via LDAP/AD).
    *   Accès au profil utilisateur.
    *   Modification des champs de profil autorisés.
    *   Synchronisation des données depuis LDAP/AD.
    *   Gestion des rôles et permissions (vérification des accès selon les rôles).
*   **Module Actualités :**
    *   Création, édition, suppression d'actualités.
    *   Publication/Dépublication, planification.
    *   Gestion des catégories, ciblage.
    *   Affichage (liste, détail), filtres.
    *   Gestion des commentaires.
*   **Module GED :**
    *   Création/Suppression de dossiers.
    *   Upload/Téléchargement de fichiers (différents types/tailles).
    *   Gestion des versions (check-in/check-out, historique).
    *   Gestion des métadonnées.
    *   Gestion des permissions par dossier/fichier.
    *   Prévisualisation de documents.
    *   Fonctionnalité de corbeille.
*   **Module Calendrier :**
    *   Création/Édition/Suppression d'événements (simples, récurrents).
    *   Gestion des participants et des invitations.
    *   Affichage (mois, semaine, jour), navigation.
    *   Gestion des calendriers multiples et partages.
    *   Rappels.
*   **Module Forums :**
    *   Création/Suppression de forums/sujets.
    *   Publication de messages/réponses.
    *   Modération.
    *   Abonnements et notifications.
*   **Module Moteur de Recherche Global :**
    *   Recherche par mots-clés sur tous les contenus indexés.
    *   Pertinence des résultats.
    *   Filtrage par type de contenu, date, etc.
    *   Prise en compte des droits d'accès dans les résultats.
    *   Suggestions et correction orthographique.
*   **Notifications :**
    *   Réception des notifications (in-app, email).
    *   Marquage comme lu/non lu.
    *   Paramètres de notification.
*   **Espaces Collaboratifs :**
    *   Création/Gestion d'un espace.
    *   Fonctionnalités spécifiques à l'espace (actualités, documents, tâches).

### 3.2. Tests d’Utilisabilité (UX)

*   **Objectif :** Évaluer la facilité d'utilisation, l'intuitivité, l'ergonomie et la satisfaction globale de l'utilisateur.
*   **Méthodes :**
    *   **Revue Experte (Heuristique) :** Évaluation par des experts UX basée sur des critères ergonomiques (ex: critères de Bastien & Scapin, heuristiques de Nielsen).
    *   **Tests Utilisateurs (Scénarios) :** Observation d'utilisateurs réels (représentatifs des différents profils) réalisant des tâches types sur le portail. Collecte de retours qualitatifs (difficultés rencontrées, suggestions) et quantitatifs (temps de complétion, taux de succès).
*   **Checklist indicative pour la revue experte / observation :**
    *   **Clarté de la navigation :** Menus, liens, breadcrumb sont-ils compréhensibles ? L'utilisateur sait-il où il est et comment aller ailleurs ?
    *   **Lisibilité et présentation de l'information :** Contraste, taille des polices, organisation visuelle.
    *   **Efficacité :** L'utilisateur peut-il accomplir les tâches rapidement ? Y a-t-il des étapes inutiles ?
    *   **Consistance :** Les éléments d'interface (boutons, icônes, terminologie) sont-ils utilisés de manière cohérente à travers le portail ?
    *   **Gestion des erreurs :** Les messages d'erreur sont-ils clairs et utiles ? Le système aide-t-il à corriger les erreurs ?
    *   **Feedback du système :** L'utilisateur reçoit-il un retour approprié après chaque action ?
    *   **Contrôle utilisateur et liberté :** L'utilisateur peut-il facilement annuler une action ou revenir en arrière ?
    *   **Prévention des erreurs :** Le design aide-t-il à éviter les erreurs courantes ?
    *   **Charge cognitive :** L'interface est-elle simple à comprendre ou demande-t-elle trop d'effort mental ?
    *   **Satisfaction subjective :** L'expérience est-elle agréable ?

### 3.3. Tests de Compatibilité Navigateur et Appareils (Responsive Design)

*   **Objectif :** S'assurer que le portail s'affiche et fonctionne correctement sur différents navigateurs web et tailles d'écran (desktop, tablette, mobile).
*   **Navigateurs Cibles (à définir avec la Cour des Comptes, ex :)**
    *   Google Chrome (dernière version)
    *   Mozilla Firefox (dernière version)
    *   Microsoft Edge (dernière version)
    *   Safari (dernière version, si pertinent)
*   **Appareils/Résolutions Cibles :**
    *   Desktop (ex: 1920x1080, 1366x768)
    *   Tablette (ex: 768x1024, 1024x768 - portrait/paysage)
    *   Mobile (ex: 375x667, 414x896 - portrait/paysage)
*   **Checklist :**
    *   Affichage correct de la mise en page (pas de chevauchements, de contenus coupés).
    *   Lisibilité des textes.
    *   Fonctionnalité de tous les éléments interactifs (boutons, menus déroulants, champs de saisie).
    *   Navigation tactile fluide sur mobile/tablette.
    *   Performance d'affichage acceptable sur les différentes configurations.
    *   Adaptation des images et médias.

### 3.4. Tests de Sécurité

*   **Objectif :** Identifier et corriger les vulnérabilités de sécurité du portail.
*   **Référence :** Plan de Sécurité & Confidentialité (PLAN-SECURITE.md), OWASP Top 10, OWASP ASVS (Application Security Verification Standard).
*   **Checklist (basée sur les risques courants et les mesures du plan de sécurité) :**
    *   **Authentification :**
        *   Robustesse du SSO (pas de contournement possible).
        *   Gestion sécurisée des tokens (pas de fuite, expiration correcte).
        *   Protection contre le brute-force sur la page de login (gérée par l'IDP).
        *   Déconnexion effective (invalidation session/tokens).
        *   Vérification de l'application de la MFA pour les comptes sensibles.
    *   **Gestion des Accès (Autorisation) :**
        *   Vérification stricte des permissions RBAC pour chaque fonctionnalité et accès aux données.
        *   Pas d'escalade de privilèges possible.
        *   Pas d'accès direct non autorisé à des URL/API (idor - Insecure Direct Object References).
    *   **Injection (SQL, NoSQL, LDAP, OS Command) :**
        *   Tous les champs de saisie utilisateur sont-ils correctement validés et sanitisés ?
        *   Utilisation d'ORM/requêtes préparées partout.
    *   **Cross-Site Scripting (XSS) :**
        *   Stored XSS : Les données affichées (provenant des utilisateurs) sont-elles correctement encodées ?
        *   Reflected XSS : Les paramètres d'URL sont-ils encodés avant affichage ?
        *   DOM XSS : Vérification des manipulations du DOM par JavaScript.
        *   Présence et configuration correcte du header Content Security Policy (CSP).
    *   **Cross-Site Request Forgery (CSRF) :**
        *   Les actions sensibles modifiant l'état sont-elles protégées par des tokens anti-CSRF ou autre mécanisme (ex: SameSite cookies, vérification de l'origine) ?
    *   **Sécurité des Communications :**
        *   TLS/HTTPS utilisé partout ? Configuration TLS correcte (versions, ciphers) ?
        *   Pas de contenu mixte (HTTP et HTTPS sur la même page).
        *   HSTS activé.
    *   **Gestion des Erreurs et Journalisation :**
        *   Les messages d'erreur ne divulguent pas d'informations techniques sensibles.
        *   Les logs ne contiennent pas de données sensibles en clair (mots de passe, tokens).
        *   Les événements de sécurité sont correctement journalisés.
    *   **Sécurité des Fichiers Uploadés (GED) :**
        *   Validation du type de fichier (liste blanche).
        *   Scan antivirus des fichiers uploadés (si possible/requis).
        *   Pas d'exécution de code côté serveur à partir des fichiers uploadés.
        *   Contrôle d'accès strict aux fichiers.
    *   **Configuration de Sécurité des Composants :**
        *   Pas de comptes par défaut/faibles sur les serveurs, bases de données, IDP.
        *   Patchs de sécurité appliqués.
        *   Headers de sécurité HTTP bien configurés.
    *   **Tests d'Intrusion (Pentest) :** À réaliser par une équipe spécialisée (interne ou externe) avant la mise en production majeure. Le rapport de pentest servira de base à des corrections.

### 3.5. Tests de Performance (optionnels pour un intranet, mais à considérer)

*   **Objectif :** Vérifier la réactivité, la stabilité et la capacité du portail sous une charge utilisateur attendue.
*   **Types de Tests :**
    *   **Tests de Charge :** Simuler le nombre d'utilisateurs concurrents attendus et observer le comportement.
    *   **Tests de Stress :** Augmenter la charge au-delà des limites attendues pour identifier les points de rupture.
    *   **Tests d'Endurance :** Maintenir une charge normale sur une période prolongée pour détecter les fuites de mémoire ou la dégradation des performances.
*   **Indicateurs Clés à Mesurer :**
    *   Temps de réponse moyen des pages/API.
    *   Débit (requêtes par seconde).
    *   Taux d'erreur sous charge.
    *   Utilisation des ressources serveur (CPU, RAM, I/O).
*   **Outils :** JMeter, k6, Gatling, LoadRunner.

## 4. Validation par le Commanditaire (Recette Utilisateur - UAT)

*   **Objectif :** Obtenir la validation formelle du commanditaire (Cour des Comptes) que le portail répond aux besoins et exigences spécifiés.
*   **Processus :**
    1.  Préparation de l'environnement de recette (miroir de la production).
    2.  Fourniture de jeux de données de test représentatifs.
    3.  Définition de scénarios de recette par des utilisateurs clés désignés par le commanditaire. Ces scénarios couvrent les principaux parcours utilisateurs et fonctionnalités critiques.
    4.  Exécution des scénarios par les utilisateurs clés, accompagnés par l'équipe projet si besoin.
    5.  Enregistrement des anomalies constatées.
    6.  Correction des anomalies bloquantes/majeures par l'équipe de développement.
    7.  Nouvelle session de recette si nécessaire.
    8.  Signature du procès-verbal (PV) de recette par le commanditaire.
*   **Livrable :** PV de recette signé.

## 5. Livrables de Tests (Documentation)

*   **Plan de Test Global** (ce document).
*   **Cahier de Cas de Test Fonctionnels** (détaillant chaque cas de test).
*   **Rapports d'Exécution des Tests** (pour chaque cycle de test, indiquant les résultats, statuts, anomalies).
*   **Liste des Anomalies** (suivi dans l'outil de bug tracking).
*   **Rapport de Tests d'Utilisabilité.**
*   **Rapport de Tests de Compatibilité.**
*   **Rapport de Tests de Sécurité** (incluant les résultats des scans et des pentests).
*   **Rapport de Tests de Performance** (si effectués).
*   **Procès-Verbal de Recette Utilisateur.**

---
*Document préparé par : Primex Software*
*Rédigé par : Jules AI – Agent IA Senior*
*Date : 2023-10-27*
*URL : https://primex-software.com*
```
