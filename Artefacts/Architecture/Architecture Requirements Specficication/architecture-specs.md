# Spécification des Exigences pour l'Architecture

**Projet : Plateforme Foosus Géoconsciente**  
**Client : Foosus**  
**Préparé par : Mathieu Baro**  
**N° de Version du Document : 0.1 - DRAFT**  
**Date de Version du Document : Octobre 2025**

---

## Table des Matières

1. Objet de ce document
2. Mesures du succès
3. Exigences pour l'architecture
4. Contrats de service business
5. Contrats de service application
6. Lignes directrices pour l'implémentation
7. Spécifications pour l'implémentation
8. Standards pour l'implémentation
9. Exigences pour l'interopérabilité
10. Exigences pour le management du service IT
11. Contraintes
12. Hypothèses

---

## 1. Objet de ce document

La Spécification des Exigences pour l'Architecture fournit un ensemble de déclarations **quantitatives et mesurables** qui définissent ce que doit accomplir le projet d'implémentation pour être conforme à l'architecture cible de Foosus.

Ce document **complète** la Déclaration de Travail d'Architecture :

- **Déclaration de Travail** : Vision qualitative, intention architecturale (le "pourquoi" et le "quoi")
- **Spécification des Exigences** : Vision quantitative, critères mesurables (le "combien" et "dans quelles limites")

Ce document constituera un composant clé du contrat d'implémentation avec les équipes de développement et servira de base pour la validation du prototype Phase 1.

**Public cible :**

- Équipes de développement (Frontend, Backend, DevOps)
- Testeurs et QA
- Chef de projet technique
- Product Owner (validation acceptance)

---

## 2. Mesures du succès

### 2.1 Critères de succès du prototype Phase 1

Le prototype sera considéré comme réussi si **tous** les critères suivants sont atteints à la fin du Cycle 3 (Mois 6) :

| **ID** | **Critère**                           | **Valeur cible**    | **Méthode de mesure**         | **Priorité** |
| ------ | ------------------------------------- | ------------------- | ----------------------------- | ------------ |
| S1     | Recherche géolocalisée opérationnelle | 100% fonctionnelle  | Tests automatisés E2E         | P0           |
| S2     | Latence recherche (p95)               | < 200ms             | Tests de charge (k6/Gatling)  | P0           |
| S3     | Création commandes bout-en-bout       | 100% fonctionnelle  | Tests automatisés E2E         | P0           |
| S4     | Disponibilité prototype               | ≥ 99.5% sur M5-M6   | Monitoring CloudWatch         | P0           |
| S5     | Couverture tests automatisés          | ≥ 80%               | Coverage reports (Jest/JUnit) | P0           |
| S6     | Temps build + déploiement             | < 15 minutes        | Métriques CI/CD               | P1           |
| S7     | Coût infrastructure mensuel           | < 2 000 USD         | AWS Cost Explorer             | P0           |
| S8     | Taux d'erreur API (4xx+5xx)           | < 1%                | CloudWatch Metrics            | P1           |
| S9     | API Façade Legacy opérationnelle      | ≥ 99% disponibilité | Monitoring dédié              | P0           |
| S10    | Documentation architecture            | 100% complète       | Revue comité pilotage         | P0           |

### 2.2 Métriques business (post-déploiement production)

Ces métriques seront trackées après le déploiement en production (Phase 2+) :

| **Métrique**                         | **Valeur baseline** | **Objectif 6 mois** | **Objectif 12 mois** |
| ------------------------------------ | ------------------- | ------------------- | -------------------- |
| Inscriptions utilisateurs/jour       | Actuel inconnu      | +10% vs baseline    | +30% vs baseline     |
| Adhésion producteurs/mois            | 1.4                 | 4                   | 8                    |
| Taux conversion recherche → commande | [À mesurer]         | +15%                | +30%                 |
| Taux abandon panier                  | [À mesurer]         | -20%                | -40%                 |
| NPS (Net Promoter Score)             | [À mesurer]         | ≥ 40                | ≥ 60                 |
| Incidents P1/mois                    | >25 (legacy)        | <5                  | <1                   |
| Délai moyen de mise en production    | 3.5 semaines        | <1 semaine          | <3 jours             |

---

## 3. Exigences pour l'architecture

### 3.1 Exigences fonctionnelles

#### 3.1.1 Recherche géolocalisée de fournisseurs

