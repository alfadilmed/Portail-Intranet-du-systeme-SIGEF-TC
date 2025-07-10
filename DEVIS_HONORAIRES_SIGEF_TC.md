# Section 6 – Devis & Honoraires – Projet SIGEF-TC

---

## 6.1. Méthodologie de chiffrage

L'estimation des charges pour la réalisation du projet SIGEF-TC a été établie en adoptant une approche modulaire et itérative, en cohérence avec la méthodologie Agile proposée dans la roadmap de réalisation.

Notre méthodologie de chiffrage se décompose comme suit :

1.  **Analyse Fonctionnelle Détaillée par Module :** Chaque module fonctionnel du SIGEF-TC, tel que défini dans la portée du projet, a fait l'objet d'une analyse pour identifier les fonctionnalités clés, les interfaces utilisateurs, les intégrations et la complexité technique intrinsèque.
2.  **Estimation par Module Basée sur l'Effort :** Pour chaque module, une estimation de la charge de travail a été réalisée en jours-homme (j.h). Cette estimation prend en compte les phases de :
    *   Conception technique détaillée.
    *   Développement (frontend et backend).
    *   Tests unitaires et d'intégration.
    *   Documentation technique spécifique au module.
    *   Participation aux revues de sprint et aux démonstrations.
3.  **Prise en Compte des Charges Transverses :** Des charges additionnelles ont été estimées pour les activités transverses indispensables au succès du projet, telles que :
    *   Gestion de projet et coordination Agile (Scrum Master, Product Owner côté Primex Software).
    *   Architecture logicielle et expertise technique transverse.
    *   Tests d'intégration globaux et tests de performance.
    *   Préparation des environnements (développement, test, pré-production).
    *   Formation des utilisateurs clés et administrateeurs.
    *   Rédaction de la documentation projet globale.
4.  **Approche Agile :** Le chiffrage est basé sur une estimation de l'effort nécessaire pour compléter les "user stories" prioritaires de chaque module pour atteindre un Produit Minimum Viable (MVP) pour les premières phases, puis des itérations d'enrichissement. La roadmap Agile (découpage en sprints) a servi de base pour séquencer ces efforts. La flexibilité inhérente à l'Agile permet d'ajuster les priorités, mais l'estimation globale vise à couvrir l'ensemble de la portée fonctionnelle initialement définie.
5.  **Unité de Mesure :** L'unité de mesure principale est le **jour-homme (j.h)**, représentant le travail d'un consultant qualifié sur une journée de 8 heures.

Cette méthode permet de fournir une estimation aussi réaliste que possible à ce stade du projet, tout en reconnaissant que des ajustements pourront être nécessaires au fur et à mesure de l'avancement et des retours des utilisateurs, conformément aux principes Agiles.

## 6.2. Estimation des charges (par module et global)

Les charges estimées ci-dessous sont exprimées en jours-homme (j.h) et couvrent la conception, le développement, les tests unitaires/intégration spécifiques au module, et la documentation technique associée. Ces estimations sont basées sur la complexité perçue de chaque module et les interdépendances identifiées.

*   **Module 01 – Gestion des Ressources Humaines (RH) :** 180 j.h
    *   *Comprend la gestion administrative, le portail employé/manager, la gestion des absences, et l'interface/module de paie.*
*   **Module 02 – Gestion Financière :** 200 j.h
    *   *Comprend la comptabilité générale/analytique, la gestion budgétaire interne, le suivi des dépenses et recettes de la Cour.*
*   **Module 03 – Gestion du Patrimoine :** 120 j.h
    *   *Inventaire, cycle de vie des actifs, maintenance, amortissements.*
*   **Module 04 – Gestion Numérique des Documents (GND) :** 220 j.h
    *   *Référentiel, versioning, workflows de validation, recherche avancée, archivage.*
*   **Module 05 – Gestion des Fichiers :** 80 j.h
    *   *Stockage de fichiers bruts, partage simple, interface explorateur.*
*   **Module 06 – Gestion des Entités et Plaintes :** 150 j.h
    *   *Référentiel entités contrôlées, processus de gestion des plaintes.*
*   **Module 07 – Bibliothèque Numérique :** 100 j.h
    *   *Catalogue en ligne, gestion du fonds documentaire, recherche.*
