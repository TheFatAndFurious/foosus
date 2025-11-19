---
title: "Contrat d'Architecture avec le Business"
subtitle: "Plateforme Foosus Géoconsciente"
project: "Plateforme Foosus Géoconsciente - Phase 1"
client: "Foosus"
author: "Mathieu Baro"
version: "0.1 - DRAFT"
date: "Octobre 2025"
status: "Brouillon pour validation"
type: "Contrat d'Architecture Business"
---

# Contrat d'Architecture avec le Business

**Plateforme Foosus Géoconsciente**

---

## Informations du Document

| Champ               | Valeur                                    |
| ------------------- | ----------------------------------------- |
| **Projet**          | Plateforme Foosus Géoconsciente - Phase 1 |
| **Client**          | Foosus                                    |
| **Préparé par**     | Mathieu Baro                              |
| **Version**         | 0.1 - DRAFT                               |
| **Date**            | Octobre 2025                              |
| **Statut**          | Brouillon pour validation                 |
| **Type de contrat** | Contrat d'Architecture Business           |

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

L'implémentation réussie de ces accords sera livrée grâce à une gouvernance de l'architecture efficace. En implémentant une approche dirigée du management de contrats, les éléments suivants seront garantis :

- **Un système de contrôle continu** pour vérifier l'intégrité, les changements, les prises de décisions, et l'audit de toutes les activités relatives à l'architecture au sein de l'organisation.

- **L'adhésion aux principes, standards et conditions requises** des architectures existantes ou en développement.

- **L'identification des risques** dans tous les aspects du développement et de l'implémentation de l'architecture, y compris le développement interne en fonction des standards acceptés, des politiques, des technologies et des produits.

- **Un ensemble de processus et de pratiques** qui garantissent la transparence, la responsabilité et la discipline au regard du développement et de l'utilisation de tous les artefacts architecturaux.

- **Un accord formel** sur l'organe de gouvernance responsable du contrat, son degré d'autorité, et le périmètre de l'architecture sous la gouvernance de cet organe.

Ceci est une **déclaration d'intention signée** sur la conception et le développement de l'architecture d'entreprise de Foosus, entre l'architecte logiciel et les parties prenantes Business (C-level).

---

## 2. Introduction et contexte

### 2.1 Contexte du projet

Foosus fait face à un **déclin critique des inscriptions utilisateurs** dû à l'instabilité de sa plateforme historique. La dette technique accumulée a généré plus de **25 incidents P1 par mois** et un délai moyen de mise en production de **3,5 semaines**, empêchant toute innovation rapide.

En réponse, Foosus investit dans une nouvelle plateforme géoconsciente basée sur une **architecture microservices cloud-native (AWS)**, permettant de connecter consommateurs et producteurs locaux via la géolocalisation.

**Enjeux business critiques :**

- Inscriptions utilisateurs en déclin (métrique clé investisseurs)
- Adhésion producteurs stagnante (1,4/mois, objectif : 4/mois)
- Image de marque dégradée par les pannes visibles
- Impossibilité de supporter les pics de charge marketing
- Absence d'agilité pour expérimenter et innover

### 2.2 Sponsors et parties prenantes

**Sponsor exécutif :**

- **Ash Callum, CEO** - Sponsor principal du projet

**Parties prenantes business clés :**

- **Natasha Jarson, CIO** - Responsable architecture et infrastructure
- **Daniel Anthony, CPO** - Responsable produit et expérience utilisateur
- **Jo Kumar, CFO** - Responsable budget et viabilité économique
- **Jack Harkness, Directeur Opérations** - Responsable support et qualité service

**Fonction Architecture :**

- **Mathieu Baro** - Garant de l'architecture d'entreprise

### 2.3 Autorisation du projet

| Paramètre                     | Valeur                                             |
| ----------------------------- | -------------------------------------------------- |
| **Budget Phase 1**            | 50 000 USD (45 190 €)                              |
| **Durée Phase 1**             | 6 mois (Octobre 2025 - Mars 2026)                  |
| **Budget opérationnel cloud** | 2 000 USD/mois maximum                             |
| **Équipes mobilisées**        | 3 pôles de 3 personnes (Frontend, Backend, DevOps) |

---

## 3. La nature de l'accord

### 3.1 Type de contrat

Ce contrat est un **ACCORD DE PARTENARIAT** entre :

**PARTIE A :** La Fonction Architecture (représentée par Mathieu Baro)

**PARTIE B :** Les Sponsors Business (représentés par le Comité de Pilotage : Ash Callum CEO, Natasha Jarson CIO, Daniel Anthony CPO, Jo Kumar CFO)

**Type :** Contrat d'Architecture Business (Business Architecture Contract)

**Durée :** Phase 1 de 6 mois, renouvelable pour les phases suivantes

### 3.2 Engagements mutuels

**La Fonction Architecture s'engage à :**

- Définir une architecture d'entreprise cible alignée sur les objectifs business
- Livrer un prototype fonctionnel validant la faisabilité technique
- Respecter les contraintes budgétaires (50K USD Phase 1, 2K USD/mois cloud)
- Maintenir une communication transparente (revues hebdomadaires + réunions mensuelles)
- Documenter toutes les décisions architecturales majeures (ADRs)
- Garantir la conformité aux standards de sécurité et réglementaires (RGPD)

