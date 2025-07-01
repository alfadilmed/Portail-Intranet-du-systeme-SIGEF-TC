# Fiche Module : Suivi Budgétaire (Comptes de l’État)

## Nom du module (officiel)
Suivi Budgétaire (Comptes de l’État)

## Objectif
Permettre à la Cour des Comptes d'exercer sa mission de contrôle de l'exécution du budget de l'État en collectant, analysant et suivant les données des lois de finances (recettes, dépenses) et en produisant des rapports. Distinct de la gestion financière interne de la Cour.

## Fonctionnalités
*   Importation et intégration des données d'exécution budgétaire de l'État (manuelle ou via Interopérabilité).
*   Contrôle de conformité de l'exécution par rapport aux autorisations.
*   Analyse des écarts prévisions/réalisations.
*   Suivi des dépenses (par ministère, programme, nature) et des recettes (par type, source).
*   Analyse de la soutenabilité budgétaire et de la dette.
*   Production de synthèses, tableaux de bord, visualisations.
*   Identification des risques/anomalies dans la gestion budgétaire de l'État.
*   Aide à la préparation du Rapport sur l'Exécution de la Loi de Finances (RELF).
*   Gestion des nomenclatures budgétaires de l'État.

## Données en entrée
*   Fichiers de données d'exécution budgétaire de l'État (provenant du Ministère des Finances, DGCI, etc.).
*   Lois de finances initiales et rectificatives.
*   Nomenclatures budgétaires et comptables de l'État.
*   Données macroéconomiques pertinentes.

## Données en sortie
*   Base de données consolidée de l'exécution budgétaire de l'État.
*   Rapports d'analyse des écarts.
*   Tableaux de bord sur l'exécution des recettes et dépenses.
*   Visualisations graphiques des tendances budgétaires.
*   Observations et recommandations de la Cour.
*   Contributions au RELF.

## Règles de gestion spécifiques
*   Mapping entre les nomenclatures de l'État et la structure d'analyse de la Cour.
*   Règles de validation et de contrôle de cohérence des données importées.
*   Méthodologies de calcul des indicateurs d'exécution budgétaire.
*   Périodicité de la collecte et de l'analyse des données.

## UI/UX wireframe simplifié (si pertinent)
*   **Tableau de bord "Exécution Globale" :** KPIs (Taux d'exécution des dépenses/recettes global), graphiques (Évolution des dépenses par grand ministère, Structure des recettes).
*   **Interface d'analyse de programme budgétaire :** Sélection d'un programme, affichage des crédits ouverts, consommés, disponibles, écarts, avec possibilité de drill-down par action/sous-action.
*   **Module d'importation de données :** Sélectionner source, type de fichier, période, bouton "Importer", suivi de l'importation.

## Critères d’acceptation
*   Les données d'exécution budgétaire d'une période peuvent être importées et validées.
*   Un rapport comparant les dépenses autorisées et exécutées pour un ministère peut être généré.
*   Un tableau de bord montrant l'évolution des recettes fiscales sur plusieurs années est disponible.
*   Le système alerte en cas d'écart significatif non justifié sur un programme.
*   Les données nécessaires à la section "analyse de l'exécution budgétaire" du RELF peuvent être extraites.

## Points de vigilance
*   Qualité, disponibilité et ponctualité des données sources de l'État.
*   Complexité et hétérogénéité des systèmes d'information financiers de l'État.
*   Adaptabilité aux changements de nomenclatures ou de lois de finances.
*   Sécurité des données financières sensibles de l'État.
*   Besoin de compétences pointues en finances publiques pour l'analyse.

## Technologies envisagées
*   **Backend :** Node.js (Express) ou Laravel, potentiellement avec des outils ETL.
*   **Frontend :** React.js ou Vue.js.
*   **Base de données :** PostgreSQL, potentiellement une base de données orientée colonnes pour l'analytique (ex: ClickHouse) si volumes très importants.
*   **API :** RESTful (pour l'import via Interopérabilité et l'export vers BI).
*   **Outils de visualisation :** Bibliothèques JS (D3.js, Chart.js) ou intégration avec le module BI.

---
Document préparé par : Primex Software
Rédigé par : Team Primex Software
URL : https://primex-software.com
Date : 2024-07-26
