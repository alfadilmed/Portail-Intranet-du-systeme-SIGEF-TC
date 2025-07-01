## Diagrammes UML : Gestion du Patrimoine

### 1. Diagramme de Cas d’Usage

```mermaid
        +---------------------+     +----------------------+
        | Gestionnaire        |---->| Enregistrer Bien     |
        | du Patrimoine       |     +----------------------+
        +---------------------+              |
               |                             | (inclut)
               | Affecte                     v
               v                      +----------------------+
        +---------------------+     | Identifier Bien      |
        | Agent Cour          |<----| (par code-barres)  |
        +---------------------+     +----------------------+
               | (Utilise bien)              |
               |                             | (etend)
        +---------------------+     +----------------------+
        | Technicien          |---->| Suivre Maintenance   |
        | de Maintenance      |     +----------------------+
        +---------------------+              |
               |                             | Notifie
               v                             v
        +---------------------+     +----------------------+
        | Module Financier    |<----| Calculer Amortissmt  |
        +---------------------+     +----------------------+
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26

### 2. Diagramme de Classes Simplifié

```mermaid
        +-----------------+       +-----------------+
        | BienPatrimoine  |       | Affectation     |
        +-----------------+       +-----------------+
        | - idBien        | 1    *| - idAffectation |
        | - designation   |------>| - dateAffect    |
        | - dateAcq       |       | - lieu          |
        | - valeurAcq     |       | - utilisateur   |
        | - etat          |       +-----------------+
        | + Creer()       |
        | + Sortir()      |
        +-----------------+
               | 1
               | Appartient
               v *
        +-----------------+       +-----------------+
        | CategorieBien   |       | Maintenance     |
        +-----------------+       +-----------------+
        | - idCategorie   | 1    *| - idMaintenance |
        | - libelle       |<------| - dateInterv    |
        +-----------------+       | - typeInterv    |
                                  | - cout          |
                                  | + Planifier()   |
                                  +-----------------+
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26

### 3. Diagramme d'Activités : Processus d'acquisition d'un nouveau bien

```mermaid
graph TD
    A[Demande d'Achat Bien] --> B[Validation Achat (Financier)];
    B -- Approuvé --> C[Réception du Bien];
    C --> D[Vérification Conformité Bien];
    D -- Conforme --> E[Enregistrement du Bien];
    E --> F[Attribution Identifiant Unique];
    F --> G[Saisie Caractéristiques (valeur, etc.)];
    G --> H[Affectation Initiale (Service, Lieu)];
    H --> I[Mise à jour Inventaire];
    I --> J[Notification au Gestionnaire Patrimoine];
    J --> K[Fin];
    B -- Rejeté --> K;
    D -- Non Conforme --> L[Retour Fournisseur];
    L --> K;
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26
