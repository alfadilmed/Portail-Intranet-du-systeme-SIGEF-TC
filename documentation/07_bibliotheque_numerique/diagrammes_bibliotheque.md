## Diagrammes UML : Bibliothèque Numérique

### 1. Diagramme de Cas d’Usage

```mermaid
        +-----------------+     +----------------------+
        | Agent Cour      |---->| Rechercher Ressource |
        +-----------------+     +----------------------+
               |                             |
               | Consulte                    | (inclut <<Afficher Details>>)
               v                             v
        +-----------------+     +----------------------+
        | Utilisateur     |---->| Consulter Document   |
        | (authentifie)   |     | (PDF, ePub)          |
        +-----------------+     +----------------------+
               |                             |
               |                             | (etend par <<Sauvegarder Favori>>)
               v                             v
        +-----------------+     +----------------------+
        | Bibliothecaire  |---->| Cataloguer Ressource |
        +-----------------+     +----------------------+
               |                             |
               | Gere                        | (inclut <<Gerer Abonnements>>)
               v                             v
        +-----------------+     +----------------------+
        | Systeme Externe |<----| Moissonner Metadonnees|
        | (OAI-PMH)       |     | (si ouvert)          |
        +-----------------+     +----------------------+
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26

### 2. Diagramme de Classes Simplifié

```mermaid
        +-----------------+       +-----------------+
        | RessourceDoc    |       | Auteur          |
        +-----------------+       +-----------------+
        | - idRessource   |------>| - idAuteur      |
        | - titre         |*      | - nom           |
        | - editeur       |       | - prenom        |
        | - datePub       |       +-----------------+
        | - type (livre,  |
        |   article, loi) |
        | + Afficher()    |
        +-----------------+
               | 1
               | Est classée dans
               v *
        +-----------------+       +-----------------+
        | Categorie       |       | FichierAttache  |
        +-----------------+       +-----------------+
        | - idCategorie   | 1    *| - idFichier     |
        | - libelle       |<------| - nomFichier    |
        +-----------------+       | - chemin        |
                                  | - format (PDF)  |
                                  +-----------------+
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26

### 3. Diagramme d'Activités : Recherche et consultation d'un document

```mermaid
graph TD
    A[Utilisateur accède à la Bibliothèque] --> B[Saisit critères de recherche];
    B --> C[Système exécute la recherche];
    C --> D[Affichage liste des résultats];
    D --> E{Résultats pertinents?};
    E -- Oui --> F[Utilisateur sélectionne une ressource];
    F --> G[Affichage détails de la ressource];
    G --> H{Document numérique disponible?};
    H -- Oui --> I[Utilisateur clique "Consulter"];
    I --> J[Affichage/Téléchargement du document];
    J --> Z[Fin];
    H -- Non (lien externe) --> K[Redirection vers ressource externe];
    K --> Z;
    E -- Non --> L[Utilisateur affine recherche];
    L --> C;
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26
