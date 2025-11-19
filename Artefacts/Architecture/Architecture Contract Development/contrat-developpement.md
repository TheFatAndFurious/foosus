---
title: "Contrat de Conception et de Développement de l'Architecture"
subtitle: "Plateforme Foosus Géoconsciente"
project: "Plateforme Foosus Géoconsciente - Phase 1"
client: "Foosus"
author: "Mathieu Baro"
version: "0.1 - DRAFT"
date: "Novembre 2025"
status: "Brouillon pour validation"
type: "Contrat d'Architecture Développement"
---

# Contrat de Conception et de Développement de l'Architecture

**Plateforme Foosus Géoconsciente**

---

## Informations du Document

| Champ               | Valeur                                    |
| ------------------- | ----------------------------------------- |
| **Projet**          | Plateforme Foosus Géoconsciente - Phase 1 |
| **Client**          | Foosus                                    |
| **Préparé par**     | Mathieu Baro                              |
| **Version**         | 0.1 - DRAFT                               |
| **Date**            | Novembre 2025                             |
| **Statut**          | Brouillon pour validation                 |
| **Type de contrat** | Contrat d'Architecture Développement      |

---

## Table des Matières

1. [Objet de ce document](#1-objet-de-ce-document)
2. [Introduction et contexte](#2-introduction-et-contexte)
3. [La nature de l'accord](#3-la-nature-de-laccord)
4. [Objectifs et périmètre](#4-objectifs-et-périmètre)
5. [Description de l'architecture, principes stratégiques et conditions requises](#5-description-de-larchitecture-principes-stratégiques-et-conditions-requises)
6. [Livrables architecturaux](#6-livrables-architecturaux)
7. [Plan de travail commun priorisé](#7-plan-de-travail-commun-priorisé)
8. [Plan de communication](#8-plan-de-communication)
9. [Risques et facteurs de réduction](#9-risques-et-facteurs-de-réduction)
10. [Hypothèses](#10-hypothèses)
11. [Critères d'acceptation et procédures](#11-critères-dacceptation-et-procédures)
12. [Procédures de changement de périmètre](#12-procédures-de-changement-de-périmètre)
13. [Calendrier](#13-calendrier)
14. [Phases de livrables définies](#14-phases-de-livrables-définies)
15. [Personnes approuvant ce plan](#15-personnes-approuvant-ce-plan)

---

## 1. Objet de ce document

Les **Contrats d'Architecture** sont les accords communs entre les partenaires de développement et les sponsors sur les livrables, la qualité, et la correspondance à l'objectif d'une architecture.

L'implémentation réussie de ces accords sera livrée grâce à une gouvernance de l'architecture efficace (voir TOGAF Partie VII, Gouvernance de l'architecture). En implémentant une approche dirigée du management de contrats, les éléments suivants seront garantis :

- **Un système de contrôle continu** pour vérifier l'intégrité, les changements, les prises de décisions, et l'audit de toutes les activités relatives à l'architecture au sein de l'organisation.

- **L'adhésion aux principes, standards et conditions requises** des architectures existantes ou en développement.

- **L'identification des risques** dans tous les aspects du développement et de l'implémentation de l'architecture, y compris le développement interne en fonction des standards acceptés, des politiques, des technologies et des produits, de même que les aspects opérationnels des architectures de façon à ce que l'organisation puisse poursuivre son business au sein d'un environnement résilient.

- **Un ensemble de processus et de pratiques** qui garantissent la transparence, la responsabilité et la discipline au regard du développement et de l'utilisation de tous les artefacts architecturaux.

- **Un accord formel** sur l'organe de gouvernance responsable du contrat, son degré d'autorité, et le périmètre de l'architecture sous la gouvernance de cet organe.

Ceci est une **déclaration d'intention signée** sur la conception et le développement de l'architecture d'entreprise, ou de parties significatives de celles-ci, de la part d'organisations partenaires, y compris les intégrateurs système, fournisseurs d'applications, et fournisseurs de service.

### 1.1 Contexte d'externalisation

De plus en plus, le développement d'un ou plusieurs domaine(s) d'architecture (business, données, application, technologie) peut être externalisé, avec la fonction d'architecture de l'entreprise fournissant une vue d'ensemble de l'architecture d'entreprise globale, ainsi que la coordination et le contrôle de l'effort total.

Dans certains cas, même ce rôle de supervision peut être externalisé, bien que la plupart des entreprises préfèrent conserver cette responsabilité clé en interne.

Quelles que soient les spécificités des dispositions d'externalisation, les dispositions elles-mêmes seront normalement gouvernées par un Contrat d'Architecture qui définit les livrables, la qualité, et la correspondance à l'objectif de l'architecture développée, ainsi que les processus de collaboration pour les partenaires du développement de l'architecture.

---

## 2. Introduction et contexte

### Contexte du projet

Foosus, plateforme de mise en relation entre consommateurs et producteurs locaux, entreprend une transformation majeure de son infrastructure technologique pour répondre à la croissance du marché et améliorer l'expérience utilisateur.

**Contexte business** :

- Système legacy monolithique atteignant ses limites en termes de performance et de scalabilité
- Besoin d'une solution capable de supporter 5 000 utilisateurs simultanés
- Opportunité de différenciation par la géolocalisation en temps réel
- Exigences réglementaires strictes (GDPR, données personnelles)
- Contraintes budgétaires ($50,000 pour la Phase 1) et temporelles (6 mois)

**Contexte technique** :

- Migration d'un monolithe vers une architecture microservices cloud-native
- Adoption d'AWS comme plateforme cloud
- Implémentation progressive via le pattern Strangler Fig
- Coexistence nécessaire avec le système legacy durant la transition

**Organisation du développement** :

- Équipe Frontend : 3 développeurs (Expo, TypeScript)
- Équipe Backend : 3 développeurs (Node.js, NestJS)
- Équipe DevOps : 3 ingénieurs (AWS, Infrastructure as Code)
- Engineering Manager : Pete Parker
- Architecture Function Lead : Supervision et coordination

---

## La nature de l'accord

Ce Contrat de Développement de l'Architecture établit un accord formel entre :

**Parties contractantes** :

- **Sponsors du projet** : CEO Ash Callum, CIO Natasha Jarson, CPO Daniel Anthony, CFO Jo Kumar
- **Équipes de développement** : Frontend Team, Backend Team, DevOps Team
- **Function d'Architecture** : Architecture Function Lead
- **Management Engineering** : Pete Parker, Engineering Manager

**Nature de l'engagement** :

Ce contrat formalise les engagements réciproques suivants :

1. **Engagements des équipes de développement** :

   - Respecter les principes architecturaux et standards techniques définis
   - Livrer des composants conformes aux spécifications d'architecture
   - Participer aux revues d'architecture et processus de gouvernance
   - Implémenter les patterns et pratiques recommandés
   - Maintenir la documentation technique à jour

2. **Engagements de la fonction Architecture** :

   - Fournir des spécifications claires et réalisables
   - Assurer un support technique continu aux équipes
   - Faciliter la résolution des problèmes architecturaux
   - Adapter l'architecture aux contraintes identifiées
   - Maintenir la cohérence globale du système

3. **Engagements des sponsors** :
   - Fournir les ressources nécessaires (budget, temps, personnel)
   - Valider les décisions architecturales majeures
   - Arbitrer les conflits de priorités
   - Supporter les changements organisationnels nécessaires

**Périmètre de gouvernance** :

- Architecture des microservices de la Phase 1 (Geolocation Search, Order Management)
- Infrastructure AWS et services cloud utilisés
- Pratiques de développement, déploiement et opérations
- Standards de qualité, sécurité et performance
- Processus de revue et validation architecturale

**Durée du contrat** :

- Phase 1 : 6 mois (novembre 2025 - avril 2026)
- Révision trimestrielle obligatoire
- Renouvellement pour Phase 2 après évaluation des résultats

## Objectifs et périmètre

### Objectifs

Les objectifs business de ce Travail d'Architecture sont les suivants :

#### Objectif Business 1 : Améliorer significativement la performance et la scalabilité

**Description** :
Migrer de l'architecture monolithique legacy vers une architecture microservices cloud-native capable de supporter la croissance prévue de l'activité.

**Critères de succès mesurables** :

- Support de 5 000 utilisateurs simultanés avec un taux de disponibilité de 99,99%
- Latence p95 < 200ms pour les recherches géolocalisées
- Temps de chargement initial < 3 secondes
- Capacité de scaling horizontal automatique basé sur la charge

**Justification business** :
L'architecture actuelle limite la croissance commerciale. La nouvelle architecture permettra d'acquérir de nouveaux marchés sans dégradation de l'expérience utilisateur.

#### Objectif Business 2 : Accélérer le time-to-market des nouvelles fonctionnalités

**Description** :
Établir une architecture modulaire permettant le développement, le test et le déploiement indépendants des composants.

**Critères de succès mesurables** :

- Réduction du cycle de déploiement de 2 semaines à 1 jour
- Capacité de déployer un microservice sans impact sur les autres
- Taux d'échec de déploiement < 5%
- Rollback possible en moins de 5 minutes

**Justification business** :
Accélérer l'innovation et répondre rapidement aux besoins du marché pour maintenir l'avantage compétitif de Foosus.

#### Objectif Business 3 : Réduire les coûts opérationnels à moyen terme

**Description** :
Optimiser l'utilisation des ressources cloud via l'auto-scaling, la conteneurisation et l'automatisation.

**Critères de succès mesurables** :

- Réduction de 30% des coûts d'infrastructure sur 12 mois
- Utilisation moyenne des ressources > 70%
- Automatisation de 90% des tâches opérationnelles répétitives

**Justification business** :
L'optimisation des coûts permettra de réinvestir dans l'innovation et d'améliorer la rentabilité.

#### Objectif Business 4 : Assurer la conformité réglementaire et la sécurité

**Description** :
Implémenter une architecture secure-by-design respectant les exigences GDPR et les standards de sécurité.

**Critères de succès mesurables** :

- Conformité GDPR complète (données France uniquement en Phase 1)
- Chiffrement de toutes les données sensibles (transit et repos)
- Audit trail complet de toutes les opérations critiques
- Zéro incident de sécurité majeur (P0-P1)

**Justification business** :
La conformité est non-négociable et la confiance des utilisateurs est un actif stratégique pour Foosus.

---

### Périmètre

#### Périmètre technique inclus

**Microservices de la Phase 1** :

- **Geolocation Search Service** : Recherche de producteurs par proximité géographique
- **Order Management Service** : Gestion du cycle de vie des commandes (création, suivi, statuts)

**Infrastructure et plateforme** :

- Services AWS : ECS/Fargate, RDS PostgreSQL, ElastiCache Redis, S3, CloudFront, Route53, CloudWatch
- Infrastructure as Code : Terraform pour provisionnement
- CI/CD : GitHub Actions, AWS CodePipeline
- Monitoring et observabilité : CloudWatch, logs centralisés, métriques APM

**Patterns et pratiques** :

- Architecture microservices avec API Gateway
- Event-driven architecture (EventBridge)
- Strangler Fig pattern pour migration progressive
- Domain-Driven Design pour modélisation métier
- CQRS où approprié

**Qualité et sécurité** :

- Tests automatisés (unit, integration, e2e)
- Revues de code obligatoires
- Analyse de sécurité (SAST, DAST)
- Performance testing et load testing

#### Périmètre explicitement exclu

**Hors périmètre Phase 1** :

- Système de paiement en ligne (paiement à la livraison uniquement)
- Internationalisation (France uniquement)
- Application mobile native (web responsive uniquement)
- Migration des autres modules legacy (sera Phase 2+)
- Analytics avancés et BI (version basique uniquement)
- Service de notifications push (emails uniquement)

**Limitations Phase 1** :

- Pas de multi-région (région France uniquement)
- Pas de disaster recovery complet (backups quotidiens uniquement)
- Pas de A/B testing framework (sera Phase 2)

#### Contraintes acceptées

**Contraintes budgétaires** :

- Budget maximum : $50,000 pour Phase 1
- Utilisation de services AWS managés pour optimiser les coûts
- Pas d'embauche externe (équipes existantes uniquement)

**Contraintes temporelles** :

- Durée : 6 mois maximum
- Livraison incrémentale tous les 2 sprints (4 semaines)
- MVP fonctionnel à mi-parcours (3 mois)

**Contraintes techniques** :

- Stack technique imposée : Node.js/NestJS backend, Expo frontend
- Cloud provider : AWS uniquement
- Pas de changement d'organisation des équipes

---

### Parties prenantes, préoccupations et visions

| Partie prenante                       | Préoccupations                                                                                                                        | Vision / Perspectives                                                                                                                                          |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Ash Callum (CEO)**                  | - ROI et impact sur la croissance<br>- Time-to-market<br>- Différenciation compétitive<br>- Risques de migration                      | **Vision Business** :<br>- Roadmap de migration<br>- Business case et projections financières<br>- Analyse compétitive<br>- KPIs business                      |
| **Natasha Jarson (CIO)**              | - Faisabilité technique<br>- Respect du budget et planning<br>- Qualité de l'architecture<br>- Réduction de la dette technique        | **Vision Technique** :<br>- Architecture de référence<br>- Standards techniques<br>- Plan de migration détaillé<br>- Stratégie de réduction de dette technique |
| **Daniel Anthony (CPO)**              | - Expérience utilisateur<br>- Nouvelles fonctionnalités possibles<br>- Performance perçue<br>- Compatibilité avec roadmap produit     | **Vision Produit** :<br>- Journey maps utilisateurs<br>- Matrice features/architecture<br>- Métriques UX<br>- Roadmap fonctionnelle                            |
| **Jo Kumar (CFO)**                    | - Contrôle des coûts<br>- Prévisibilité budgétaire<br>- ROI financier<br>- Optimisation des dépenses cloud                            | **Vision Financière** :<br>- Modèle de coûts détaillé<br>- Projections TCO<br>- Analyse coût/bénéfice<br>- Plan d'optimisation des coûts                       |
| **Pete Parker (Engineering Manager)** | - Faisabilité pour les équipes<br>- Charge de travail réaliste<br>- Compétences requises<br>- Risques techniques<br>- Qualité du code | **Vision Développement** :<br>- Architecture logicielle détaillée<br>- Standards de code<br>- Plan de montée en compétence<br>- Métriques de qualité           |
| **Équipes de Développement**          | - Clarté des spécifications<br>- Outils et frameworks<br>- Processus de développement<br>- Support technique<br>- Charge de travail   | **Vision Implémentation** :<br>- Spécifications techniques détaillées<br>- Guides de développement<br>- Architecture des composants<br>- Patterns et exemples  |
| **Équipe DevOps**                     | - Automatisation<br>- Fiabilité de l'infrastructure<br>- Monitoring et alerting<br>- Gestion des incidents                            | **Vision Opérations** :<br>- Architecture d'infrastructure<br>- Stratégie de déploiement<br>- Plan de monitoring<br>- Runbooks et procédures                   |

---

## Description de l'architecture, principes stratégiques et conditions requises

### Description de l'architecture

#### Architecture globale

L'architecture cible est une **architecture microservices cloud-native** déployée sur AWS, organisée selon les principes suivants :

**Couche Frontend** :

- Application Expo/TypeScript en Single Page Application (SPA)
- Hébergée sur S3 avec distribution CloudFront
- Communication avec backend via API Gateway REST
- Responsive design (mobile-first)

**Couche Backend - Microservices** :

- **Geolocation Search Service** :
  - Recherche géographique via PostGIS
  - Cache Redis pour optimisation des requêtes fréquentes
  - API REST : `GET /api/v1/producers/nearby`
  - Base de données : RDS PostgreSQL avec extension PostGIS
- **Order Management Service** :
  - Gestion du cycle de vie des commandes
  - Event-driven via EventBridge pour notifications
  - API REST : `POST /api/v1/orders`, `GET /api/v1/orders/{id}`, `PATCH /api/v1/orders/{id}/status`
  - Base de données : RDS PostgreSQL

**Couche Infrastructure** :

- **Compute** : ECS Fargate pour orchestration des conteneurs
- **Données** : RDS PostgreSQL (multi-AZ pour HA), ElastiCache Redis
- **Stockage** : S3 pour assets statiques et fichiers
- **Réseau** : VPC avec subnets publics/privés, NAT Gateway, Security Groups
- **CDN** : CloudFront pour distribution mondiale
- **DNS** : Route53 pour gestion DNS
- **API** : API Gateway comme point d'entrée unique

**Couche Observabilité** :

- Logs : CloudWatch Logs avec centralisation
- Métriques : CloudWatch Metrics + métriques custom
- Tracing : AWS X-Ray pour distributed tracing
- Alerting : CloudWatch Alarms + SNS pour notifications

#### Stratégie de migration - Pattern Strangler Fig

La migration s'effectuera progressivement pour minimiser les risques :

**Phase 1a (Mois 1-2)** : Infrastructure et premier microservice

- Setup infrastructure AWS (IaC avec Terraform)
- Déploiement Geolocation Search Service
- Routage partiel via API Gateway (nouveaux endpoints)
- Legacy continue de gérer les autres fonctionnalités

**Phase 1b (Mois 3-4)** : Second microservice

- Déploiement Order Management Service
- Routage étendu via API Gateway
- Synchronisation bidirectionnelle legacy ↔ nouveau système
- Tests de charge et validation

**Phase 1c (Mois 5-6)** : Stabilisation et optimisation

- Optimisations de performance
- Monitoring et fine-tuning
- Documentation et formation
- Préparation Phase 2

**Critères de succès de la migration** :

- Aucune interruption de service > 5 minutes
- Aucune perte de données
- Rollback possible à tout moment
- Performance égale ou supérieure au legacy

---

### Principes stratégiques

Les principes architecturaux suivants guident toutes les décisions techniques :

#### Principe 1 : Cloud-Native First

**Énoncé** : Privilégier les services managés AWS plutôt que les solutions auto-hébergées.

**Justification** :

- Réduit la charge opérationnelle
- Améliore la disponibilité et la résilience
- Accélère le time-to-market
- Optimise les coûts (pas de gestion d'infrastructure)

**Implications** :

- Utiliser RDS au lieu de PostgreSQL auto-hébergé
- Utiliser ElastiCache au lieu de Redis auto-géré
- Utiliser ECS Fargate au lieu de gérer des EC2

#### Principe 2 : API-First Design

**Énoncé** : Toutes les fonctionnalités doivent être exposées via des APIs REST bien définies.

**Justification** :

- Facilite l'intégration future (mobile, partenaires)
- Permet le développement parallèle frontend/backend
- Favorise la réutilisabilité
- Simplifie les tests

**Implications** :

- Spécification OpenAPI pour toutes les APIs
- Versionning des APIs (v1, v2)
- Documentation Swagger automatique
- Contract testing obligatoire

#### Principe 3 : Security by Design

**Énoncé** : La sécurité est intégrée dès la conception, pas ajoutée a posteriori.

**Justification** :

- Conformité GDPR obligatoire
- Protection des données sensibles (restaurants, producteurs)
- Réputation de Foosus en jeu
- Coût de correction plus élevé si fait tardivement

**Implications** :

- Chiffrement systématique (TLS, encryption at rest)
- Principe du moindre privilège (IAM roles)
- Audit trail de toutes les opérations sensibles
- Revue de sécurité pour chaque composant

#### Principe 4 : Observability is Key

**Énoncé** : Tous les composants doivent être observables (logs, métriques, traces).

**Justification** :

- Détection rapide des problèmes
- Facilite le debugging en production
- Permet l'optimisation basée sur les données réelles
- Essentiel pour SLA 99.9%

**Implications** :

- Logging structuré obligatoire (JSON)
- Métriques custom pour KPIs business
- Distributed tracing pour requêtes inter-services
- Dashboards en temps réel

#### Principe 5 : Fail Fast, Fail Safe

**Énoncé** : Les systèmes doivent détecter les erreurs rapidement et se dégrader gracieusement.

**Justification** :

- Améliore l'expérience utilisateur
- Réduit l'impact des incidents
- Facilite le diagnostic
- Augmente la résilience globale

**Implications** :

- Health checks sur tous les services
- Circuit breakers pour appels externes
- Timeouts appropriés
- Fallback strategies (cache, données par défaut)

#### Principe 6 : Infrastructure as Code

**Énoncé** : Toute l'infrastructure doit être provisionnée et gérée via du code versionné.

**Justification** :

- Reproductibilité (dev, staging, prod)
- Traçabilité des changements
- Facilite disaster recovery
- Documentation automatique de l'infrastructure

**Implications** :

- Terraform pour tous les composants AWS
- Pas de modification manuelle via console
- Revue de code pour changements d'infrastructure
- Versioning et tagging de tous les modules

#### Principe 7 : Automatisation Maximale

**Énoncé** : Automatiser tout ce qui peut l'être (tests, déploiements, monitoring).

**Justification** :

- Réduit les erreurs humaines
- Accélère les livraisons
- Libère du temps pour l'innovation
- Améliore la qualité

**Implications** :

- CI/CD complet avec GitHub Actions
- Tests automatisés à tous les niveaux
- Déploiements blue-green automatisés
- Alerting et auto-remediation où possible

#### Principe 8 : Data Privacy by Default

**Énoncé** : Les données personnelles sont protégées par défaut et minimisées.

**Justification** :

- Conformité GDPR
- Protection des utilisateurs
- Réduction des risques légaux
- Confiance utilisateurs

**Implications** :

- Collecte minimale de données (purpose limitation)
- Données France uniquement en Phase 1
- Rétention limitée et documentée
- Droit à l'oubli implémenté

---

### Référence aux Conditions requises pour l'architecture

Ce contrat de développement s'appuie sur les documents suivants qui définissent les exigences détaillées :

1. **Architecture Requirements Specification** (référence: ARS-FOOSUS-2025-001)

   - Exigences fonctionnelles détaillées
   - Exigences non-fonctionnelles (performance, sécurité, scalabilité)
   - Contraintes techniques
   - Standards de qualité

2. **Statement of Architecture Work** (référence: SAW-FOOSUS-2025-001)

   - Scope détaillé du travail d'architecture
   - Livrables attendus
   - Ressources allouées
   - Timeline et milestones

3. **Architecture Contract - Business** (référence: ACB-FOOSUS-2025-001)
   - Engagements business
   - KPIs et métriques business
   - Gouvernance business

Les équipes de développement s'engagent à implémenter l'architecture conformément à ces spécifications. Toute dérogation devra faire l'objet d'une Architecture Decision Record (ADR) et être validée par le comité d'architecture.

---

## Livrables architecturaux

### Documentation, Code et Métriques

**1. Documentation d'Architecture**

| Livrable                                 | Description                                                    | Format                     | Responsable              | Échéance            |
| ---------------------------------------- | -------------------------------------------------------------- | -------------------------- | ------------------------ | ------------------- |
| **Architecture Decision Records (ADRs)** | Documentation de toutes les décisions architecturales majeures | Markdown dans repo Git     | Architecture Lead        | Continu             |
| **Component Diagrams**                   | Diagrammes détaillés de chaque microservice                    | C4 Model - Level 3         | Backend Team + Arch Lead | Mois 1, MAJ continu |
| **API Specifications**                   | Spécifications OpenAPI 3.0 complètes                           | YAML/JSON + Swagger UI     | Backend Team             | Mois 2              |
| **Data Models**                          | Schémas de bases de données, dictionnaire de données           | ERD + SQL DDL              | Backend Team             | Mois 1              |
| **Infrastructure Architecture**          | Architecture détaillée infrastructure AWS                      | Terraform code + Diagrams  | DevOps Team              | Mois 1              |
| **Security Architecture**                | Modèle de sécurité, authentification, chiffrement              | Diagrammes + Documentation | DevOps + Arch Lead       | Mois 2              |

**2. Guides et Standards**

| Livrable                  | Description                            | Format                    | Responsable         | Échéance |
| ------------------------- | -------------------------------------- | ------------------------- | ------------------- | -------- |
| **Coding Standards**      | Guidelines de code frontend et backend | Markdown + ESLint configs | Tech Leads          | Mois 1   |
| **API Design Guidelines** | Standards pour design d'APIs REST      | Markdown                  | Backend Lead        | Mois 1   |
| **Testing Strategy**      | Stratégie de test complète             | Markdown                  | Engineering Manager | Mois 1   |
| **Deployment Guide**      | Procédures de déploiement et rollback  | Markdown + Scripts        | DevOps Team         | Mois 2   |
| **Monitoring Guide**      | Configuration monitoring et alertes    | Markdown + Terraform      | DevOps Team         | Mois 3   |

**3. Code et Infrastructure**

| Livrable                       | Description                        | Format              | Responsable   | Échéance |
| ------------------------------ | ---------------------------------- | ------------------- | ------------- | -------- |
| **Infrastructure as Code**     | Code Terraform complet             | Terraform modules   | DevOps Team   | Mois 2   |
| **CI/CD Pipelines**            | Pipelines pour build, test, deploy | GitHub Actions YAML | DevOps Team   | Mois 2   |
| **Geolocation Search Service** | Code source microservice           | TypeScript/NestJS   | Backend Team  | Mois 3   |
| **Order Management Service**   | Code source microservice           | TypeScript/NestJS   | Backend Team  | Mois 4   |
| **Frontend Application**       | Application React complète         | TypeScript/React    | Frontend Team | Mois 4   |
| **Shared Libraries**           | Bibliothèques partagées            | NPM packages        | Backend Team  | Mois 2   |

---

### Métriques de l'architecture cible

**Métriques techniques**

| Métrique                     | Cible    | Outil de mesure    | Responsable   |
| ---------------------------- | -------- | ------------------ | ------------- |
| **Disponibilité**            | ≥ 99.9%  | CloudWatch Uptime  | DevOps Team   |
| **Latence p95 Geolocation**  | < 200ms  | CloudWatch Metrics | Backend Team  |
| **Latence p95 Orders**       | < 500ms  | CloudWatch Metrics | Backend Team  |
| **Users simultanés**         | ≥ 5,000  | Load testing (K6)  | QA + DevOps   |
| **Temps chargement**         | < 3s     | Lighthouse CI      | Frontend Team |
| **Taux d'erreur API**        | < 0.1%   | CloudWatch Logs    | Backend Team  |
| **Couverture tests**         | ≥ 80%    | Jest coverage      | Dev Teams     |
| **Vulnérabilités critiques** | 0        | Snyk + OWASP       | DevOps Team   |
| **MTTR**                     | < 30 min | Incident tracking  | DevOps Team   |

**Métriques business**

| Métrique                 | Baseline | Cible Phase 1 | Mesure                  | Responsable         |
| ------------------------ | -------- | ------------- | ----------------------- | ------------------- |
| **Temps recherche géo**  | 2-5s     | < 1s          | Analytics               | Product Team        |
| **Taux conversion**      | 12%      | ≥ 15%         | Analytics               | Product Team        |
| **NPS**                  | 45       | ≥ 55          | Surveys                 | Product Team        |
| **Coût par transaction** | $0.15    | < $0.10       | AWS Cost / Transactions | CFO                 |
| **Vélocité équipe**      | 35 pts   | ≥ 45 pts      | Jira                    | Engineering Manager |
| **Incidents P0-P1/mois** | 4-6      | < 2           | Incident tracking       | Engineering Manager |

---

### Phases de livrables définies

**Phase 1a : Fondations (Mois 1-2)**

**Objectif** : Établir les fondations architecturales et déployer le premier microservice.

Livrables majeurs :

- Infrastructure AWS complète (Terraform)
- CI/CD pipelines opérationnelles
- Geolocation Search Service déployé en production
- Documentation architecture (ADRs, Component Diagrams)
- Standards et guidelines établis

**Phase 1b : Extension (Mois 3-4)**

**Objectif** : Ajouter le second microservice et intégration frontend complète.

Livrables majeurs :

- Order Management Service déployé en production
- Frontend React avec intégration des 2 microservices
- API Gateway configuré avec routage complet
- Monitoring et alerting opérationnels
- Load testing validé (5,000 users)

**Phase 1c : Optimisation (Mois 5-6)**

**Objectif** : Optimiser, sécuriser et préparer la production complète.

Livrables majeurs :

- Optimisations de performance appliquées
- Security audit et remédiation complète
- Documentation finale
- Formation équipes
- Rapport Phase 1 + recommandations Phase 2

---

## Plan de travail commun priorisé

Cette section décrit toutes les activités et tous les livrables pour le travail d'architecture, organisés par workstream.

### Vue d'ensemble des Workstreams

| Workstream                         | Durée  | Équipe           | Priorité | Livrables principaux                          |
| ---------------------------------- | ------ | ---------------- | -------- | --------------------------------------------- |
| **WS1: Infrastructure & DevOps**   | S1-S8  | DevOps Team      | **P1**   | Infrastructure AWS, CI/CD, Monitoring         |
| **WS2: Backend Microservices**     | S3-S16 | Backend Team     | **P1**   | Geolocation Service, Order Service, Libraries |
| **WS3: Frontend Application**      | S1-S22 | Frontend Team    | **P2**   | React App, UI Components, Intégrations        |
| **WS4: Migration & Legacy**        | S7-S18 | Backend + DevOps | **P2**   | API Gateway, Sync données, Tests migration    |
| **WS5: Documentation & Formation** | S1-S22 | All Teams        | **P3**   | Docs technique, Guides, Formation             |
| **WS6: Sécurité & Conformité**     | S1-S14 | DevOps + Legal   | **P1**   | Security arch, GDPR compliance                |
| **WS7: Qualité & Testing**         | S1-S22 | QA + Dev Teams   | **P2**   | Test strategy, Test suite, Performance tests  |

---

### Workstream 1 : Infrastructure & DevOps

#### WS1.1 - Setup Infrastructure AWS (Semaines 1-4) - **CRITIQUE**

**Activités** :

1. Conception architecture réseau (VPC, subnets, NAT Gateway)
2. Définition politiques sécurité (Security Groups, IAM roles)
3. Développement modules Terraform
4. Provisionnement 3 environnements (dev, staging, prod)
5. Configuration CloudWatch, X-Ray, AWS Backup
6. Documentation infrastructure

**Livrables** :

- Code Terraform complet et versionné
- 3 environnements AWS opérationnels
- Documentation architecture infrastructure
- Runbook gestion infrastructure

**Critères d'acceptation** :

- Infrastructure reproductible via `terraform apply`
- Conformité standards sécurité AWS
- Coûts dans budget
- Documentation complète

**Responsable** : DevOps Team | **Durée** : 4 semaines

---

#### WS1.2 - CI/CD Pipelines (Semaines 3-6)

**Activités** :

1. Design stratégie CI/CD (branching, environments, approvals)
2. Configuration GitHub Actions (backend, frontend)
3. Intégration tests automatisés dans pipelines
4. Configuration analyse sécurité (Snyk, OWASP)
5. Configuration SonarQube pour qualité code
6. Setup déploiement blue-green sur ECS
7. Configuration rollback automatique
8. Documentation pipelines

**Livrables** :

- Pipelines GitHub Actions opérationnelles
- Stratégie branching documentée
- Déploiements automatisés vers tous les environnements
- Procédure rollback testée

**Critères d'acceptation** :

- Déploiement en < 15 minutes
- Taux succès > 95%
- Rollback en < 5 minutes
- Gates de qualité actives

**Responsable** : DevOps Team | **Durée** : 4 semaines

---

#### WS1.3 - Monitoring & Observability (Semaines 5-8)

**Activités** :

1. Configuration CloudWatch Dashboards
2. Setup métriques custom pour KPIs
3. Configuration alertes CloudWatch
4. Intégration AWS X-Ray pour tracing
5. Configuration logs structurés (JSON)
6. Création runbooks pour incidents
7. Configuration on-call rotation
8. Définition SLIs/SLOs/SLAs
9. Formation équipes sur monitoring

**Livrables** :

- Dashboards CloudWatch opérationnels
- Alertes pour indicateurs critiques
- Runbooks pour top 10 incidents
- Procédures escalation documentées

**Critères d'acceptation** :

- Visibilité complète sur tous composants
- Alertes sous 2 min pour incidents critiques
- MTTD < 5 minutes

**Responsable** : DevOps Team + Backend Leads | **Durée** : 4 semaines

---

### Workstream 2 : Backend Microservices

#### WS2.1 - Geolocation Search Service (Semaines 3-10) - **CRITIQUE**

**Activités** :

- Semaines 3-4 : Design & Setup (architecture, data model, API spec)
- Semaines 5-7 : Développement (repository, service, controller layers)
- Semaines 8-10 : Tests & Déploiement (integration tests, load testing, prod)

**Livrables** :

- Service déployé et opérationnel
- API REST complète avec Swagger
- Tests automatisés (coverage > 80%)
- Rapport performance (load testing)
- Documentation technique

**Critères d'acceptation** :

- Latence p95 < 200ms
- Support 5,000 users simultanés
- Cache hit rate > 85%
- API conforme OpenAPI

**Responsable** : Backend Team (3 dev) | **Durée** : 8 semaines

---

#### WS2.2 - Order Management Service (Semaines 9-16)

**Activités** :

- Semaines 9-10 : Design & Setup (architecture, state machine, events)
- Semaines 11-13 : Développement (repository, state machine, event-driven)
- Semaines 14-16 : Tests & Déploiement (integration, load testing, prod)

**Livrables** :

- Service déployé et opérationnel
- API REST complète
- Event-driven architecture (EventBridge)
- State machine commandes testée
- Tests automatisés (coverage > 80%)

**Critères d'acceptation** :

- Latence p95 < 500ms
- Gestion correcte états commandes
- Events publiés correctement
- Intégration avec Geolocation Service

**Responsable** : Backend Team (3 dev) | **Durée** : 8 semaines

---

#### WS2.3 - Shared Libraries & Tools (Semaines 5-8)

**Activités** :

1. Design architecture shared libraries
2. Implémentation logger (structured JSON, correlation IDs)
3. Implémentation error handling
4. Implémentation validation library
5. Implémentation auth/authorization utilities
6. Packaging NPM libraries
7. Documentation d'utilisation

**Livrables** :

- NPM packages privés
- Documentation complète
- Exemples d'utilisation
- Tests unitaires (coverage > 90%)

**Responsable** : Backend Team (1-2 dev) | **Durée** : 4 semaines

---

### Workstream 3 : Frontend Application

#### WS3.1 - Architecture Frontend & Setup (Semaines 1-4)

**Livrables** :

- Projet React configuré
- Architecture frontend documentée
- Guidelines développement
- Tests infrastructure
- CI/CD pipeline

**Responsable** : Frontend Team | **Durée** : 4 semaines

---

#### WS3.2 - Composants UI & Design System (Semaines 3-8)

**Livrables** :

- Bibliothèque composants UI
- Storybook avec documentation
- Design system documenté
- Tests unitaires composants

**Responsable** : Frontend Team | **Durée** : 6 semaines

---

#### WS3.3 - Intégration Geolocation Search (Semaines 11-14)

**Livrables** :

- Fonctionnalité recherche géo complète
- Intégration API backend
- Tests automatisés (unit, e2e)

**Responsable** : Frontend Team (2 dev) | **Durée** : 4 semaines

---

#### WS3.4 - Intégration Order Management (Semaines 15-18)

**Livrables** :

- Fonctionnalité gestion commandes complète
- Flow complet utilisateur
- Tests e2e du flow

**Responsable** : Frontend Team (2 dev) | **Durée** : 4 semaines

---

#### WS3.5 - Optimisation & Performance (Semaines 19-22)

**Livrables** :

- Application optimisée (Lighthouse > 90)
- Bundle sizes réduits
- PWA fonctionnelle
- Monitoring RUM

**Responsable** : Frontend Team | **Durée** : 4 semaines

---

### Workstream 4 : Migration & Intégration Legacy

#### WS4.1 - API Gateway & Routing (Semaines 7-10)

**Livrables** :

- API Gateway configuré
- Routage hybride legacy/microservices
- Feature flags opérationnels

**Responsable** : DevOps + Backend Lead | **Durée** : 4 semaines

---

#### WS4.2 - Synchronisation Données Legacy (Semaines 11-14)

**Livrables** :

- Processus synchronisation opérationnel
- Migration données historiques
- Synchronisation temps réel
- Monitoring cohérence données

**Responsable** : Backend + DevOps Teams | **Durée** : 4 semaines

---

#### WS4.3 - Tests de Migration (Semaines 15-18)

**Livrables** :

- Plan tests de migration exécuté
- Rapports performance comparatifs
- Validation business
- Recommandations migration complète

**Responsable** : QA + Engineering Manager | **Durée** : 4 semaines

---

### Workstream 5 : Documentation & Formation

#### WS5.1 - Documentation Technique (Continu, S1-S24)

**Livrables** :

- Documentation architecture complète
- ADRs pour décisions majeures
- Documentation composants
- Runbooks

**Responsable** : Architecture Lead + All Teams | **Durée** : Continu

---

#### WS5.2 - Developer Guides (Semaines 1-8)

**Livrables** :

- Coding Standards
- API Design Guidelines
- Testing Strategy
- Templates et checklists

**Responsable** : Architecture Lead + Tech Leads | **Durée** : 8 semaines

---

#### WS5.3 - Formation Équipes (Semaines 10-16)

**Livrables** :

- Sessions formation complétées
- Matériel formation
- Évaluation compétences

**Responsable** : Architecture Lead + Engineering Manager | **Durée** : 7 semaines

---

#### WS5.4 - Documentation Utilisateur (Semaines 18-22)

**Livrables** :

- User guides
- Vidéos tutorielles
- Runbooks opérationnels
- Status page

**Responsable** : Product + DevOps Teams | **Durée** : 5 semaines

---

### Workstream 6 : Sécurité & Conformité

#### WS6.1 - Security Architecture (Semaines 1-12) - **CRITIQUE**

**Livrables** :

- Security architecture documentée
- Threat model
- Authentication/Authorization implémentés
- Chiffrement bout en bout
- Rapport security testing

**Responsable** : DevOps + Backend + Security Consultant | **Durée** : 12 semaines

---

#### WS6.2 - GDPR Compliance (Semaines 8-14)

**Livrables** :

- Architecture conforme GDPR
- Fonctionnalités GDPR (accès, oubli, portabilité)
- Privacy policies
- Rapport audit GDPR

**Responsable** : Legal + DevOps + Backend Teams | **Durée** : 7 semaines

---

### Workstream 7 : Qualité & Testing

#### WS7.1 - Testing Strategy (Semaines 1-6)

**Livrables** :

- Stratégie test documentée
- Infrastructure tests opérationnelle
- Tests dans CI/CD
- Code coverage reporting

**Responsable** : QA Lead + Engineering Manager | **Durée** : 6 semaines

---

#### WS7.2 - Test Development (Semaines 4-22, continu)

**Livrables** :

- Test suite complète
- Coverage ≥ 80%
- Tests e2e pour journeys critiques
- Rapports tests automatiques

**Responsable** : QA + Dev Teams | **Durée** : 19 semaines

---

#### WS7.3 - Performance Testing (Semaines 16-20)

**Livrables** :

- Rapports performance testing
- Optimisations validées
- Confirmation 5,000 users
- Recommandations futures

**Responsable** : QA + DevOps + Backend Teams | **Durée** : 5 semaines

---

### Priorisation

**Priorité 1 (Critical Path - P1)** :

- WS1.1 : Infrastructure AWS
- WS1.2 : CI/CD Pipelines
- WS2.1 : Geolocation Search Service
- WS3.1 : Architecture Frontend
- WS6.1 : Security Architecture

**Priorité 2 (Important - P2)** :

- WS1.3 : Monitoring
- WS2.2 : Order Management
- WS3.2 : Composants UI
- WS4.1 : API Gateway
- WS7.1 : Testing Strategy

**Priorité 3 (Standard - P3)** :

- WS3.3, WS3.4 : Intégrations
- WS4.2 : Sync Legacy
- WS5 : Documentation
- WS7.2 : Test Development

**Priorité 4 (Nice to have - P4)** :

- WS3.5 : Optimisation
- WS4.3 : Tests Migration
- WS5.3 : Formation
- WS7.3 : Performance Testing

---

## Plan de communication

### Événements de communication réguliers

| Événement                | Canaux             | Formats             | Contenu                          | Rythme                  | Participants                   |
| ------------------------ | ------------------ | ------------------- | -------------------------------- | ----------------------- | ------------------------------ |
| **Daily Standup**        | Slack + Visio      | Synchrone (15 min)  | Done, Todo, Blocages             | Quotidien (9h30)        | Dev Teams + EM                 |
| **Architecture Review**  | Confluence + Visio | Synchrone (1h)      | ADRs, Décisions, Problèmes       | Hebdo (Mer 14h)         | Arch Lead + Tech Leads + CIO   |
| **Sprint Review**        | Jira + Visio       | Synchrone (1.5h)    | Démo, Feedback                   | Bi-hebdo (fin sprint)   | Teams + Stakeholders           |
| **Sprint Retrospective** | Miro + Visio       | Synchrone (1h)      | What went well/wrong             | Bi-hebdo (après review) | Dev Teams + EM                 |
| **Sprint Planning**      | Jira + Visio       | Synchrone (2h)      | Priorisation, Estimation         | Bi-hebdo (début sprint) | Dev Teams + PO + EM            |
| **Steering Committee**   | Google Meet        | Synchrone (1h)      | Avancement, Budget, Risques      | Mensuel (1er Mar)       | CEO, CIO, CPO, CFO + Arch + EM |
| **Technical Sync**       | Slack + Visio      | Sync/Async (30 min) | Sync technique inter-équipes     | Hebdo (Lun 10h)         | Tech Leads + Arch Lead         |
| **Status Report**        | Email + Confluence | Asynchrone          | Résumé avancement, KPIs, Risques | Hebdo (Ven 17h)         | EM → All stakeholders          |

### Canaux de communication

| Canal                    | Utilisation                       | Audience                      | Conventions                         |
| ------------------------ | --------------------------------- | ----------------------------- | ----------------------------------- |
| **#foosus-architecture** | Discussions architecturales, ADRs | Arch Lead, Tech Leads, CIO    | Threads par sujet                   |
| **#foosus-dev-frontend** | Communication équipe frontend     | Frontend Team                 | Questions tech, coordination        |
| **#foosus-dev-backend**  | Communication équipe backend      | Backend Team                  | Questions tech, coordination        |
| **#foosus-devops**       | Communication DevOps              | DevOps Team                   | Incidents, déploiements, alertes    |
| **#foosus-general**      | Communication générale            | All teams + stakeholders      | Annonces, célébrations              |
| **#foosus-incidents**    | Gestion incidents                 | DevOps + On-Call + EM         | Alertes, coordination, post-mortems |
| **GitHub PRs**           | Revues de code                    | Développeurs                  | ≥1 approbation, CI/CD ok            |
| **Confluence**           | Documentation                     | All teams                     | Architecture, runbooks, ADRs        |
| **Jira**                 | Suivi tâches                      | Dev Teams + Product + Manager | Stories, estimation, statuts        |

### Escalation path

**Niveau 1 - Équipe** : Résolution interne (< 4h)  
**Niveau 2 - Engineering Manager** : Si blocage > 4h (< 24h)  
**Niveau 3 - CIO + Architecture Lead** : Décision architecturale majeure (< 48h)  
**Niveau 4 - Steering Committee** : Impact business critique (< 72h)

---

## Risques et facteurs de réduction

### Structure de gouvernance

#### Comité de Pilotage (Steering Committee)

**Membres** : Ash Callum (CEO), Natasha Jarson (CIO), Daniel Anthony (CPO), Jo Kumar (CFO)  
**Fréquence** : Mensuel  
**Autorité** : Validation changements scope, arbitrage, budget additionnel, Go/No-Go production

#### Comité d'Architecture

**Membres** : Natasha Jarson (CIO), Architecture Lead, Pete Parker (EM), Tech Leads  
**Fréquence** : Hebdomadaire  
**Autorité** : Validation ADRs, approbation dérogations, conformité architecturale

#### Équipe de Livraison

**Membres** : Pete Parker (EM), Frontend/Backend/DevOps Teams, QA  
**Fréquence** : Daily standups, sprint ceremonies  
**Autorité** : Décisions implémentation, priorisation interne sprint

---

### Analyse des risques

| ID      | Risque                             | Gravité      | Proba       | Facteur de réduction                                                             | Propriétaire                       |
| ------- | ---------------------------------- | ------------ | ----------- | -------------------------------------------------------------------------------- | ---------------------------------- |
| **R1**  | Dépassement budget ($50k)          | **Haute**    | Moyenne     | Monitoring AWS quotidien, alertes 80/90/100%, optimisations continues            | Jo Kumar (CFO) + DevOps            |
| **R2**  | Retard livraison (> 6 mois)        | **Haute**    | Moyenne     | Planning conservateur, MVP à M3, priorisation stricte, suivi vélocité            | Pete Parker (EM)                   |
| **R3**  | Complexité technique sous-estimée  | **Haute**    | Haute       | POCs, formation équipes, support Arch Lead continu, code reviews                 | Architecture Lead                  |
| **R4**  | Problèmes performance              | **Haute**    | Moyenne     | Load testing précoce, optimisation continue, monitoring temps réel               | Backend + DevOps Leads             |
| **R5**  | Vulnérabilités sécurité            | **Critique** | Faible      | Security by design, SAST/DAST automatisés, penetration testing                   | DevOps + Security Consultant       |
| **R6**  | Non-conformité GDPR                | **Critique** | Faible      | Audit GDPR dès design, data residency France, revue légale                       | Legal + DevOps                     |
| **R7**  | Perte de données migration         | **Critique** | Faible      | Migration incrémentale, sync bidirectionnelle, backups quotidiens, rollback plan | Backend + DevOps Leads             |
| **R8**  | Dépendance membre clé              | **Moyenne**  | Moyenne     | Documentation exhaustive, pair programming, partage connaissance                 | Pete Parker (EM)                   |
| **R9**  | Résistance changement équipes      | **Moyenne**  | Moyenne     | Formation proactive, support Arch Lead, implication décisions, quick wins        | EM + Arch Lead                     |
| **R10** | Compatibilité legacy/microservices | **Moyenne**  | Haute       | API Gateway découplage, contract testing, feature flags, monitoring              | Backend Lead                       |
| **R11** | Turnover équipe                    | **Moyenne**  | Faible      | Documentation, knowledge sharing, environnement motivant, onboarding             | Pete Parker + HR                   |
| **R12** | Indisponibilité AWS                | **Haute**    | Très faible | Multi-AZ, monitoring, status page, plan communication crise                      | DevOps Lead                        |
| **R13** | Scope creep                        | **Moyenne**  | Haute       | Scope défini clairement, processus changement formel, priorisation MoSCoW        | Daniel Anthony (CPO) + Pete Parker |
| **R14** | Complexité sync legacy             | **Moyenne**  | Moyenne     | POC synchronisation early, tests cohérence, logs détaillés                       | Backend Lead                       |
| **R15** | Dette technique                    | **Moyenne**  | Moyenne     | Code reviews (2 approbations), SonarQube CI/CD, refactoring 20% temps            | Tech Leads                         |

### Top 5 risques prioritaires

1. **R3** - Complexité technique (Haute prob, Haute grav) → Formation, POCs, support renforcé
2. **R1** - Dépassement budget (Moy prob, Haute grav) → Monitoring quotidien, alertes
3. **R10** - Compatibilité legacy (Haute prob, Moy grav) → Contract testing, API Gateway
4. **R2** - Retard livraison (Moy prob, Haute grav) → Suivi vélocité, escalation rapide
5. **R5** - Vulnérabilités (Faible prob, Grav critique) → Security by design, scans auto

---

## Hypothèses

| ID      | Hypothèse                                             | Impact si fausse                                  | Propriétaire            | Statut           |
| ------- | ----------------------------------------------------- | ------------------------------------------------- | ----------------------- | ---------------- |
| **H1**  | Équipes (3 pers/équipe) ont capacité et disponibilité | Retards, recrutement externe, surcharge           | Pete Parker             | ✅ Validé        |
| **H2**  | Compétences microservices/AWS suffisantes             | Qualité compromise, retards, consultants          | Pete Parker + Arch Lead | ⚠️ À risque      |
| **H3**  | Budget $50k couvre AWS, outils, formations            | Dépassement, arbitrages scope/qualité             | Jo Kumar                | ✅ Validé        |
| **H4**  | Legacy peut coexister avec microservices              | Migration complexe, dev additionnels legacy       | Backend Lead            | 🔄 En validation |
| **H5**  | Données legacy de qualité suffisante                  | Efforts data cleansing importants, retards        | Backend Lead            | 🔄 En validation |
| **H6**  | AWS services disponibles région France                | Nécessité autre région, compliance issues         | DevOps Lead             | ✅ Validé        |
| **H7**  | Environnements dev/staging sans délai                 | Retard démarrage, dev ralenti                     | DevOps Lead             | ✅ Validé        |
| **H8**  | Outils (GitHub, Jira, etc.) disponibles               | Retards admin, coûts licences                     | Pete Parker             | ✅ Validé        |
| **H9**  | Legal team support GDPR dans délais                   | Retards validation, risques non-conformité        | Natasha Jarson          | ⚠️ À risque      |
| **H10** | Utilisateurs prêts à adopter nouvelles features       | Faible adoption, ROI compromise                   | Daniel Anthony          | 🔄 En validation |
| **H11** | Legacy stable durant migration                        | Efforts sync augmentés, complexité                | Backend Lead            | ✅ Validé        |
| **H12** | PostGIS performance requise (< 200ms)                 | Optimisations importantes, solutions alternatives | Backend Lead            | 🔄 En validation |
| **H13** | Pas de changements réglementaires majeurs             | Efforts conformité additionnels, retards          | Legal Team              | ✅ Validé        |
| **H14** | Dépendances externes stables                          | Efforts migration, bugs, retards                  | DevOps Lead             | ⚠️ À risque      |
| **H15** | Trafic croît progressivement vers 5k                  | Scaling rapide urgent, risques performance        | Daniel Anthony          | 🔄 En validation |

### Actions sur hypothèses à risque

**H2 - Compétences** : Formation microservices AWS (S1-2), support Arch Lead quotidien, POCs  
**H9 - Support Legal** : Kickoff meeting immédiat, clarifier disponibilités, backup consultant  
**H14 - Dépendances** : Lock versions critiques, monitoring breaking changes, tests auto

---

## Critères d'acceptation et procédures

### Métriques et KPIs de l'État Cible

**Métriques techniques**

| Métrique                     | Cible          | Technique de mesure | Justification                    |
| ---------------------------- | -------------- | ------------------- | -------------------------------- |
| **Disponibilité service**    | ≥ 99.9%        | CloudWatch Uptime   | SLA, satisfaction utilisateurs   |
| **Latence p95 Geolocation**  | < 200ms        | CloudWatch Metrics  | UX fluide, compétitivité         |
| **Latence p95 Orders**       | < 500ms        | CloudWatch Metrics  | Acceptabilité CRUD               |
| **Users simultanés**         | ≥ 5,000        | Load testing (K6)   | Capacité business requise        |
| **Temps chargement FCP**     | < 1.5s         | Lighthouse CI       | Engagement, taux rebond          |
| **Time to Interactive**      | < 3.5s         | Lighthouse CI       | UX, utilisabilité                |
| **Taux erreur API**          | < 0.1%         | CloudWatch Logs     | Fiabilité système                |
| **Coverage tests critique**  | ≥ 95%          | Jest + SonarQube    | Fiabilité code business          |
| **Coverage tests global**    | ≥ 80%          | Jest + SonarQube    | Qualité globale                  |
| **Vulnérabilités critiques** | 0              | Snyk + OWASP        | Sécurité, conformité             |
| **Cache hit rate**           | > 85%          | ElastiCache Metrics | Performance, réduction charge DB |
| **MTTD**                     | < 5 min        | Incident tracking   | Réactivité incidents             |
| **MTTR**                     | < 30 min       | Incident tracking   | Résilience système               |
| **Deployment frequency**     | ≥ 1/jour (dev) | GitHub Actions      | Agilité, continuous delivery     |

**Métriques business**

| Métrique                       | Baseline | Cible    | Technique de mesure       | Justification       |
| ------------------------------ | -------- | -------- | ------------------------- | ------------------- |
| **Time-to-market features**    | 2 sem    | < 1 sem  | Jira (story → prod)       | Agilité business    |
| **Coût par transaction**       | $0.15    | < $0.10  | AWS Cost / transactions   | Rentabilité         |
| **Coût infra mensuel**         | -        | < $8,333 | AWS Cost Explorer         | Budget annuel       |
| **Vélocité équipe**            | 35 pts   | ≥ 45 pts | Jira                      | Productivité accrue |
| **Incidents P0-P1/mois**       | 4-6      | < 2      | Incident tracking         | Stabilité, qualité  |
| **Temps résolution incidents** | 4h       | < 2h     | Incident tracking         | Efficacité ops      |
| **Taux bugs production**       | 8/mois   | < 3/mois | Bug tracking              | Qualité code        |
| **Adoption features Phase 1**  | 0%       | 100%     | Analytics + feature flags | Succès migration    |
| **NPS**                        | 45       | ≥ 55     | Surveys in-app            | Amélioration UX     |
| **Taux conversion recherche**  | 12%      | ≥ 15%    | Analytics funnel          | Efficacité business |
| **Users actifs mensuels**      | 15k      | ≥ 25k    | Analytics                 | Croissance business |

---

### Procédure d'acceptation

#### Phase 1a - Fondations (M1-M2)

**Critères** :

1. Infrastructure AWS dans 3 environnements (Terraform)
2. CI/CD opérationnelles (build, test, deploy)
3. Geolocation Service en staging et prod (latence < 200ms, coverage ≥ 80%)
4. Documentation architecture complète (ADRs, diagrams)

**Processus** :

1. Démo technique (1h) : Équipes → Comité Architecture
2. Revue documentation (30 min) : Architecture Lead valide
3. Tests d'acceptation (2h) : QA exécute test suite
4. Revue métriques (30 min) : Validation cibles atteintes
5. Signature : CIO + Architecture Lead

**Délai acceptation** : 5 jours ouvrés

---

#### Phase 1b - Extension (M3-M4)

**Critères** :

1. Order Management Service en prod (latence < 500ms, coverage ≥ 80%)
2. Frontend React intégré avec 2 microservices en prod
3. API Gateway avec routage complet
4. Load testing validé : 5,000 users simultanés
5. Monitoring opérationnel pour tous composants

**Processus** :

1. Démo end-to-end (1.5h) : Flow complet recherche → commande
2. Revue technique (1h) : Code review composants critiques
3. Validation performance (2h) : Load tests
4. Validation business (1h) : Product Owner valide fonctionnalités
5. Tests rollback (1h) : Validation retour legacy fonctionne
6. Signature : CIO + CPO + Architecture Lead

**Délai acceptation** : 7 jours ouvrés

---

#### Phase 1c - Optimisation (M5-M6)

**Critères** :

1. Optimisations performance appliquées et validées
2. Security audit complété, vulnérabilités critiques résolues
3. Conformité GDPR validée (audit interne/externe)
4. Documentation finale complète (technique, utilisateur, opérationnelle)
5. Formation équipes avec évaluations positives
6. Runbooks testés sur incidents simulés
7. Migration 100% trafic vers microservices
8. Rapport Phase 1 + recommandations Phase 2

**Processus** :

1. Revue sécurité (2h) : Résultats audit + remédiations
2. Validation GDPR (1h) : Conformité avec Legal team
3. Démo opérationnelle (1h) : Monitoring, alerting, runbooks
4. Revue documentation (1h) : Complétude par stakeholders
5. Validation business (1h) : Métriques (NPS, conversion, adoption)
6. Présentation Steering (2h) : Présentation complète + Phase 2
7. Signature : Tous membres Steering Committee

**Délai acceptation** : 10 jours ouvrés

---

#### Critères de non-acceptation (Blockers)

Un livrable sera **refusé** si :

1. **Sécurité** : Vulnérabilités critiques (CVSS ≥ 9.0) non résolues
2. **Performance** : Métriques non atteintes (latence, scalabilité)
3. **Tests** : Coverage < 80% ou tests critiques échouent
4. **Documentation** : Documentation technique incomplète
5. **Conformité** : Non-conformité GDPR identifiée
6. **Bugs** : Bugs P0 ou > 3 bugs P1 non résolus
7. **Standards** : Non-respect coding standards ou principes architecture

En cas de non-acceptation : **5 jours ouvrés** pour corriger avant nouvelle revue.

---

### Procédure de réception définitive (End of Phase 1)

**Conditions** :

1. Toutes phases (1a, 1b, 1c) acceptées
2. Système en prod stable ≥ 4 semaines
3. SLA 99.9% atteint sur 4 dernières semaines
4. Métriques business atteintes ou en progression claire
5. Aucun incident P0 dans 2 dernières semaines
6. Budget respecté (≤ $50k) ou écarts justifiés
7. Formation équipes complétée
8. Documentation validée par tous stakeholders

**Processus** :

1. Rapport de clôture (EM) : Bilan complet projet
2. Présentation Steering (2h) : Résultats, learnings, recommandations Phase 2
3. Revue financière (30 min) : CFO valide coûts finaux
4. Décision Go/No-Go Phase 2
5. Célébration d'équipe

**Date cible** : 30 avril 2026

---

## Procédures de changement de périmètre

### Principes

- Scope Phase 1 fixe par défaut
- Impact analysis obligatoire (budget, planning, qualité, risques)
- Priorisation stricte (MoSCoW : Must/Should/Could/Won't have)
- Traçabilité complète (Jira + Confluence)

---

### Processus

**Étape 1 : Soumission** (Formulaire Jira)

- Qui : N'importe quel stakeholder
- Infos : Titre, justification, description, priorité perçue, urgence

**Étape 2 : Évaluation technique** (5 jours ouvrés)

- Responsables : Arch Lead + EM + Tech Leads
- Livrable : Rapport d'impact technique (effort, dépendances, risques)

**Étape 3 : Évaluation business** (3 jours ouvrés)

- Responsables : CPO + CIO + CFO
- Livrable : Business case (valeur, coût/bénéfice, impact planning/budget)

**Étape 4 : Décision**

- **Niveau 1** (Comité Architecture) : Changements mineurs (< 5 story points, pas d'impact budget/planning) → 2 jours
- **Niveau 2** (Steering) : Changements majeurs (≥ 5 pts, impact budget/planning) → 5 jours

**Options** :

- Approuvé Phase 1 : Ajouté au backlog, re-priorisation
- Approuvé Phase 2 : Backlog Phase 2, pas d'impact Phase 1
- Rejeté : Ne sera pas implémenté, justification fournie
- Différé : Décision repoussée (plus d'infos nécessaires)

**Étape 5 : Communication** (immédiate)

- EM notifie demandeur
- MAJ backlog Jira
- MAJ roadmap si nécessaire
- Communication équipes
- Update Change Log (Confluence)

---

### Critères d'évaluation

| Critère                    | Poids | Questions clés                                                   |
| -------------------------- | ----- | ---------------------------------------------------------------- |
| **Valeur business**        | 30%   | Impact revenus/coûts ? Satisfaction user ? Avantage compétitif ? |
| **Urgence**                | 25%   | Bloquant business ? Deadline externe ? Peut attendre Phase 2 ?   |
| **Effort**                 | 20%   | Story points ? Jours-personnes ? Équipes impactées ?             |
| **Risque**                 | 15%   | Risques techniques ? Impact stabilité ? Sécurité ?               |
| **Alignement stratégique** | 10%   | Aligné vision ? Cohérent principes ? Impact dette technique ?    |

---

## Calendrier

### Vue d'ensemble - 6 mois (26 semaines)

**Début** : 1er novembre 2025  
**Fin** : 30 avril 2026

### Milestones critiques (Critical Path)

| Milestone | Date             | Description                      | Critère succès                          |
| --------- | ---------------- | -------------------------------- | --------------------------------------- |
| **M1**    | 2025-11-08 (S1)  | Environnements dev opérationnels | Développeurs peuvent coder              |
| **M2**    | 2025-11-29 (S4)  | Infrastructure AWS complète      | 3 environnements provisionnés et testés |
| **M3**    | 2025-12-27 (S8)  | CI/CD opérationnel               | Déploiement automatique fonctionnel     |
| **M4**    | 2026-01-17 (S10) | Geolocation Service staging      | Service déployé, tests passent          |
| **M5**    | 2026-01-31 (S12) | **Geolocation Service PROD** ✅  | En prod, métriques OK                   |
| **M6**    | 2026-02-21 (S16) | Order Management staging         | Service déployé, intégration OK         |
| **M7**    | 2026-03-07 (S18) | **Order Management PROD** ✅     | En prod, métriques OK                   |
| **M8**    | 2026-03-21 (S20) | **Application complète PROD** ✅ | Frontend + 2 services opérationnels     |
| **M9**    | 2026-04-11 (S24) | 75% trafic microservices         | Migration progressive validée           |
| **M10**   | 2026-04-18 (S25) | **100% trafic microservices** ✅ | Migration complète                      |
| **M11**   | 2026-04-30 (S26) | **FIN DE PHASE 1** ✅            | Tous critères acceptation validés       |

---

### Timeline par mois

**Mois 1 (Nov 2025)** - Setup & Fondations

- S1 : Kickoff, env dev ✅ **M1**
- S4 : Infrastructure AWS complète ✅ **M2**

**Mois 2 (Déc 2025)** - Premier microservice & CI/CD

- S8 : CI/CD opérationnel ✅ **M3**

**Mois 3 (Jan 2026)** - Déploiement Geolocation

- S10 : Geolocation staging ✅ **M4**
- S12 : **Geolocation PROD** ✅ **M5** 🎉

**Mois 4 (Fév 2026)** - Order Management

- S16 : Order Management staging ✅ **M6**

**Mois 5 (Mars 2026)** - Production complète

- S18 : **Order Management PROD** ✅ **M7** 🎉
- S20 : **Application complète** ✅ **M8** 🎉

**Mois 6 (Avr 2026)** - Migration & Clôture

- S24 : 75% trafic microservices ✅ **M9**
- S25 : **100% trafic microservices** ✅ **M10** 🎉
- S26 : **FIN PHASE 1** ✅ **M11** 🎉

---

## Phases de livrables définies

Voir section "Livrables architecturaux" ci-dessus pour détails complets.

**Résumé** :

- **Phase 1a (M1-M2)** : Fondations - Infrastructure + Geolocation Service
- **Phase 1b (M3-M4)** : Extension - Order Service + Frontend intégré
- **Phase 1c (M5-M6)** : Stabilisation - Optimisation + Sécurité + Migration 100%

---

## Personnes approuvant ce plan

| Rôle                    | Nom            | Domaine                  | Date signature     | Statut        |
| ----------------------- | -------------- | ------------------------ | ------------------ | ------------- |
| **CEO**                 | Ash Callum     | Vision business, ROI     | **\*\***\_**\*\*** | ⏳ En attente |
| **CIO**                 | Natasha Jarson | Vision technique, budget | **\*\***\_**\*\*** | ⏳ En attente |
| **CPO**                 | Daniel Anthony | Produit, adoption        | **\*\***\_**\*\*** | ⏳ En attente |
| **CFO**                 | Jo Kumar       | Budget, coûts, ROI       | **\*\***\_**\*\*** | ⏳ En attente |
| **Engineering Manager** | Pete Parker    | Faisabilité, planning    | **\*\***\_**\*\*** | ⏳ En attente |
| **Architecture Lead**   | Mathieu Baro   | Architecture, standards  | **\*\***\_**\*\*** | ⏳ En attente |

---

### Déclaration d'engagement

En signant, les parties s'engagent à :

1. **Respecter les termes** de ce contrat
2. **Fournir les ressources** (budget, temps, personnel)
3. **Participer activement** à la gouvernance
4. **Supporter les équipes**
5. **Communiquer de manière transparente**
6. **Escalader rapidement** les blocages
7. **Valider formellement** les livrables

---

### Procédure de signature

1. **Revue** (5 jours) : Commentaires des signataires
2. **Incorporation** (3 jours) : Arch Lead intègre feedbacks
3. **Revue finale** (2 jours) : Validation changements
4. **Signature électronique** : Via Confluence
5. **Publication** : Document publié et communiqué

**Date cible signature** : 15 novembre 2025

---

### Modifications du contrat

Toute modification nécessite :

1. Proposition par signataire
2. Impact analysis (Arch Lead + EM)
3. Revue Steering Committee
4. Approbation formelle (tous signataires)
5. Versioning (v1.1, v1.2, etc.)
6. Communication à toutes équipes

---

## Annexes

### Annexe A : Glossaire

| Terme             | Définition                                          |
| ----------------- | --------------------------------------------------- |
| **ADR**           | Architecture Decision Record                        |
| **API Gateway**   | Point d'entrée unique pour requêtes microservices   |
| **Blue-Green**    | Stratégie déploiement avec 2 env pour zéro-downtime |
| **CQRS**          | Command Query Responsibility Segregation            |
| **DDD**           | Domain-Driven Design                                |
| **ECS Fargate**   | Service AWS orchestration conteneurs serverless     |
| **EventBridge**   | Service AWS bus d'événements                        |
| **GDPR**          | General Data Protection Regulation                  |
| **IaC**           | Infrastructure as Code                              |
| **Microservices** | Style architectural services indépendants           |
| **MTTR**          | Mean Time To Recovery                               |
| **MTTD**          | Mean Time To Detect                                 |
| **NPS**           | Net Promoter Score                                  |
| **PostGIS**       | Extension PostgreSQL données géospatiales           |
| **RDS**           | Relational Database Service AWS                     |
| **SLA**           | Service Level Agreement                             |
| **Strangler Fig** | Pattern migration progressive                       |
| **TDD**           | Test-Driven Development                             |

---

### Annexe B : Références

**Documents projet** :

- Statement of Architecture Work (SAW-FOOSUS-2025-001)
- Architecture Requirements Specification (ARS-FOOSUS-2025-001)
- Architecture Contract - Business (ACB-FOOSUS-2025-001)

**Standards** :

- TOGAF 9.2
- AWS Well-Architected Framework
- The Twelve-Factor App
- C4 Model for Software Architecture

---

### Annexe C : Contacts

| Rôle                | Email                    | Disponibilité |
| ------------------- | ------------------------ | ------------- |
| CEO                 | ash.callum@foosus.fr     | Sur RDV       |
| CIO                 | natasha.jarson@foosus.fr | 9h-18h        |
| CPO                 | daniel.anthony@foosus.fr | 9h-18h        |
| CFO                 | jo.kumar@foosus.fr       | 9h-17h        |
| Engineering Manager | pete.parker@foosus.fr    | 9h-19h        |
| Architecture Lead   | mathieu.baro@foosus.fr   | 8h-19h        |

**Urgences (P0)** : Slack #foosus-incidents + PagerDuty

---

### Annexe D : Outils et accès

| Outil           | URL                       | Usage             |
| --------------- | ------------------------- | ----------------- |
| **GitHub**      | github.com/foosus         | Code, PRs, CI/CD  |
| **Jira**        | foosus.atlassian.net      | Backlog, tracking |
| **Confluence**  | foosus.atlassian.net/wiki | Documentation     |
| **AWS Console** | console.aws.amazon.com    | Infrastructure    |
| **Slack**       | foosus.slack.com          | Communication     |
| **SonarQube**   | sonar.foosus.internal     | Code quality      |

---

## Document Control

**Historique** :

| Version | Date       | Auteur                     | Changements      |
| ------- | ---------- | -------------------------- | ---------------- |
| 1.0     | 2025-11-05 | Architecture Function Lead | Version initiale |

**Prochaine revue** : 2026-02-05 (3 mois après signature)

---

**FIN DU DOCUMENT**

---

_Document confidentiel destiné uniquement aux parties prenantes du projet Foosus._  
_Toute reproduction ou distribution non autorisée est interdite._
