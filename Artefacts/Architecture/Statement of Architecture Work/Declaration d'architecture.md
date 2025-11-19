# Déclaration de Travail d'Architecture

**Projet : Plateforme Foosus Géoconsciente**  
**Client : Foosus**
**Préparé par : Mathieu Baro**

---

## Information sur le document

|                         |                                           |
| ----------------------- | ----------------------------------------- |
| **Nom du projet**       | Plateforme Foosus Géoconsciente - Phase 1 |
| **Préparé par**         | Mathieu Baro - Architecte logiciel        |
| **Version du document** | 0.1 - DRAFT                               |
| **Date de version**     | Octobre 2025                              |
| **Statut**              | Brouillon pour révision                   |

---

## 1. Objet de ce document

Ce document définit la Déclaration de Travail d'Architecture pour la nouvelle plateforme Foosus géolocalisée. Il établit le périmètre, l'approche et les objectifs du projet d'architecture qui permettra à Foosus de :

- Reconstruire sa plateforme sur une architecture moderne et scalable
- Supporter la croissance de la base utilisateurs via la géolocalisation
- Réduire la dette technique accumulée
- Permettre l'innovation rapide et l'expérimentation
- Maintenabilité et évolutivité <= à étayer

Cette déclaration constitue le contrat entre la fonction Architecture et les parties prenantes du projet pour la phase initiale de 6 mois.

---

## 2. Déclaration de travail d'architecture

### 2.1 Requête du projet et contexte

**Contexte Business**

Foosus fait face à un déclin des inscriptions utilisateurs dû à l'instabilité de sa plateforme historique. La dette technique accumulée empêche l'innovation et génère plus de 25 incidents P1 (expliquer p1) par mois. Les études de marché montrent une opportunité significative dans le marché local avec géolocalisation, niche non exploitée par les concurrents.

**Drivers du changement**

- Déclin des inscriptions utilisateurs (métrique clé pour les investisseurs)
- Impossibilité de supporter les pics de charge marketing
- Plus de 12 pannes majeures en 2024 dues à des déploiements hasardeux
- Délai moyen de mise en production : 3,5 semaines (cible : < 1 semaine)

**Autorisation du projet**

- Budget Phase 1 : 50 000 euros
- Durée : 6 mois
- Objectif : Définir l'architecture + développer un prototype fonctionnel
- Sponsor : Ash Callum (CEO)

### 2.2 Description du projet et périmètre

**Vue d'ensemble**

Conception et prototypage d'une nouvelle plateforme cloud-native basée sur une architecture microservices, permettant la recherche géolocalisée de producteurs locaux et la gestion des commandes. La plateforme coexistera initialement avec le système legacy en mode maintenance.

**Périmètre Phase 1 (6 mois)**

**Dans le périmètre :**

- Architecture d'entreprise cible (microservices cloud-native)
- Service de recherche géolocalisée (MVP)
- Service de gestion des commandes simplifié
- Infrastructure AWS de base (compute, storage, networking)
- Pipeline CI/CD et pratiques DevOps
- Interfaces web et mobile (responsive design)
- Observabilité et monitoring de base

**Hors périmètre Phase 1 :**

- Intégration avec systèmes de paiement tiers
- Migration des données legacy
- Décommissionnement de la plateforme existante
- Système de facturation automatisé
- Features avancées (recommandations, analytics complexes)

### 2.3 Alignement stratégique

Cette architecture s'aligne sur les objectifs stratégiques de Foosus :

1. **Croissance utilisateurs** : Géolocalisation pour attirer de nouveaux segments
2. **Stabilité opérationnelle** : Réduire les incidents P1 de >25/mois à <1/mois
3. **Agilité business** : Permettre l'expérimentation et les déploiements fréquents
4. **Excellence technique** : Attirer et retenir les talents avec une stack moderne

---

## 3. Objectifs et périmètre

### 3.1 Objectifs

Les objectifs business de ce travail d'architecture sont :

| **Objectif Business**                          | **Notes**                                        |
| ---------------------------------------------- | ------------------------------------------------ |
| Augmenter les inscriptions utilisateurs de 10% | Via géolocalisation et meilleure UX              |
| Passer de 1,4 à 4 adhésions producteurs/mois   | Plateforme plus attractive et stable             |
| Réduire délai de parution de 3,5 sem à <1 sem  | CI/CD automatisé, déploiements sans interruption |
| Réduire incidents P1 de >25/mois à <1/mois     | Architecture résiliente, monitoring proactif     |
| Supporter expansion multi-régions              | Architecture distribuée, CDN global              |
| Permettre déploiements 24/7 sans interruption  | Zero-downtime deployments                        |

### 3.2 Parties prenantes, préoccupations et visions

| **Partie prenante**            | **Préoccupation**                                  | **Vision à créer**                                |
| ------------------------------ | -------------------------------------------------- | ------------------------------------------------- |
| Ash Callum (CEO)               | Taux d'inscription en baisse, viabilité long terme | Vision architecture business, roadmap croissance  |
| Natasha Jarson (CIO)           | Dette technique, stabilité, innovation             | Architecture technique cible, stratégie migration |
| Daniel Anthony (CPO)           | Time-to-market, expérimentation produit            | Architecture modulaire permettant A/B testing     |
| Pete Parker (Resp. Ingénierie) | Complexité système, autonomie équipes              | Bounded contexts clairs, architecture découplée   |
| Jo Kumar (CFO)                 | Coûts infrastructure, ROI investissement           | Analyse coût/bénéfice, optimisation cloud         |
| Équipes Dev                    | DX (Developer Experience), outils modernes         | Stack technologique cohérente, documentation      |

---

## 4. Rôles et responsabilités

### 4.1 Structure de gouvernance