**Les Sponsors Business s'engagent à :**

- Fournir les ressources humaines et budgétaires allouées
- Participer activement aux revues d'architecture hebdomadaires
- Prendre les décisions de priorisation dans les délais impartis
- Geler les changements sur la plateforme legacy (maintenance uniquement)
- Valider les jalons critiques (Go/No-Go Cycle 1)
- Accepter une approche itérative avec apprentissages progressifs

### 3.3 Gouvernance du contrat

**Comité de Pilotage Architecture :**

- **Fréquence :** Réunions hebdomadaires (1H)
- **Participants obligatoires :** CIO, CPO, Fonction Architecture
- **Participants optionnels :** CEO, CFO (selon agenda)
- **Objectif :** Validation des décisions architecturales majeures, suivi avancement, gestion des risques

**Processus de décision :**

- **Décisions mineures** (<10K USD impact) : Fonction Architecture autonome
- **Décisions majeures** (>10K USD impact ou changement scope) : Validation Comité de Pilotage
- **Décisions bloquantes :** Escalation CEO sous 48h

**Mécanisme d'arbitrage :**

En cas de désaccord entre Fonction Architecture et Sponsors Business :

1. Discussion au Comité de Pilotage (tentative consensus)
2. Si pas de consensus : Vote (majorité simple)
3. Si blocage : Arbitrage CEO (décision finale)

---

## 4. Objectifs et périmètre

### 4.1 Objectifs business

Les objectifs business de ce travail d'architecture sont les suivants (!controler les objectifs dans les documents) :

| ID  | Objectif Business                                    | Notes / Critères de succès                            |
| --- | ---------------------------------------------------- | ----------------------------------------------------- |
| OB1 | Augmenter les inscriptions utilisateurs              | +10% par rapport à la baseline actuelle               |
| OB2 | Augmenter l'adhésion de producteurs alimentaires     | Passer de 1,4/mois à 4/mois                           |
| OB3 | Réduire le délai moyen de mise en production         | De 3,5 semaines à < 1 semaine                         |
| OB4 | Réduire drastiquement les incidents de production P1 | De >25/mois à <1/mois                                 |
| OB5 | Supporter l'expansion géographique multi-régions     | Architecture scalable pour plusieurs villes/pays      |
| OB6 | Permettre l'innovation et l'expérimentation rapide   | Déploiements sans interruption, A/B testing           |
| OB7 | Améliorer la réputation de la marque Foosus          | Zéro panne visible par les utilisateurs en production |

### 4.2 Périmètre Phase 1 (6 mois)

**Dans le périmètre :**

- ✅ Architecture d'entreprise cible documentée
- ✅ Prototype fonctionnel :
  - Recherche géolocalisée de fournisseurs/produits (MVP)
  - Gestion des commandes simplifiée (panier, confirmation)
  - Authentification utilisateurs (nouveaux + legacy via API Façade)
- ✅ Infrastructure AWS de base (EKS, RDS, DynamoDB, S3, CloudFront)
- ✅ Pipeline CI/CD automatisé
- ✅ Monitoring et observabilité
- ✅ Interfaces web et mobile responsive
- ✅ API Façade Legacy pour lecture données utilisateurs existants
- ✅ Documentation complète (architecture, APIs, runbooks)

**Hors périmètre Phase 1 :**

- ❌ Intégration systèmes de paiement en ligne (Stripe/PayPal) → Phase 2
- ❌ Migration complète des données legacy → Phase 2
- ❌ Décommissionnement plateforme existante → Phase 2/3
- ❌ Système de facturation automatisé → Phase 2
- ❌ Features avancées (recommandations ML, analytics complexes) → Phase 2+

### 4.3 Parties prenantes, préoccupations et visions

| Partie prenante          | Préoccupation                                                     | Vision à créer                                         |
| ------------------------ | ----------------------------------------------------------------- | ------------------------------------------------------ |
| Ash Callum (CEO)         | Taux d'inscription en baisse, viabilité long terme, investisseurs | Vision stratégique : roadmap croissance, business case |
| Natasha Jarson (CIO)     | Dette technique, stabilité, innovation bloquée                    | Architecture technique cible, stratégie migration      |
| Daniel Anthony (CPO)     | Time-to-market, capacité d'expérimentation produit                | Architecture modulaire permettant A/B testing          |
| Jo Kumar (CFO)           | Coûts infrastructure, ROI investissement, viabilité économique    | Analyse coût/bénéfice, optimisation cloud              |
| Jack Harkness (Dir. Ops) | Qualité de service, incidents, support utilisateurs               | Plan réduction incidents, SLAs clairs                  |

---

## 5. Description de l'architecture, principes stratégiques et conditions requises

### 5.1 Description de l'architecture

**Vision de l'état cible :**

Une plateforme cloud-native basée sur une architecture microservices, hébergée sur AWS, permettant de connecter consommateurs et producteurs locaux via la géolocalisation, avec les caractéristiques suivantes :