| **ID**       | **Exigence**                                                                                       | **Critère d'acceptation**                               | **Priorité** |
| ------------ | -------------------------------------------------------------------------------------------------- | ------------------------------------------------------- | ------------ |
| F-SEARCH-001 | Le système doit permettre la recherche de fournisseurs par géolocalisation                         | Rayon configurable de 1 à 50 km                         | P0           |
| F-SEARCH-002 | La recherche doit utiliser la position GPS de l'utilisateur (mobile) ou l'adresse saisie (desktop) | Précision ± 100m en mobile, adresse exacte desktop      | P0           |
| F-SEARCH-003 | Les résultats doivent être triés par distance par défaut                                           | Distance calculée en ligne droite (à vol d'oiseau)      | P0           |
| F-SEARCH-004 | Le système doit afficher la distance entre utilisateur et fournisseur                              | Affichage en km avec 1 décimale (ex: 2.3 km)            | P0           |
| F-SEARCH-005 | L'utilisateur doit pouvoir filtrer par catégorie de produit                                        | Min 10 catégories (légumes, fruits, viandes, etc.)      | P0           |
| F-SEARCH-006 | L'utilisateur doit pouvoir filtrer par disponibilité immédiate                                     | Produits en stock uniquement                            | P1           |
| F-SEARCH-007 | Les résultats doivent afficher 20 fournisseurs par page avec pagination                            | Chargement lazy (infini scroll mobile)                  | P1           |
| F-SEARCH-008 | Le système doit afficher les fournisseurs sur une carte interactive                                | Intégration carte (Google Maps / Mapbox / AWS Location) | P1           |
| F-SEARCH-009 | La recherche doit supporter les filtres multiples (ET logique)                                     | Catégorie + distance + disponibilité simultanément      | P1           |
| F-SEARCH-010 | Le système doit sauvegarder les dernières recherches de l'utilisateur                              | Historique 10 dernières recherches                      | P2           |

#### 3.1.2 Gestion des offres alimentaires (fournisseurs)

| **ID**      | **Exigence**                                                            | **Critère d'acceptation**                                       | **Priorité** |
| ----------- | ----------------------------------------------------------------------- | --------------------------------------------------------------- | ------------ |
| F-OFFER-001 | Un fournisseur doit pouvoir créer une offre alimentaire                 | Champs : nom, description, prix, unité, catégorie, stock, image | P0           |
| F-OFFER-002 | Une offre doit être associée à une localisation géographique précise    | Coordonnées GPS + adresse textuelle                             | P0           |
| F-OFFER-003 | Un fournisseur doit pouvoir modifier le stock d'une offre en temps réel | Update instantané (< 5 sec propagation)                         | P0           |
| F-OFFER-004 | Le système doit supporter les images produits                           | Format JPEG/PNG, max 5MB, compression automatique               | P1           |
| F-OFFER-005 | Une offre doit pouvoir être désactivée temporairement                   | Statut : actif / inactif / rupture stock                        | P1           |
| F-OFFER-006 | Le système doit afficher les informations nutritionnelles (Phase 2)     | Indice glycémique, calories, allergènes                         | P2           |

#### 3.1.3 Gestion des commandes

| **ID**      | **Exigence**                                                               | **Critère d'acceptation**                                            | **Priorité** |
| ----------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------- | ------------ |
| F-ORDER-001 | Un utilisateur doit pouvoir ajouter des offres à un panier                 | Panier multi-fournisseurs supporté                                   | P0           |
| F-ORDER-002 | Le système doit calculer automatiquement le total de la commande           | Prix unitaire × quantité + (frais livraison si applicable Phase 2)   | P0           |
| F-ORDER-003 | Un utilisateur doit pouvoir modifier son panier avant confirmation         | Quantités, suppression articles                                      | P0           |
| F-ORDER-004 | Un utilisateur doit pouvoir confirmer une commande                         | Passage état : brouillon → confirmée                                 | P0           |
| F-ORDER-005 | Le système doit générer un numéro unique de commande                       | Format : ORD-YYYYMMDD-XXXXX (ex: ORD-20251022-00123)                 | P0           |
| F-ORDER-006 | Un utilisateur ne doit PAS pouvoir modifier une commande confirmée         | Modification bloquée après confirmation                              | P0           |
| F-ORDER-007 | Un utilisateur doit pouvoir annuler une commande confirmée sous conditions | Annulation possible si statut ≠ "en cours de livraison"              | P1           |
| F-ORDER-008 | Le système doit envoyer une notification au fournisseur à la confirmation  | Email + (Phase 2) notification in-app                                | P0           |
| F-ORDER-009 | Un utilisateur doit pouvoir consulter l'historique de ses commandes        | Liste paginée, tri par date décroissante                             | P1           |
| F-ORDER-010 | Le système doit supporter plusieurs états de commande                      | États : brouillon, confirmée, en préparation, prête, livrée, annulée | P1           |
| F-ORDER-011 | Le paiement à la livraison doit être supporté (Phase 1)                    | Pas d'intégration paiement en ligne Phase 1                          | P0           |
| F-ORDER-012 | Intégration paiement en ligne (Phase 2)                                    | Stripe / PayPal - Hors scope Phase 1                                 | P2           |

#### 3.1.4 Gestion des utilisateurs

| **ID**     | **Exigence**                                                 | **Critère d'acceptation**                              | **Priorité** |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------ | ------------ |
| F-USER-001 | Nouveaux utilisateurs peuvent s'inscrire                     | Email + mot de passe + type (consommateur/fournisseur) | P0           |
| F-USER-002 | Les utilisateurs existants (legacy) doivent être accessibles | Lecture via API Façade Legacy                          | P0           |
| F-USER-003 | Authentification via email/mot de passe                      | JWT token, expiration 24h                              | P0           |
| F-USER-004 | Les utilisateurs peuvent réinitialiser leur mot de passe     | Email avec lien expirable (1h)                         | P1           |
| F-USER-005 | Les utilisateurs peuvent mettre à jour leur profil           | Nom, adresse, téléphone, avatar                        | P1           |
| F-USER-006 | Les fournisseurs doivent avoir un profil étendu              | Description, horaires, photos, certifications          | P1           |
| F-USER-007 | Authentification OAuth (Google/Facebook) (Phase 2)           | Hors scope Phase 1                                     | P2           |
| F-USER-008 | Vérification email obligatoire à l'inscription               | Email de confirmation avec lien                        | P1           |

### 3.2 Exigences non-fonctionnelles (NFRs)

#### 3.2.1 Performance

| **ID**       | **Exigence**                             | **Valeur cible**   | **Méthode de mesure**       | **Priorité** |
| ------------ | ---------------------------------------- | ------------------ | --------------------------- | ------------ |
| NFR-PERF-001 | Latence API recherche géolocalisée (p50) | < 100ms            | Tests de charge, CloudWatch | P0           |
| NFR-PERF-002 | Latence API recherche géolocalisée (p95) | < 200ms            | Tests de charge, CloudWatch | P0           |
| NFR-PERF-003 | Latence API recherche géolocalisée (p99) | < 500ms            | Tests de charge, CloudWatch | P1           |
| NFR-PERF-004 | Latence création commande (p95)          | < 300ms            | Tests de charge, CloudWatch | P0           |
| NFR-PERF-005 | Latence API Façade Legacy (p95)          | < 300ms            | Monitoring dédié            | P0           |
| NFR-PERF-006 | Latence chargement page frontend (p95)   | < 2 secondes       | Lighthouse, WebPageTest     | P0           |
| NFR-PERF-007 | Time to Interactive (TTI) mobile (p95)   | < 3 secondes       | Lighthouse mobile           | P1           |
| NFR-PERF-008 | Débit recherches géolocalisées           | ≥ 500 req/sec      | Tests de charge (k6)        | P0           |
| NFR-PERF-009 | Débit création commandes                 | ≥ 100 req/sec      | Tests de charge (k6)        | P1           |
| NFR-PERF-010 | Taille bundle JavaScript frontend        | < 500 KB (gzipped) | Webpack Bundle Analyzer     | P1           |

**Charge cible Phase 1 (prototype) :**

- **Utilisateurs concurrents** : 5 000 simultanés
- **Requêtes/seconde totales** : ~1 000 req/sec (moyenne)
- **Pics de charge** : x2 (10 000 utilisateurs, 2 000 req/sec) !! augmenter !!

**Capacité de scalabilité :**

- Architecture doit supporter scaling horizontal jusqu'à 50 000 utilisateurs concurrents (x10) sans refonte majeure

#### 3.2.2 Disponibilité et Fiabilité

| **ID**        | **Exigence**                            | **Valeur cible**                        | **Priorité** |
| ------------- | --------------------------------------- | --------------------------------------- | ------------ |
| NFR-AVAIL-001 | Disponibilité du système (SLA)          | ≥ 99.9% (8.76h downtime/an max)         | P0           |
| NFR-AVAIL-002 | Disponibilité API Façade Legacy         | ≥ 99.5%                                 | P0           |
| NFR-AVAIL-003 | RTO (Recovery Time Objective)           | < 15 minutes (incidents majeurs)        | P0           |
| NFR-AVAIL-004 | RPO (Recovery Point Objective)          | < 1 heure (perte données acceptable)    | P1           |
| NFR-AVAIL-005 | MTTR (Mean Time To Repair)              | < 30 minutes (incidents P1)             | P1           |
| NFR-AVAIL-006 | Taux de succès API (non-erreur)         | ≥ 99% (< 1% d'erreurs 4xx+5xx)          | P0           |
| NFR-AVAIL-007 | Zero-downtime deployments               | 100% des déploiements sans interruption | P0           |
| NFR-AVAIL-008 | Pas de fenêtre de maintenance planifiée | Déploiements 24/7 possibles             | P0           |

**Calcul disponibilité 99.9% :**

- Downtime acceptable par an : 8.76 heures
- Downtime acceptable par mois : ~43 minutes
- Downtime acceptable par semaine : ~10 minutes

**Stratégie haute disponibilité :**

- Déploiement multi-AZ (Availability Zones) AWS
- Load balancing automatique
- Health checks et auto-healing
- Circuit breakers pour isolation des pannes

#### 3.2.3 Scalabilité

| **ID**        | **Exigence**                         | **Valeur cible**                                       | **Priorité** |
| ------------- | ------------------------------------ | ------------------------------------------------------ | ------------ |
| NFR-SCALE-001 | Scalabilité horizontale des services | Tous les services doivent supporter scaling horizontal | P0           |
| NFR-SCALE-002 | Auto-scaling basé sur la charge      | Déclenchement si CPU > 70% ou requêtes > seuil         | P0           |
| NFR-SCALE-003 | Temps de scaling (scale-up)          | < 5 minutes pour ajout instances                       | P1           |
| NFR-SCALE-004 | Temps de scaling (scale-down)        | < 10 minutes pour retrait instances (après cooldown)   | P2           |
| NFR-SCALE-005 | Croissance données supportée         | +30% utilisateurs/mois pendant 12 mois (x4.5 total)    | P0           |
| NFR-SCALE-006 | Volumétrie fournisseurs              | Jusqu'à 10 000 fournisseurs actifs                     | P0           |
| NFR-SCALE-007 | Volumétrie produits                  | Jusqu'à 100 000 offres alimentaires actives            | P0           |
| NFR-SCALE-008 | Volumétrie commandes                 | Jusqu'à 1 000 commandes/heure en pic                   | P1           |
| NFR-SCALE-009 | Taille base de données               | Jusqu'à 500 GB (Phase 1), 5 TB (Phase 2)               | P1           |

**Modèle de croissance prévu :**

- **Mois 1** : 1 000 utilisateurs actifs
- **Mois 6** : 4 500 utilisateurs actifs (x4.5 avec 30%/mois)
- **Mois 12** : 20 000 utilisateurs actifs

#### 3.2.4 Sécurité

| **ID**      | **Exigence**                                 | **Détail**                                                    | **Priorité** |
| ----------- | -------------------------------------------- | ------------------------------------------------------------- | ------------ |
| NFR-SEC-001 | Authentification forte                       | JWT tokens, expiration 24h, refresh tokens 7 jours            | P0           |
| NFR-SEC-002 | Chiffrement en transit (TLS)                 | TLS 1.3 minimum pour toutes les communications                | P0           |
| NFR-SEC-003 | Chiffrement au repos                         | Base de données et S3 chiffrés (AWS KMS)                      | P0           |
| NFR-SEC-004 | Protection contre injections SQL             | ORM/Query builders, parameterized queries                     | P0           |
| NFR-SEC-005 | Protection XSS (Cross-Site Scripting)        | Sanitization inputs, Content Security Policy (CSP)            | P0           |
| NFR-SEC-006 | Protection CSRF (Cross-Site Request Forgery) | CSRF tokens, SameSite cookies                                 | P0           |
| NFR-SEC-007 | Rate limiting APIs                           | Max 100 req/min par IP, 1000 req/min par user authentifié     | P0           |
| NFR-SEC-008 | WAF (Web Application Firewall)               | AWS WAF avec règles OWASP Top 10                              | P1           |
| NFR-SEC-009 | Principe du moindre privilège (IAM)          | Rôles IAM dédiés par service, pas de credentials hardcodés    | P0           |
| NFR-SEC-010 | Rotation des secrets                         | Automatique tous les 90 jours (AWS Secrets Manager)           | P1           |
| NFR-SEC-011 | Audit logs                                   | Tous les accès aux données personnelles loggés                | P0           |
| NFR-SEC-012 | Conformité RGPD                              | Consentement, portabilité, droit à l'oubli implémentés        | P0           |
| NFR-SEC-013 | Scan vulnérabilités                          | Images Docker scannées (Trivy), dépendances (Snyk/Dependabot) | P1           |
| NFR-SEC-014 | Authentification multi-facteur (MFA)         | Pour comptes admin uniquement (Phase 1)                       | P1           |
| NFR-SEC-015 | Protection DDoS                              | AWS Shield Standard (gratuit), Shield Advanced (Phase 2)      | P1           |

**Données sensibles à protéger :**

- Informations personnelles (RGPD) : nom, email, téléphone, adresse
- Localisation GPS précise des utilisateurs
- Données de paiement (Phase 2 : conformité PCI-DSS)
- Credentials d'authentification (hachage bcrypt/Argon2)

#### 3.2.5 Utilisabilité et Accessibilité

| **ID**     | **Exigence**                      | **Valeur cible**                                          | **Priorité** |
| ---------- | --------------------------------- | --------------------------------------------------------- | ------------ |
| NFR-UX-001 | Responsive design                 | Support mobile (320px), tablet (768px), desktop (1024px+) | P0           |
| NFR-UX-002 | Compatibilité navigateurs         | Chrome, Firefox, Safari, Edge (2 dernières versions)      | P0           |
| NFR-UX-003 | Accessibilité WCAG                | Niveau AA (WCAG 2.1)                                      | P1           |
| NFR-UX-004 | Support hors-ligne (PWA)          | Cache des dernières recherches, navigation basique        | P2           |
| NFR-UX-005 | Internationalisation (i18n)       | Support Français (Phase 1), multi-langues (Phase 2)       | P1           |
| NFR-UX-006 | Performance réseau lent           | Utilisable sur connexion 3G (≥ 1 Mbps)                    | P1           |
| NFR-UX-007 | Taille données chargement initial | < 2 MB total (HTML + CSS + JS + images)                   | P1           |

#### 3.2.6 Maintenabilité et Observabilité

| **ID**        | **Exigence**                         | **Détail**                                              | **Priorité** |
| ------------- | ------------------------------------ | ------------------------------------------------------- | ------------ |
| NFR-MAINT-001 | Couverture tests unitaires           | ≥ 80% coverage                                          | P0           |
| NFR-MAINT-002 | Couverture tests intégration         | 100% endpoints critiques (P0)                           | P0           |
| NFR-MAINT-003 | Tests E2E automatisés                | Scénarios utilisateurs principaux (recherche, commande) | P0           |
| NFR-MAINT-004 | Documentation code                   | JSDoc/JavaDoc pour fonctions publiques                  | P1           |
| NFR-MAINT-005 | Documentation APIs                   | OpenAPI 3.0 pour toutes les APIs REST                   | P0           |
| NFR-MAINT-006 | Logs structurés                      | Format JSON avec correlation-id                         | P0           |
| NFR-MAINT-007 | Métriques applicatives               | Golden Signals : latence, trafic, erreurs, saturation   | P0           |
| NFR-MAINT-008 | Distributed tracing                  | AWS X-Ray pour traces end-to-end                        | P1           |
| NFR-MAINT-009 | Dashboards monitoring                | Grafana/CloudWatch avec vues business et technique      | P0           |
| NFR-MAINT-010 | Alerting proactif                    | PagerDuty/SNS pour incidents critiques                  | P0           |
| NFR-MAINT-011 | Retention logs                       | 30 jours (hot), 90 jours (archive)                      | P1           |
| NFR-MAINT-012 | Architecture Decision Records (ADRs) | Toutes décisions majeures documentées                   | P1           |

---

## 4. Contrats de service business

### 4.1 Accords de niveau de service (SLA)

Les SLAs définissent les engagements contractuels envers les utilisateurs business (consommateurs et fournisseurs).

#### 4.1.1 SLA Disponibilité

| **Métrique**             | **Engagement** | **Mesure**             | **Pénalité si non-respect**     |
| ------------------------ | -------------- | ---------------------- | ------------------------------- |
| Disponibilité mensuelle  | ≥ 99.9%        | Uptime monitoring 24/7 | Crédit 10% coûts hébergement    |
| Incidents critiques (P1) | < 2 par mois   | Système de ticketing   | Rapport post-mortem obligatoire |
| Temps résolution P1      | < 2 heures     | Depuis détection       | Escalation automatique          |
| Temps résolution P2      | < 8 heures     | Depuis détection       | Suivi par management            |

**Définition incident P1 (critique) :**

- Recherche géolocalisée indisponible
- Création de commandes impossible
- Perte de données utilisateurs
- Faille de sécurité critique

#### 4.1.2 SLA Performance

| **Métrique**                | **Engagement** | **Mesure**                   | **Fenêtre de temps** |
| --------------------------- | -------------- | ---------------------------- | -------------------- |
| Latence recherche (p95)     | < 200ms        | CloudWatch RUM               | Moyenne mensuelle    |
| Latence commande (p95)      | < 300ms        | CloudWatch RUM               | Moyenne mensuelle    |
| Temps chargement page (p95) | < 2s           | Google Analytics, Lighthouse | Moyenne mensuelle    |

**Exclusions SLA :**

- Maintenance programmée avec préavis 72h (max 2h/trimestre)
- Force majeure (pannes AWS région entière, catastrophe naturelle)
- Attaques DDoS > 1 Gbps
- Problèmes côté client (navigateur obsolète, connexion < 1 Mbps)

### 4.2 Engagements business

| **Engagement**              | **Détail**                                           | **Responsable**            |
| --------------------------- | ---------------------------------------------------- | -------------------------- |
| Support utilisateurs        | Heures bureau (9h-18h CET) + astreinte P1            | Équipe Support             |
| Onboarding fournisseurs     | Validation sous 48h ouvrées                          | Équipe Produit             |
| Traitement litiges          | Réponse sous 24h, résolution sous 5 jours            | Équipe Satisfaction Client |
| Mises à jour fonctionnelles | Au moins 1 release/2 semaines                        | Équipe Dev                 |
| Communication incidents     | Email + status page sous 15 min (incidents > 30 min) | DevOps                     |

---

## 5. Contrats de service application

### 5.1 Objectifs de niveau de service (SLO)

Les SLOs sont des objectifs internes plus stricts que les SLAs, avec marge de manœuvre.

#### 5.1.1 SLOs Performance

| **Service**       | **Métrique**     | **SLO (objectif interne)** | **SLA (engagement externe)** |
| ----------------- | ---------------- | -------------------------- | ---------------------------- |
| Search Service    | Latence p95      | < 150ms                    | < 200ms                      |
| Search Service    | Latence p99      | < 400ms                    | < 500ms                      |
| Order Service     | Latence p95      | < 250ms                    | < 300ms                      |
| User Service      | Latence p95      | < 100ms                    | < 200ms                      |
| API Gateway       | Latence overhead | < 10ms                     | < 20ms                       |
| API Façade Legacy | Latence p95      | < 250ms                    | < 300ms                      |

#### 5.1.2 SLOs Disponibilité

| **Service**        | **SLO (objectif interne)** | **SLA (engagement externe)** |
| ------------------ | -------------------------- | ---------------------------- |
| Plateforme globale | 99.95%                     | 99.9%                        |
| Search Service     | 99.99%                     | 99.9%                        |
| Order Service      | 99.95%                     | 99.9%                        |
| API Façade Legacy  | 99.5%                      | 99.5%                        |
| Frontend (CDN)     | 99.99%                     | 99.9%                        |

**Budget d'erreur mensuel (Error Budget) :**

- SLO 99.95% = 21 minutes downtime/mois max
- Si dépassé : freeze des features, focus stabilité

#### 5.1.3 SLOs Fiabilité

| **Métrique**               | **SLO**                    | **Action si non-atteint**     |
| -------------------------- | -------------------------- | ----------------------------- |
| Taux de succès API         | ≥ 99.5%                    | Investigation immédiate       |
| Taux erreurs 5xx           | < 0.1%                     | Rollback automatique si spike |
| Déploiements réussis       | ≥ 95%                      | Revue process CI/CD           |
| Tests automatisés passants | 100% (gate de déploiement) | Blocage déploiement           |

### 5.2 Indicateurs de niveau de service (SLI)

Les SLIs sont les métriques concrètes mesurées pour évaluer les SLOs.

#### 5.2.1 SLIs à monitorer en continu

| **SLI**            | **Calcul**                                 | **Seuil alerte**        | **Fréquence mesure** |
| ------------------ | ------------------------------------------ | ----------------------- | -------------------- |
| Availability       | (requêtes réussies / total requêtes) × 100 | < 99.9% sur 5 min       | Temps réel           |
| Latency p95        | 95e percentile temps réponse               | > SLO service           | Temps réel           |
| Error Rate         | (erreurs 5xx / total requêtes) × 100       | > 0.5%                  | Temps réel           |
| Saturation CPU     | % utilisation CPU moyenne pods             | > 80%                   | 1 minute             |
| Saturation Mémoire | % utilisation RAM moyenne pods             | > 85%                   | 1 minute             |
| Throughput         | Requêtes par seconde                       | Chute > 30% vs baseline | Temps réel           |

**Dashboard SLI obligatoire :**
Un dashboard centralisé affichera tous les SLIs en temps réel, visible par toutes les équipes.

---

## 6. Lignes directrices pour l'implémentation

### 6.1 Principes architecturaux à respecter

| **Principe**               | **Application concrète**                                     | **Validation**          |
| -------------------------- | ------------------------------------------------------------ | ----------------------- |
| **Responsabilité unique**  | Chaque microservice gère un seul domaine métier              | Revue architecture      |
| **Couplage faible**        | Communication uniquement via APIs REST/GraphQL               | Tests d'intégration     |
| **Database per Service**   | Chaque service possède sa propre base de données             | Audit schémas DB        |
| **Idempotence**            | Toutes les APIs POST/PUT/DELETE doivent être idempotentes    | Tests automatisés       |
| **Fail-fast**              | Validation des inputs en entrée de service                   | Coverage validation     |
| **Circuit breaker**        | Protection contre pannes en cascade (legacy, services tiers) | Tests chaos engineering |
| **Stateless services**     | Aucun état local dans les services (session dans Redis/DB)   | Validation scalabilité  |
| **API-first design**       | Contrats OpenAPI définis avant implémentation                | Revue specs avant dev   |
| **Event-driven**           | Événements pour communication asynchrone quand approprié     | Architecture review     |
| **Observabilité intégrée** | Logs, metrics, traces dans chaque service dès le départ      | Checklist déploiement   |

### 6.2 Patterns obligatoires

#### 6.2.1 Patterns de résilience

| **Pattern**              | **Quand l'utiliser**                          | **Implémentation**                                       | **Priorité** |
| ------------------------ | --------------------------------------------- | -------------------------------------------------------- | ------------ |
| **Circuit Breaker**      | Appels à API Façade Legacy, services externes | Hystrix, Resilience4j, ou AWS AppConfig                  | P0           |
| **Retry avec backoff**   | Erreurs transitoires (503, timeout)           | Max 3 retries, backoff exponentiel (100ms, 200ms, 400ms) | P0           |
| **Timeout**              | Tous les appels réseau                        | 500ms API Legacy, 200ms inter-services, 30s frontend     | P0           |
| **Bulkhead**             | Isolation des pools de ressources             | Thread pools séparés par type d'opération                | P1           |
| **Rate Limiting**        | Protection contre abus                        | API Gateway (100 req/min/IP) + applicatif                | P0           |
| **Graceful Degradation** | Fonctionnalités non-critiques en échec        | Mode dégradé avec message utilisateur clair              | P1           |

#### 6.2.2 Patterns de données

| **Pattern**             | **Quand l'utiliser**                           | **Implémentation**              | **Priorité** |
| ----------------------- | ---------------------------------------------- | ------------------------------- | ------------ |
| **CQRS (léger)**        | Séparation lecture/écriture si perf nécessaire | Modèles read vs write distincts | P2           |
| **Event Sourcing**      | Audit trail, synchronisation (sélectif)        | EventBridge/DynamoDB Streams    | P2           |
| **Saga Pattern**        | Transactions distribuées (Phase 2)             | Orchestration ou chorégraphie   | P3           |
| **Cache-Aside**         | Données fréquemment lues, peu modifiées        | Redis avec TTL approprié        | P1           |
| **Write-Through Cache** | Cohérence critique (stock produits)            | Update cache + DB atomiquement  | P2           |

#### 6.2.3 Patterns de communication

| **Pattern**                    | **Quand l'utiliser**                              | **Implémentation**                    | **Priorité** |
| ------------------------------ | ------------------------------------------------- | ------------------------------------- | ------------ |
| **API Gateway**                | Point d'entrée unique, routage intelligent        | AWS API Gateway ou Kong               | P0           |
| **Backend for Frontend (BFF)** | Optimisations spécifiques web vs mobile (Phase 2) | GraphQL ou REST BFF                   | P2           |
| **Strangler Fig**              | Migration progressive du legacy                   | API Gateway avec routage conditionnel | P0           |
| **Publish-Subscribe**          | Événements asynchrones (notifications, analytics) | SNS/EventBridge                       | P1           |

### 6.3 Décisions technologiques par domaine

#### 6.3.1 Backend Services

**Choix à valider Cycle 1 avec équipe Backend :**

| **Technologie**       | **Options**                                                    | **Critères de sélection**                   |
| --------------------- | -------------------------------------------------------------- | ------------------------------------------- |
| **Langage principal** | Node.js (TypeScript) OU Java (Spring Boot) OU Python (FastAPI) | Compétences équipe, performance, écosystème |
| **Framework API**     | Express/NestJS OU Spring Boot OU FastAPI                       | Productivité, type-safety, communauté       |
| **ORM/Query Builder** | Prisma (Node) OU JPA/Hibernate (Java) OU SQLAlchemy (Python)   | Type-safety, migrations, performance        |

**Standards obligatoires (indépendants du langage) :**

- ✅ Tests unitaires : Jest/JUnit/Pytest (≥80% coverage)
- ✅ Linting : ESLint/Checkstyle/Pylint (CI gate)
- ✅ Format code : Prettier/Google Java Format/Black (auto-format)
- ✅ Documentation : OpenAPI 3.0 généré depuis code

#### 6.3.2 Frontend Application

**Choix à valider Cycle 1 avec équipe Frontend :**

| **Technologie**      | **Options**                                            | **Critères de sélection**                          |
| -------------------- | ------------------------------------------------------ | -------------------------------------------------- |
| **Framework**        | React 18+ OU Vue 3+ OU Angular 17+                     | Compétences équipe, performance mobile, écosystème |
| **State Management** | Redux/Zustand (React) OU Pinia (Vue) OU NgRx (Angular) | Complexité app, DX                                 |
| **Styling**          | Tailwind CSS OU Material-UI/Vuetify/Angular Material   | Vitesse développement, cohérence design            |
| **Bundler**          | Vite OU Webpack 5                                      | Performance build, HMR                             |

**Standards obligatoires :**

- ✅ TypeScript (strict mode) pour type-safety
- ✅ Tests : Jest + React Testing Library / Vue Test Utils
- ✅ E2E : Playwright ou Cypress
- ✅ Lighthouse score : Performance ≥90, Accessibility ≥90

#### 6.3.3 Infrastructure et DevOps

**Technologies déjà sélectionnées (Déclaration de Travail) :**

| **Domaine**          | **Technologie**                   | **Justification**                           |
| -------------------- | --------------------------------- | ------------------------------------------- |
| **Cloud Provider**   | AWS                               | Services géospatiaux, écosystème mature     |
| **Conteneurisation** | Docker                            | Standard industrie                          |
| **Orchestration**    | Amazon EKS (Kubernetes)           | Portabilité, scalabilité                    |
| **CI/CD**            | GitHub Actions OU GitLab CI       | Intégration Git, flexibilité                |
| **IaC**              | Terraform                         | Portabilité multi-cloud, langage déclaratif |
| **Monitoring**       | CloudWatch + Prometheus + Grafana | Métriques AWS + custom                      |
| **Tracing**          | AWS X-Ray                         | Intégration native AWS                      |
| **Logs**             | CloudWatch Logs → (Phase 2) ELK   | Coûts optimisés Phase 1                     |

---

## 7. Spécifications pour l'implémentation

### 7.1 Architecture des microservices

#### 7.1.1 Services à développer Phase 1

| **Service**              | **Responsabilité**                           | **APIs exposées**                                                | **Dépendances**                | **Base de données**   |
| ------------------------ | -------------------------------------------- | ---------------------------------------------------------------- | ------------------------------ | --------------------- |
| **Search Service**       | Recherche géolocalisée fournisseurs/produits | `POST /search`, `GET /search/history`                            | Supplier Service               | DynamoDB (geospatial) |
| **Supplier Service**     | Gestion fournisseurs et offres               | `GET/POST/PUT /suppliers`, `GET/POST/PUT /offers`                | -                              | PostgreSQL (RDS)      |
| **Order Service**        | Gestion commandes                            | `GET/POST/PUT /orders`, `GET /orders/{id}`                       | Supplier Service, User Service | PostgreSQL (RDS)      |
| **User Service**         | Gestion utilisateurs                         | `POST /auth/login`, `POST /auth/register`, `GET/PUT /users/{id}` | API Façade Legacy (lecture)    | PostgreSQL (RDS)      |
| **API Façade Legacy**    | Exposition REST du legacy                    | `GET /legacy/users/{id}`, `GET /legacy/orders`                   | Legacy System (VPS)            | N/A (proxy)           |
| **Notification Service** | Emails, notifications push (Phase 2)         | `POST /notifications/email`                                      | SES/SNS                        | DynamoDB (logs)       |

#### 7.1.2 Spécifications par service

**Search Service - Spécifications détaillées**

**Endpoints :**

```
POST /api/v1/search
Request Body:
{
  "latitude": 48.8566,        // Required
  "longitude": 2.3522,        // Required
  "radius": 10,               // Required, km (1-50)
  "categories": ["legumes"],  // Optional, array
  "availableOnly": true,      // Optional, boolean
  "page": 1,                  // Optional, default 1
  "limit": 20                 // Optional, default 20, max 50
}

Response 200:
{
  "results": [
    {
      "supplierId": "supp_123",
      "name": "Ferme Bio Martin",
      "distance": 2.3,        // km, 1 décimale
      "location": {
        "lat": 48.8700,
        "lng": 2.3400
      },
      "offers": [
        {
          "offerId": "off_456",
          "name": "Tomates bio",
          "price": 3.50,
          "unit": "kg",
          "category": "legumes",
          "inStock": true,
          "imageUrl": "https://cdn.foosus.com/..."
        }
      ]
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 20,
    "total": 47,
    "hasMore": true
  },
  "query": { /* echo des params */ }
}
```

**Algorithme de recherche géospatiale :**

1. Utiliser DynamoDB Geohashing pour requête initiale (rayon + marge 20%)
2. Filtrer résultats par distance exacte (calcul Haversine)
3. Appliquer filtres additionnels (catégorie, disponibilité)
4. Trier par distance croissante
5. Paginer (limit/offset)

**Performance target :**

- Latence p95 : <200ms
- Cache Redis : 5 minutes pour requêtes identiques
- Index DynamoDB GSI : `location-geohash` + `category`

**Order Service - Spécifications détaillées**

**Machine à états des commandes :**

```
┌─────────┐
│ DRAFT   │ (panier non confirmé)
└────┬────┘
     │ POST /orders/{id}/confirm
     ▼
┌──────────┐
│CONFIRMED │ (commande validée par client)
└────┬─────┘
     │ (notification fournisseur)
     ▼
┌───────────┐
│ PREPARING │ (en préparation par fournisseur)
└────┬──────┘
     │
     ▼
┌────────┐
│ READY  │ (prête pour livraison/retrait)
└────┬───┘
     │
     ▼
┌───────────┐
│ DELIVERED │ (livrée/récupérée)
└───────────┘

Transitions autorisées :
- DRAFT → CONFIRMED → PREPARING → READY → DELIVERED
- CONFIRMED → CANCELLED (si pas encore PREPARING)
- PREPARING → CANCELLED (avec accord fournisseur)
```

**Règles métier :**

- Une commande DRAFT peut être modifiée à volonté
- Une commande CONFIRMED ne peut plus être modifiée, seulement annulée
- Stock produits réservé lors de passage DRAFT → CONFIRMED
- Stock libéré lors de CANCELLED
- Timeout DRAFT : 24h sans activité → suppression automatique

### 7.2 Base de données - Schémas

#### 7.2.1 DynamoDB - Search Service

**Table : Suppliers (geospatial)**

```
PK: supplier_id (String)
SK: METADATA

Attributes:
- name (String)
- description (String)
- location_lat (Number, index)
- location_lng (Number, index)
- location_geohash (String, GSI PK)  // Precision 7 (~150m)
- address (String)
- created_at (String, ISO8601)
- updated_at (String, ISO8601)

GSI: LocationIndex
- PK: location_geohash
- SK: supplier_id
```

**Table : Offers (produits)**

```
PK: supplier_id (String)
SK: offer_id (String)

Attributes:
- name (String)
- description (String)
- price (Number, Decimal)
- unit (String)  // kg, piece, litre
- category (String, GSI PK)
- in_stock (Boolean)
- stock_quantity (Number)
- image_url (String)
- created_at (String)
- updated_at (String)

GSI: CategoryIndex
- PK: category
- SK: supplier_id#offer_id
```

#### 7.2.2 PostgreSQL - Order Service

**Schema SQL :**

```sql
-- Table: orders
CREATE TABLE orders (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  order_number VARCHAR(50) UNIQUE NOT NULL, -- ORD-20251022-00123
  user_id UUID NOT NULL,
  supplier_id UUID NOT NULL,
  status VARCHAR(20) NOT NULL CHECK (status IN (
    'DRAFT', 'CONFIRMED', 'PREPARING', 'READY', 'DELIVERED', 'CANCELLED'
  )),
  total_amount DECIMAL(10, 2) NOT NULL,
  currency VARCHAR(3) DEFAULT 'EUR',
  payment_method VARCHAR(20) DEFAULT 'CASH_ON_DELIVERY',
  delivery_address JSONB,  -- {street, city, zipCode, country}
  notes TEXT,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW(),
  confirmed_at TIMESTAMP,
  delivered_at TIMESTAMP,
  cancelled_at TIMESTAMP
);

CREATE INDEX idx_orders_user_id ON orders(user_id);
CREATE INDEX idx_orders_supplier_id ON orders(supplier_id);
CREATE INDEX idx_orders_status ON orders(status);
CREATE INDEX idx_orders_created_at ON orders(created_at DESC);

-- Table: order_items
CREATE TABLE order_items (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  order_id UUID NOT NULL REFERENCES orders(id) ON DELETE CASCADE,
  offer_id UUID NOT NULL,
  offer_name VARCHAR(255) NOT NULL,  -- Snapshot du nom
  quantity INTEGER NOT NULL CHECK (quantity > 0),
  unit_price DECIMAL(10, 2) NOT NULL,
  subtotal DECIMAL(10, 2) NOT NULL,
  created_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_order_items_order_id ON order_items(order_id);

-- Table: order_status_history (audit trail)
CREATE TABLE order_status_history (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  order_id UUID NOT NULL REFERENCES orders(id) ON DELETE CASCADE,
  from_status VARCHAR(20),
  to_status VARCHAR(20) NOT NULL,
  changed_by UUID,  -- user_id or system
  changed_at TIMESTAMP DEFAULT NOW(),
  notes TEXT
);

CREATE INDEX idx_order_history_order_id ON order_status_history(order_id);
```

#### 7.2.3 PostgreSQL - User Service

**Schema SQL :**

```sql
-- Table: users
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email VARCHAR(255) UNIQUE NOT NULL,
  password_hash VARCHAR(255) NOT NULL,  -- bcrypt
  user_type VARCHAR(20) NOT NULL CHECK (user_type IN ('CONSUMER', 'SUPPLIER', 'ADMIN')),
  first_name VARCHAR(100),
  last_name VARCHAR(100),
  phone VARCHAR(20),
  email_verified BOOLEAN DEFAULT FALSE,
  email_verification_token VARCHAR(255),
  password_reset_token VARCHAR(255),
  password_reset_expires TIMESTAMP,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW(),
  last_login_at TIMESTAMP
);

CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_users_type ON users(user_type);

-- Table: user_addresses
CREATE TABLE user_addresses (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID NOT NULL REFERENCES users(id) ON DELETE CASCADE,
  address_type VARCHAR(20) DEFAULT 'DELIVERY', -- DELIVERY, BILLING
  street VARCHAR(255) NOT NULL,
  city VARCHAR(100) NOT NULL,
  zip_code VARCHAR(20) NOT NULL,
  country VARCHAR(2) DEFAULT 'FR',
  latitude DECIMAL(10, 8),
  longitude DECIMAL(11, 8),
  is_default BOOLEAN DEFAULT FALSE,
  created_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_addresses_user_id ON user_addresses(user_id);

-- Table: supplier_profiles (données étendues fournisseurs)
CREATE TABLE supplier_profiles (
  user_id UUID PRIMARY KEY REFERENCES users(id) ON DELETE CASCADE,
  business_name VARCHAR(255) NOT NULL,
  description TEXT,
  business_hours JSONB,  -- {monday: "8h-18h", ...}
  certifications TEXT[],  -- ["Bio", "Label Rouge"]
  avatar_url VARCHAR(500),
  cover_image_url VARCHAR(500),
  rating DECIMAL(2, 1),  -- 0.0 - 5.0
  total_reviews INTEGER DEFAULT 0,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);
```

### 7.3 APIs REST - Conventions

#### 7.3.1 Standards de nommage

**URLs :**

- Ressources au pluriel : `/api/v1/orders`, `/api/v1/suppliers`
- Identifiants dans le path : `/api/v1/orders/{orderId}`
- Actions via verbes HTTP, pas dans URL : `POST /orders/{id}/confirm` (acceptable), pas `/orders/confirm/{id}`
- Query params pour filtres : `GET /orders?status=CONFIRMED&page=2`
- Versioning dans URL : `/api/v1/`, `/api/v2/`

**Verbes HTTP :**

- `GET` : Lecture, idempotent, cacheable
- `POST` : Création, non-idempotent (sauf avec idempotency-key)
- `PUT` : Remplacement complet, idempotent
- `PATCH` : Modification partielle, idempotent
- `DELETE` : Suppression, idempotent

#### 7.3.2 Format des réponses

**Succès (2xx) :**

```json
{
  "data": {
    /* objet ou array */
  },
  "meta": {
    "requestId": "req_abc123",
    "timestamp": "2025-10-22T14:30:00Z"
  }
}
```

**Pagination :**

```json
{
  "data": [
    /* items */
  ],
  "pagination": {
    "page": 2,
    "limit": 20,
    "total": 157,
    "totalPages": 8,
    "hasMore": true,
    "nextPage": "/api/v1/orders?page=3"
  }
}
```

**Erreurs (4xx, 5xx) :**

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Les données fournies sont invalides",
    "details": [
      {
        "field": "email",
        "message": "Format email invalide"
      }
    ],
    "requestId": "req_abc123",
    "timestamp": "2025-10-22T14:30:00Z"
  }
}
```

**Codes HTTP standard :**

- `200 OK` : Succès GET/PUT/PATCH
- `201 Created` : Succès POST (création)
- `204 No Content` : Succès DELETE
- `400 Bad Request` : Validation failed
- `401 Unauthorized` : Authentication required
- `403 Forbidden` : Authenticated but not authorized
- `404 Not Found` : Ressource inexistante
- `409 Conflict` : État invalide (ex: commande déjà confirmée)
- `422 Unprocessable Entity` : Business rule violation
- `429 Too Many Requests` : Rate limit exceeded
- `500 Internal Server Error` : Erreur serveur
- `503 Service Unavailable` : Service temporairement down

#### 7.3.3 Headers obligatoires

**Requêtes :**

```
Authorization: Bearer <jwt_token>
Content-Type: application/json
Accept: application/json
X-Request-ID: <uuid>  // Correlation ID
X-Client-Version: 1.2.3  // Version app cliente
```

**Réponses :**

```
Content-Type: application/json
X-Request-ID: <uuid>  // Echo du request ID
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 847
X-RateLimit-Reset: 1635174000
Cache-Control: no-cache (ou max-age=300 si cacheable)
```

### 7.4 Authentification et autorisation

#### 7.4.1 JWT Token Structure

**Access Token (durée: 24h) :**

```json
{
  "sub": "user_123abc", // User ID
  "email": "user@example.com",
  "type": "CONSUMER", // CONSUMER | SUPPLIER | ADMIN
  "iat": 1635170400, // Issued at
  "exp": 1635256800, // Expiration (24h)
  "jti": "token_xyz789" // Token ID (pour révocation)
}
```

**Refresh Token (durée: 7 jours) :**

- Stocké en httpOnly cookie
- Utilisé pour obtenir un nouveau access token
- Révoqué lors de logout

#### 7.4.2 Flow d'authentification

```
1. POST /auth/login {email, password}
   ← 200 {accessToken, refreshToken (cookie)}