**Comité de pilotage Architecture**

- Sponsor : Ash Callum (CEO)
- Décideurs : Natasha Jarson (CIO), Daniel Anthony (CPO), Pete Parker (Resp. Eng)
- Fonction Architecture : Mathieu Baro
- Fréquence : Revues bi-hebdomadaires

**Équipes d'exécution**

- **Équipe Frontend** : Développement interfaces web/mobile responsive
- **Équipe Backend** : Développement microservices métier
- **Équipe DevOps** : Infrastructure cloud, CI/CD, observabilité

### 4.2 Matrice RACI

| **Activité**                       | **Architecte** | **CIO** | **Équipes Dev** | **DevOps** |
| ---------------------------------- | -------------- | ------- | --------------- | ---------- |
| Définition vision architecture     | R              | C       | C               | C          |
| Choix patterns techniques          | R              | A       | C               | C          |
| Définition infrastructure cloud    | C              | A       | I               | R          |
| Développement prototype            | C              | I       | R               | R          |
| Validation principes architecture  | R              | A       | C               | I          |
| Définition contrats d'architecture | R              | C       | C               | C          |

R: Responsible, A: Accountable, C: Consulted, I: Informed

---

## 5. Approche architecturale

### 5.1 Process d'architecture

Approche adaptée basée sur TOGAF ADM, ajustée pour un contexte Agile/Lean :

| **Phase ADM**                  | **Utilisation dans ce projet** | **Notes**                                      |
| ------------------------------ | ------------------------------ | ---------------------------------------------- |
| Préliminaire                   | ✅ Complet                     | Principes, framework, contexte organisationnel |
| A - Vision                     | ✅ Complet                     | Document en cours                              |
| B - Architecture Business      | ✅ Cible uniquement            | Focus sur nouveaux processus géolocalisés      |
| C - Architecture SI (Data)     | ✅ Cible uniquement            | Modèles de données microservices               |
| C - Architecture SI (Apps)     | ✅ Cible uniquement            | Cartographie services, APIs                    |
| D - Architecture Techno        | ✅ Cible uniquement            | Stack AWS, patterns cloud-native               |
| E - Opportunités & Solutions   | ✅ Simplifié                   | Focus prototype Phase 1                        |
| F - Planning Migration         | ⚠️ Phase 2                     | Coexistence legacy définie, détails en Phase 2 |
| G - Gouvernance Implémentation | ✅ Adapté                      | Revues continues, pas de waterfall             |
| H - Management du changement   | ✅ Simplifié                   | Adaptation culture, formation équipes          |

**Approche itérative** : 3 cycles de 2 mois avec démos et rétrospectives

### 5.2 Contenu de l'architecture

Artefacts à produire pendant la Phase 1 :

| **Zone de contenu**            | **Artefacts prévus**                                                                            | **Priorité** |
| ------------------------------ | ----------------------------------------------------------------------------------------------- | ------------ |
| **Principes & Vision**         | - Principes architecturaux<br>- Architecture Vision (ce doc)<br>- Requirements Specification    | P0           |
| **Architecture Business**      | - Cartographie capacités métier<br>- Processus géolocalisés (AS-IS vs TO-BE)                    | P0           |
| **Architecture Data**          | - Modèles de domaine par service<br>- Stratégie cohérence données<br>- Patterns géospatiaux     | P0           |
| **Architecture Applications**  | - Cartographie microservices<br>- Diagrammes de composants<br>- Spécifications APIs (contracts) | P0           |
| **Architecture Technologique** | - Diagramme infrastructure AWS<br>- Choix technologiques justifiés<br>- Patterns déploiement    | P0           |
| **Réalisation**                | - Prototype fonctionnel<br>- Guides développeur<br>- Runbooks DevOps                            | P0           |

### 5.3 Stratégie de migration et coexistence

**Approche : Strangler Fig Pattern**

Nous adoptons le **Strangler Fig pattern** pour migrer progressivement de la plateforme legacy vers la nouvelle architecture microservices sans interruption de service. Ce pattern, inspiré de la figuier étrangleur qui pousse autour d'un arbre hôte, permet de remplacer graduellement l'ancien système.

**Principe de fonctionnement :**

1. **Routage intelligent** : Un API Gateway/Proxy route le trafic vers l'ancien ou le nouveau système selon la fonctionnalité demandée
2. **Migration par capacité** : Chaque fonctionnalité business est migrée indépendamment
3. **Coexistence** : Les deux systèmes fonctionnent en parallèle pendant la transition (12-18 mois estimés)
4. **Décommissionnement progressif** : Quand une fonctionnalité est validée sur la nouvelle plateforme, elle est retirée de l'ancienne

**Ordre de migration Phase 1 (Prototype 6 mois) :**

| **Priorité** | **Capacité business**          | **Statut**                       | **Risque**                      |
| ------------ | ------------------------------ | -------------------------------- | ------------------------------- |
| P0           | Recherche géolocalisée         | Nouveau système uniquement       | Faible - nouvelle feature       |
| P1           | Gestion commandes (simplifiée) | Nouveau système uniquement       | Moyen - coexistence possible    |
| P2           | Gestion utilisateurs           | Lecture legacy, écriture nouveau | Moyen - synchronisation requise |
| Hors scope   | Système de paiement existant   | Legacy uniquement                | N/A - Phase 2                   |
| Hors scope   | Back-office admin              | Legacy uniquement                | N/A - Phase 2                   |

**Architecture de coexistence (Phase 1) :**

