# Fiche Module : Gestion des Ressources Humaines (RH)

## Nom du module (officiel)
Gestion des Ressources Humaines (RH)

## Objectif
Centraliser et optimiser la gestion du cycle de vie complet des employés de la Cour des Comptes, du recrutement au départ, incluant l'administration, la paie, les carrières et les absences.

## Fonctionnalités
*   Gestion des dossiers employés (données personnelles, contrats, carrière).
*   Processus de recrutement (de l'offre à l'embauche).
*   Gestion des temps, congés et absences (demandes, validations, soldes).
*   Gestion de la paie (calcul, bulletins, déclarations) ou interface paie.
*   Gestion des carrières et des compétences (évaluations, formations).
*   Portail libre-service pour employés et managers.
*   Reporting RH et tableaux de bord.
*   Gestion documentaire RH (contrats, avenants).

## Données en entrée
*   Informations des candidats.
*   Données personnelles et contractuelles des employés.
*   Demandes de congés, arrêts maladie.
*   Variables de paie.
*   Résultats des évaluations.
*   Plans de formation.

## Données en sortie
*   Dossiers employés mis à jour.
*   Contrats de travail.
*   Bulletins de paie.
*   Ordres de virement (paie).
*   Déclarations sociales.
*   Planning des congés.
*   Rapports RH (effectifs, masse salariale, absentéisme).
*   Attestations employeur.

## Règles de gestion spécifiques
*   Calcul des droits à congé selon l'ancienneté et le statut.
*   Application des barèmes de la fonction publique pour la paie.
*   Workflows de validation pour les demandes de congés, formations, etc.
*   Respect des échéances légales pour les déclarations sociales et la paie.
*   Politique de confidentialité stricte pour les données personnelles.

## UI/UX wireframe simplifié (si pertinent)
*   **Tableau de bord Admin RH :** Widgets KPIs (effectif, demandes en attente), accès rapide aux fonctionnalités.
*   **Portail Employé :** Section "Mes informations", "Mes demandes de congés" (calendrier, formulaire), "Mes bulletins de paie".
*   **Fiche Employé :** Onglets (Infos perso, Contrat, Carrière, Absences, Paie, Documents).

## Critères d’acceptation
*   Un nouvel employé peut être enregistré avec toutes ses informations contractuelles.
*   Un employé peut soumettre une demande de congé via le portail.
*   Un manager peut approuver/refuser une demande de congé.
*   Le calcul d'un bulletin de paie est correct pour un cas type.
*   Un rapport sur l'effectif par département peut être généré.

## Points de vigilance
*   Sécurité et confidentialité des données personnelles et salariales (RGPD).
*   Exactitude et ponctualité de la paie.
*   Complexité des règles de gestion spécifiques à la fonction publique.
*   Intégration avec le module financier et la plateforme d'authentification.
*   Conduite du changement pour l'adoption par les utilisateurs.

## Technologies envisagées
*   **Backend :** Node.js (Express) ou Laravel.
*   **Frontend :** React.js ou Vue.js.
*   **Base de données :** PostgreSQL.
*   **API :** RESTful.

---
Document préparé par : Primex Software
Rédigé par : Team Primex Software
URL : https://primex-software.com
Date : 2024-07-26