2. Requêtes authentifiées:
   GET /api/v1/orders
   Header: Authorization: Bearer <accessToken>
   ← 200 {data}

3. Token expiré (401):
   ← 401 {error: "TOKEN_EXPIRED"}

4. Refresh token:
   POST /auth/refresh (refreshToken auto depuis cookie)
   ← 200 {accessToken, new refreshToken}

5. Logout:
   POST /auth/logout
   ← 204 (révocation tokens)
```

#### 7.4.3 Permissions par type d'utilisateur

| **Action**              | **CONSUMER**              | **SUPPLIER** | **ADMIN**   |
| ----------------------- | ------------------------- | ------------ | ----------- |
| Rechercher fournisseurs | ✅                        | ✅           | ✅          |
| Créer commande          | ✅                        | ❌           | ✅          |
| Voir ses commandes      | ✅ (propres)              | ✅ (reçues)  | ✅ (toutes) |
| Modifier commande DRAFT | ✅ (propre)               | ❌           | ✅          |
| Annuler commande        | ✅ (propre, si CONFIRMED) | ✅ (reçue)   | ✅          |
| Créer offre alimentaire | ❌                        | ✅ (propre)  | ✅          |
| Modifier offre          | ❌                        | ✅ (propre)  | ✅          |
| Gérer utilisateurs      | ❌                        | ❌           | ✅          |

---

## 8. Standards pour l'implémentation

### 8.1 Standards de code

#### 8.1.1 Conventions de nommage

**Général :**

- Variables/fonctions : `camelCase` (JavaScript/TypeScript/Java)
- Classes/Composants : `PascalCase`
- Constantes : `UPPER_SNAKE_CASE`
- Fichiers : `kebab-case.ts` ou `PascalCase.tsx` (composants React)
- Base de données : `snake_case` (tables, colonnes)

**Spécifique :**

- Booleans : `isActive`, `hasPermission`, `canEdit`
- Handlers : `handleClick`, `onSubmit`
- Hooks (React) : `useCustomHook`
- Services/Classes : Noms descriptifs (`OrderService`, `PaymentProcessor`)

#### 8.1.2 Structure de projet

**Backend Service (exemple Node.js/TypeScript) :**

```
src/
├── controllers/     # HTTP handlers
├── services/        # Business logic
├── repositories/    # Data access layer
├── models/          # Domain entities, DTOs
├── middlewares/     # Auth, validation, error handling
├── utils/           # Helpers, formatters
├── config/          # Configuration (DB, AWS, etc.)
├── routes/          # Route definitions
└── app.ts           # Entry point

