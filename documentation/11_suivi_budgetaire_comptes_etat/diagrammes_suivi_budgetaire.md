## Diagrammes UML : Suivi Budgétaire (Comptes de l’État)

### 1. Diagramme de Cas d’Usage

```mermaid
        +-----------------+     +----------------------+
        | Analyste        |---->| Importer Donnees     |
        | Budgétaire (Cour)|    | Execution Budget     |
        +-----------------+     +----------------------+
               |                             |
               | Analyse                     | (inclut <<Valider Donnees>>)
               v                             v
        +-----------------+     +----------------------+
        | Magistrat Cour  |---->| Consulter Tableaux   |
        +-----------------+     | de Bord Execution    |
               |                +----------------------+
               |                             |
               | Genere                      | (etend par <<Comparer avec Loi de Finances>>)
               v                             v
        +----------------------+     +----------------------+
        | Systeme Ministere    |<----| Generer Rapport      |
        | Finances (Source)    |     | d'Analyse            |
        +----------------------+     +----------------------+
               ^                             |
               |                             | (contribue à)
        +-----------------+     +----------------------+
        | Module Interop  |---->| Collecter Donnees    |
        +-----------------+     | (Automatiquement)    |
                                +----------------------+
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26

### 2. Diagramme de Classes Simplifié

```mermaid
        +-----------------+       +---------------------+
        | LoiFinances     |       | LigneExecutionBudget|
        +-----------------+       +---------------------+
        | - annee         | 1    *| - idLigne           |
        | - type (LFI,LFR)|------>| - codeProgramme     |
        | - refDocument   |       | - codeAction        |
        +-----------------+       | - montantExecute    |
                                  | - type (Dep/Rec)    |
        +-----------------+       | - dateExecution     |
        | ProgrammeBudget |       +---------------------+
        +-----------------+                | 1
        | - codeProgramme |                | Provient de
        | - libelle       |<---------------v
        | - dotationInitiale|       +---------------------+
        +-----------------+       | SourceDonnee        |
                                  +---------------------+
                                  | - nomSource (MinFin)|
                                  | - dateImport        |
                                  +---------------------+
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26

### 3. Diagramme d'Activités : Analyse d'exécution d'un programme budgétaire

```mermaid
graph TD
    A[Sélection Programme et Période] --> B[Import/Chargement Données d'Exécution];
    B --> C[Récupération Crédits Votés (Loi de Finances)];
    C --> D[Rapprochement Exécution vs. Voté];
    D --> E[Calcul des Écarts (montant, %)];
    E --> F{Écarts Significatifs?};
    F -- Oui --> G[Analyse Détaillée des Causes];
    G --> H[Rédaction Observation/Recommandation];
    H --> I[Génération Rapport d'Analyse du Programme];
    I --> J[Fin];
    F -- Non --> I;
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26
