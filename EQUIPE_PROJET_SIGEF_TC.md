# 👥 Équipe Projet SIGEF-TC – Version Officielle Primex Software

## 🎯 Objectif de l'équipe
L'équipe projet SIGEF-TC a pour objectif principal la conception, le développement, et le déploiement réussi du Système Intégré de Gestion et de Contrôle de la Cour des Comptes, en respectant le périmètre MVP (Produit Minimum Viable) défini, l'enveloppe budgétaire de 450 000 USD, et la roadmap agile révisée. L'équipe vise à livrer une solution de haute qualité, répondant aux besoins critiques de la Cour des Comptes, tout en favorisant une collaboration étroite et une communication transparente avec toutes les parties prenantes.

## 🧩 Rôles et Profils Clés

| Rôle                                  | Description                                                                                                                                                                                             | Profil Cible (Primex Software ou Client)                                  |
| :------------------------------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :------------------------------------------------------------------------ |
| **Product Owner (PO)**                | Responsable de la vision du produit et de la maximisation de sa valeur. Définit et priorise le backlog produit (user stories) en collaboration avec les parties prenantes. Valide les fonctionnalités livrées. | Expert fonctionnel SIGEF-TC (Client/Cour des Comptes), accompagné par un Proxy PO Primex si besoin. |
| **Scrum Master (SM)**                 | Facilite les processus Agile et Scrum. Élimine les obstacles pour l'équipe. S'assure que l'équipe est productive et respecte les valeurs Agile. Coach l'équipe et l'organisation.                         | Consultant Agile expérimenté (Primex Software).                             |
| **Architecte Logiciel**               | Définit et maintient l'architecture technique globale du système. Garantit la cohérence, la performance, la sécurité et l'évolutivité de la solution. Guide les choix technologiques.                    | Architecte logiciel senior, expérimenté en systèmes complexes (Primex Software). |
| **Développeur Backend**               | Conçoit, développe et maintient la logique métier côté serveur, les API, et les interactions avec la base de données pour les modules SIGEF-TC.                                                            | Développeur expérimenté (Node.js/Laravel, PostgreSQL) (Primex Software).   |
| **Développeur Frontend**              | Conçoit, développe et maintient les interfaces utilisateur web et mobiles (si PWA). S'assure de l'ergonomie, de l'accessibilité et de la réactivité des interfaces.                                    | Développeur expérimenté (React/Vue.js) (Primex Software).                  |
| **Testeur / Ingénieur QA**            | Définit la stratégie de test. Conçoit, exécute les plans de test (manuels et automatisés si possible). Identifie et suit les anomalies. Garantit la qualité des livrables.                               | Ingénieur QA expérimenté, connaissance des outils de test (Primex Software). |
| **UX/UI Designer**                    | Conçoit l'expérience utilisateur globale et les interfaces graphiques. Crée les maquettes, les wireframes et les prototypes. S'assure de l'utilisabilité et de l'attractivité du système.             | UX/UI Designer (Primex Software, intervention ponctuelle/partagée).       |
| **Expert DevOps / Ingénieur Système** | Met en place et maintient l'infrastructure d'intégration continue et de déploiement continu (CI/CD). Gère les environnements, la configuration, le monitoring et l'automatisation des déploiements. | Ingénieur DevOps/Système expérimenté (Primex Software).                    |
| **Responsable Documentation**         | Supervise et participe à la création et à la maintenance de toute la documentation projet (technique, fonctionnelle, utilisateur). Assure sa cohérence et son accessibilité.                           | Rédacteur technique / Analyste fonctionnel (Primex Software, rôle partagé). |
| **Formateur Fonctionnel**             | Conçoit et dispense les formations aux utilisateurs finaux et aux administrateurs de la Cour des Comptes. Prépare les supports de formation.                                                              | Consultant/Formateur expérimenté sur des solutions similaires (Primex Software). |
| **Support utilisateur (N2/N3)**       | Fournit une assistance technique et fonctionnelle après la mise en production, en escalade des demandes non résolues par le support de premier niveau (interne à la Cour).                               | Équipe support Primex Software (post-projet ou contrat de maintenance).     |
| **Référents Fonctionnels Client**     | (Partie Prenante - Cour des Comptes) Experts métiers de la Cour des Comptes pour chaque domaine fonctionnel (RH, Finances, Greffe, etc.). Participent à la définition des besoins, aux tests et à la validation. | Personnel clé désigné par la Cour des Comptes.                            |
| **Chef de Projet Client**             | (Partie Prenante - Cour des Comptes) Point de contact principal côté Cour des Comptes, facilite la prise de décision, la disponibilité des référents métiers et la validation des livrables.                    | Cadre désigné par la Cour des Comptes.                                    |