- **SCALABILITÉ :** Supporter la croissance de 30%/mois des utilisateurs
- **DISPONIBILITÉ :** 99.9% (8.76h downtime/an maximum)
- **PERFORMANCE :** Recherche géolocalisée < 200ms (p95)
- **AGILITÉ :** Déploiements sans interruption, plusieurs fois par semaine
- **OBSERVABILITÉ :** Monitoring temps réel de la santé business et technique
- **RÉSILIENCE :** Isolation des pannes, auto-healing, circuit breakers

**Approche de migration : Strangler Fig Pattern**

Migration progressive sans big-bang :

- Coexistence plateforme legacy (maintenance) + nouvelle plateforme (12-18 mois)
- Routage intelligent via API Gateway (nouveau vs ancien système)
- Migration par capacité business (recherche → commandes → paiements → ...)
- Rollback possible à tout moment (< 5 minutes)

### 5.2 Principes stratégiques

**Principes business :**

1. Soutenir l'innovation et l'agilité du business grâce à l'extensibilité
2. Soutenir la réputation de la marque grâce à la stabilité
3. Maximiser la valeur business, minimiser le time-to-market
4. Prendre des décisions pilotées par les données (metrics-driven)

**Principes architecturaux :**

1. Responsabilité unique : Un microservice = Un domaine métier
2. Couplage faible : Communication uniquement via APIs
3. Idempotence : Toutes les opérations réessayables en toute sécurité
4. Observabilité intégrée : Logs, metrics, traces dès la conception
5. Sécurité by design : Chiffrement, authentification, principe du moindre privilège
6. Fail-fast : Validation stricte, erreurs explicites
7. Database per Service : Isolation des données par microservice

**Principes opérationnels :**

1. Zero-downtime deployments : Pas d'interruption de service
2. Infrastructure as Code : Reproductibilité, versioning
3. Automatisation maximale : CI/CD, tests, monitoring, scaling
4. Documentation as Code : Toujours à jour, versionnée avec le code

### 5.3 Conditions requises pour l'architecture

Référence au document : **"Spécification des Exigences Architecturales v0.1"**

**Résumé des conditions clés :**

**Performance :**

- Latence recherche géolocalisée (p95) : < 200ms
- Latence création commande (p95) : < 300ms
- Débit : 500 req/sec recherche, 100 req/sec commandes
- Charge cible : 5 000 utilisateurs concurrents (scalable à 50 000)

**Disponibilité :**

- SLA : 99.9% (8.76h downtime/an max)
- RTO : < 15 minutes
- RPO : < 1 heure

**Sécurité :**

- Conformité RGPD obligatoire
- Chiffrement en transit (TLS 1.3) et au repos (AWS KMS)
- Authentification JWT, rotation secrets tous les 90 jours
- Scan vulnérabilités automatique (images Docker, dépendances)

**Scalabilité :**

- Croissance supportée : +30% utilisateurs/mois pendant 12 mois
- Volumétrie : 10K fournisseurs, 100K produits, 1K commandes/heure

**Conformité :**

- RGPD : Consentement, portabilité, droit à l'oubli
- Données hébergées en UE (eu-west-3 Paris)
- Audit logs pour tous accès données personnelles

---

---

## 6. Livrables architecturaux

### 6.1 Livrables architecturaux qui satisfont aux conditions requises business

**Développement de l'architecture :**

| ID  | Livrable                                       | Échéance | Responsable                     |
| --- | ---------------------------------------------- | -------- | ------------------------------- |
| L1  | Vision d'Architecture                          | Mois 1   | Fonction Architecture           |
| L2  | Spécification des Exigences Architecturales    | Mois 1   | Fonction Architecture           |
| L3  | Contrats d'Architecture (Business + Dev)       | Mois 1   | Fonction Architecture           |
| L4  | Architecture de haut niveau (diagrammes, ADRs) | Mois 2   | Fonction Architecture           |
| L5  | Spécifications APIs (OpenAPI 3.0)              | Mois 2-4 | Fonction Archi + Équipe Backend |
| L6  | Documentation d'architecture complète          | Mois 6   | Fonction Architecture           |

**Mesures de l'architecture cible :**

| ID  | Métrique                             | Valeur cible | Méthode de mesure |
| --- | ------------------------------------ | ------------ | ----------------- |
| M1  | Couverture tests automatisés         | ≥ 80%        | Coverage reports  |
| M2  | Latence recherche géolocalisée (p95) | < 200ms      | Tests de charge   |
| M3  | Disponibilité prototype (M5-M6)      | ≥ 99.5%      | CloudWatch        |
| M4  | Coût infrastructure mensuel          | < 2 000 USD  | AWS Cost Explorer |
| M5  | Temps build + déploiement            | < 15 min     | Métriques CI/CD   |

**Livraison de l'architecture et métriques business :**

| ID  | Métrique Business (post-déploiement) | Objectif    | Horizon          |
| --- | ------------------------------------ | ----------- | ---------------- |
| MB1 | Inscriptions utilisateurs/jour       | +10%        | 6 mois post-prod |
| MB2 | Adhésion producteurs/mois            | 4           | 6 mois post-prod |
| MB3 | Incidents P1/mois                    | < 5 / < 1   | 3 / 12 mois      |
| MB4 | Délai moyen de mise en production    | < 1 semaine | 6 mois post-prod |
| MB5 | Taux conversion recherche→commande   | +15%        | 6 mois post-prod |

