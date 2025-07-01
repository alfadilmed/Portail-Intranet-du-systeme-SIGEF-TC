# Planification Agile / Roadmap de Réalisation - Projet SIGEF-TC

## Introduction
Cette roadmap propose une approche agile pour le développement et le déploiement du Système Intégré de Gestion et de Contrôle de la Cour des Comptes (SIGEF-TC). Elle est organisée en sprints et jalons majeurs, avec une priorisation logique des modules. Les estimations de temps sont indicatives et devront être affinées.

## Principes Agiles
*   **Développement itératif et incrémental :** Livrer de la valeur fonctionnelle à chaque sprint.
*   **Collaboration étroite :** Implication continue des parties prenantes de la Cour des Comptes.
*   **Flexibilité et adaptation :** Capacité à ajuster les priorités en fonction des retours et des besoins émergents.
*   **Qualité intégrée :** Tests continus et validation à chaque étape.

## Durée des Sprints
*   **Sprints de 3 semaines** (recommandé pour un bon équilibre entre planification, développement et revue).

## Estimations de Temps
Les estimations sont données en nombre de sprints par module ou groupe de modules. Un sprint représente l'effort d'une équipe pluridisciplinaire (développement, test, UX/UI, PO).

## Priorisation des Modules
La priorisation vise à livrer rapidement les fondations techniques et les modules à plus forte valeur ajoutée ou à fort impact transversal.

---

## Roadmap Détaillée

### Phase 1 : Fondations et Modules Cœur (Estim. 6-9 mois)

**Sprint 0 : Cadrage & Environnement (1 Sprint)**
*   **Objectifs :**
    *   Finalisation du cadrage détaillé avec la Cour des Comptes.
    *   Mise en place de l'environnement de développement, de test et d'intégration continue (CI/CD).
    *   Choix techniques finaux (frameworks, outils spécifiques).
    *   Formation initiale de l'équipe projet aux processus de la Cour.
    *   Définition détaillée des users stories pour le premier lot de modules.
*   **Livrables :** Environnement technique opérationnel, backlog produit initial détaillé, charte projet validée.

**Sprint 1-3 : Plateforme d’Authentification et Gestion des Entités (Utilisateurs) (3 Sprints)**
*   **Objectifs :** Développement du socle de sécurité : SSO, gestion des utilisateurs, rôles et permissions de base.
*   **Fonctionnalités clés :** Authentification, gestion des comptes, rôles admin/utilisateur simple.
*   **Livrables :** Module d'authentification fonctionnel, API de gestion des utilisateurs/rôles.
*   **Jalon 1 : Socle de Sécurité Opérationnel.**

**Sprint 4-7 : Gestion Numérique des Documents (GND) - Version Initiale (4 Sprints)**
*   **Objectifs :** Fournir les fonctionnalités de base pour le stockage, la recherche et le versioning des documents. Essentiel pour de nombreux autres modules.
*   **Fonctionnalités clés :** Dépôt, recherche simple, versioning, plan de classement de base, droits d'accès.
*   **Livrables :** GND avec fonctionnalités de base, API pour intégration.

**Sprint 8-10 : Gestion des Ressources Humaines (RH) - Volet Administratif & Paie (3 Sprints)**
*   **Objectifs :** Gérer les dossiers employés, les contrats, et les éléments de base de la paie ou l'interface vers le système de paie.
*   **Fonctionnalités clés :** Dossier employé, gestion des contrats, absences simples, préparation des variables de paie.
*   **Livrables :** Module RH fonctionnel pour l'administration du personnel et la paie.
*   **Jalon 2 : Gestion Administrative RH et Documents de Base Opérationnels.**

---

### Phase 2 : Modules Métiers Clés (Estim. 9-12 mois)

**Sprint 11-14 : Gestion Financière - Comptabilité & Budget Internes (4 Sprints)**
*   **Objectifs :** Gérer la comptabilité interne de la Cour et le suivi de son propre budget.
*   **Fonctionnalités clés :** Comptabilité générale, suivi budgétaire interne, gestion des dépenses de la Cour.
*   **Livrables :** Module financier fonctionnel pour les opérations internes.

**Sprint 15-19 : E-Comptes / Traitement procédural - Version Initiale (5 Sprints)**
*   **Objectifs :** Dématérialiser une ou deux procédures types simples, de la saisine à la notification, en s'appuyant sur la GND et l'Authentification.
*   **Fonctionnalités clés :** Enregistrement d'affaire, gestion des pièces (via GND), workflow simple, notifications de base.
*   **Livrables :** Module E-Comptes pour 1-2 procédures, portail externe de base pour dépôt.
*   **Jalon 3 : Première Procédure Dématérialisée Opérationnelle.**

