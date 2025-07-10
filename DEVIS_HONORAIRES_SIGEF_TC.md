# Section 6 – Devis & Honoraires – Projet SIGEF-TC

---

## 6.1. Méthodologie de chiffrage (Révisée pour Contrainte Budgétaire)

L'estimation des charges pour la réalisation du projet SIGEF-TC a été révisée pour s'aligner sur la contrainte budgétaire de 450 000 USD. Cette révision maintient une approche modulaire et itérative, en cohérence avec la méthodologie Agile, mais met un accent accru sur l'optimisation des efforts et la livraison d'un Produit Minimum Viable (MVP) robuste pour chaque module dans les premières phases.

Notre méthodologie de chiffrage révisée se décompose comme suit :

1.  **Priorisation Stratégique des Fonctionnalités (MVP) :** Pour chaque module, les fonctionnalités ont été rigoureusement priorisées pour se concentrer sur le noyau essentiel (MVP) qui apporte le maximum de valeur ajoutée et répond aux besoins critiques de la Cour des Comptes. Les fonctionnalités secondaires ou "nice-to-have" sont envisagées pour des itérations ultérieures, potentiellement hors de cette enveloppe budgétaire initiale ou via des optimisations de gains de productivité.
2.  **Estimation par Module Optimisée :** L'estimation de la charge de travail par module en jours-homme (j.h) a été revue à la baisse. Cette optimisation repose sur :
    *   Un périmètre fonctionnel MVP plus strict pour la phase initiale.
    *   La capitalisation sur des composants réutilisables et des "patterns" de développement éprouvés.
    *   Une rationalisation des phases de conception et de documentation pour se concentrer sur l'essentiel requis pour le développement et la maintenance.
    *   Le développement (frontend et backend), les tests unitaires et d'intégration, ainsi que la documentation technique spécifique au module restent inclus.
3.  **Rationalisation des Charges Transverses :** Les charges pour les activités transverses ont été réévaluées pour optimiser les coûts tout en préservant les fonctions essentielles de pilotage, de qualité et de support :
    *   Gestion de projet Agile efficiente, avec des cérémonies optimisées.
    *   Expertise architecturale ciblée sur les points critiques.
    *   Stratégie de tests d'intégration et de performance focalisée sur les flux majeurs.
    *   Mutualisation des efforts de documentation et de formation.
4.  **Approche Agile Maintenue :** Le chiffrage reste basé sur l'effort pour compléter les "user stories" du MVP. La flexibilité Agile est conservée pour permettre des ajustements, mais dans le respect strict de l'enveloppe budgétaire globale. La roadmap sera adaptée pour refléter cette priorisation.
5.  **Unité de Mesure :** L'unité de mesure principale demeure le **jour-homme (j.h)**.

Cette méthodologie révisée vise à fournir une solution fonctionnelle et de qualité répondant aux besoins fondamentaux de la Cour des Comptes, tout en respectant la contrainte budgétaire fixée. Elle implique une collaboration étroite avec la Cour pour valider les priorités MVP et pour envisager des évolutions futures de manière phasée.

## 6.2. Estimation des charges (par module et global) (Révisée)

Les charges estimées ci-dessous sont exprimées en jours-homme (j.h) et ont été révisées pour s'inscrire dans l'enveloppe budgétaire globale de 450 000 USD. Cette révision implique un focus sur un Produit Minimum Viable (MVP) pour chaque module lors des phases initiales, avec une optimisation des efforts de développement.

*   **Module 01 – Gestion des Ressources Humaines (RH) :** 70 j.h
    *   *MVP : Gestion administrative de base, portail employé pour consultation, gestion simplifiée des absences.*
*   **Module 02 – Gestion Financière :** 80 j.h
    *   *MVP : Comptabilité générale essentielle, suivi budgétaire interne simplifié, gestion basique des dépenses.*
*   **Module 03 – Gestion du Patrimoine :** 50 j.h
    *   *MVP : Inventaire de base, suivi des affectations principales.*
*   **Module 04 – Gestion Numérique des Documents (GND) :** 90 j.h
    *   *MVP : Référentiel central, dépôt/consultation, versioning simple, recherche basique.*
*   **Module 05 – Gestion des Fichiers :** 30 j.h
    *   *MVP : Stockage et partage de fichiers de travail essentiels.*
*   **Module 06 – Gestion des Entités et Plaintes :** 60 j.h
    *   *MVP : Référentiel entités minimal, processus de base pour enregistrement et suivi des plaintes.*
*   **Module 07 – Bibliothèque Numérique :** 40 j.h
    *   *MVP : Catalogue en ligne avec recherche simple sur un fonds documentaire initial.*