```
┌─────────────────────────────────────────────────────────┐
│                    Utilisateurs                         │
│              (Web / Mobile)                             │
└────────────────────┬────────────────────────────────────┘
                     │
                     ▼
         ┌───────────────────────┐
         │   API Gateway / CDN   │
         │  (Routage intelligent)│
         └──────┬───────────┬────┘
                │           │
       ┌────────▼──┐    ┌───▼─────────────────┐
       │  NOUVEAU  │    │   LEGACY SYSTEM     │
       │  SYSTÈME  │    │  (Maintenance only) │
       │           │    │                     │
       │ ┌───────┐ │    │  - Paiements        │
       │ │Search │ │    │  - Back-office      │
       │ │ Geo   │ │    │  - Anciennes        │
       │ └───────┘ │    │    commandes        │
       │ ┌───────┐ │    │                     │
       │ │Orders │ │    │                     │
       │ │Service│ │    │                     │
       │ └───────┘ │    └─────────────────────┘
       │           │
       │  AWS      │
       └───────────┘
```

**Stratégie de routage (règles de décision) :**

- **Recherche avec géolocalisation** → Toujours nouveau système
- **Création de commande** → Nouveau système (Phase 1)
- **Consultation anciennes commandes** → Legacy (temporairement)
- **Paiement** → Legacy (hors scope Phase 1)
- **Administration** → Legacy (hors scope Phase 1)

**Garanties de continuité :**

1. **Aucune interruption de service** : Les utilisateurs peuvent continuer d'utiliser les fonctionnalités legacy pendant la migration
2. **Rollback possible** : En cas de problème, le routing peut revenir à 100% legacy en < 5 minutes
3. **Tests A/B possibles** : Possibilité de router progressivement (ex: 10%, 50%, 100% du trafic)
4. **Monitoring unifié** : Observabilité des deux systèmes pour comparer les performances

**Métriques de migration (KPIs de transition) :**

| **Métrique**                 | **Valeur initiale** | **Cible Phase 1**   | **Cible finale** |
| ---------------------------- | ------------------- | ------------------- | ---------------- |
| % trafic sur nouveau système | 0%                  | 15-25%              | 100%             |
| Nombre de capacités migrées  | 0                   | 2 (Search + Orders) | Toutes           |
| Incidents liés à coexistence | N/A                 | < 2/mois            | 0                |
| Latence added by routing     | N/A                 | < 10ms              | < 5ms            |

**Plan de décommissionnement (post-Phase 1) :**

- **Mois 7-12** : Migration données utilisateurs, intégration paiements
- **Mois 13-18** : Migration back-office, décommissionnement progressif legacy
- **Mois 19-24** : Extinction complète plateforme legacy

**Risques spécifiques à la coexistence et mitigations :**

| **Risque**                         | **Mitigation**                                                |
| ---------------------------------- | ------------------------------------------------------------- |
| Incohérence données entre systèmes | Event sourcing, synchronisation unidirectionnelle vers legacy |
| Performance du routing             | CDN + caching agressif, routage au niveau DNS si possible     |
| Complexité opérationnelle          | Runbooks clairs, monitoring unifié, équipe dédiée transition  |
| Régression sur legacy              | Gel des changements legacy (maintenance only strict)          |

#### 5.3.1 Stratégie d'intégration inter-systèmes

La coexistence des deux systèmes nécessite une stratégie claire de communication et d'intégration. Nous adoptons une approche **API-first** avec une **façade moderne sur le legacy**.

**Architecture d'intégration :**

```
┌────────────────────────────────────────────────────┐
│              Clients (Web/Mobile)                  │
└─────────────────────┬──────────────────────────────┘
                      │
            ┌─────────▼─────────┐
            │   API Gateway     │ ← Point d'entrée unifié
            │   (AWS)           │    + Routage intelligent
            └────┬──────────┬───┘
                 │          │
        ┌────────▼───┐   ┌──▼──────────────┐
        │  Nouveaux  │   │  API Façade     │ ← Nouvelle couche
        │  Services  │   │  Legacy         │    REST moderne
        │  (AWS)     │   │  (à créer)      │
        │            │   └────┬────────────┘
        │  ┌──────┐  │        │
        │  │Search│  │        │
        │  │ Geo  │  │   ┌────▼──────────┐
        │  └──────┘  │   │ Legacy System │
        │  ┌──────┐  │   │ (Existant)    │
        │  │Orders│──┼──→│               │ ← Communication
        │  └──────┘  │   │ - Paiements   │    si nécessaire
        └────────────┘   │ - Users       │
                         │ - Old Orders  │
                         └───────────────┘
```

**Composants d'intégration à développer :**

**1. API Façade Legacy (Priorité P0 - Cycle 1)**

Une couche REST moderne exposant les fonctionnalités legacy nécessaires :

| **Endpoint**                | **Méthode** | **Usage**                             | **Priorité** |
| --------------------------- | ----------- | ------------------------------------- | ------------ |
| `/legacy/users/{id}`        | GET         | Consulter utilisateur existant        | P0           |
| `/legacy/users/{id}/orders` | GET         | Historique commandes anciennes        | P1           |
| `/legacy/suppliers/{id}`    | GET         | Info fournisseur legacy (transition)  | P1           |
| `/legacy/payments/methods`  | GET         | Moyens de paiement utilisateur        | P2 (Phase 2) |
| `/legacy/orders`            | POST        | Créer commande dans legacy (fallback) | P2           |

**Caractéristiques techniques :**

- Format : REST/JSON (OpenAPI 3.0)
- Authentification : OAuth2 token partagé
- Timeout : 500ms max (legacy peut être lent)
- Resilience : Circuit breaker (si legacy down, dégradation gracieuse)
- Logging : Corrélation d'ID pour traçabilité

**Effort estimé :** 2-3 semaines équipe Backend (Cycle 1)

**2. Stratégie de données par entité**

Nous définissons pour chaque type de donnée quelle est la **source de vérité** et la stratégie de synchronisation :