tests/
├── unit/
├── integration/
└── e2e/

docs/
├── api/             # OpenAPI specs
└── architecture/    # ADRs
```

**Frontend Application (exemple React) :**

```
src/
├── components/      # Composants réutilisables
│   ├── common/      # Boutons, inputs, etc.
│   └── features/    # Composants métier
├── pages/           # Pages/routes
├── services/        # API clients
├── hooks/           # Custom React hooks
├── store/           # State management (Redux/Zustand)
├── utils/           # Helpers
├── types/           # TypeScript types/interfaces
├── assets/          # Images, fonts
└── App.tsx          # Entry point
```

#### 8.1.3 Documentation code

**Fonctions publiques :**

````typescript
/**
 * Recherche des fournisseurs par géolocalisation.
 *
 * @param latitude - Latitude du point de recherche (WGS84)
 * @param longitude - Longitude du point de recherche (WGS84)
 * @param radius - Rayon de recherche en kilomètres (1-50)
 * @param options - Options de filtrage additionnelles
 * @returns Liste paginée de fournisseurs avec distance
 * @throws {ValidationError} Si les coordonnées sont invalides
 * @throws {ServiceUnavailableError} Si le service de géolocalisation est down
 *
 * @example
 * ```typescript
 * const results = await searchSuppliers(48.8566, 2.3522, 10, {
 *   categories: ['legumes'],
 *   availableOnly: true
 * });
 * ```
 */
export async function searchSuppliers(
  latitude: number,
  longitude: number,
  radius: number,
  options?: SearchOptions
): Promise<PaginatedResults<Supplier>> {
  // Implementation
}
````

### 8.2 Standards de tests

#### 8.2.1 Pyramide de tests

```
         /\
        /  \    E2E Tests (5%)
       /____\   - Scénarios utilisateurs critiques
      /      \
     /        \ Integration Tests (25%)
    /__________\ - Contrats APIs, DB interactions
   /            \
  /              \ Unit Tests (70%)
 /________________\ - Fonctions, classes, composants isolés