### 6.2 Phases de livraison définies

**Cycle 1 (Mois 1-2) : FONDATIONS & VISION**

- **Objectif :** Établir les fondations architecturales et valider la faisabilité
- **Livrables business :**
  - Vision d'architecture validée
  - POC géolocalisation DynamoDB (latence < 200ms prouvée)
  - Stratégie de migration Strangler Fig documentée
- **Milestone :** Go/No-Go architecture par Comité de Pilotage

**Cycle 2 (Mois 3-4) : PROTOTYPE CORE**

- **Objectif :** Développer le cœur du système (recherche géolocalisée)
- **Livrables business :**
  - Démo fonctionnelle recherche géolocalisée
  - Utilisateurs peuvent chercher fournisseurs par rayon
  - Interface web responsive fonctionnelle
- **Milestone :** Validation UX/UI par CPO + démo investisseurs

**Cycle 3 (Mois 5-6) : COMPLÉTION & COMMANDES**

- **Objectif :** Ajouter les commandes et finaliser le prototype
- **Livrables business :**
  - Parcours complet : recherche → ajout panier → commande → confirmation
  - Notifications email fournisseurs
  - Coexistence legacy/nouveau démontrée (API Façade opérationnelle)
- **Milestone :** Prototype end-to-end présenté au C-level + validation Go Phase 2

---

## 7. Plan de travail commun priorisé

### 7.1 Item de travail 1 : Recherche géolocalisée (P0)

**Activités :**

- Conception service de recherche géospatiale (DynamoDB + geohashing)
- Développement algorithme calcul distance (Haversine)
- Intégration cartographie (AWS Location Service ou Google Maps)
- Interface utilisateur : saisie localisation + affichage résultats
- Tests de performance (latence < 200ms p95)

**Livrables :**

- Search Service opérationnel
- Interface web/mobile responsive pour la recherche
- Documentation API (OpenAPI 3.0)
- Tests automatisés (unitaires + intégration + E2E)

**Critères d'acceptation business :**

- ✅ Utilisateur peut chercher fournisseurs dans un rayon de 1 à 50 km
- ✅ Résultats affichent distance en km (1 décimale)
- ✅ Résultats triés par proximité
- ✅ Latence < 200ms (p95) sous charge de 100 utilisateurs concurrents
- ✅ Fournisseurs affichés sur carte interactive

**Priorité :** P0 (Bloquant)
**Échéance :** Mois 4 (fin Cycle 2)

### 7.2 Item de travail 2 : Gestion des commandes (P0)

**Activités :**

- Conception Order Service avec machine à états (DRAFT → CONFIRMED → ...)
- Développement panier multi-fournisseurs
- Calcul automatique totaux commande
- Notifications email fournisseurs (via SES)
- Tests bout-en-bout parcours complet

**Livrables :**

- Order Service opérationnel
- Interface panier et confirmation commande
- Système de notifications email
- Documentation API (OpenAPI 3.0)
- Tests automatisés

**Critères d'acceptation business :**

- ✅ Utilisateur peut ajouter produits au panier
- ✅ Utilisateur peut modifier panier avant confirmation
- ✅ Confirmation génère numéro commande unique (ORD-YYYYMMDD-XXXXX)
- ✅ Fournisseur reçoit email automatique à la confirmation
- ✅ Utilisateur peut consulter historique de ses commandes

**Priorité :** P0 (Bloquant)
**Échéance :** Mois 6 (fin Cycle 3)

### 7.3 Item de travail 3 : API Façade Legacy (P0)

**Activités :**

- Reverse engineering système legacy (structure DB, APIs existantes)
- Développement API Façade REST moderne
- Tests d'intégration avec legacy
- Load testing (capacité 50+ req/sec)
- Documentation OpenAPI + runbooks troubleshooting

**Livrables :**

- API Façade Legacy déployée et opérationnelle
- Endpoints P0 : `GET /legacy/users/{id}`, `GET /legacy/users/{id}/orders`
- Circuit breaker configuré (timeout 500ms)
- Monitoring dédié (latence, disponibilité)

**Critères d'acceptation business :**

- ✅ Utilisateurs legacy peuvent se connecter sur nouvelle plateforme
- ✅ Historique commandes legacy consultable
- ✅ Latence < 300ms (p95)
- ✅ Disponibilité ≥ 99%
- ✅ Mode dégradé si legacy indisponible (message clair utilisateur)

**Priorité :** P0 (Bloquant)
**Échéance :** Mois 4 (fin Cycle 2)

### 7.4 Item de travail 4 : Infrastructure & CI/CD (P1)

**Activités :**

- Provisioning infrastructure AWS (EKS, RDS, DynamoDB, S3, CloudFront)
- Configuration pipeline CI/CD (GitHub Actions ou GitLab CI)
- Setup monitoring (CloudWatch, X-Ray, Grafana)
- Configuration auto-scaling (HPA Kubernetes)
- Tests de charge et optimisation

**Livrables :**

- Infrastructure AWS opérationnelle (multi-AZ)
- Pipeline CI/CD automatisé (build → test → deploy < 15 min)
- Dashboards monitoring (business + technique)
- Alerting configuré (PagerDuty)
- Documentation infrastructure (Terraform, runbooks)

