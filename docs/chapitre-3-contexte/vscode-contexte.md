# :material-microsoft-visual-studio-code: VS Code — Configuration du Contexte Projet

<span class="badge-vscode">VS Code</span> <span class="badge-intermediate">Intermédiaire</span>

## Présentation
Ce guide vous montre comment structurer votre projet VS Code pour donner à Copilot le meilleur contexte possible. Un projet bien structuré = des suggestions plus pertinentes.

---

## Structure du dossier .github/

Le dossier `.github/` à la racine de votre projet est le hub central de personnalisation Copilot :

```
mon-projet/
├── .github/
│   ├── copilot-instructions.md          ← Instructions globales
│   ├── instructions/                    ← Instructions ciblées
│   │   ├── typescript.instructions.md
│   │   └── tests.instructions.md
│   ├── prompts/                         ← Prompts réutilisables
│   │   ├── code-review.prompt.md
│   │   └── generate-tests.prompt.md
│   ├── agents/                          ← Agents custom
│   │   └── documentation-writer.agent.md
│   └── skills/                          ← Skills de connaissance
│       └── domain-model/
│           └── SKILL.md
├── .copilotignore                       ← Exclusions Copilot
├── .vscode/
│   ├── settings.json                    ← Settings Copilot du workspace
│   └── extensions.json                  ← Extensions recommandées
└── src/
```

---

## Le fichier .copilotignore

`.copilotignore` fonctionne comme `.gitignore` mais pour exclure des fichiers du contexte Copilot.

### Syntaxe

```gitignore
# .copilotignore — Exclusions du contexte Copilot

# Fichiers sensibles
.env
.env.*
*.env
secrets.json
*credentials*
*secret*

# Données de test volumineuses
test-data/
fixtures/large-*.json
seeds/

# Fichiers générés (Copilot n'a pas besoin de les voir)
dist/
build/
coverage/
*.min.js
*.bundle.js

# Documentation générée automatiquement
docs/generated/
api-doc/

# Dépendances (trop volumineuses)
node_modules/
vendor/

# Données sensibles métier
data/clients/
data/financial/
reports/confidential/
```

!!! warning "`.copilotignore` vs `.gitignore`"
    Ces deux fichiers sont indépendants. Un fichier dans `.gitignore` n'est pas automatiquement exclu de Copilot, et vice-versa. Vous pouvez avoir des fichiers versionnés avec Git mais exclus du contexte Copilot.

---

## Configuration du workspace (.code-workspace)

Un fichier `.code-workspace` permet d'ouvrir plusieurs dossiers ensemble dans VS Code — Copilot utilise tous ces dossiers comme contexte :

```json
// mon-projet.code-workspace
{
    "folders": [
        {
            "name": "Backend",
            "path": "./backend"
        },
        {
            "name": "Frontend",
            "path": "./frontend"
        },
        {
            "name": "Shared Types",
            "path": "./shared"
        }
    ],
    "settings": {
        "github.copilot.enable": {
            "*": true,
            "dotenv": false,
            "plaintext": false
        },
        "github.copilot.chat.localeOverride": "fr"
    },
    "extensions": {
        "recommendations": [
            "GitHub.copilot",
            "GitHub.copilot-chat"
        ]
    }
}
```

!!! tip "Avantage du workspace multi-dossiers"
    Avec un workspace multi-dossiers, Copilot peut voir les types partagés entre backend et frontend simultanément — ce qui améliore considérablement la cohérence des suggestions.

---

## Exemples de structures de projets optimisées

### Projet Node.js / TypeScript

```
my-api/
├── .github/
│   ├── copilot-instructions.md
│   └── instructions/
│       ├── typescript.instructions.md
│       └── tests.instructions.md
├── .copilotignore
├── .vscode/
│   └── settings.json
├── src/
│   ├── controllers/          ← Handlers HTTP
│   │   └── UserController.ts
│   ├── services/             ← Logique métier
│   │   └── UserService.ts
│   ├── repositories/         ← Accès données
│   │   └── UserRepository.ts
│   ├── models/               ← Types et interfaces
│   │   └── User.ts
│   ├── middlewares/          ← Middlewares Express
│   ├── utils/                ← Fonctions utilitaires
│   └── errors/               ← Classes d'erreurs custom
├── tests/
│   ├── unit/
│   └── integration/
├── package.json              ← Copilot lit les dépendances
├── tsconfig.json             ← Copilot comprend la config TS
└── README.md                 ← Important pour le contexte !
```

