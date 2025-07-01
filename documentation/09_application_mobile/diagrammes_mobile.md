## Diagrammes UML : Application Mobile

### 1. Diagramme de Cas d’Usage

```mermaid
        +-----------------+     +----------------------+
        | Agent Cour      |---->| Se Connecter (Mobile)|
        | (en déplacement)|     +----------------------+
        +-----------------+              |
               |                         | (inclut <<Synchro Donnees>>)
               | Consulte                v
        +-----------------+     +----------------------+
        | Utilisateur     |---->| Recevoir Notification|
        | Mobile          |     +----------------------+
        +-----------------+              |
               |                         | (etend par <<Consulter Detail Tache>>)
               | Valide                  v
        +-----------------+     +----------------------+
        | Module RH/Finance|<----| Valider Demande      |
        | (Backend)       |     | (Conge/Depense)      |
        +-----------------+     +----------------------+
               ^                         |
               |                         |
        +-----------------+     +----------------------+
        | Module E-Comptes|<----| Consulter Etat Doss. |
        | (Backend)       |     +----------------------+
        +-----------------+
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26

### 2. Diagramme de Classes Simplifié (Focus sur données locales)

```mermaid
        +-----------------+       +-----------------+
        | Notification    |       | TacheMobile     |
        +-----------------+       +-----------------+
        | - idNotif       |       | - idTache       |
        | - titre         |       | - description   |
        | - message       |       | - type (Validat°)|
        | - date          |       | - statut        |
        | - lu (boolean)  |       | - lienModuleSrc |
        | + MarquerCommeLu()|       | + Valider()     |
        +-----------------+       +-----------------+
               | *                          | *
               |                            |
        +----------------------+  +----------------------+
        | DonneesSynchronisees |  | ConfigurationApp     |
        +----------------------+  +----------------------+
        | - dernierSync        |  | - urlServeur         |
        | - agendaItems (list) |  | - frequenceSync (int)|
        | - documentsHorsLigne |  | - notifActive(bool)  |
        |   (list de refs)     |  | + EnregistrerPrefs() |
        | + Synchroniser()     |  +----------------------+
        +----------------------+
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26

### 3. Diagramme de Séquence : Validation d'une demande de congé

```mermaid
sequenceDiagram
    participant AM as AppMobile
    participant BFF as BackendForFrontend
    participant MRH as ModuleRH_Backend

    Utilisateur->>+AM: Ouvre notification "Demande de congé X"
    AM->>+AM: Affiche détails demande
    Utilisateur->>+AM: Clique "Approuver"
    AM->>+BFF: POST /validation/conge (idDemande, "approuve")
    BFF->>+MRH: API_ValiderConge(idDemande, "approuve", idManager)
    MRH->>+MRH: Met à jour statut demande
    MRH-->>-BFF: ConfirmationValidation (succes)
    BFF-->>-AM: Reponse {status: "succes"}
    AM->>+AM: Met à jour UI (demande approuvée)
    AM-->>-Utilisateur: Affiche "Demande approuvée"
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26
