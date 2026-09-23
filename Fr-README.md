🧪 API Testing avec Postman – Système de gestion des utilisateurs

# Postman 
# REST API
# JavaScript
# Newman
# QA

## 📌 Présentation du projet

Ce projet est un projet de test d'API REST réalisé dans le cadre d'un portfolio QA afin de démontrer des compétences pratiques en matière de tests d'API avec Postman.

Le projet se concentre sur le test d'une API de gestion des utilisateurs et couvre notamment l'authentification, les opérations CRUD, les tests positifs et négatifs, les assertions automatisées, l'exécution des tests et le reporting.

L'objectif est de simuler un workflow QA réaliste pour une application basée sur une API.

---

## 🎯 Objectifs du projet

Les principaux objectifs de ce projet sont les suivants :

- Analyser les endpoints REST et les exigences
- Concevoir des scénarios et cas de test API
- Tester les workflows d'authentification
- Valider les opérations CRUD
- Effectuer des tests positifs et négatifs
- Valider les codes de statut HTTP
- Valider la structure des réponses JSON
- Valider les données retournées
- Implémenter des assertions automatisées avec JavaScript
- Utiliser les variables d'environnement Postman
- Exécuter les collections avec Postman Collection Runner
- Exécuter les tests API avec Newman
- Générer des rapports d'exécution
- Documenter les anomalies détectées pendant les tests
- Maintenir la traçabilité entre exigences, scénarios de test, cas de test et anomalies

---
## Résultats de l'exécution

| Metric | Result |
|---|---:|
| Test Cases | 30 |
| Executed | 30 |
| PASS | 28 |
| FAIL | 2 |
| Pass Rate | 93.3% |
| Execution Coverage | 100% |
| Jira Defects | 2 |
| Newman Assertions | 80 |

---

### Key Defects

- **SCRUM-26** — Invalid credentials return HTTP 200 and a token
- **SCRUM-27** — Request without API key returns HTTP 200

---

## 🧩 Application sous test

Ce projet utilise ReqRes, une API REST publique conçue à des fins de test et de démonstration.

L'API permet notamment de pratiquer :

- L'authentification
- La récupération des utilisateurs
- La création des utilisateurs
- La modification des utilisateurs
- La suppression des utilisateurs
- La gestion des erreurs

### API

```text 
ReqRes
https://reqres.in
```

«Remarque : ReqRes est une API publique de démonstration. Son comportement et ses exigences d'authentification peuvent évoluer au fil du temps. Les résultats présentés dans ce repository seront basés sur le comportement réellement observé lors de l'exécution des tests.»

---

## 🛠️ Outils et technologies

| Outil / Technologie | Utilisation |
|---|---|
| Postman | Envoi des requêtes API et automatisation des tests |
| JavaScript | Scripts de test et assertions Postman |
| Newman | Exécution des collections en ligne de commande |
| GitHub | Gestion des versions et documentation du projet |
| Markdown | Documentation QA |
| REST API | Interface de l'application sous test |
| JSON | Données des requêtes et réponses |

---

## 🔐 Tests d'authentification

Les tests d'authentification couvrent notamment les scénarios suivants :

- Connexion avec des identifiants valides
- Connexion avec des identifiants invalides
- Connexion sans informations d'identification
- Données d'authentification invalides
- Validation du token
- Validation des réponses liées à l'authentification

Exemple de workflow :

```text 
Identifiants valides
       ↓
POST /api/login
       ↓
Authentification
       ↓
Token
```
---

## 👤 Tests de gestion des utilisateurs – CRUD

Le projet couvre les principales opérations CRUD :

| Opération | Méthode HTTP | Objectif |
|---|---|---|
| Create | POST | Créer un utilisateur |
| Read | GET | Récupérer les utilisateurs |
| Update | PUT | Modifier un utilisateur |
| Partial Update | PATCH | Modifier partiellement un utilisateur |
| Delete | DELETE | Supprimer un utilisateur |

---

## 🧪 Approche de test

Les approches et techniques de test suivantes sont appliquées lorsque cela est pertinent :

### Tests positifs

Des données valides et des actions attendues sont utilisées afin de vérifier le comportement normal de l'API.

### Tests négatifs

Des données invalides, des champs manquants et des requêtes incorrectes sont utilisés afin de vérifier la gestion des erreurs.

### Analyse des valeurs limites

Les valeurs situées autour des limites pertinentes sont testées lorsque cela est applicable.

### Partitionnement en classes d'équivalence

Les données d'entrée sont divisées en classes représentatives valides et invalides.

### Tests fonctionnels

Les fonctionnalités de l'API sont validées par rapport au comportement attendu.

### Tests exploratoires

Des comportements supplémentaires de l'API et des risques potentiels sont explorés au-delà des cas de test prédéfinis.

### Tests de régression

Les fonctionnalités API précédemment testées peuvent être réexécutées après des modifications.

### Retest

Les anomalies précédemment signalées peuvent être testées à nouveau après la correction fournie par l'équipe de développement.

---

## 📋 Couverture des tests

Le projet est prévu pour couvrir :

- Authentification
- Récupération des utilisateurs
- Création des utilisateurs
- Modification des utilisateurs
- Modification partielle des utilisateurs
- Suppression des utilisateurs
- Identifiants utilisateur invalides
- Champs manquants dans les requêtes
- Identifiants de connexion invalides
- Endpoints invalides
- Validation des réponses
- Validation des codes de statut
- Validation de la structure JSON
- Validation du temps de réponse
- Validation de l'authentification

