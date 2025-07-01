## Diagrammes UML : Business Intelligence (BI)

### 1. Diagramme de Cas d’Usage

```mermaid
        +-----------------+     +----------------------+
        | Analyste BI /   |---->| Creer Tableau de Bord|
        | Utilisateur Avce|     +----------------------+
        +-----------------+              |
               |                         | (inclut <<Definir KPIs>>)
               | Consulte                | (utilise <<Data Warehouse>>)
               v                         v
        +-----------------+     +----------------------+
        | Decider (Direction|---->| Consulter Rapport    |
        | Chef Service)   |     | Strategique          |
        +-----------------+     +----------------------+
               |                             |
               |                             | (etend par <<Exporter Donnees PDF/Excel>>)
               v                             v
        +-----------------+     +----------------------+
        | Processus ETL   |---->| Alimenter Data       |
        +-----------------+     | Warehouse            |
               ^                  +----------------------+
               | (Fournit donnees)           |
        +-----------------+                  |
        | Modules SIGEF-TC|------------------+
        | (Sources)       |
        +-----------------+
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26

### 2. Diagramme de Classes Simplifié (Focus sur Data Warehouse et Rapport)

```mermaid
        +-----------------+       +-----------------+
        | Fait            |       | Dimension       |
        | (ex: F_Depenses)|       +-----------------+
        +-----------------+       | - idDim         |
        | - idDimTemps    |------>| - attribut1     |
        | - idDimService  |------>| - attribut2     |
        | - mesure1       |       +-----------------+
        | - mesure2       |         (ex: D_Temps, D_Service)
        +-----------------+
               | 1..*
               | Utilise
               v 1
        +-----------------+       +-----------------+
        | RapportBI       |       | KPI             |
        +-----------------+       +-----------------+
        | - idRapport     | 1    *| - idKPI         |
        | - titre         |<------| - nomKPI        |
        | - type          |       | - formuleCalcul |
        | (Dashboard,     |       | - seuilAlerte   |
        |  Pagine)        |       +-----------------+
        | + Generer()     |
        | + Exporter()    |
        +-----------------+
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26

### 3. Diagramme d'Activités : Processus ETL quotidien (simplifié)

```mermaid
graph TD
    A[Début Planification ETL (Nuit)] --> B[Extraction Données Module RH];
    B --> C[Transformation Données RH];
    C --> D[Chargement Données RH dans DW];

    A --> E[Extraction Données Module Financier];
    E --> F[Transformation Données Financier];
    F --> G[Chargement Données Financier dans DW];

    A --> H[Extraction Données Module E-Comptes];
    H --> I[Transformation Données E-Comptes];
    I --> J[Chargement Données E-Comptes dans DW];

    D --> K[Validation et Contrôle Qualité Post-Chargement];
    G --> K;
    J --> K;

    K --> L[Mise à Jour des Agrégats/Cubes OLAP];
    L --> M[Notification Fin ETL];
    M --> N[Fin];
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26