*   **Module 08 – E-Comptes / Traitement procédural :** 120 j.h
    *   *MVP : Dématérialisation d'une procédure type principale, gestion des pièces via GND, workflow de base.*
*   **Module 09 – Application Mobile :** 60 j.h
    *   *MVP : Notifications clés, consultation de tâches urgentes (approche PWA privilégiée pour optimiser).*
*   **Module 10 – Portail Intranet :** 50 j.h
    *   *MVP : Accès aux modules, annuaire de base, diffusion d'actualités essentielles.*
*   **Module 11 – Suivi Budgétaire (Comptes de l’État) :** 70 j.h
    *   *MVP : Import manuel/semi-automatisé des données clés, tableaux de bord de suivi principaux.*
*   **Module 12 – Plateforme d’Authentification et Gestion des Entités (Utilisateurs) :** 70 j.h
    *   *MVP : SSO fonctionnel, gestion utilisateurs/rôles de base (sécurité non compromise).*
*   **Module 13 – Interopérabilité :** 70 j.h
    *   *MVP : Mise en place des 1 ou 2 connecteurs les plus critiques (ex: pour Suivi Budgétaire État).*
*   **Module 14 – Business Intelligence (BI) :** 75 j.h
    *   *MVP : ETL pour 1-2 modules sources, développement de quelques dashboards de direction essentiels.*

**Sous-Total Charges Modules Fonctionnels (Révisé) :** 935 j.h

---
**Charges Transverses (Révisées et Optimisées) :**

*   **Gestion de Projet et Coordination Agile :** 150 j.h
    *   *Pilotage resserré, focus sur la livraison MVP, communication optimisée.*
*   **Architecture Logicielle et Expertise Technique :** 60 j.h
    *   *Interventions ciblées sur les choix structurants et les points de blocage.*
*   **Tests d'Intégration Globaux & Assurance Qualité :** 80 j.h
    *   *Focus sur les flux critiques inter-modules et la validation du MVP.*
*   **Déploiement, Infra & DevOps (mutualisé) :** 50 j.h
    *   *Processus CI/CD optimisés, gestion d'environnements rationalisée.*
*   **Documentation Projet Globale (essentielle) :** 30 j.h
    *   *Concentration sur les manuels utilisateurs et d'administration du MVP.*
*   **Formation des Utilisateurs Clés (MVP) :** 40 j.h
    *   *Formation ciblée sur les fonctionnalités du MVP livré.*

**Sous-Total Charges Transverses (Révisé) :** 410 j.h

---
**Estimation Globale des Charges (Révisée) :**

*   Charge Modules Fonctionnels (MVP) : 935 j.h
*   Charge Transverses (Optimisées) : 410 j.h
*   **TOTAL ESTIMÉ DU PROJET (Révisé) : 1345 j.h**

Cette estimation révisée reflète un effort concentré sur la livraison d'un Produit Minimum Viable (MVP) robuste et fonctionnel pour chaque module, dans le respect de la nouvelle enveloppe budgétaire. Les fonctionnalités plus avancées ou les enrichissements pourront faire l'objet de phases ultérieures, après évaluation de la valeur apportée par ce premier périmètre.

## 6.3. Coût horaire ou forfaitaire (Révisé)

### Taux Journalier Moyen (TJM)
Pour s'aligner sur la contrainte budgétaire globale tout en maintenant une équipe qualifiée, le Taux Journalier Moyen (TJM) consolidé a été révisé. Ce taux continue de prendre en compte un mix de profils d'experts (architectes, développeurs, testeurs, chefs de projet). L'optimisation des coûts est également recherchée par une allocation judicieuse des ressources seniors sur les tâches critiques et l'encadrement efficace des profils plus juniors.

*   **Taux Journalier Moyen (TJM) Révisé : $334 USD / jour-homme**

Ce TJM révisé permet d'atteindre l'objectif budgétaire avec la charge de travail optimisée. Il reflète un engagement de Primex Software à fournir la meilleure valeur possible dans le cadre de l'enveloppe allouée, en s'appuyant sur des processus de développement efficients et une gestion de projet rigoureuse.

### Mode de Facturation
Le projet SIGEF-TC sera facturé en **régie contrôlée**, sur la base des jours-homme consommés et validés à la fin de chaque sprint ou période convenue.