**`copilot-instructions.md` adapté :**
```markdown
# Instructions Copilot — my-api

Stack : Node.js 20, TypeScript 5.3, Express 4, PostgreSQL 15, Prisma ORM, Jest.

Architecture :
- controllers/ : ne contiennent que la gestion HTTP (pas de logique métier)
- services/ : toute la logique métier ici
- repositories/ : uniquement les accès DB (via Prisma)
- models/ : interfaces TypeScript et types Zod

Conventions :
- TypeScript strict, pas de `any`
- Gestion d'erreurs : classes dans `src/errors/`, jamais `throw new Error("message")`
- Tests : Jest, AAA pattern (Arrange/Act/Assert), coverage > 80%
```

### Projet React / TypeScript

```
my-app/
├── .github/
│   ├── copilot-instructions.md
│   └── instructions/
│       ├── react.instructions.md     ← Composants
│       └── state.instructions.md     ← Redux/Zustand
├── .copilotignore
├── src/
│   ├── components/
│   │   ├── shared/           ← Composants réutilisables
│   │   └── pages/            ← Composants de page
│   ├── hooks/                ← Custom hooks
│   ├── store/                ← State management (Redux)
│   ├── api/                  ← Appels API (Axios)
│   ├── types/                ← Types TypeScript partagés
│   └── utils/                ← Fonctions utilitaires
├── public/
├── package.json
├── tsconfig.json
└── tailwind.config.js        ← Copilot comprend votre config Tailwind
```

### Projet Python

```
my-python-project/
├── .github/
│   └── copilot-instructions.md
├── .copilotignore
├── src/
│   └── my_project/
│       ├── __init__.py
│       ├── models/           ← Modèles de données
│       ├── services/         ← Logique métier
│       ├── api/              ← Endpoints FastAPI/Django
│       └── utils/            ← Utilitaires
├── tests/
│   ├── unit/
│   └── integration/
├── pyproject.toml            ← Copilot lit les dépendances et config
├── requirements.txt          ← ou requirements/dev.txt, prod.txt
├── .python-version           ← Version Python pour Copilot
└── README.md
```

---

## Bonnes pratiques pour améliorer le contexte

### 1. Un README.md informatif

```markdown
# Mon Projet

## Description
API REST pour [description précise].

## Stack
- Language : TypeScript 5
- Framework : Express 4
- Base de données : PostgreSQL 15 avec Prisma ORM
- Tests : Jest + Supertest

## Architecture
[Décrire les couches et leur rôle]

## Conventions de code
[Ou lien vers CONTRIBUTING.md]
```

### 2. Commentaires de fichier (en tête)

```typescript
/**
 * UserService — Gestion du cycle de vie des utilisateurs
 * 
 * Ce service gère : création, authentification, mise à jour du profil,
 * désactivation de compte et gestion des rôles.
 * 
 * Dépendances : UserRepository, EmailService, AuditLogger
 */
export class UserService {
```

### 3. Fichiers index.ts / index.py bien exportés

```typescript
// src/services/index.ts — Tableau de bord des services disponibles
export { UserService } from './UserService';
export { ProductService } from './ProductService';
export { OrderService } from './OrderService';
// Copilot comprend immédiatement quels services existent
```

### 4. Variables d'environnement documentées (sans les valeurs)

```typescript
// src/config/env.ts — Configuration des variables d'environnement
export const config = {
    database: {
        url: process.env.DATABASE_URL!,    // postgresql://user:pass@host/db
        poolSize: Number(process.env.DB_POOL_SIZE ?? '10'),
    },
    auth: {
        jwtSecret: process.env.JWT_SECRET!,  // Min 256 bits
        jwtExpiry: process.env.JWT_EXPIRY ?? '24h',
    },
};
```

---

## Optimisation des onglets ouverts

Copilot utilise vos onglets ouverts comme contexte supplémentaire. Organisez vos onglets stratégiquement :

| Situation | Onglets recommandés à garder ouverts |
|-----------|-------------------------------------|
| Travail sur un service | Interface/type, Repository, Service, Tests du service |
| Création d'un endpoint | Controller pattern existant, Service correspondant, types de réponse |
| Debugging | Fichier avec l'erreur, logs, fichier de config |
| Refactoring | Fichier source, tests, et les fichiers qui l'importent |

---

## Prochaines étapes

- [IntelliJ — Contexte projet](intellij-contexte.md) — Équivalents pour IntelliJ
- [Comparaison contexte](comparaison-contexte.md) — Différences entre les deux IDEs
- [Bonnes pratiques](../chapitre-4-bonnes-pratiques/index.md) — Aller plus loin