---

## 🤖 Automatisation des tests avec Postman

Les tests Postman sont implémentés à l'aide d'assertions JavaScript.

Exemple :

```text 
pm.test("Le code de statut est 200", function () {
    pm.response.to.have.status(200);
});
```

Validation de la réponse :

```text 
pm.test("La réponse contient la propriété data", function () {
    const response = pm.response.json();

    pm.expect(response).to.have.property("data");
});
```

Validation du temps de réponse :

```text 
pm.test("Le temps de réponse est inférieur à 1000 ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(1000);
});
```

---

## 🌍 Variables d'environnement

L'environnement Postman utilise notamment les variables suivantes :

| Variable | Purpose |
|---|---|
| `base_url` | Base API URL |
| `api_key` | API authentication |
| `user_id` | User identifier |
| `created_user_id` | Created user identifier |
| `token` | Authentication token |
| `environment` | Test environment |

Exemple :

``` text 
{{base_url}}/api/users/{{user_id}}
```

Les valeurs sensibles telles que les clés API ne sont pas enregistrées dans le repository public.

---

## 🔄 Workflow API de bout en bout

Le projet comprend un workflow de gestion des utilisateurs de bout en bout :
```text 
Connexion
  ↓
Récupération des utilisateurs
  ↓
Récupération d'un utilisateur
  ↓
Création d'un utilisateur
  ↓
Modification d'un utilisateur
  ↓
Modification partielle
  ↓
Suppression d'un utilisateur

Ce workflow permet de démontrer comment plusieurs requêtes API peuvent être combinées afin de vérifier un parcours fonctionnel complet.
```

---

## 📊 Exécution des tests

L'exécution des tests est réalisée avec :

- Postman
- Postman Collection Runner
- Newman

Chaque exécution peut enregistrer les informations suivantes :

- ID du cas de test
- Résultat attendu
- Résultat réel
- Statut
- Date d'exécution
- Environnement
- Preuve / Evidence
- ID de l'anomalie associée

Les statuts d'exécution possibles sont :
```text 
PASS
FAIL
BLOCKED
NOT RUN
```
---

## 🐞 Gestion des anomalies

Les anomalies identifiées pendant les tests sont documentées à l'aide d'un format structuré de rapport de bug.

Chaque anomalie peut contenir :

- ID du bug
- Résumé
- Endpoint
- Environnement
- Prérequis
- Étapes pour reproduire
- Résultat attendu
- Résultat réel
- Sévérité
- Priorité
- Evidence
- Statut

---

## 📈 Reporting des tests

Newman est utilisé pour exécuter la collection Postman depuis la ligne de commande et générer les rapports d'exécution.

Exemple :
```text 
newman run User-Management-API.postman_collection.json
```

Génération d'un rapport HTML :
```text 
newman run User-Management-API.postman_collection.json \
-r cli,html
```
Les résultats finaux de l'exécution seront documentés dans le répertoire :

09-Reports/

---

📁 Structure du projet
```text 
qa-api-testing-postman/
│
├── README.md
│
├── 01-API-Analysis/
│   ├── API-Documentation.md
│   ├── Endpoint-Matrix.md
│   └── API-Risks.md
│
├── 02-Test-Plan/
│   └── Test-Plan.md
│
├── 03-Test-Scenarios/
│   └── Test-Scenarios.md
│
├── 04-Test-Cases/
│   └── Test-Cases.md
│
├── 05-Test-Data/
│   └── Test-Data.md
│
├── 06-Postman/
│   ├── Collections/
│   │   └── User-Management-API.postman_collection.json
│   │
│   └── Environments/
│       └── QA-API-Environment.postman_environment.json
│
├── 07-Test-Execution/
│   └── Test-Execution.md
│
├── 08-Bug-Reports/
│   └── Bug-Reports.md
│
├── 09-Reports/
│   ├── Newman-Report.html
│   └── Execution-Summary.md
│
├── 10-Evidence/
│   └── README.md
│
└── 11-Test-Summary/
    └── Test-Summary.md
```
---

## 🔗 Traçabilité

La traçabilité est maintenue tout au long du processus de test :
```text 
Exigence
     ↓
Scénario de test
     ↓
Cas de test
     ↓
Requête Postman
     ↓
Exécution du test
     ↓
Anomalie
```
Cette approche permet d'avoir une visibilité sur la couverture des tests et sur l'impact des anomalies identifiées.

---

## 🎓 Compétences démontrées

Ce projet permet de démontrer des compétences pratiques en :

- API Testing
- REST API
- Postman
- Méthodes HTTP
- JSON
- Codes de statut HTTP
- Tests d'authentification
- Tests CRUD
- Tests positifs
- Tests négatifs
- Tests fonctionnels
- Tests exploratoires
- Conception de tests
- Assertions JavaScript
- Variables d'environnement
- Bases de l'automatisation des tests
- Collection Runner
- Newman
- Analyse de documentation API
- Gestion des anomalies
- Reporting des tests
- GitHub
- Documentation QA

---

## 👨‍💻 Auteur
### Radjibou IBRAHIM 
QA Junior / Manual QA Tester

Ce projet fait partie de mon portfolio QA et démontre mes compétences pratiques en tests d'API avec Postman et Newman.