| **Entité**                            | **Source de vérité** | **Stratégie Phase 1**        | **Notes**                |
| ------------------------------------- | -------------------- | ---------------------------- | ------------------------ |
| **Utilisateurs existants**            | Legacy               | Lecture seule via API Façade | Pas de modification      |
| **Nouveaux utilisateurs**             | Nouveau système      | Isolés (pas de sync)         | Migration bulk Phase 2   |
| **Fournisseurs existants**            | Legacy               | Lecture via API si besoin    | Transition progressive   |
| **Nouveaux fournisseurs**             | Nouveau système      | Isolés                       | Focus producteurs locaux |
| **Offres alimentaires géolocalisées** | Nouveau système      | Indépendantes                | Nouvelle feature         |
| **Anciennes commandes**               | Legacy               | Lecture seule via API        | Consultation historique  |
| **Nouvelles commandes**               | Nouveau système      | Isolées                      | Géolocalisées uniquement |
| **Paiements**                         | Legacy               | API Façade (Phase 2)         | Hors scope Phase 1       |
| **Sessions/Auth**                     | Partagé              | Token JWT commun             | SSO entre systèmes       |

**3. Patterns de communication**

**Pattern A : Lecture synchrone (requête/réponse)**

```
Nouveau Service Orders
    ↓ HTTP GET (timeout 500ms)
API Façade Legacy
    ↓ Query
Legacy Database
    ↓ Response
API Façade Legacy
    ↓ JSON
Nouveau Service Orders (+ cache local 5min)
```

**Usage :** Consultation données utilisateur, historique commandes

**Pattern B : Écriture asynchrone (Phase 2)**

```
Nouveau Service
    ↓ Event (AWS EventBridge)
Lambda/Consumer
    ↓ HTTP POST
API Façade Legacy
    ↓ Insert
Legacy Database
```

**Usage :** Synchronisation événements importants (notifications, audit)

**Pattern C : Pas de communication (isolation)**

```
Nouveau Service
    ↓ Opérations isolées
Nouvelle Database (DynamoDB/RDS)
```

**Usage :** Recherche géolocalisée, nouvelles commandes Phase 1

**4. Gestion des défaillances et résilience**

**Scénario 1 : API Legacy indisponible**

- Circuit breaker s'ouvre après 3 échecs
- Dégradation gracieuse : message utilisateur clair
- Fallback : données en cache si disponibles
- Alerting : PagerDuty notification équipe

**Scénario 2 : Legacy lent (> 500ms)**

- Timeout strict à 500ms
- Retry avec backoff exponentiel (max 2 retries)
- Métriques de latence trackées
- Si dégradation persistante : mode dégradé automatique

**Scénario 3 : Nouveau système indisponible**

- API Gateway route 100% vers legacy
- Rollback automatique si healthcheck échoue
- RTO (Recovery Time Objective) : < 5 minutes

**5. Contrats d'API et gouvernance**

**Tous les échanges inter-systèmes doivent :**

- ✅ Être documentés en OpenAPI 3.0
- ✅ Avoir des tests de contrat automatisés (Pact/Spring Cloud Contract)
- ✅ Respecter le versioning sémantique (v1, v2...)
- ✅ Inclure correlation-id pour traçabilité
- ✅ Être monitorés (latence, erreurs, volume)

**Processus de changement :**

1. Proposition de changement d'API (ADR)
2. Revue architecture (backward compatibility)
3. Mise à jour contrats OpenAPI
4. Tests de contrat validés
5. Déploiement avec versioning

**6. Observabilité inter-systèmes**

**Métriques clés à monitorer :**

| **Métrique**              | **Cible**        | **Alerte si** | **Action**             |
| ------------------------- | ---------------- | ------------- | ---------------------- |
| Latence API Façade (p95)  | < 300ms          | > 500ms       | Investigation legacy   |
| Taux d'erreur intégration | < 0.1%           | > 1%          | Circuit breaker        |
| Disponibilité API Façade  | > 99.5%          | < 99%         | Escalade équipe legacy |
| Volume d'appels /jour     | Baseline +/- 20% | Pic anormal   | Vérifier routing       |
| Timeout rate              | < 0.5%           | > 2%          | Optimisation requêtes  |

**Dashboards requis :**

- Vue unifiée : nouveau + legacy (Grafana/CloudWatch)
- Distributed tracing (AWS X-Ray) : suivi requête end-to-end
- Logs centralisés (ELK/CloudWatch Logs) : corrélation des incidents

**7. Plan de développement API Façade**

**Cycle 1 (M1-M2) :**

- Sprint 1-2 : Analyse APIs legacy existantes (ou reverse engineering)
- Sprint 3 : Développement API Façade (endpoints P0)
- Sprint 4 : Tests, documentation OpenAPI, monitoring

**Livrables Cycle 1 :**

- Spécification OpenAPI 3.0 complète
- API Façade déployée (endpoints P0)
- Tests de contrat automatisés
- Runbook troubleshooting intégration

**Équipe dédiée (Cycle 1) :**

- 1 développeur senior Backend (lead)
- 1 développeur connaissant le legacy (expert métier)
- Support DevOps pour infra/monitoring

**Risques spécifiques intégration :**

| **Risque**                           | **Gravité** | **Probabilité** | **Mitigation**                                |
| ------------------------------------ | ----------- | --------------- | --------------------------------------------- |
| Documentation legacy inexistante     | Élevée      | Élevée          | Reverse engineering, tests exploratoires      |
| Performances legacy insuffisantes    | Moyenne     | Moyenne         | Caching agressif, timeouts stricts            |
| Changements non coordonnés           | Moyenne     | Faible          | Gel strict legacy, tests de contrat           |
| Sécurité : exposition données legacy | Élevée      | Faible          | API Gateway avec authentification, audit logs |

