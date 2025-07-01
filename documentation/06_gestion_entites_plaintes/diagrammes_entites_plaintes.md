## Diagrammes UML : Gestion des Entités et Plaintes

### 1. Diagramme de Cas d’Usage

```mermaid
        +-----------------+     +----------------------+
        | Citoyen/Plaignant|---->| Soumettre Plainte    |
        +-----------------+     +----------------------+
               |                             ^
               | (Consulte statut)           | (via Portail Web)
               v                             |
        +-----------------+     +----------------------+
        | Greffier        |---->| Enregistrer Plainte  |
        +-----------------+     +----------------------+
               |                             |
               | Qualifie                    | (inclut <<Qualifier Recevabilité>>)
               v                             v
        +-----------------+     +----------------------+
        | Analyste Plainte|---->| Instruire Plainte    |
        +-----------------+     +----------------------+
               |                             |
               |                             | (utilise)
               v                             v
        +-----------------+     +----------------------+
        | Agent Cour      |---->| Gerer Entite Auditee |
        +-----------------+     +----------------------+
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26

### 2. Diagramme de Classes Simplifié

```mermaid
        +-----------------+       +-----------------+
        | Plainte         |       | Plaignant       |
        +-----------------+       +-----------------+
        | - idPlainte     | 1    1| - idPlai        |
        | - dateReception |------>| - nom (optionnel)|
        | - description   |       | - contact       |
        | - statut        |       +-----------------+
        | + Enregistrer() |
        | + Instruire()   |
        +-----------------+
               | 1..*
               | Concerne
               v 0..1
        +-----------------+       +-----------------+
        | EntiteAuditee   |       | PieceJointe     |
        +-----------------+       +-----------------+
        | - idEntite      | 1    *| - idPj          |
        | - nomEntite     |<------| - nomFichier    |
        | - type          |       | - typeMime      |
        | + Ajouter()     |       | (lien vers GND) |
        +-----------------+       +-----------------+
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26

### 3. Diagramme d'Activités : Traitement d'une nouvelle plainte

```mermaid
graph TD
    A[Réception Plainte (Portail/Courrier)] --> B[Enregistrement au Greffe];
    B --> C[Attribution Numéro Unique];
    C --> D[Accusé de Réception au Plaignant];
    D --> E[Analyse de Recevabilité];
    E -- Recevable --> F[Qualification de la Plainte];
    F --> G[Affectation à un Analyste/Instructeur];
    G --> H[Instruction (collecte infos, auditions si besoin)];
    H --> I{Décision?};
    I -- Classement sans suite --> J[Notification Plaignant];
    I -- Transmission autre organisme --> K[Notification Plaignant et Transmission];
    I -- Ouverture procédure CdC --> L[Lien vers Module E-Comptes];
    J --> M[Fin];
    K --> M;
    L --> M;
    E -- Irrecevable --> N[Notification Plaignant (motif)];
    N --> M;
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26
