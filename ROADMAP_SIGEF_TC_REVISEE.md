# 🛠️ Roadmap SIGEF-TC – Version Révisée Budget-Contraint

## 📌 Paramètres

*   **Budget Global Cible :** $450,000 USD
*   **Charge Globale Estimée du Projet :** 1345 jours-homme (j.h)
*   **Taux Journalier Moyen (TJM) de référence :** $334 USD / jour-homme
*   **Durée d'un Sprint recommandée :** 3 semaines (15 jours ouvrés)
*   **Composition Équipe de Réalisation (dédiée aux tâches estimées en j.h) :** 4 personnes (développeurs, testeurs QA).
    *   *Les rôles transverses comme Chef de Projet, Architecte sont couverts par les charges transverses.*
*   **Capacité Brute de l'Équipe par Sprint :** 4 personnes * 15 jours = 60 j.h
*   **Charges Transverses Estimées (Gestion Projet, Archi, QA globale, DevOps, Doc, Formation) :** 410 j.h
*   **Répartition Moyenne des Charges Transverses par Sprint :** 410 j.h / 23 sprints ≈ 17.8 j.h/sprint
*   **Capacité Nette par Sprint pour le Développement des Modules :** 60 j.h - 17.8 j.h ≈ 42.2 j.h/sprint
*   **Nombre Total de Sprints Estimé :** 23 sprints

## 📆 Nouvelle Structure par Phase

La roadmap est structurée en phases, chacune visant la livraison d'un ensemble cohérent de fonctionnalités MVP (Produit Minimum Viable). Les charges transverses sont réparties et consommées tout au long de ces phases.

### Phase 1 – Fondations Techniques et Fonctionnelles MVP (Durée : ~5.25 mois | 7 Sprints | Modules: 294 j.h)

*   **Objectif :** Mettre en place le socle technique indispensable (Authentification, GND de base) et les premières briques fonctionnelles RH et Gestion de Fichiers.
*   **Sprint 0 :** Cadrage détaillé final, configuration fine des environnements et outils CI/CD (couvert par charges transverses initiales).

*   **Sprint 1 :** (Capacité module ~42 j.h)
    *   Module 12 – Plateforme d’Authentification & Gestion Entités (Utilisateurs) (Partie 1/2) : 42 j.h (sur 70 j.h)
*   **Sprint 2 :** (Capacité module ~42 j.h)
    *   Module 12 – Plateforme d’Authentification & Gestion Entités (Utilisateurs) (Partie 2/2) : 28 j.h
    *   Module 04 – Gestion Numérique des Documents (GND) (Partie 1/3) : 14 j.h (sur 90 j.h)
    *   *Jalon Clé : Socle d'authentification et de sécurité MVP opérationnel.*
*   **Sprint 3 :** (Capacité module ~42 j.h)
    *   Module 04 – Gestion Numérique des Documents (GND) (Partie 2/3) : 42 j.h
*   **Sprint 4 :** (Capacité module ~42 j.h)
    *   Module 04 – Gestion Numérique des Documents (GND) (Partie 3/3) : 34 j.h
    *   Module 05 – Gestion des Fichiers (Partie 1/2) : 8 j.h (sur 30 j.h)
    *   *Jalon Clé : Gestion documentaire MVP (dépôt, consultation, versioning simple) fonctionnelle.*
*   **Sprint 5 :** (Capacité module ~42 j.h)
    *   Module 05 – Gestion des Fichiers (Partie 2/2) : 22 j.h
    *   Module 01 – Gestion des Ressources Humaines (RH) (Partie 1/2) : 20 j.h (sur 70 j.h)
*   **Sprint 6 :** (Capacité module ~42 j.h)
    *   Module 01 – Gestion des Ressources Humaines (RH) (Partie 2/2) : 42 j.h (sur 50 j.h restants)
*   **Sprint 7 :** (Capacité module ~42 j.h)
    *   Module 01 – Gestion des Ressources Humaines (RH) (Fin) : 8 j.h
    *   Module 02 – Gestion Financière (Partie 1/2) : 34 j.h (sur 80 j.h)
    *   *Jalon Clé : Processus RH administratifs MVP et gestion de fichiers simples opérationnels.*

### Phase 2 – Déploiement des Modules Métiers Centraux MVP (Durée : ~6 mois | 8 Sprints | Modules: 338 j.h)

*   **Objectif :** Livrer le MVP des modules métiers critiques (Finances, E-Comptes, Plaintes) et initier les capacités d'échange de données et de suivi budgétaire de l'État.

*   **Sprint 8 :** (Capacité module ~46 j.h - ajustement ponctuel)
    *   Module 02 – Gestion Financière (Partie 2/2) : 46 j.h
    *   *Jalon Clé : Gestion financière interne MVP opérationnelle.*
*   **Sprint 9 :** (Capacité module ~42 j.h)
    *   Module 08 – E-Comptes / Traitement procédural (Partie 1/3) : 42 j.h (sur 120 j.h)
*   **Sprint 10 :** (Capacité module ~42 j.h)
    *   Module 08 – E-Comptes / Traitement procédural (Partie 2/3) : 42 j.h
*   **Sprint 11 :** (Capacité module ~42 j.h)
    *   Module 08 – E-Comptes / Traitement procédural (Partie 3/3) : 36 j.h
    *   Module 06 – Gestion des Entités et Plaintes (Partie 1/2) : 6 j.h (sur 60 j.h)
    *   *Jalon Clé : Première procédure E-Comptes MVP dématérialisée.*