**Critères d'acceptation business :**

- ✅ Déploiements sans interruption de service (Blue/Green)
- ✅ Rollback possible en < 5 minutes
- ✅ Coût mensuel < 2 000 USD
- ✅ Disponibilité > 99.5% (M5-M6)
- ✅ Auto-scaling fonctionnel (CPU > 70% → +pods)

**Priorité :** P1 (Important)
**Échéance :** Mois 3 (milieu Cycle 2) pour infra, Mois 6 pour optimisation

### 7.5 Item de travail 5 : Authentification & Gestion Utilisateurs (P1)

**Activités :**

- Conception User Service avec support dual (nouveaux + legacy)
- Implémentation authentification JWT (access + refresh tokens)
- Intégration API Façade Legacy pour utilisateurs existants
- Interface inscription/connexion responsive
- Tests de sécurité (OWASP Top 10)

**Livrables :**

- User Service opérationnel
- Système d'authentification JWT
- Interfaces inscription/connexion/profil
- Documentation API (OpenAPI 3.0)
- Tests de sécurité validés

**Critères d'acceptation business :**

- ✅ Nouveaux utilisateurs peuvent s'inscrire (email + mot de passe)
- ✅ Utilisateurs legacy peuvent se connecter (via API Façade)
- ✅ Tokens JWT expiration 24h, refresh 7 jours
- ✅ Réinitialisation mot de passe fonctionnelle
- ✅ Conformité RGPD (consentement, portabilité)

**Priorité :** P1 (Important)
**Échéance :** Mois 3 (milieu Cycle 2)

---

## 8. Plan de communication

### 8.1 Rituels de communication

**Revues bi-hebdomadaires Comité de Pilotage (2h) :**

- **Participants :** CIO, CPO, Fonction Architecture, (+CEO/CFO selon besoin)
- **Agenda type :**
  - Avancement vs. plan (30 min)
  - Décisions architecturales à valider (45 min)
  - Gestion des risques et blocages (30 min)
  - Actions et prochaines étapes (15 min)
- **Livrables :** Compte-rendu + décisions documentées (ADRs si applicable)

**Stand-ups quotidiens équipes (15 min) :**

- **Participants :** Équipes Frontend, Backend, DevOps + Fonction Architecture (rotation)
- **Format :** Hier / Aujourd'hui / Blocages

**Démos de fin de cycle (1h30) :**

- **Participants :** Toutes parties prenantes + équipes
- **Cycle 1 :** Go/No-Go architecture
- **Cycle 2 :** Démo recherche géolocalisée + investisseurs
- **Cycle 3 :** Démo end-to-end + validation Go Phase 2

**Rétrospectives de cycle (1h) :**

- **Participants :** Équipes + Fonction Architecture
- **Format :** What went well / What to improve / Actions

### 8.2 Canaux de communication

| Canal          | Usage                                | Fréquence         |
| -------------- | ------------------------------------ | ----------------- |
| **Slack**      | Communication quotidienne, questions | Continue          |
| **Confluence** | Documentation centralisée            | Mise à jour hebdo |
| **GitHub**     | Code, ADRs, issues techniques        | Continue          |
| **Miro**       | Architecture visuelle collaborative  | Ateliers          |
| **Email**      | Communications formelles, décisions  | Selon besoin      |

### 8.3 Reporting

**Dashboard de suivi (Confluence, mise à jour hebdomadaire) :**

- État d'avancement par item de travail (RAG status)
- Métriques clés (coûts, performance, couverture tests)
- Risques actifs et plans de mitigation
- Décisions en attente de validation

**Rapport mensuel exécutif (1 page) :**

- Résumé avancement vs. objectifs
- Budget consommé vs. prévu
- Risques majeurs
- Décisions requises

---

## 9. Risques et facteurs de réduction

### 9.1 Analyse des risques

| ID  | Risque                                                | Gravité | Probabilité | Facteur de réduction                                           | Propriétaire            |
| --- | ----------------------------------------------------- | ------- | ----------- | -------------------------------------------------------------- | ----------------------- |
| R1  | Sous-estimation complexité microservices              | Élevée  | Moyenne     | Prototypage précoce, formation équipes, patterns établis       | Fonction Architecture   |
| R2  | Dépassement budget cloud AWS                          | Moyenne | Élevée      | Monitoring coûts, optimisation continue, réservation instances | DevOps + CFO            |
| R3  | Résistance au changement équipes legacy               | Moyenne | Moyenne     | Implication précoce, formation, quick wins visibles            | CIO + Fonction Archi    |
| R4  | Performance recherche géospatiale insuffisante        | Élevée  | Faible      | POC précoce, tests charge, caching agressif                    | Backend + DevOps        |
| R5  | Manque d'expertise cloud-native dans équipes          | Moyenne | Élevée      | Formation AWS, pair programming, documentation                 | CIO + Resp. Eng         |
| R6  | Indisponibilité pendant migration données             | Élevée  | Faible      | Strangler Fig pattern, coexistence 12-18 mois, rollback < 5min | DevOps + Fonction Archi |
| R7  | Scope creep pendant Phase 1                           | Moyenne | Élevée      | Backlog priorisé strict, MVP focus, contrats clairs            | CPO + Fonction Archi    |
| R8  | API Façade Legacy : documentation inexistante         | Élevée  | Élevée      | Reverse engineering, expert legacy dédié, tests exploratoires  | Backend + Resp. Eng     |
| R9  | Performances legacy insuffisantes sous charge         | Moyenne | Moyenne     | Caching agressif, circuit breaker, timeouts 500ms max          | DevOps + Backend        |
| R10 | Choix technologiques inadaptés découverts tardivement | Moyenne | Faible      | POCs Cycle 1, ADRs documentés, décisions réversibles           | Fonction Archi          |

