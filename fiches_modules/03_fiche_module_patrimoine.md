# Fiche Module : Gestion du Patrimoine

## Nom du module (officiel)
Gestion du Patrimoine

## Objectif
Permettre un suivi précis et complet de tous les actifs (biens mobiliers et immobiliers) de la Cour des Comptes, de leur acquisition à leur sortie d'inventaire, incluant l'affectation, la maintenance et l'amortissement.

## Fonctionnalités
*   Inventaire centralisé des biens (fiches descriptives, identification, localisation, valeur).
*   Gestion du cycle de vie des actifs (acquisition, affectation, maintenance, cession, mise au rebut).
*   Suivi des mouvements et transferts de biens.
*   Planification et suivi des opérations de maintenance.
*   Calcul des amortissements (interface avec le module financier).
*   Gestion des inventaires physiques (rapprochement avec la base de données).
*   Reporting sur l'état et la valeur du patrimoine.
*   Gestion des codes-barres/QR codes pour identification.

## Données en entrée
*   Informations d'achat des nouveaux biens (factures, bons de livraison).
*   Données de l'inventaire existant.
*   Demandes de mouvement de biens.
*   Rapports d'intervention de maintenance.
*   Informations de cession ou de mise au rebut.

## Données en sortie
*   Inventaire du patrimoine à jour.
*   Fiches de biens détaillées.
*   Historique des mouvements et maintenances par bien.
*   Plan de maintenance.
*   Calculs d'amortissement (transmis au module financier).
*   Rapports sur la valeur du patrimoine, les biens par service, etc.
*   Procès-verbaux de sortie d'inventaire.

## Règles de gestion spécifiques
*   Chaque bien doit avoir un identifiant unique.
*   Les mouvements de biens doivent être tracés et validés.
*   Les calculs d'amortissement doivent suivre les normes comptables.
*   Procédure formelle pour la sortie d'inventaire des biens.
*   Rapprochement périodique entre l'inventaire physique et l'inventaire comptable.

## UI/UX wireframe simplifié (si pertinent)
*   **Tableau de bord Gestionnaire Patrimoine :** KPIs (nombre de biens, valeur totale, biens nécessitant maintenance), liste des mouvements récents.
*   **Fiche Bien :** Champs (ID, désignation, catégorie, date d'acquisition, valeur, localisation, service affectataire, état), onglets (Mouvements, Maintenance, Amortissement, Documents liés).
*   **Formulaire de demande de mouvement de bien.**

## Critères d’acceptation
*   Un nouveau bien peut être ajouté à l'inventaire avec toutes ses caractéristiques.
*   Un bien peut être affecté à un service et à un utilisateur.
*   Une opération de maintenance peut être enregistrée pour un bien.
*   Le calcul de l'amortissement pour un bien est correct et transmis au module financier.
*   Un rapport listant tous les biens d'une catégorie spécifique peut être généré.

## Points de vigilance
*   Fiabilité de l'identification et de la localisation des biens.
*   Intégration étroite avec le module de Gestion Financière pour les aspects comptables (valeur d'acquisition, amortissements, cessions).
*   Complexité des inventaires physiques périodiques.
*   Gestion des biens de faible valeur.
*   Sécurisation des informations sur les biens de valeur.

## Technologies envisagées
*   **Backend :** Node.js (Express) ou Laravel.
*   **Frontend :** React.js ou Vue.js.
*   **Base de données :** PostgreSQL.
*   **API :** RESTful.
*   **Mobile (optionnel) :** Application pour inventaire avec scan de codes-barres (PWA ou natif).

---
Document préparé par : Primex Software
Rédigé par : Team Primex Software
URL : https://primex-software.com
Date : 2024-07-26
