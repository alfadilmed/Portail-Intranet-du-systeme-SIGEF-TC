# Documentation Fonctionnelle & Technique : E-Comptes / Traitement procédural

## Objectif du module

Le module E-Comptes / Traitement procédural est au cœur des activités juridictionnelles et de contrôle de la Cour des Comptes. Il vise à dématérialiser et à gérer l'ensemble du cycle de vie des dossiers de contrôle, d'audit, de jugement des comptes, et autres procédures relevant de la compétence de la Cour. Cela inclut la saisine, l'instruction, les échanges contradictoires, la tenue des audiences (si applicable), la délibération, la notification des arrêts/rapports, et le suivi de leur exécution.

## Acteurs concernés

*   Magistrats de la Cour des Comptes (Présidents de chambre, Conseillers, Auditeurs)
*   Greffiers (pour la gestion administrative et procédurale des dossiers)
*   Rapporteurs
*   Entités contrôlées / justiciables (pour la soumission de pièces, réponses aux communications)
*   Avocats ou représentants des justiciables
*   Personnel administratif supportant les procédures

## Cas d’usage

*   **Enregistrement des affaires/dossiers :** Saisine de la Cour, ouverture de nouveaux dossiers de contrôle ou de jugement.
*   **Constitution du dossier numérique :** Dépôt et organisation des pièces (comptes, pièces justificatives, correspondances, notes d'instruction).
*   **Instruction des dossiers :** Désignation de rapporteur, planification des actes d'instruction, demandes de pièces complémentaires, auditions.
*   **Communication des griefs / observations :** Notification aux entités contrôlées ou aux justiciables.
*   **Gestion des échanges contradictoires :** Réception et gestion des réponses, mémoires, observations des parties.
*   **Planification et gestion des audiences** (si applicable).
*   **Préparation des projets d'arrêts ou de rapports.**
*   **Processus de délibération** (enregistrement des décisions).
*   **Notification des arrêts et rapports définitifs.**
*   **Suivi de l'exécution des décisions/recommandations.**
*   **Gestion des délais procéduraux.**
*   **Archivage des dossiers clos.**

## Fonctionnalités clés

*   **Dossier numérique unique et sécurisé par affaire.**
*   **Workflow procédural configurable** adapté aux différents types de contentieux/contrôles.
*   **Gestion des rôles et des habilitations** très fine pour l'accès aux dossiers et aux fonctionnalités.
*   **Tableau de bord pour chaque acteur** (Magistrat, Greffier) avec les tâches à accomplir, les échéances.
*   **Suivi de l'état d'avancement de chaque dossier.**
*   **Module de gestion des pièces :** Dépôt, indexation, recherche, liaison avec les actes de procédure.
*   **Outils de communication sécurisée** avec les parties externes (portail justiciable/entité contrôlée).
*   **Génération de documents types** (notifications, convocations, projets d'arrêts).
*   **Signature électronique des actes et décisions.**
*   **Calcul et suivi des délais légaux et réglementaires.**
*   **Journal d'audit complet de toutes les actions** au sein d'un dossier.
*   **Fonctionnalités de recherche avancée** dans les dossiers et les pièces.
*   **Gestion des intervenants** (parties, avocats, experts).
*   **Module de préparation et de suivi des délibérations.**
*   **Historique complet de la procédure.**

## Interfaces attendues

*   **Interface utilisateur web sécurisée et dédiée** pour les acteurs internes de la Cour (Magistrats, Greffiers).
*   **Portail externe sécurisé** pour les entités contrôlées/justiciables permettant :
    *   La consultation des communications de la Cour.
    *   Le dépôt de réponses et de pièces.
    *   Le suivi de l'état de leur dossier (informations limitées).
*   **API** pour l'intégration avec d'autres modules (GND pour les pièces, Gestion des Entités, BI).

## Diagramme fonctionnel simplifié (UML si possible)

```mermaid
graph TD
    A[Greffe/Saisine] -- Crée dossier --> B(Système E-Comptes/Traitement Procédural);
    B -- Gère Pièces (via GND) & Métadonnées Procédurales --> C[Dossier Numérique de l'Affaire];
    D[Magistrat/Rapporteur] -- Instruit/Analyse dossier --> C;
    D -- Prépare projets (Arrêts/Rapports) --> C;
    B -- Notifie (Communications/Griefs) --> E[Portail Externe (Entité/Justiciable)];
    E -- Reçoit réponses/pièces --> B;
    B -- Gère Workflow Procédural (Délais, Étapes) --> F[Moteur de Workflow];
    B -- Gère Audiences/Délibérations --> G[Module Audience/Délibération];
    G -- Enregistre Décisions --> C;
    B -- Notifie Décisions Finales --> E;
    H[Système d'Authentification] -- Authentifie --> D;
    H -- Authentifie --> A;
    H -- Authentifie (spécifique) --> E;
    I[Module GND] -- Stocke/Versionne pièces --> C;
    J[Module Gestion Entités] -- Fournit infos sur --> E;
```

## Contraintes techniques ou juridiques

*   **Très haute sécurité et confidentialité des données procédurales.**
*   **Respect strict des règles de procédure et des droits de la défense.**
*   **Inaltérabilité et force probante des actes et décisions numériques** (signature électronique, horodatage qualifié).
*   **Traçabilité absolue de toutes les actions.**
*   **Gestion des habilitations extrêmement rigoureuse.**
*   **Disponibilité critique du système.**
*   **Archivage légal des dossiers judiciaires/de contrôle.**
*   **Conformité aux lois sur la dématérialisation des procédures judiciaires/administratives.**

## Dépendances avec d’autres modules

*   **Gestion Numérique des Documents (GND) :** Indispensable pour le stockage sécurisé, le versioning et l'archivage de toutes les pièces des dossiers. Le module E-Comptes gère la logique procédurale autour de ces documents.
*   **Plateforme d’Authentification et Gestion des Entités :** Pour l'authentification forte des acteurs internes et l'authentification des utilisateurs du portail externe. Le module "Gestion des Entités" fournit les informations sur les parties concernées.
*   **Gestion des Entités et Plaintes :** Une plainte peut être à l'origine d'une procédure gérée dans E-Comptes. Le référentiel des entités est utilisé.
*   **Business Intelligence (BI) :** Pour l'analyse statistique de l'activité juridictionnelle/de contrôle (délais moyens, types d'affaires, résultats).
*   **Portail Intranet :** Peut fournir un accès au module pour les utilisateurs internes.
*   **Bibliothèque Numérique :** Peut être consultée par les magistrats lors de l'instruction des affaires.
*   **Application Mobile :** Consultation de l'état des dossiers, notifications pour les magistrats.

## Spécifications API (si applicables)

*   **API RESTful interne** pour :
    *   Interagir avec la GND pour la gestion des pièces.
    *   Récupérer des informations sur les entités depuis le module dédié.
    *   Envoyer des données agrégées au module BI.
*   **Endpoints pour :**
    *   `/cases` : Gestion des dossiers/affaires.
    *   `/cases/{id}/documents` : Liaison avec les documents dans la GND.
    *   `/cases/{id}/actors` : Gestion des parties prenantes.
    *   `/cases/{id}/workflow` : Suivi et avancement dans le workflow procédural.
    *   `/notifications` : Gestion des communications avec le portail externe.
*   **Authentification via OAuth2 (flux sécurisés).**
*   **Chiffrement des données sensibles en transit et au repos.**
*   **API spécifique pour le portail externe** (sécurisée et limitée aux fonctionnalités nécessaires).

---
Document préparé par : Primex Software
Rédigé par : Team Primex Software
URL : https://primex-software.com
Date : 2024-07-26