**Sprint 20-22 : Gestion des Entités (Contrôlées) et Plaintes - Volet Plaintes (3 Sprints)**
*   **Objectifs :** Mettre en place la réception et le suivi des plaintes. Le référentiel des entités sera initié.
*   **Fonctionnalités clés :** Formulaire de plainte en ligne, enregistrement, qualification, suivi simple.
*   **Livrables :** Système de gestion des plaintes fonctionnel.

---

### Phase 3 : Consolidation et Extension (Estim. 9-12 mois)

**Sprint 23-25 : Portail Intranet (3 Sprints)**
*   **Objectifs :** Fournir le point d'accès unifié aux modules existants, actualités, annuaire.
*   **Fonctionnalités clés :** SSO via Plateforme Auth, affichage news, annuaire (depuis RH), liens vers modules.
*   **Livrables :** Portail Intranet V1.

**Sprint 26-29 : Suivi Budgétaire (Comptes de l’État) - Version Initiale (4 Sprints)**
*   **Objectifs :** Mettre en place l'import et l'analyse de base des données d'exécution du budget de l'État.
*   **Fonctionnalités clés :** Import de données (manuel/semi-auto), tableaux de bord de base, comparaison prévisions/réalisations.
*   **Livrables :** Module de Suivi Budgétaire V1 avec premiers rapports.
*   **Jalon 4 : Capacités d'Analyse Budgétaire État et Intranet Opérationnels.**

**Sprint 30-32 : Interopérabilité - Connecteurs Clés (3 Sprints)**
*   **Objectifs :** Développer les connecteurs prioritaires (ex: pour Suivi Budgétaire État, pour RH État).
*   **Fonctionnalités clés :** Connecteurs pour MinFin, SIGRH État.
*   **Livrables :** Premiers flux d'échange de données automatisés.

**Sprint 33-35 : Gestion du Patrimoine (3 Sprints)**
*   **Objectifs :** Gérer l'inventaire des biens de la Cour.
*   **Fonctionnalités clés :** Inventaire, affectation, suivi de base.
*   **Livrables :** Module de gestion du patrimoine V1.

---

### Phase 4 : Enrichissement et Optimisation (Estim. 6-9 mois)

**Sprint 36-38 : Business Intelligence (BI) - Version Initiale (3 Sprints)**
*   **Objectifs :** Mettre en place les premiers tableaux de bord consolidés à partir des modules existants.
*   **Fonctionnalités clés :** ETL depuis 2-3 modules clés, premiers dashboards pour la Direction.
*   **Livrables :** Plateforme BI V1 avec quelques tableaux de bord.

**Sprint 39-40 : Bibliothèque Numérique (2 Sprints)**
*   **Objectifs :** Fournir l'accès au fonds documentaire de référence.
*   **Fonctionnalités clés :** Catalogue en ligne, recherche, consultation.
*   **Livrables :** Bibliothèque numérique V1.
*   **Jalon 5 : Capacités BI et Accès aux Connaissances Opérationnels.**

**Sprint 41-42 : Gestion des Fichiers (2 Sprints)**
*   **Objectifs :** Fournir l'espace de stockage de fichiers bruts.
*   **Fonctionnalités clés :** Stockage, partage simple.
*   **Livrables :** Module de gestion de fichiers V1.

**Sprint 43-45 : Application Mobile - Version Initiale (3 Sprints)**
*   **Objectifs :** Fournir les fonctionnalités mobiles prioritaires (notifications, validations simples).
*   **Fonctionnalités clés :** Notifications, consultation de tâches, validation de congés.
*   **Livrables :** Application mobile V1 (PWA ou natif).

---

### Phase 5 : Améliorations Continues et Finalisation (Flexible)

*   **Itérations sur E-Comptes :** Ajout de nouvelles procédures, enrichissement des fonctionnalités.
*   **Itérations sur GND :** Workflows avancés, signature électronique.
*   **Itérations sur BI :** Nouveaux dashboards, self-service.
*   **Itérations sur Interopérabilité :** Ajout de nouveaux connecteurs.
*   **Tests de performance et de sécurité globaux.**
*   **Formation approfondie des utilisateurs.**
*   **Préparation au déploiement final et à la mise en production généralisée.**
*   **Jalon Final : SIGEF-TC Complet et Déployé.**

## Livrables à Chaque Étape (Sprint Review)
*   Logiciel fonctionnel et testé pour les fonctionnalités du sprint.
*   Documentation mise à jour.
*   Démonstration des fonctionnalités réalisées.
*   Retours utilisateurs collectés pour le sprint suivant.

## Gestion de Projet et Outils
*   **Suivi des tâches :** Jira, Trello, Asana ou équivalent.
*   **Gestion de code source :** Git (GitHub, GitLab, Bitbucket).
*   **CI/CD :** Jenkins, GitLab CI, GitHub Actions.
*   **Communication :** Réunions quotidiennes (daily stand-ups), revues de sprint, rétrospectives.

---
Document préparé par : Primex Software
Rédigé par : Team Primex Software
URL : https://primex-software.com
Date : 2024-07-26
