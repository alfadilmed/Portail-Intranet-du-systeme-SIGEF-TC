## Diagrammes UML : Portail Intranet

### 1. Diagramme de Cas d’Usage

```mermaid
        +-----------------+     +----------------------+
        | Agent Cour      |---->| Consulter Actualites |
        +-----------------+     +----------------------+
               |                             |
               | Accede                      | (inclut <<Afficher Tableau de Bord Perso>>)
               v                             v
        +-----------------+     +----------------------+
        | Utilisateur     |---->| Rechercher Annuaire  |
        | (Authentifie)   |     +----------------------+
        +-----------------+              |
               |                         | (etend par <<Recherche Globale SIGEF>>)
               | Utilise lien            v
        +-----------------+     +----------------------+
        | Contributeur    |---->| Publier Contenu      |
        | (Com/RH)        |     | (via CMS)            |
        +-----------------+     +----------------------+
               ^                         |
               |                         |
        +-----------------+     +----------------------+
        | Module Externes |---->| Fournir Notifications|
        | (RH, EComptes...) |   | (pour Widgets)       |
        +-----------------+     +----------------------+
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26

### 2. Diagramme de Classes Simplifié (Focus sur le contenu)

```mermaid
        +-----------------+       +-----------------+
        | PageContenu     |       | Actualite       |
        +-----------------+       +-----------------+
        | - idPage        |       | - idActualite   |
        | - titre         |       | - titre         |
        | - contenuHTML   |       | - contenu       |
        | - dateModif     |       | - datePub       |
        | + Afficher()    |       | - auteur        |
        +-----------------+       +-----------------+
               |                             |
        +-----------------+       +-----------------+
        | Widget          |       | AnnuaireEntree  |
        +-----------------+       +-----------------+
        | - idWidget      |       | - idEmploye     |
        | - type          |       | - nom, prenom   |
        | - configJSON    |       | - service, poste|
        | + Afficher()    |       | - email, tel    |
        +-----------------+       +-----------------+
        (Source: Module RH)
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26

### 3. Diagramme d'Activités : Publication d'une actualité

```mermaid
graph TD
    A[Contributeur se connecte au CMS] --> B[Crée nouvelle actualité];
    B --> C[Rédige titre et contenu];
    C --> D[Ajoute images/pièces jointes (optionnel)];
    D --> E[Sélectionne catégorie/tags];
    E --> F{Workflow de validation requis?};
    F -- Oui --> G[Soumet pour validation];
    G --> H[Validateur notifié];
    H --> I[Validateur relit et approuve];
    I -- Approuvé --> J[Actualité publiée sur l'Intranet];
    I -- Rejeté --> K[Notification au contributeur avec motif];
    K --> C;
    F -- Non --> J;
    J --> L[Fin];
```
Diagramme généré par : Team Primex Software
Pour : Primex Software (https://primex-software.com)
Date : 2024-07-26
