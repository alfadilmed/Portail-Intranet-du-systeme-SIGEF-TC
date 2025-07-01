# Documentation Fonctionnelle & Technique : Gestion des Ressources Humaines (RH)

## Objectif du module

L'objectif du module de Gestion des Ressources Humaines (RH) est de fournir une plateforme centralisée pour gérer l'ensemble du cycle de vie des employés de la Cour des Comptes, de leur recrutement à leur départ, en passant par la gestion de leur carrière, de leurs absences, de leurs compétences et de leur paie.

## Acteurs concernés

*   Administrateurs RH
*   Gestionnaires RH
*   Employés de la Cour des Comptes
*   Responsables de départements/services
*   Auditeurs (pour consultation des données RH pertinentes)

## Cas d’usage

*   **Recrutement :** Publication d'offres, gestion des candidatures, planification des entretiens, sélection des candidats.
*   **Gestion administrative du personnel :** Création et mise à jour des dossiers employés, gestion des contrats, suivi des périodes d'essai.
*   **Gestion des temps et des absences :** Suivi des congés, RTT, arrêts maladie, gestion des plannings.
*   **Gestion de la paie :** Calcul des salaires, génération des bulletins de paie, gestion des déclarations sociales.
*   **Gestion des carrières et des compétences :** Suivi des évaluations, gestion des formations, plans de développement individuels.
*   **Départ de l'employé :** Gestion des démissions, licenciements, départs à la retraite, solde de tout compte.

## Fonctionnalités clés

*   **Base de données employés centralisée :** Informations personnelles, contractuelles, administratives.
*   **Portail employé :** Accès aux informations personnelles, demandes de congés, consultation des bulletins de paie.
*   **Portail manager :** Validation des demandes de congés, suivi des équipes, accès aux évaluations.
*   **Gestion des recrutements :** De la publication de l'offre à l'embauche.
*   **Gestion des congés et absences :** Workflows de demande et validation.
*   **Module de paie intégré ou interfacé :** Calcul et édition des fiches de paie.
*   **Gestion des formations :** Catalogue de formations, inscriptions, suivi.
*   **Gestion des évaluations :** Campagnes d'évaluation, formulaires, suivi des objectifs.
*   **Reporting RH :** Tableaux de bord, indicateurs clés (effectifs, turnover, absentéisme).
*   **Gestion documentaire RH :** Stockage sécurisé des documents relatifs aux employés (contrats, avenants, etc.).

## Interfaces attendues

*   **Interface utilisateur web responsive** pour les administrateurs, gestionnaires et employés.
*   **API** pour l'intégration avec d'autres modules (ex: Gestion Financière pour la paie, Plateforme d'Authentification).
*   **Interface d'import/export de données** (ex: pour la paie, pour les données de l'annuaire).

## Diagramme fonctionnel simplifié (UML si possible)

```mermaid
graph TD
    A[Utilisateur (Employé/Manager/Admin RH)] -- Accède au portail --> B(Portail RH);
    B -- Gère données personnelles --> C[Base de Données Employés];
    B -- Demande/Valide congés --> D[Gestion des Temps & Absences];
    D -- Met à jour --> C;
    B -- Gère carrière/formation --> E[Gestion Carrières & Compétences];
    E -- Met à jour --> C;
    F[Admin RH] -- Gère recrutement --> G[Module Recrutement];
    G -- Crée nouvel employé --> C;
    F -- Gère paie --> H[Module Paie];
    H -- Récupère données --> C;
    H -- Interagit avec --> I[Système Financier Externe/Module];
    J[Système d'Authentification] -- Authentifie --> B;
    C -- Fournit données pour reporting --> K[Reporting RH];
```

## Contraintes techniques ou juridiques

*   **Sécurité des données personnelles :** Conformité avec le RGPD et les lois locales sur la protection des données.
*   **Confidentialité des informations salariales et personnelles.**
*   **Traçabilité des actions :** Journalisation des modifications importantes.
*   **Disponibilité et performance** du système, notamment pour le portail employé.
*   **Intégration avec les systèmes de paie existants ou futurs.**
*   **Archivage légal** des documents RH.

## Dépendances avec d’autres modules

*   **Plateforme d’Authentification et Gestion des Entités :** Pour l'authentification des utilisateurs et la gestion des droits d'accès.
*   **Gestion Financière :** Pour la transmission des informations de paie et le suivi des coûts liés aux RH.
*   **Gestion Numérique des Documents :** Pour le stockage et l'archivage des documents RH.
*   **Portail Intranet :** Pour la diffusion d'informations RH générales et l'accès au module RH.
*   **Business Intelligence (BI) :** Pour l'analyse avancée des données RH et la création de rapports personnalisés.

## Spécifications API (si applicables)

*   **API RESTful** pour les opérations CRUD sur les entités RH (employés, contrats, absences, etc.).
*   **Endpoints pour :**
    *   `/employees` : Gestion des employés.
    *   `/leaves` : Gestion des demandes de congés.
    *   `/recruitments` : Gestion des processus de recrutement.
    *   `/payrolls` : Accès aux données de paie (potentiellement limité).
    *   `/trainings` : Gestion des formations.
*   **Authentification via OAuth2** (jetons Bearer).
*   **Formats de données :** JSON.
*   **Versioning de l'API.**

---
Document préparé par : Primex Software
Rédigé par : Team Primex Software
URL : https://primex-software.com
Date : 2024-07-26