**Justification du choix de la régie contrôlée (maintenue) :**
1.  **Adaptabilité Agile :** Essentielle pour un projet MVP qui évoluera avec les retours utilisateurs. La régie permet d'ajuster le périmètre des sprints sans renégociations lourdes, en se concentrant sur la livraison de valeur dans le respect de l'enveloppe globale.
2.  **Transparence et Suivi Budgétaire :** La facturation basée sur l'effort réel, avec des rapports d'activité clairs, permet à la Cour des Comptes un suivi précis de la consommation budgétaire par rapport aux estimations.
3.  **Collaboration Étroite :** Ce mode favorise l'implication continue de la Cour dans la priorisation et la validation, ce qui est crucial pour s'assurer que le MVP développé correspond aux attentes.
4.  **Maîtrise des Coûts dans un Cadre Contraint :** La "régie contrôlée" signifie que Primex Software s'engage à gérer le projet pour respecter le budget global de 450 000 USD pour le périmètre MVP défini. Un suivi conjoint et des alertes proactives seront mis en place pour toute déviation par rapport aux charges estimées par sprint/module, permettant des décisions rapides pour rester dans l'enveloppe.

L'objectif est de livrer un maximum de valeur fonctionnelle dans le cadre budgétaire défini, en utilisant la flexibilité de la régie pour optimiser les choix et les efforts tout au long du projet.

## 6.4. Tableau récapitulatif des coûts (Révisé)

Le tableau ci-dessous présente une synthèse des charges estimées révisées par module et pour les activités transverses, ainsi que les coûts correspondants calculés sur la base du Taux Journalier Moyen (TJM) révisé de **$334 USD**.

| Module / Activité                                         | Charge estimée (j.h) | Coût estimé (USD) |
|-----------------------------------------------------------|----------------------|-------------------|
| Module 01 – Gestion des Ressources Humaines (RH)          | 70                   | $23,380           |
| Module 02 – Gestion Financière                            | 80                   | $26,720           |
| Module 03 – Gestion du Patrimoine                         | 50                   | $16,700           |
| Module 04 – Gestion Numérique des Documents (GND)         | 90                   | $30,060           |
| Module 05 – Gestion des Fichiers                          | 30                   | $10,020           |
| Module 06 – Gestion des Entités et Plaintes               | 60                   | $20,040           |
| Module 07 – Bibliothèque Numérique                        | 40                   | $13,360           |
| Module 08 – E-Comptes / Traitement procédural             | 120                  | $40,080           |
| Module 09 – Application Mobile                            | 60                   | $20,040           |
| Module 10 – Portail Intranet                              | 50                   | $16,700           |
| Module 11 – Suivi Budgétaire (Comptes de l’État)          | 70                   | $23,380           |
| Module 12 – Plateforme d’Authentification & Gestion Entités | 70                   | $23,380           |
| Module 13 – Interopérabilité                              | 70                   | $23,380           |
| Module 14 – Business Intelligence (BI)                    | 75                   | $25,050           |
| **Sous-Total Modules Fonctionnels (MVP)**                 | **935**              | **$312,290**      |
|                                                           |                      |                   |
| Gestion de Projet et Coordination Agile (Optimisée)       | 150                  | $50,100           |
| Architecture Logicielle et Expertise Technique (Ciblée)   | 60                   | $20,040           |
| Tests d'Intégration Globaux & QA (Focus MVP)              | 80                   | $26,720           |
| Déploiement, Infra & DevOps (Mutualisé)                   | 50                   | $16,700           |
| Documentation Projet Globale (Essentielle)                | 30                   | $10,020           |
| Formation des Utilisateurs Clés (MVP)                     | 40                   | $13,360           |
| **Sous-Total Charges Transverses (Optimisées)**           | **410**              | **$136,940**      |
|                                                           |                      |                   |
| **TOTAL GLOBAL ESTIMÉ (Révisé)**                          | **1345**             | **$449,230**      |

**Remarques importantes (actualisées) :**
*   Les coûts estimés ci-dessus sont calculés pour atteindre un Produit Minimum Viable (MVP) robuste pour chaque module et pour les fonctions transverses essentielles, dans le respect de l'enveloppe budgétaire de 450 000 USD.
*   Ces coûts n'incluent pas les éventuels coûts de licences logicielles tierces (SGBD propriétaires, outils BI spécifiques si non open-source, etc.), les coûts d'infrastructure d'hébergement à long terme, ni les éventuels frais de déplacement ou de mission spécifiques qui seraient à convenir séparément.
*   Cette estimation est fournie à titre indicatif. Le mode de facturation en régie contrôlée impliquera un suivi des consommations réelles par rapport à ces estimations, avec des revues périodiques conjointes pour assurer l'alignement avec les objectifs budgétaires et fonctionnels du MVP.
*   Toute fonctionnalité additionnelle ou extension de périmètre au-delà du MVP défini devra faire l'objet d'une évaluation et d'un chiffrage complémentaires.

---
Rédigé par : Team Primex Software
