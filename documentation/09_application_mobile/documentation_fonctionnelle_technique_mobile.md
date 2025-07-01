# Documentation Fonctionnelle & Technique : Application Mobile

## Objectif du module

L'application mobile SIGEF-TC vise à fournir aux agents de la Cour des Comptes (principalement) un accès nomade à certaines fonctionnalités clés du système, améliorant ainsi leur productivité et leur réactivité, notamment lors de déplacements ou de missions sur le terrain. Elle peut également, de manière plus limitée, offrir des services aux usagers externes.

## Acteurs concernés

*   **Agents de la Cour des Comptes :** Magistrats, auditeurs, contrôleurs, personnel administratif.
*   **(Optionnel) Usagers externes :** Plaignants (pour suivi simplifié), entités contrôlées (notifications).

## Cas d’usage

**Pour les agents de la Cour :**
*   **Consultation de planning et d'agenda** (lien avec RH ou calendrier).
*   **Notifications push** pour les tâches urgentes, les nouvelles communications dans E-Comptes, les validations requises (congés RH, dépenses financières).
*   **Accès simplifié à l'annuaire interne.**
*   **Consultation de documents clés en mode déconnecté** (après synchronisation).
*   **Prise de notes rapides** lors de missions, potentiellement avec photos, à synchroniser ensuite.
*   **Validation de demandes simples** (ex: congés, petites dépenses).
*   **Accès à des tableaux de bord synthétiques** (ex: avancement de ses dossiers, indicateurs BI clés).
*   **Consultation de l'état d'avancement de ses dossiers** (E-Comptes).
*   **(Optionnel) Scan de codes-barres/QR codes** pour l'inventaire du patrimoine.
*   **(Optionnel) Enregistrement vocal sécurisé** pour mémos.

**(Optionnel) Pour les usagers externes :**
*   Notifications push sur l'avancement d'une plainte.
*   Accès à un suivi simplifié de leur dossier (E-Comptes).

## Fonctionnalités clés

*   **Authentification sécurisée** (biométrie, code PIN, en plus du login/mot de passe).
*   **Synchronisation des données** pour un accès hors ligne (partiel).
*   **Tableau de bord personnalisé.**
*   **Système de notifications push configurables.**
*   **Interface utilisateur intuitive et adaptée aux mobiles** (iOS & Android).
*   **Accès sécurisé aux données sensibles.**
*   **Consultation de documents (PDF, Office) optimisée.**
*   **Prise de notes enrichies** (texte, photo, audio).
*   **(Si PWA) Fonctionnalités hors-ligne via Service Workers.**
*   **(Si natif) Intégration avec les fonctionnalités du téléphone** (calendrier, contacts, appareil photo).
*   **Module de gestion des préférences utilisateur** (notifications, synchronisation).
*   **Sécurité :** Chiffrement local des données, communication sécurisée avec le backend.

## Interfaces attendues

*   **Interface utilisateur native (iOS/Android) ou Progressive Web App (PWA).**
*   **Communication via API RESTful/GraphQL sécurisée** avec les modules backend du SIGEF-TC.

## Diagramme fonctionnel simplifié (UML si possible)

```mermaid
graph TD
    A[Utilisateur Mobile (Agent/Externe)] -- S'authentifie --> B(Application Mobile);
    B -- Synchronise données/reçoit notifications --> C[Serveur SIGEF-TC (via API Gateway)];
    C -- Interagit avec --> D[Module RH (Congés, Annuaire)];
    C -- Interagit avec --> E[Module E-Comptes (Dossiers, Notifications)];
    C -- Interagit avec --> F[Module GND (Documents)];
    C -- Interagit avec --> G[Module BI (Tableaux de bord)];
    C -- Interagit avec --> H[Module Gestion du Patrimoine (Inventaire)];
    B -- Permet consultation hors-ligne --> I[Stockage Local Sécurisé];
    B -- Permet prise de notes/médias --> I;
    I -- Synchronise avec --> C;
    J[Admin SIGEF-TC] -- Gère versions/déploiement App --> K[Store d'applications/Serveur Web pour PWA];
```