## 📆 Répartition par Phase (basée sur la Roadmap Révisée – 23 Sprints)

**Durée des Sprints :** 3 semaines.

**Profils Permanents au sein de l'Équipe de Réalisation Agile (Primex Software) :**
*   Développeurs Backend (2)
*   Développeur Frontend (1)
*   Testeur / Ingénieur QA (1)
*(Ces 4 profils sont dédiés à 100% aux tâches de développement et de test des modules durant les sprints actifs sur ces modules).*

**Autres Profils Primex Software (implication variable selon les phases) :**

### Phase 1 – Fondations Techniques et Fonctionnelles MVP (Durée : ~5.25 mois | 7 Sprints)
*   **Objectif :** Socle technique (Auth, GND base), premiers modules fonctionnels (RH, Fichiers).
*   **Équipe type et implication estimée (Primex Software) :**
    *   **Product Owner (Coordination Primex) :** ~70% (forte implication pour définir le backlog MVP)
    *   **Scrum Master :** ~60% (mise en place des rituels, coaching initial)
    *   **Architecte Logiciel :** ~80% (définition architecture cible, choix structurants)
    *   **Développeurs Backend (2) :** 100%
    *   **Développeur Frontend (1) :** 100%
    *   **Testeur / Ingénieur QA (1) :** 100%
    *   **UX/UI Designer :** ~40-50% (maquettes initiales Auth, GND, RH, portails)
    *   **Expert DevOps :** ~50% (mise en place CI/CD, environnements initiaux)
    *   **Responsable Documentation :** ~20% (initiation structure documentaire, support)