---

## 10. Hypothèses

| ID  | Hypothèse                                                            | Impact si fausse                        | Propriétaire            |
| --- | -------------------------------------------------------------------- | --------------------------------------- | ----------------------- |
| H1  | Les équipes peuvent monter en compétence cloud-native en 6 mois      | Retard projet, qualité réduite          | CIO                     |
| H2  | La plateforme legacy peut rester stable en mode maintenance strict   | Ressources détournées, incidents legacy | Resp. Eng               |
| H3  | AWS peut fournir les performances géospatiales requises (<200ms p95) | Changement provider, refonte            | DevOps (validé POC M1)  |
| H4  | Le budget 50K USD couvre architecture + prototype                    | Réduction scope                         | CFO                     |
| H5  | Les utilisateurs adopteront progressivement la nouvelle plateforme   | Stratégie adoption à revoir             | CMO + CPO               |
| H6  | Le legacy peut supporter 50+ req/sec via API Façade                  | Saturation système, latence élevée      | DevOps (load test M1)   |
| H7  | L'équipe peut accéder au code et DB legacy pour reverse engineering  | Blocage développement API Façade        | Resp. Eng (confirmé M1) |
| H8  | Les équipes Frontend/Backend acceptent la stack proposée             | Friction équipes, courbe apprentissage  | CIO (workshop M1)       |

---

## 11. Critères d'acceptation et procédures

### 11.1 Métriques et KPIs

**Métriques de succès du projet (Phase 1) :**

| Métrique                             | Valeur cible  | Méthode de mesure                | Justification                  |
| ------------------------------------ | ------------- | -------------------------------- | ------------------------------ |
| Temps réponse recherche géolocalisée | < 200ms (p95) | Tests de performance automatisés | UX critique pour adoption      |
| Disponibilité prototype              | > 99%         | Monitoring CloudWatch            | Prouver stabilité architecture |
| Couverture tests automatisés         | > 80%         | CI/CD pipeline                   | Qualité et confiance           |
| Temps de build et déploiement        | < 15 min      | Métriques CI/CD                  | Feedback rapide développeurs   |
| Coût infrastructure mensuel          | < 2000 USD    | AWS Cost Explorer                | Viabilité économique           |
| Satisfaction équipes dev (NPS)       | > 40          | Survey fin de cycle              | Adoption et engagement         |
| Latence API Façade Legacy (p95)      | < 300ms       | CloudWatch/X-Ray                 | Performance intégration        |
| Disponibilité API Façade             | > 99.5%       | Monitoring continu               | Fiabilité coexistence          |

### 11.2 Critères d'acceptation Phase 1

Le prototype sera considéré comme **accepté** si :

**1. Fonctionnel**

- ✅ Recherche géolocalisée opérationnelle (rayon configurable)
- ✅ Création et gestion de commandes bout-en-bout
- ✅ Interface responsive (web + mobile)
- ✅ Utilisateurs peuvent créer comptes et naviguer
- ✅ Intégration legacy opérationnelle (lecture données utilisateurs)

**2. Technique**

- ✅ Architecture microservices déployée sur AWS
- ✅ API Façade Legacy fonctionnelle (endpoints P0/P1)
- ✅ CI/CD automatisé avec tests (y compris tests de contrat)
- ✅ Monitoring et alerting configurés (nouveau + legacy)
- ✅ Documentation architecture complète

**3. Performance**

- ✅ Métriques cibles atteintes (voir tableau ci-dessus)
- ✅ Tests de charge validés (100 utilisateurs concurrents minimum)

**4. Gouvernance**

- ✅ Contrats d'architecture signés
- ✅ Principes et patterns documentés
- ✅ ADRs (décisions) tracées
- ✅ Plan Phase 2 validé

### 11.3 Procédure d'acceptation

1. **Revue technique** (Semaine M6-2) : Équipe engineering + DevOps
2. **Revue architecture** (Semaine M6-1) : Comité de pilotage
3. **Démo exécutive** (Semaine M6) : C-level + investisseurs
4. **Décision Go/No-Go Phase 2** (Fin M6)

---

## 12. Procédures de changement de périmètre

### 12.1 Processus de gestion du changement

Toute demande de changement de périmètre doit suivre le processus suivant :

**1. Soumission de la demande de changement**

- **Qui :** Toute partie prenante (Business ou Technique)
- **Format :** Template "Change Request" (Confluence)
- **Contenu obligatoire :**
  - Description du changement
  - Justification business
  - Impact estimé (délai, coût, ressources)
  - Priorité proposée (P0/P1/P2)

