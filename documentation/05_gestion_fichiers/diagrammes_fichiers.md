## Diagrammes UML : Gestion des Fichiers

### 1. Diagramme de Cas d’Usage

```mermaid
        +-----------------+     +----------------------+
        | Utilisateur     |---->| Televerser Fichier   |
        +-----------------+     +----------------------+
               |                             |
               | Organise                    | (inclut)
               v                             v
        +-----------------+     +----------------------+
        | Agent Cour      |---->| Creer Dossier        |
        +-----------------+     +----------------------+
               |                             |
               | Partage                     | (etend par <<Gestion Quotas>>)
               v                             v
        +-----------------+     +----------------------+
        | Autre Utilisateur|---->| Telecharger Fichier  |
        | (Collaborateur) |     | (partage)            |
        +-----------------+     +----------------------+
               ^                             |
               |                             |
        +-----------------+     +----------------------+
        | Admin Systeme   |---->| Gerer Permissions    |
        +-----------------+     +----------------------+
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26

### 2. Diagramme de Classes Simplifié

```mermaid
        +-----------------+       +-----------------+
        | Fichier         |       | Dossier         |
        +-----------------+       +-----------------+
        | - idFichier     | *     | - idDossier     |
        | - nom           |------>| - nom           |
        | - taille        |       | - dateCreation  |
        | - type          |       | + Creer()       |
        | - cheminStockage|       | + Supprimer()   |
        | + Televerser()  |       +-----------------+
        | + Telecharger() |         | 1 Parent
        +-----------------+         |
               | 1                  | Contient
               |                    v * Enfants
        +-----------------+
        | Partage         |
        +-----------------+
        | - idPartage     |
        | - dateExpiration|
        | - typeAcces     |  (Lecture/Ecriture)
        | + CreerLien()   |
        +-----------------+
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26

### 3. Diagramme d'Activités : Partage d'un dossier

```mermaid
graph TD
    A[Utilisateur sélectionne dossier] --> B[Choisit "Partager"];
    B --> C[Saisit email(s) collaborateur(s)];
    C --> D[Définit permissions (Lecture/Ecriture)];
    D --> E{Partage avec lien temporaire?};
    E -- Oui --> F[Définit date d'expiration];
    F --> G[Génère lien de partage sécurisé];
    G --> H[Système envoie notification/lien];
    H --> I[Fin];
    E -- Non --> J[Applique permissions directes];
    J --> H;
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26
