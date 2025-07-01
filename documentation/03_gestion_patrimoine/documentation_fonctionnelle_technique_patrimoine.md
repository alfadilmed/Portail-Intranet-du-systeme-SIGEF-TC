# Documentation Fonctionnelle & Technique : Gestion du Patrimoine

## Objectif du module

Le module de Gestion du Patrimoine a pour objectif de permettre un suivi précis et complet de tous les actifs (biens mobiliers et immobiliers) de la Cour des Comptes. Cela inclut leur acquisition, leur affectation, leur maintenance, leur amortissement et leur sortie d'inventaire.

## Acteurs concernés

*   Gestionnaire du patrimoine
*   Services techniques (pour la maintenance)
*   Service financier (pour la comptabilisation et l'amortissement)
*   Utilisateurs des biens (pour l'affectation)
*   Responsables de départements/services
*   Auditeurs

## Cas d’usage

*   **Inventaire des biens :** Enregistrement initial et mise à jour de la base de données des actifs.
*   **Acquisition de nouveaux biens :** Processus d'enregistrement des nouveaux actifs, y compris leur coût, date d'acquisition, fournisseur.
*   **Affectation des biens :** Suivi de l'emplacement et de l'utilisateur responsable de chaque bien.
*   **Gestion de la maintenance :** Planification et suivi des opérations de maintenance préventive et curative.
*   **Calcul des amortissements :** Calcul automatique des dotations aux amortissements selon les règles comptables.
*   **Cession ou mise au rebut des biens :** Processus de sortie d'inventaire des actifs (vente, don, destruction).
*   **Suivi des contrats de location ou de leasing.**
*   **Valorisation du patrimoine.**
*   **Reporting sur l'état et la valeur du patrimoine.**

## Fonctionnalités clés

*   **Base de données centralisée des actifs** avec fiches descriptives détaillées (catégorie, identification, localisation, état, valeur, etc.).
*   **Gestion du cycle de vie des actifs :** De l'acquisition à la sortie.
*   **Identification unique des biens** (codes-barres, QR codes, RFID).
*   **Gestion des mouvements et transferts** de biens entre services ou localisations.
*   **Module de gestion de la maintenance** (interne ou externe).
*   **Calcul automatique des amortissements** (linéaire, dégressif, etc.).
*   **Gestion des inventaires physiques** et rapprochement avec la base de données.
*   **Historique complet des modifications** pour chaque bien.
*   **Gestion des assurances et garanties** liées aux biens.
*   **Reporting et tableaux de bord** sur l'état du patrimoine.
*   **Intégration avec la gestion financière** pour les aspects comptables.

## Interfaces attendues

*   **Interface utilisateur web responsive** pour les gestionnaires du patrimoine et autres acteurs.
*   **Application mobile (optionnelle)** pour faciliter les inventaires sur le terrain (scan de codes-barres).
*   **API** pour l'intégration avec le module de Gestion Financière.
*   **Interface d'import/export de données** (ex: pour l'inventaire initial).

## Diagramme fonctionnel simplifié (UML si possible)

```mermaid
graph TD
    A[Utilisateur (Gestionnaire Patrimoine/Technicien)] -- Accède au module --> B(Module Gestion du Patrimoine);
    B -- Enregistre/Met à jour bien --> C[Base de Données des Actifs];
    B -- Gère affectations --> C;
    B -- Planifie/Suit maintenance --> D[Gestion de la Maintenance];
    D -- Met à jour état du bien --> C;
    C -- Fournit données pour calcul --> E[Calcul des Amortissements];
    E -- Envoie données à --> F[Module Gestion Financière];
    G[Service Achats/Financier] -- Enregistre nouvelle acquisition --> C;
    B -- Gère sortie d'inventaire --> C;
    H[Système d'Authentification] -- Authentifie --> B;
    I[Inventaire Physique (Mobile App/Manuel)] -- Compare avec --> C;
    C -- Fournit données pour reporting --> J[Reporting Patrimoine];
```

## Contraintes techniques ou juridiques

*   **Respect des règles comptables** pour l'évaluation et l'amortissement des biens.
*   **Sécurité des données** relatives à la valeur et à la localisation des actifs.
*   **Traçabilité des mouvements** et des modifications apportées aux fiches des biens.
*   **Fiabilité de l'inventaire** pour éviter les pertes ou les vols.
*   **Pérennité de l'archivage** des informations sur les biens, même après leur sortie.

## Dépendances avec d’autres modules

*   **Gestion Financière :** Pour la comptabilisation des acquisitions, des cessions, et surtout pour l'enregistrement des dotations aux amortissements.
*   **Plateforme d’Authentification et Gestion des Entités :** Pour l'authentification des utilisateurs et la gestion des droits d'accès.
*   **Gestion Numérique des Documents :** Pour l'archivage des documents liés aux biens (factures d'achat, contrats de maintenance, rapports d'expertise).
*   **Business Intelligence (BI) :** Pour des analyses avancées sur la composition, la valeur et l'évolution du patrimoine.
*   **Gestion des Fichiers (potentiellement) :** Si des plans ou schémas techniques des biens immobiliers sont gérés.

## Spécifications API (si applicables)

*   **API RESTful** pour :
    *   La création, la lecture, la mise à jour et la suppression (logique) des fiches d'actifs.
    *   La récupération des informations pour le module financier (valeur d'acquisition, date de mise en service, taux d'amortissement).
*   **Endpoints pour :**
    *   `/assets` : Gestion des fiches d'actifs.
    *   `/assets/{id}/ maintenances` : Suivi des maintenances pour un actif.
    *   `/assets/{id}/movements` : Historique des affectations d'un actif.
    *   `/depreciation_calculations` : Pour exposer les résultats des calculs d'amortissement.
*   **Authentification via OAuth2.**
*   **Formats de données :** JSON.

---
Document préparé par : Primex Software
Rédigé par : Team Primex Software
URL : https://primex-software.com
Date : 2024-07-26