**Hypothèses clés :**

| **ID** | **Hypothèse**                                       | **Impact si fausse**  | **Validation**        |
| ------ | --------------------------------------------------- | --------------------- | --------------------- |
| I1     | Le legacy peut supporter 50 req/sec supplémentaires | Saturation, latence   | Load testing Cycle 1  |
| I2     | La structure DB legacy est stable                   | Rupture de contrat    | Documentation + tests |
| I3     | L'équipe peut accéder au code/DB legacy             | Blocage développement | Accès confirmé M1     |

### 5.4 Orientations technologiques stratégiques

Cette section définit les choix technologiques de haut niveau qui guideront l'implémentation. Les détails techniques précis seront documentés dans la Spécification des Exigences Architecturales.

#### 5.4.1 Cloud Provider : Amazon Web Services (AWS)

**Choix retenu :** AWS comme plateforme cloud principale

**Justifications :**

- **Services géospatiaux natifs** : Amazon Location Service, DynamoDB avec indexation géospatiale
- **Écosystème microservices mature** : EKS, ECS, Lambda, API Gateway, EventBridge
- **Optimisation coûts** : Reserved Instances, Savings Plans, auto-scaling granulaire
- **Conformité et sécurité** : Certifications requises (RGPD), outils natifs (IAM, KMS)
- **Adoption industrie** : Standard de facto, documentation extensive, communauté active

**Alternatives considérées mais non retenues (Phase 1) :**

- Google Cloud Platform (GCP) : Excellents services ML/AI mais moins mature sur géospatial
- Microsoft Azure : Forte si intégration Microsoft existante (non applicable à Foosus)
- Multi-cloud : Complexité opérationnelle trop élevée pour une startup

**Principe directeur :** Éviter le vendor lock-in excessif via conteneurisation et abstraction des services managés critiques.

#### 5.4.2 Architecture applicative : Microservices containerisés

**Pattern architectural :** Microservices découplés

**Justifications :**

- **Scalabilité indépendante** : Recherche géolocalisée peut scaler différemment des commandes
- **Autonomie des équipes** : Équipes frontend/backend/DevOps peuvent itérer indépendamment
- **Résilience** : Isolation des pannes (bulkhead pattern)
- **Déploiement continu** : Chaque service déployable indépendamment
- **Technologie polyglotte** : Choix du meilleur outil par service (si justifié)

**Technologies de conteneurisation :**

- **Docker** : Conteneurisation standard industrie
- **Amazon EKS (Elastic Kubernetes Service)** : Orchestration Kubernetes managée
  - Alternative considérée : ECS (plus simple) vs EKS (plus standard, portable)
  - Choix EKS pour portabilité long terme et compétences marché

**Topologie des services (Phase 1) :**