**2. Analyse d'impact (48h max)**

- **Responsable :** Fonction Architecture + équipes concernées
- **Livrables :**
  - Analyse technique détaillée
  - Estimation coût/délai
  - Impact sur planning et autres items
  - Alternatives éventuelles

**3. Décision**

| Type de changement                   | Niveau de décision    | Délai      |
| ------------------------------------ | --------------------- | ---------- |
| Impact < 5K USD, pas de délai        | Fonction Architecture | 24h        |
| Impact 5K-10K USD, délai < 1 semaine | CIO + CPO             | 48h        |
| Impact > 10K USD ou changement scope | Comité de Pilotage    | 1 semaine  |
| Impact majeur (> 20K USD)            | CEO                   | 2 semaines |

**4. Communication et mise à jour**

- Mise à jour backlog priorisé
- Notification toutes parties prenantes
- Update documentation (plan de travail, budget, planning)

### 12.2 Mécanisme de protection contre le scope creep

**Règles strictes Phase 1 :**

- ✅ **Maximum 2 changements majeurs** (>10K USD) acceptés sur toute la Phase 1
- ✅ **Budget de contingence** : 10% du budget total (5K USD) réservé aux changements mineurs
- ✅ **Backlog Phase 2** : Toute demande non-critique reportée automatiquement
- ✅ **Principe du "swap"** : Ajout d'un item P0 → Retrait obligatoire d'un autre item P0

**Mécanisme d'alerte :**

Si le scope augmente de plus de 15% par rapport au périmètre initial → Alerte automatique au CEO + revue extraordinaire du Comité de Pilotage.

---

## 13. Calendrier

### 13.1 Planning global Phase 1

**Vue d'ensemble (6 mois) :**

```
┌─────────────┬─────────────┬─────────────┬─────────────┬─────────────┬─────────────┐
│   Mois 1    │   Mois 2    │   Mois 3    │   Mois 4    │   Mois 5    │   Mois 6    │
├─────────────┴─────────────┴─────────────┴─────────────┴─────────────┴─────────────┤
│ ◄───── Cycle 1 ──────►│◄────── Cycle 2 ─────────►│◄────── Cycle 3 ─────────►     │
│ Fondations & Vision   │   Prototype Core          │   Complétion & Commandes      │
└───────────────────────┴───────────────────────────┴───────────────────────────────┘
```

**Jalons critiques :**

| Date       | Jalon                               | Décision/Livrable                                |
| ---------- | ----------------------------------- | ------------------------------------------------ |
| **Fin M1** | Vision & Spécifications validées    | Go/No-Go architecture par Comité Pilotage        |
| **Fin M2** | POC géolocalisation validé          | Validation performances (<200ms prouvé)          |
| **Fin M4** | Démo recherche géolocalisée         | Validation UX/UI + démo investisseurs            |
| **Mi-M5**  | Revue Go/No-Go Phase 2 préliminaire | Décision investissement Phase 2 (pré-validation) |
| **Fin M6** | Prototype end-to-end                | Décision finale Go/No-Go Phase 2                 |

### 13.2 Planning détaillé par cycle

**Cycle 1 (M1-M2) : Fondations & Vision**

| Semaine | Activités principales                                        | Livrables                         |
| ------- | ------------------------------------------------------------ | --------------------------------- |
| S1      | - Kick-off projet<br>- Workshops architecture avec équipes   | Vision d'Architecture v0.1        |
| S2      | - Rédaction Spécifications Exigences<br>- Rédaction Contrats | Spécifications + Contrats signés  |
| S3      | - POC DynamoDB géospatial<br>- POC EKS                       | Preuve de concept validée         |
| S4      | - Setup infrastructure base<br>- Load testing legacy         | Infra dev opérationnelle          |
| S5-S6   | - Architecture détaillée services<br>- Spécifications APIs   | Diagrammes + ADRs + Specs OpenAPI |
| S7-S8   | - Finalisation documentation<br>- Préparation revue Go/No-Go | Documentation complète, démo POC  |

**Milestone Cycle 1 :** Go/No-Go architecture par Comité de Pilotage (fin S8)

**Cycle 2 (M3-M4) : Prototype Core**

| Semaine | Activités principales                                                 | Livrables                           |
| ------- | --------------------------------------------------------------------- | ----------------------------------- |
| S9-S10  | - Développement Search Service<br>- Développement User Service        | Services opérationnels (env dev)    |
| S11-S12 | - Développement API Façade Legacy<br>- Intégration cartographie       | API Façade fonctionnelle            |
| S13-S14 | - Développement interface recherche (frontend)<br>- Tests intégration | Interface responsive opérationnelle |
| S15-S16 | - Tests E2E<br>- Optimisation performance<br>- Démo investisseurs     | Démo recherche géolocalisée validée |

**Milestone Cycle 2 :** Validation UX/UI par CPO + démo investisseurs (fin S16)

**Cycle 3 (M5-M6) : Complétion & Commandes**