*   **Module 08 – E-Comptes / Traitement procédural :** 300 j.h
    *   *Module central et complexe, dématérialisation des dossiers, workflows procéduraux, portail externe.*
*   **Module 09 – Application Mobile :** 150 j.h
    *   *Notifications, consultations, validations simples (PWA ou natif).*
*   **Module 10 – Portail Intranet :** 130 j.h
    *   *CMS, actualités, annuaire, agrégation d'informations, accès aux modules.*
*   **Module 11 – Suivi Budgétaire (Comptes de l’État) :** 180 j.h
    *   *Import de données externes, analyse, reporting sur l'exécution du budget de l'État.*
*   **Module 12 – Plateforme d’Authentification et Gestion des Entités (Utilisateurs) :** 160 j.h
    *   *SSO, gestion des utilisateurs, rôles, permissions (socle technique essentiel).*
*   **Module 13 – Interopérabilité :** 170 j.h
    *   *Passerelle d'échanges, connecteurs systèmes externes, transformations de données.*
*   **Module 14 – Business Intelligence (BI) :** 190 j.h
    *   *Data Warehouse, ETL, tableaux de bord, reporting, self-service BI.*

**Sous-Total Charges Modules Fonctionnels :** 2330 j.h

---
**Charges Transverses :**

Ces charges sont essentielles pour la bonne conduite et la qualité globale du projet.

*   **Gestion de Projet et Coordination Agile :** 350 j.h
    *   *Suivi des sprints, planification, gestion des risques, communication, animation des cérémonies Agile.*
*   **Architecture Logicielle et Expertise Technique :** 150 j.h
    *   *Conception de l'architecture globale, choix techniques, support aux équipes de développement, revues de code.*
*   **Tests d'Intégration Globaux & Assurance Qualité (hors tests modules) :** 200 j.h
    *   *Tests des flux inter-modules, tests de performance, tests de sécurité (hors pentests spécifiques), validation fonctionnelle globale.*
*   **Déploiement, Infra & DevOps :** 120 j.h
    *   *Mise en place et maintenance des environnements, CI/CD, scripts de déploiement.*
*   **Documentation Projet Globale (hors doc modules) :** 80 j.h
    *   *Manuel utilisateur général, manuel d'administration, documentation d'exploitation.*
*   **Formation des Utilisateurs Clés et Administrateurs :** 100 j.h
    *   *Préparation des supports, sessions de formation.*

**Sous-Total Charges Transverses :** 1000 j.h

---
**Estimation Globale des Charges :**

*   Charge Modules Fonctionnels : 2330 j.h
*   Charge Transverses : 1000 j.h
*   **TOTAL ESTIMÉ DU PROJET : 3330 j.h**

Cette estimation globale représente l'effort total envisagé pour la réalisation complète du projet SIGEF-TC, de la conception à la mise en service et formation initiale. Elle sera ventilée et affinée au sein des différents sprints de la roadmap Agile.

## 6.3. Coût horaire ou forfaitaire

### Taux Journalier Moyen (TJM)
Pour l'estimation des coûts du projet SIGEF-TC, un Taux Journalier Moyen (TJM) consolidé est appliqué. Ce taux prend en compte la diversité des profils d'experts qui interviendront sur le projet (architectes, développeurs seniors/juniors, testeurs, chefs de projet, experts fonctionnels, etc.).

*   **Taux Journalier Moyen (TJM) : $400 USD / jour-homme**

Ce TJM est une moyenne pondérée reflétant l'expertise requise pour un projet de transformation numérique d'envergure pour une institution publique. Il est compétitif par rapport aux standards du marché pour des prestations de cette nature, garantissant l'accès à des ressources qualifiées et expérimentées.

### Mode de Facturation
Le projet SIGEF-TC sera, pour sa majeure partie, facturé en **régie contrôlée**, sur la base des jours-homme consommés et validés à la fin de chaque sprint ou période convenue.