*   **Sprint 12 :** (Capacité module ~42 j.h)
    *   Module 06 – Gestion des Entités et Plaintes (Partie 2/2) : 42 j.h (sur 54 j.h restants)
*   **Sprint 13 :** (Capacité module ~42 j.h)
    *   Module 06 – Gestion des Entités et Plaintes (Fin) : 12 j.h
    *   Module 13 – Interopérabilité (Partie 1/2) : 30 j.h (sur 70 j.h)
*   **Sprint 14 :** (Capacité module ~42 j.h)
    *   Module 13 – Interopérabilité (Partie 2/2) : 40 j.h
    *   *Jalon Clé : Gestion des plaintes MVP et premiers flux d'interopérabilité MVP actifs.*
*   **Sprint 15 :** (Capacité module ~42 j.h)
    *   Module 11 – Suivi Budgétaire (Comptes de l’État) (Partie 1/2) : 42 j.h (sur 70 j.h)

### Phase 3 – Finalisation du Périmètre MVP et Modules Complémentaires (Durée : ~6 mois | 8 Sprints | Modules: 303 j.h)

*   **Objectif :** Compléter le MVP de tous les modules restants, y compris les outils de support et de valorisation (Intranet, Patrimoine, Bibliothèque, Mobile, BI).

*   **Sprint 16 :** (Capacité module ~42 j.h)
    *   Module 11 – Suivi Budgétaire (Comptes de l’État) (Partie 2/2) : 28 j.h
    *   Module 10 – Portail Intranet (Partie 1/2) : 14 j.h (sur 50 j.h)
*   **Sprint 17 :** (Capacité module ~42 j.h)
    *   Module 10 – Portail Intranet (Partie 2/2) : 36 j.h
    *   Module 03 – Gestion du Patrimoine (Partie 1/2) : 6 j.h (sur 50 j.h)
    *   *Jalon Clé : Suivi budgétaire État MVP et Intranet V1 MVP disponibles.*
*   **Sprint 18 :** (Capacité module ~42 j.h)
    *   Module 03 – Gestion du Patrimoine (Partie 2/2) : 42 j.h (sur 44 j.h restants)
*   **Sprint 19 :** (Capacité module ~42 j.h)
    *   Module 03 – Gestion du Patrimoine (Fin) : 2 j.h
    *   Module 07 – Bibliothèque Numérique : 40 j.h
*   **Sprint 20 :** (Capacité module ~42 j.h)
    *   Module 09 – Application Mobile (Partie 1/2) : 42 j.h (sur 60 j.h)
*   **Sprint 21 :** (Capacité module ~42 j.h)
    *   Module 09 – Application Mobile (Partie 2/2) : 18 j.h
    *   Module 14 – Business Intelligence (BI) (Partie 1/3) : 24 j.h (sur 75 j.h)
    *   *Jalon Clé : Premières fonctionnalités mobiles MVP et dashboards BI essentiels disponibles.*
*   **Sprint 22 :** (Capacité module ~42 j.h)
    *   Module 14 – Business Intelligence (BI) (Partie 2/3) : 42 j.h
*   **Sprint 23 :** (Capacité module libre pour finalisation)
    *   Module 14 – Business Intelligence (BI) (Partie 3/3) : 9 j.h
    *   *Buffer pour finalisations, tests transversaux globaux intensifiés, préparation au déploiement.*
    *   *Jalon Clé : Ensemble du périmètre MVP SIGEF-TC fonctionnel et testé.*

## 📊 Récapitulatif
| Phase | Modules Principaux Couverts (MVP)                                     | Total j.h Modules | Durée estimée (Sprints) | Durée estimée (Semaines) | Durée estimée (Mois) |
|-------|-----------------------------------------------------------------------|-------------------|-------------------------|--------------------------|----------------------|
| 1     | Auth, GND, Fichiers, RH, début Finances                               | 294 j.h           | 7                       | 21                       | ~5.25                |
| 2     | Fin Finances, E-Comptes, Entités/Plaintes, Interop, début Suivi Budg. | 338 j.h           | 8                       | 24                       | ~6                   |
| 3     | Fin Suivi Budg., Intranet, Patrimoine, Biblio, Mobile, BI             | 303 j.h           | 8                       | 24                       | ~6                   |
| **TOTAL** | **Ensemble des 14 modules (Périmètre MVP)**                         | **935 j.h**       | **23 Sprints**          | **69 Semaines**          | **~17-18 mois**      |

*Charges transverses (Gestion Projet, Archi, QA, DevOps, Doc, Formation) estimées à 410 j.h, réparties sur les 23 sprints.*

## ✅ Total global : 1345 j.h – Respect de l’enveloppe de 450 000 USD (pour un TJM de $334 USD)

📌 **Important :** Cette roadmap est une proposition basée sur les charges estimées pour un périmètre MVP (Produit Minimum Viable) de chaque module, afin de respecter la contrainte budgétaire. La priorisation fine du contenu de chaque sprint (user stories) sera effectuée en collaboration avec la Cour des Comptes au démarrage de chaque phase et de chaque sprint. Les fonctionnalités "nice-to-have" ou les enrichissements non critiques identifiés dans la roadmap initiale ont été reportés ou nécessiteront une phase projet ultérieure. La répartition des charges transverses est une moyenne et leur consommation effective sera adaptée aux besoins de chaque sprint.

---
Rédigé par : Team Primex Software
Date : 2024-07-26