### Phase 2 – Déploiement des Modules Métiers Centraux MVP (Durée : ~6 mois | 8 Sprints)
*   **Objectif :** MVP des modules métiers critiques (Finances, E-Comptes, Plaintes), Interop, début Suivi Budgétaire.
*   **Équipe type et implication estimée (Primex Software) :**
    *   **Product Owner (Coordination Primex) :** ~60% (priorisation continue, affinage backlog)
    *   **Scrum Master :** ~50% (maintien dynamique Agile, résolution d'obstacles)
    *   **Architecte Logiciel :** ~20% (support ponctuel, validation choix spécifiques)
    *   **Développeurs Backend (2) :** 100%
    *   **Développeur Frontend (1) :** 100%
    *   **Testeur / Ingénieur QA (1) :** 100%
    *   **UX/UI Designer :** ~20% (ajustements, nouveaux composants si besoin)
    *   **Expert DevOps :** ~30% (maintenance environnements, optimisation déploiements)
    *   **Responsable Documentation :** ~30% (documentation des modules livrés)

### Phase 3 – Finalisation du Périmètre MVP et Modules Complémentaires (Durée : ~6 mois | 8 Sprints)
*   **Objectif :** Compléter le MVP de tous les modules (Intranet, Patrimoine, Biblio, Mobile, BI), finaliser les tests globaux.
*   **Équipe type et implication estimée (Primex Software) :**
    *   **Product Owner (Coordination Primex) :** ~50% (validation finale, préparation au lancement)
    *   **Scrum Master :** ~50% (focus sur la finalisation et la préparation du bilan)
    *   **Architecte Logiciel :** ~10% (revue finale, support aux optimisations)
    *   **Développeurs Backend (2) :** 100%
    *   **Développeur Frontend (1) :** 100%
    *   **Testeur / Ingénieur QA (1) :** 100% (tests finaux, non-régression, performance)
    *   **UX/UI Designer :** ~15% (finalisation UI, support documentation)
    *   **Expert DevOps :** ~20% (préparation production, optimisation)
    *   **Responsable Documentation :** ~50% (finalisation manuels utilisateurs, admin)
    *   **Formateur Fonctionnel :** ~100% sur les 2-3 derniers sprints (préparation et dispense des formations MVP)

**Implication des Parties Prenantes (Cour des Comptes) :**
*   **Chef de Projet Client :** Implication constante et élevée tout au long du projet.
*   **Référents Fonctionnels Métiers :** Forte implication lors des phases de conception et de recette de leurs modules respectifs (ateliers, validation, tests UAT). Disponibilité nécessaire pour répondre aux questions de l'équipe Primex.

## 📊 Répartition des Charges Estimées par Profil (Primex Software)

La charge globale de **1345 jours-homme (j.h)** est répartie comme suit entre les profils de l'équipe Primex Software :

| Profil                                    | Jours-homme (j.h) Estimés | Pourcentage Approximatif du Projet |
| :---------------------------------------- | :------------------------ | :--------------------------------- |
| Product Owner (Primex - Coordination)     | 70                        | 5.2%                               |
| Scrum Master                              | 80                        | 6.0%                               |
| Architecte Logiciel                       | 60                        | 4.5%                               |
| Développeurs Backend (total pour 2)       | 515                       | 38.3%                              |
| Développeur Frontend (total pour 1)       | 300                       | 22.3%                              |
| Testeur / Ingénieur QA                    | 155                       | 11.5%                              |
| UX/UI Designer                            | 40                        | 3.0%                               |
| Expert DevOps / Ingénieur Système         | 50                        | 3.7%                               |
| Responsable Documentation (Rôle partagé)  | 30                        | 2.2%                               |
| Formateur Fonctionnel                     | 40                        | 3.0%                               |
| *Marge technique / Ajustements*           | *5*                       | *0.3%*                             |
| **TOTAL PRIMEX SOFTWARE**                 | **1345**                  | **100%**                           |

*Note : Les charges des développeurs et testeurs incluent leur participation aux rituels Agile et à la documentation technique spécifique aux modules.*

## 🏛️ Structure Organisationnelle (Simplifiée)

*   **Comité de Pilotage (COPIL - Cour des Comptes & Primex Software)**
    *   (Décisions stratégiques, suivi global)
*   **Chef de Projet Client (Cour des Comptes)**
    *   **Référents Fonctionnels Métiers (Cour des Comptes)**
*   **Chef de Projet Primex / PO Primex**
    *   **Scrum Master**
        *   **Équipe de Développement Agile (Primex Software)**
            *   Développeurs Backend (2)
            *   Développeur Frontend (1)
            *   Testeur / Ingénieur QA (1)
    *   **Architecte Logiciel (Primex Software)**
    *   **Experts Ponctuels (Primex Software)**
        *   UX/UI Designer
        *   Expert DevOps
        *   Responsable Documentation
        *   Formateur Fonctionnel

## 🛠️ Environnement de Travail et Outils

*   **Gestion de Projet Agile & Suivi des Tâches :** Jira (préféré) ou Trello.
*   **Gestion de Code Source & Versioning :** Git, avec dépôt sur GitHub ou GitLab.
*   **Intégration Continue / Déploiement Continu (CI/CD) :** GitHub Actions, Jenkins, ou GitLab CI.
*   **Communication d'Équipe :** Slack ou Microsoft Teams.
*   **Documentation Collaborative & Partage de Connaissances :** Confluence, SharePoint, ou Google Workspace.
*   **Maquettage UX/UI :** Figma, Adobe XD, ou Sketch.
*   **Tests Automatisés :** Frameworks adaptés aux technologies choisies (ex: Jest, Cypress pour le frontend; JUnit/PHPUnit, Postman/Newman pour le backend).

---
**Team Primex Software** – [https://primex-software.com](https://primex-software.com)
Date : 2024-07-26