**Justification du choix de la régie contrôlée :**
1.  **Adaptabilité Agile :** La nature Agile du projet implique que les priorités et le périmètre détaillé de certaines fonctionnalités peuvent évoluer au fil des sprints, en fonction des retours de la Cour des Comptes. La régie offre la flexibilité nécessaire pour s'adapter à ces ajustements sans nécessiter de renégociations contractuelles complexes à chaque changement.
2.  **Transparence :** Ce mode de facturation assure une transparence totale sur l'effort réellement consommé. Des rapports d'activité détaillés seront fournis, permettant à la Cour de suivre précisément l'avancement et l'utilisation du budget.
3.  **Collaboration et Implication Client :** La régie favorise une collaboration étroite entre Primex Software et la Cour des Comptes. L'implication continue du client dans la validation des travaux et la définition des priorités est un facteur clé de succès pour les projets Agiles.
4.  **Maîtrise des Coûts :** Bien que la régie soit basée sur le temps passé, la "régie contrôlée" implique un suivi rigoureux des charges par rapport aux estimations initiales par module et par sprint. Des mécanismes d'alerte et de revue conjointe seront mis en place pour anticiper et gérer tout dépassement potentiel par rapport au budget global estimé.

Certains livrables très clairement définis et délimités en amont (par exemple, une phase d'audit spécifique ou un module très standardisé) pourraient éventuellement faire l'objet d'un chiffrage forfaitaire après accord mutuel, mais l'approche principale reste la régie contrôlée pour garantir la souplesse requise par la méthodologie Agile.

## 6.4. Tableau récapitulatif des coûts

Le tableau ci-dessous présente une synthèse des charges estimées par module et pour les activités transverses, ainsi que les coûts correspondants calculés sur la base du Taux Journalier Moyen (TJM) de **$400 USD**.

| Module / Activité                                         | Charge estimée (j.h) | Coût estimé (USD) |
|-----------------------------------------------------------|----------------------|-------------------|
| Module 01 – Gestion des Ressources Humaines (RH)          | 180                  | $72,000           |
| Module 02 – Gestion Financière                            | 200                  | $80,000           |
| Module 03 – Gestion du Patrimoine                         | 120                  | $48,000           |
| Module 04 – Gestion Numérique des Documents (GND)         | 220                  | $88,000           |
| Module 05 – Gestion des Fichiers                          | 80                   | $32,000           |
| Module 06 – Gestion des Entités et Plaintes               | 150                  | $60,000           |
| Module 07 – Bibliothèque Numérique                        | 100                  | $40,000           |
| Module 08 – E-Comptes / Traitement procédural             | 300                  | $120,000          |
| Module 09 – Application Mobile                            | 150                  | $60,000           |
| Module 10 – Portail Intranet                              | 130                  | $52,000           |
| Module 11 – Suivi Budgétaire (Comptes de l’État)          | 180                  | $72,000           |
| Module 12 – Plateforme d’Authentification & Gestion Entités | 160                  | $64,000           |
| Module 13 – Interopérabilité                              | 170                  | $68,000           |
| Module 14 – Business Intelligence (BI)                    | 190                  | $76,000           |
| **Sous-Total Modules Fonctionnels**                       | **2330**             | **$932,000**      |
|                                                           |                      |                   |
| Gestion de Projet et Coordination Agile                   | 350                  | $140,000          |
| Architecture Logicielle et Expertise Technique            | 150                  | $60,000           |
| Tests d'Intégration Globaux & QA                          | 200                  | $80,000           |
| Déploiement, Infra & DevOps                               | 120                  | $48,000           |
| Documentation Projet Globale                              | 80                   | $32,000           |
| Formation des Utilisateurs Clés et Administrateurs        | 100                  | $40,000           |
| **Sous-Total Charges Transverses**                        | **1000**             | **$400,000**      |
|                                                           |                      |                   |
| **TOTAL GLOBAL ESTIMÉ**                                   | **3330**             | **$1,332,000**    |

**Remarques importantes :**
*   Les coûts estimés ci-dessus n'incluent pas les éventuels coûts de licences logicielles tierces (ex: SGBD propriétaires, outils BI spécifiques si non open-source, etc.), les coûts d'infrastructure d'hébergement, ni les éventuels frais de déplacement ou de mission spécifiques qui seraient à convenir séparément.
*   Cette estimation est fournie à titre indicatif à ce stade du projet. Le mode de facturation en régie contrôlée impliquera un suivi des consommations réelles par rapport à ces estimations, avec des revues périodiques.
*   Une marge de contingence de 10-15% est souvent recommandée pour les projets de cette ampleur pour couvrir les imprévus ou les ajustements de périmètre mineurs, bien qu'elle ne soit pas explicitement incluse dans chaque ligne de ce tableau.

---
Rédigé par : Team Primex Software