## Contraintes techniques ou juridiques

*   **Sécurité des données sur l'appareil :** Chiffrement, protection contre l'accès non autorisé en cas de perte/vol du mobile.
*   **Gestion des sessions et de l'authentification robuste.**
*   **Performance et réactivité de l'application.**
*   **Optimisation de l'utilisation de la batterie et des données mobiles.**
*   **Compatibilité multiplateforme** (iOS, Android) si développement natif ou PWA bien conçue.
*   **Mises à jour faciles et sécurisées.**
*   **Respect de la vie privée et des données personnelles.**
*   **Accessibilité mobile** (directives spécifiques).

## Dépendances avec d’autres modules

L'application mobile est essentiellement une **interface client** qui consomme les services de nombreux autres modules via leurs API :
*   **Plateforme d’Authentification et Gestion des Entités :** Pour l'authentification.
*   **Gestion des Ressources Humaines (RH) :** Pour les notifications de congés, l'annuaire.
*   **E-Comptes / Traitement procédural :** Pour le suivi des dossiers, les notifications procédurales.
*   **Gestion Numérique des Documents (GND) :** Pour la consultation de documents.
*   **Gestion Financière :** Pour la validation de dépenses.
*   **Business Intelligence (BI) :** Pour l'affichage de tableaux de bord.
*   **Gestion du Patrimoine :** Pour les fonctionnalités d'inventaire mobile.
*   **Portail Intranet :** Peut partager certaines notifications ou actualités.
*   **Gestion des Entités et Plaintes :** Pour le suivi des plaintes (usagers externes).

## Spécifications API (si applicables)

L'application mobile utilisera les API existantes des différents modules back-end. Cependant, une **API Gateway** ou un **Backend For Frontend (BFF)** spécifique pourrait être mis en place pour :
*   Agréger les appels vers plusieurs modules.
*   Optimiser les payloads pour un usage mobile.
*   Gérer les sessions mobiles spécifiques.
*   Centraliser la gestion des notifications push.
*   **Endpoints spécifiques pour :**
    *   `/mobile/dashboard` : Données agrégées pour le tableau de bord mobile.
    *   `/mobile/notifications` : Gestion des inscriptions et envoi des notifications push.
    *   `/mobile/sync` : Endpoints pour la synchronisation des données hors-ligne.
*   **Authentification via OAuth2 (flux adapté aux mobiles comme Authorization Code avec PKCE).**
*   **Utilisation de jetons de rafraîchissement sécurisés.**
*   **Communication exclusivement via HTTPS.**

**Choix technologique (PWA ou Natif) :**
*   **PWA (Progressive Web App) :**
    *   Avantages : Développement unique (HTML, CSS, JS), déploiement plus simple (via URL), pas de soumission aux stores, mise à jour instantanée.
    *   Inconvénients : Accès moins complet aux fonctionnalités natives du téléphone (varie selon OS), expérience utilisateur peut être moins fluide que du natif pour des tâches complexes.
*   **Natif (iOS - Swift/Objective-C, Android - Kotlin/Java) ou Cross-Platform Natif (React Native, Flutter) :**
    *   Avantages : Meilleures performances, accès complet aux API natives, meilleure expérience utilisateur possible.
    *   Inconvénients : Coûts et temps de développement plus élevés (surtout si deux bases de code séparées), processus de validation des stores.

La recommandation serait d'évaluer la complexité des fonctionnalités souhaitées. Pour des consultations, notifications et validations simples, une PWA bien conçue pourrait suffire et serait plus rapide à développer et maintenir. Si des fonctionnalités natives avancées ou des performances optimales sont critiques, le natif ou cross-platform natif serait préférable.

---
Document préparé par : Primex Software
Rédigé par : Team Primex Software
URL : https://primex-software.com
Date : 2024-07-26