```

**Objectifs de couverture :**

- Tests unitaires : ≥80% coverage
- Tests d'intégration : 100% endpoints critiques (P0)
- Tests E2E : Scénarios principaux (recherche, commande)

#### 8.2.2 Conventions de tests

**Nommage :**

```typescript
describe("SearchService", () => {
  describe("searchSuppliers", () => {
    it("should return suppliers within radius", async () => {
      // Arrange
      const latitude = 48.8566;
      const longitude = 2.3522;
      const radius = 10;

      // Act
      const result = await searchService.searchSuppliers(
        latitude,
        longitude,
        radius
      );

      // Assert
      expect(result.results).toHaveLength(5);
      expect(result.results[0].distance).toBeLessThanOrEqual(10);
    });

    it("should throw ValidationError for invalid coordinates", async () => {
      await expect(searchService.searchSuppliers(200, 300, 10)).rejects.toThrow(
        ValidationError
      );
    });
  });
});
```

**Standards :**

- Pattern AAA : Arrange, Act, Assert
- Tests isolés : pas de dépendances entre tests
- Mocks/Stubs pour dépendances externes
- Tests déterministes : pas de randomness, pas de dates dynamiques
- Cleanup systématique : afterEach/afterAll

#### 8.2.3 Tests de contrat (API)

**Tous les endpoints doivent avoir :**

```typescript
// Contract test example (Pact or custom)
describe("POST /api/v1/search - Contract", () => {
  it("should match OpenAPI specification", async () => {
    const response = await request(app)
      .post("/api/v1/search")
      .send(validSearchRequest)
      .expect(200);

    // Validation against OpenAPI schema
    expect(response.body).toMatchSchema(schemas.SearchResponse);
  });

  it("should return 400 for invalid radius", async () => {
    const response = await request(app)
      .post("/api/v1/search")
      .send({ ...validSearchRequest, radius: 100 })
      .expect(400);

    expect(response.body.error.code).toBe("VALIDATION_ERROR");
  });
});
```

### 8.3 Standards CI/CD

#### 8.3.1 Pipeline stages

```yaml
# Pipeline template (GitHub Actions / GitLab CI)

stages:
  - lint        # Code style
  - test        # Unit + Integration tests
  - build       # Docker image
  - scan        # Security scan
  - deploy-dev  # Auto deploy to dev
  - test-e2e    # E2E tests on dev
  - deploy-stg  # Manual approval
  - deploy-prod # Manual approval

# Quality gates (bloquants):
- Linting: must pass
- Tests: ≥80% coverage, 0 failures
- Security: 0 critical vulnerabilities
- Build: success
```

#### 8.3.2