- Service de recherche géolocalisée (Search Service)
- Service de gestion des fournisseurs (Supplier Service)
- Service de gestion des commandes (Order Service)
- Service de gestion des utilisateurs (User Service)
- API Gateway (point d'entrée unique)

**Pattern complémentaires :**

- **API Gateway** : Routage, authentification, rate limiting, monitoring
- **Service Mesh (Phase 2)** : Istio/AWS App Mesh pour communication inter-services avancée
- **Event-Driven Architecture** : EventBridge/SNS pour découplage temporel

#### 5.4.3 Stratégie de données : Polyglot Persistence

**Principe :** Chaque service choisit la base de données optimale pour son cas d'usage

**Orientations par type de données :**

| **Type de données**           | **Technologie**               | **Justification**                               |
| ----------------------------- | ----------------------------- | ----------------------------------------------- |
| **Données géospatiales**      | Amazon DynamoDB + indexes géo | Performance, scalabilité, support natif geohash |
| **Données transactionnelles** | Amazon RDS PostgreSQL         | ACID, relations complexes, maturité             |
| **Cache distribué**           | Amazon ElastiCache (Redis)    | Latence ultra-faible, sessions utilisateurs     |
| **Recherche full-text**       | Amazon OpenSearch             | Recherche avancée, analytics, dashboards        |
| **Stockage objets**           | Amazon S3                     | Assets statiques, backups, data lake futur      |
| **Données temporelles**       | Amazon Timestream (Phase 2)   | Métriques, IoT futur (tracking livraisons)      |

**Patterns de données :**

- **Database per Service** : Chaque microservice possède sa propre base
- **CQRS (Command Query Responsibility Segregation)** : Séparation lecture/écriture pour performance
- **Event Sourcing (sélectif)** : Pour audit trail et synchronisation legacy

**Cohérence des données :**

- **Eventual Consistency** acceptée pour la plupart des cas d'usage
- **Strong Consistency** uniquement pour transactions financières critiques (Phase 2)

#### 5.4.4 APIs et intégration

**Approche multi-protocole selon les besoins :**

**REST (RESTful APIs)** - Communication inter-services

- Standard HTTP(S), verbes sémantiques (GET, POST, PUT, DELETE)
- JSON comme format d'échange
- Versioning dans l'URL (/v1/, /v2/) ou headers
- Documentation : OpenAPI 3.0 (Swagger)
- **Usage** : APIs backend-to-backend, intégration legacy

**GraphQL** - Exposition aux clients (web/mobile)

- Requêtes flexibles côté client (évite over-fetching)
- Schema fortement typé
- Single endpoint avec résolution de champs
- **Usage** : Frontend optimisé, applications mobiles

**gRPC (Phase 2)** - Communication haute performance

- Protocole binaire (Protocol Buffers)
- Streaming bidirectionnel
- **Usage** : Communication interne services critiques (si besoin prouvé)

**Webhooks** - Notifications asynchrones

- **Usage** : Intégration partenaires externes (Phase 2+)

**Standards transversaux :**

- **Authentication** : OAuth 2.0 + OpenID Connect (OIDC)
- **Authorization** : JWT (JSON Web Tokens) avec claims
- **Formats géospatiaux** : GeoJSON (RFC 7946)
- **Logging/Tracing** : Correlation ID dans tous les headers

#### 5.4.5 Frontend et expérience utilisateur

**Approche :** Progressive Web App (PWA) responsive

**Framework JavaScript moderne (à valider Cycle 1 avec équipe Frontend) :**

- **Options considérées** : React, Vue.js, Angular
- **Critères de sélection** :
  - Compétences actuelles équipe Frontend
  - Performance mobile (critical pour géolocalisation)
  - Écosystème de composants UI
  - Time-to-market (courbe d'apprentissage)

**Principes architecturaux frontend :**

- **Mobile-first** : Design pensé d'abord pour mobile puis adapté desktop
- **Responsive Design** : Breakpoints multiples (mobile, tablet, desktop)
- **Progressive Enhancement** : Fonctionnalités de base accessibles même sur connexions lentes
- **Offline-capable** : Service Workers pour cache local (PWA)

**Distribution :**

- **Web** : Hébergement S3 + CloudFront (CDN global)
- **Mobile** : PWA installable + (Phase 2) apps natives React Native si besoin

**Build et bundling :**

- Webpack/Vite pour bundling optimisé
- Code splitting et lazy loading
- Compression assets (images WebP, minification)

#### 5.4.6 Observabilité et monitoring

**Principe :** Observabilité intégrée dès la conception (not an afterthought)

**Trois piliers de l'observabilité :**

**1. Metrics (Métriques)**

- **AWS CloudWatch** : Métriques infrastructure et applicatives
- **Prometheus + Grafana** : Métriques custom applicatives, dashboards
- **Métriques business** : Inscriptions, commandes, recherches/min

**2. Logs (Journaux)**

- **AWS CloudWatch Logs** : Agrégation centralisée
- **ELK Stack (Phase 2)** : Elasticsearch, Logstash, Kibana pour analytics avancés
- **Format structuré** : JSON avec correlation-id pour traçabilité

**3. Traces (Traçage distribué)**

- **AWS X-Ray** : Distributed tracing end-to-end
- **OpenTelemetry** : Standard instrumentalisation (portabilité future)
- **Trace sampling** : 100% erreurs, 5-10% succès (optimisation coûts)

**Alerting :**

- PagerDuty ou AWS SNS pour notifications critiques
- Slack pour alertes non-critiques
- Escalation automatique si non-acknowledgé

**Dashboards :**

- Vue business (KPIs métier en temps réel)
- Vue technique (latence, erreurs, saturation, traffic)
- Vue coûts (AWS Cost Explorer intégré)

#### 5.4.7 CI/CD et DevOps

**Pipeline de déploiement continu :**

**Outils :**

- **Git** : GitHub ou GitLab pour versioning
- **CI** : GitHub Actions ou AWS CodePipeline
- **CD** : ArgoCD (GitOps sur Kubernetes) ou AWS CodeDeploy
- **Registre images** : Amazon ECR (Elastic Container Registry)

**Processus :**

```
Code Commit → Build → Tests Auto → Security Scan → Deploy Dev → Tests E2E → Deploy Staging → Tests Smoke → Deploy Prod
```

**Stratégie de déploiement :**

- **Blue/Green Deployment** : Bascule instantanée entre versions
- **Canary Releases** : Déploiement progressif (5% → 25% → 100%)
- **Feature Flags** : Activation/désactivation features en production (LaunchDarkly ou AWS AppConfig)

**Tests automatisés :**

- Tests unitaires (>80% couverture)
- Tests d'intégration (contrats d'API)
- Tests de bout en bout (Cypress, Playwright)
- Tests de charge (k6, Gatling)

**Infrastructure as Code (IaC) :**

- **Terraform** : Provisioning infrastructure AWS (preferred pour portabilité)
- Alternative : AWS CloudFormation (native mais vendor lock-in)
- **Helm Charts** : Déploiement applications Kubernetes

#### 5.4.8 Sécurité by Design

**Principes de sécurité intégrés :**

**Identity and Access Management (IAM) :**

- Principe du moindre privilège (least privilege)
- Rôles IAM par service (pas de credentials hardcodés)
- Rotation automatique des secrets (AWS Secrets Manager)

**Sécurité réseau :**

- VPC isolé avec subnets publics/privés
- Security Groups stricts (whitelisting)
- WAF (Web Application Firewall) sur API Gateway
- DDoS protection (AWS Shield)

**Chiffrement :**

- **Transit** : TLS 1.3 pour toutes les communications
- **At Rest** : Chiffrement base de données (KMS), S3 (SSE)

**Conformité RGPD :**

- Données personnelles identifiées et cartographiées
- Mécanismes de suppression (right to be forgotten)
- Audit logs pour traçabilité

**Scanning et audits :**

- Scan vulnérabilités images Docker (Trivy, Snyk)
- Scan dépendances (Dependabot, npm audit)
- Pentest externe (Phase 2, avant production publique)

#### 5.4.9 Décisions reportées (à valider durant implémentation)

Les choix suivants seront finalisés durant les cycles de développement selon les besoins émergents :

| **Décision**               | **Options**                      | **Quand décider**                 |
| -------------------------- | -------------------------------- | --------------------------------- |
| Framework Frontend précis  | React vs Vue.js vs Angular       | Cycle 1 (avec équipe Frontend)    |
| Message Broker             | SNS/SQS vs EventBridge vs Kafka  | Cycle 2 (volume events)           |
| Service Mesh               | Istio vs AWS App Mesh vs None    | Phase 2 (si complexité justifie)  |
| Base de données secondaire | PostgreSQL vs MySQL              | Cycle 2 (selon patterns accès)    |
| Monitoring avancé          | ELK Stack vs CloudWatch Insights | Cycle 3 (analyse coûts/bénéfices) |

**Principe ADR (Architecture Decision Records) :**
Toutes les décisions architecturales majeures seront documentées avec :

- Contexte
- Options considérées
- Décision prise
- Conséquences (trade-offs)

### 5.5 Méthodologies et standards

**Standards techniques à respecter :**

- REST/GraphQL pour APIs
- OpenAPI 3.0 pour documentation APIs
- JSON pour échanges de données
- OAuth2/OIDC pour authentification
- Standards géospatiaux (GeoJSON)

**Principes Lean Architecture :**

- Just enough architecture upfront
- Décisions réversibles privilégiées
- Feedback continu via prototypage
- Documentation as code (ADRs - Architecture Decision Records)

---

## 6. Plan de travail

### 6.1 Approche en 3 cycles de 2 mois

**Cycle 1 (M1-M2) : Fondations & Vision**

- **Objectif** : Établir les fondations architecturales et valider la faisabilité
- **Livrables** :
  - Vision d'architecture finalisée et approuvée
  - Spécification des exigences architecturales
  - Contrats d'architecture (business & dev)
  - Principes et patterns documentés
  - Architecture cible de haut niveau
  - **Stratégie de migration Strangler Fig détaillée**
  - POC infrastructure AWS + API Gateway pour routing
  - **API Façade Legacy : Analyse + Spécification OpenAPI (endpoints P0)**
  - **Load testing legacy** (capacité intégration)
  - **POC technologies clés** : DynamoDB géospatial, EKS, performances GraphQL
  - **Workshop stack technique** avec équipes (validation choix)
- **Milestone** : Go/No-Go architecture validée par comité de pilotage

**Cycle 2 (M3-M4) : Prototype Core**

- **Objectif** : Développer le cœur du système (recherche géolocalisée)
- **Livrables** :
  - Service de recherche géolocalisée fonctionnel
  - Service de gestion des fournisseurs (basique)
  - **API Façade Legacy déployée et opérationnelle** (endpoints P0/P1)
  - Infrastructure AWS déployée (compute, data, network)
  - Pipeline CI/CD opérationnel
  - Interface utilisateur prototype (web responsive)
  - Documentation APIs et guides développeur
  - **Tests de contrat API inter-systèmes automatisés**
- **Milestone** : Démo fonctionnelle recherche géolocalisée + intégration legacy

**Cycle 3 (M5-M6) : Complétion & Commandes**

- **Objectif** : Ajouter les commandes et finaliser le prototype
- **Livrables** :
  - Service de gestion des commandes
  - Interface mobile (responsive)
  - Monitoring et observabilité complets
  - **Démo de coexistence legacy/nouveau** (routing fonctionnel)
  - Tests de charge et optimisation
  - Documentation d'architecture complète
  - Plan de migration Phase 2 (détaillé)
- **Milestone** : Prototype end-to-end + coexistence démontrés au C-level

### 6.2 Rituels et communication

**Communication continue :**

- Stand-ups quotidiens (équipes dev)
- Revues architecture bi-hebdomadaires (comité pilotage)
- Démos fin de cycle (toutes parties prenantes)
- Rétrospectives (équipe étendue)

**Canaux :**

- Slack : communication quotidienne
- Confluence : documentation centralisée
- GitHub : code, ADRs, issues
- Miro : architecture visuelle collaborative

---

## 7. Risques et facteurs de réduction

### 7.1 Analyse des risques

| **ID** | **Risque**                                            | **Gravité** | **Probabilité** | **Facteur de réduction**                                           | **Propriétaire**        |
| ------ | ----------------------------------------------------- | ----------- | --------------- | ------------------------------------------------------------------ | ----------------------- |
| R1     | Sous-estimation complexité microservices              | Élevée      | Moyenne         | Prototypage précoce, formation équipes, patterns établis           | Fonction Architecture   |
| R2     | Dépassement budget cloud AWS                          | Moyenne     | Élevée          | Monitoring coûts, optimisation continue, réservation instances     | DevOps + CFO            |
| R3     | Résistance au changement équipes legacy               | Moyenne     | Moyenne         | Implication précoce, formation, quick wins visibles                | CIO + Fonction Archi    |
| R4     | Performance recherche géospatiale insuffisante        | Élevée      | Faible          | POC précoce, tests charge, caching agressif                        | Backend + DevOps        |
| R5     | Manque d'expertise cloud-native dans équipes          | Moyenne     | Élevée          | Formation AWS, pair programming, documentation                     | CIO + Resp. Eng         |
| R6     | Indisponibilité pendant migration données             | Élevée      | Faible          | **Strangler Fig pattern**, coexistence 12-18 mois, rollback < 5min | DevOps + Fonction Archi |
| R7     | Scope creep pendant Phase 1                           | Moyenne     | Élevée          | Backlog priorisé strict, MVP focus, contrats clairs                | CPO + Fonction Archi    |
| R8     | API Façade Legacy : documentation inexistante         | Élevée      | Élevée          | Reverse engineering, expert legacy dédié, tests exploratoires      | Backend + Resp. Eng     |
| R9     | Performances legacy insuffisantes sous charge         | Moyenne     | Moyenne         | Caching agressif, circuit breaker, timeouts 500ms max              | DevOps + Backend        |
| R10    | Choix technologiques inadaptés découverts tardivement | Moyenne     | Faible          | POCs Cycle 1, ADRs documentés, décisions réversibles privilégiées  | Fonction Archi          |

### 7.2 Hypothèses

| **ID** | **Hypothèse**                                                        | **Impact si fausse**                                     | **Propriétaire**        |
| ------ | -------------------------------------------------------------------- | -------------------------------------------------------- | ----------------------- |
| H1     | Les équipes peuvent monter en compétence cloud-native en 6 mois      | Retard projet, qualité réduite                           | CIO                     |
| H2     | La plateforme legacy peut rester stable en mode maintenance strict   | Ressources détournées, incidents legacy impactent projet | Resp. Eng               |
| H3     | AWS peut fournir les performances géospatiales requises              | Changement provider, coûts                               | DevOps                  |
| H4     | Le budget 50K USD couvre architecture + prototype                    | Réduction scope                                          | CFO                     |
| H5     | Les utilisateurs adopteront progressivement la nouvelle plateforme   | Stratégie adoption à revoir                              | CMO + CPO               |
| H6     | Le legacy peut supporter 50+ req/sec via API Façade                  | Saturation système, latence élevée                       | DevOps (load test M1)   |
| H7     | L'équipe peut accéder au code et DB legacy pour reverse engineering  | Blocage développement API Façade                         | Resp. Eng (confirmé M1) |
| H8     | AWS peut fournir les performances géospatiales requises (<200ms p95) | Changement provider, refonte                             | DevOps (validé POC M1)  |
| H9     | Les équipes Frontend/Backend acceptent la stack proposée             | Friction équipes, courbe apprentissage                   | CIO (workshop M1)       |

---

## 8. Critères d'acceptation et procédures

### 8.1 Métriques et KPIs

**Métriques de succès du projet (Phase 1) :**

| **Métrique**                         | **Valeur cible** | **Méthode de mesure**            | **Justification**                 |
| ------------------------------------ | ---------------- | -------------------------------- | --------------------------------- |
| Temps réponse recherche géolocalisée | < 200ms (p95)    | Tests de performance automatisés | UX critique pour adoption         |
| Disponibilité prototype              | > 99%            | Monitoring CloudWatch            | Prouver stabilité architecture    |
| Couverture tests automatisés         | > 80%            | CI/CD pipeline                   | Qualité et confiance déploiements |
| Temps de build et déploiement        | < 15 min         | Métriques CI/CD                  | Feedback rapide développeurs      |
| Coût infrastructure mensuel          | < 2000 USD       | AWS Cost Explorer                | Viabilité économique              |
| Satisfaction équipes dev (NPS)       | > 40             | Survey fin de cycle              | Adoption et engagement            |
| Latence API Façade Legacy (p95)      | < 300ms          | CloudWatch/X-Ray                 | Performance intégration           |
| Disponibilité API Façade             | > 99.5%          | Monitoring continu               | Fiabilité coexistence             |

**Métriques business (post-déploiement) :**

- Voir objectifs section 3.1 (inscriptions, producteurs, délai parution, incidents)

### 8.2 Critères d'acceptation Phase 1

**Le prototype sera considéré comme accepté si :**

1. **Fonctionnel**

   - Recherche géolocalisée opérationnelle (rayon configurable)
   - Création et gestion de commandes bout-en-bout
   - Interface responsive (web + mobile)
   - Utilisateurs peuvent créer comptes et naviguer
   - **Intégration legacy opérationnelle** (lecture données utilisateurs)

2. **Technique**

   - Architecture microservices déployée sur AWS
   - **API Façade Legacy fonctionnelle** (endpoints P0/P1)
   - CI/CD automatisé avec tests (y compris tests de contrat)
   - Monitoring et alerting configurés (nouveau + legacy)
   - Documentation architecture complète

3. **Performance**

   - Métriques cibles atteintes (voir tableau ci-dessus)
   - Tests de charge validés (100 utilisateurs concurrents minimum)

4. **Gouvernance**
   - Contrats d'architecture signés
   - Principes et patterns documentés
   - ADRs (décisions) tracées
   - Plan Phase 2 validé

### 8.3 Procédure d'acceptation

1. **Revue technique** (Semaine M6-2) : Équipe engineering + DevOps
2. **Revue architecture** (Semaine M6-1) : Comité de pilotage
3. **Démo exécutive** (Semaine M6) : C-level + investisseurs
4. **Décision Go/No-Go Phase 2** (Fin M6)

---

## 9. Approbations

### 9.1 Signatures requises

| **Rôle**               | **Nom**        | **Signature**              | **Date**   |
| ---------------------- | -------------- | -------------------------- | ---------- |
| CEO & Sponsor          | Ash Callum     | **\*\*\*\***\_**\*\*\*\*** | **\_\_\_** |
| CIO                    | Natasha Jarson | **\*\*\*\***\_**\*\*\*\*** | **\_\_\_** |
| CPO                    | Daniel Anthony | **\*\*\*\***\_**\*\*\*\*** | **\_\_\_** |
| Responsable Ingénierie | Pete Parker    | **\*\*\*\***\_**\*\*\*\*** | **\_\_\_** |
| Fonction Architecture  | [Votre nom]    | **\*\*\*\***\_**\*\*\*\*** | **\_\_\_** |

---

## 10. Prochaines étapes

Après validation de cette Déclaration de Travail :

1. **Semaine 1** : Élaboration Spécification des Exigences Architecturales
2. **Semaine 2** : Rédaction Contrats d'Architecture (Business & Dev)
3. **Semaine 3** : Architecture de haut niveau et choix technologiques
4. **Semaine 4** : Démarrage Cycle 1 - POC infrastructure

---

**Document vivant** : Cette déclaration sera mise à jour selon les apprentissages des cycles itératifs.

**Version** : 0.1 - Brouillon pour révision  
**Dernière mise à jour** : Octobre 2025