| Semaine | Activités principales                                                  | Livrables                                 |
| ------- | ---------------------------------------------------------------------- | ----------------------------------------- |
| S17-S18 | - Développement Order Service<br>- Développement interface panier      | Order Service opérationnel                |
| S19-S20 | - Intégration notifications (SES)<br>- Tests bout-en-bout commande     | Parcours commande complet                 |
| S21-S22 | - Finalisation monitoring<br>- Tests de charge<br>- Optimisation coûts | Dashboards complets, perf validées        |
| S23-S24 | - Documentation finale<br>- Préparation démo C-level<br>- Plan Phase 2 | Doc complète, démo end-to-end, Go Phase 2 |

**Milestone Cycle 3 :** Prototype end-to-end + validation Go Phase 2 (fin S24)

---

## 14. Phases de livrables définies

### 14.1 Livrables par phase

**Phase 1 (M1-M6) - PROTOTYPE & ARCHITECTURE :**

| Catégorie          | Livrables                                                                                        |
| ------------------ | ------------------------------------------------------------------------------------------------ |
| **Documentation**  | - Vision d'Architecture<br>- Spécifications Exigences<br>- Contrats Business & Dev<br>- ADRs     |
| **Architecture**   | - Diagrammes architecture cible<br>- Spécifications APIs (OpenAPI 3.0)<br>- Choix technologiques |
| **Prototype**      | - Recherche géolocalisée fonctionnelle<br>- Gestion commandes<br>- Intégration legacy            |
| **Infrastructure** | - AWS EKS, RDS, DynamoDB, S3 déployés<br>- CI/CD opérationnel<br>- Monitoring CloudWatch + X-Ray |
| **Validation**     | - Tests automatisés (≥80% coverage)<br>- Tests de charge<br>- Démos Cycles 1/2/3                 |

**Phase 2 (M7-M12) - PRODUCTION-READY :**

_(Détails définis en fin Phase 1 - Vue d'ensemble uniquement)_

| Catégorie       | Livrables prévus                                                                               |
| --------------- | ---------------------------------------------------------------------------------------------- |
| **Features**    | - Paiement en ligne (Stripe/PayPal)<br>- Migration données utilisateurs<br>- Back-office admin |
| **Scalabilité** | - Auto-scaling optimisé<br>- CDN global<br>- Multi-région (si besoin)                          |
| **Sécurité**    | - Pentest externe<br>- Conformité PCI-DSS (paiements)<br>- Audit RGPD complet                  |
| **Production**  | - Déploiement production<br>- SLAs production (99.9%)<br>- Support 24/7                        |

### 14.2 Critères de passage entre phases

**Conditions pour Go Phase 2 (validation fin M6) :**

| Critère                            | Seuil minimum               | Responsable validation |
| ---------------------------------- | --------------------------- | ---------------------- |
| Prototype fonctionnel end-to-end   | 100% parcours principaux    | CPO                    |
| Performance recherche géolocalisée | < 200ms (p95)               | CIO                    |
| Couverture tests automatisés       | ≥ 80%                       | CIO                    |
| Disponibilité prototype (M5-M6)    | ≥ 99%                       | CIO                    |
| Coût infrastructure                | < 2 000 USD/mois            | CFO                    |
| Documentation architecture         | 100% complète               | Fonction Archi         |
| Validation business case Phase 2   | ROI positif projeté 18 mois | CEO + CFO              |

**Si critères non atteints :** Phase 1 prolongée (max +2 mois) OU Projet arrêté

---

## 15. Personnes approuvant ce plan

### 15.1 Signatures requises

Ce Contrat d'Architecture Business engage les parties suivantes :

| Rôle                      | Nom            | Signature              | Date         |
| ------------------------- | -------------- | ---------------------- | ------------ |
| **CEO & Sponsor**         | Ash Callum     | **\*\***\_\_\_**\*\*** | **_/_**/2025 |
| **CIO**                   | Natasha Jarson | **\*\***\_\_\_**\*\*** | **_/_**/2025 |
| **CPO**                   | Daniel Anthony | **\*\***\_\_\_**\*\*** | **_/_**/2025 |
| **CFO**                   | Jo Kumar       | **\*\***\_\_\_**\*\*** | **_/_**/2025 |
| **Directeur Opérations**  | Jack Harkness  | **\*\***\_\_\_**\*\*** | **_/_**/2025 |
| **Fonction Architecture** | Mathieu Baro   | **\*\***\_\_\_**\*\*** | **_/_**/2025 |

### 15.2 Validation et date d'effet

**Date de validation ciblée :** [À remplir]
**Date d'effet du contrat :** [À remplir]
**Durée de validité :** 6 mois (renouvelable pour Phase 2)

### 15.3 Révisions du document

| Version | Date         | Auteur       | Changements                         |
| ------- | ------------ | ------------ | ----------------------------------- |
| 0.1     | Octobre 2025 | Mathieu Baro | Version initiale (DRAFT)            |
| 0.2     | [À venir]    | Mathieu Baro | Intégration retours Comité Pilotage |
| 1.0     | [À venir]    | Mathieu Baro | Version finale signée               |

---

**Document vivant :** Ce contrat sera mis à jour selon les apprentissages des cycles itératifs, avec validation formelle du Comité de Pilotage pour tout changement majeur.

**Version :** 0.1 - DRAFT
**Dernière mise à jour :** Octobre 2025
**Prochaine révision :** Fin Mois 1 (intégration feedbacks)
