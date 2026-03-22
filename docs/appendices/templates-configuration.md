# Templates de Configuration

Collection de templates prêts à l'emploi pour démarrer rapidement. Copiez-collez et adaptez selon votre projet.

---

## Profils VS Code `settings.json`

### Profil Débutant

```json
{
    "github.copilot.enable": {
        "*": true
    },
    "editor.inlineSuggest.enabled": true,
    "github.copilot.editor.enableAutoCompletions": true
}
```

### Profil Expert (toutes les fonctionnalités)

```json
{
    "github.copilot.enable": {
        "*": true,
        "markdown": true,
        "yaml": false,
        "dotenv": false
    },
    "editor.inlineSuggest.enabled": true,
    "github.copilot.editor.enableAutoCompletions": true,
    "github.copilot.chat.codeGeneration.useInstructionFiles": true,
    "github.copilot.chat.localeOverride": "fr",
    "github.copilot.renameSuggestions.triggerAutomatically": true
}
```

### Profil Équipe (conventions partagées)

```json
{
    "github.copilot.enable": {
        "*": true,
        "markdown": false,
        "plaintext": false
    },
    "editor.inlineSuggest.enabled": true,
    "github.copilot.chat.codeGeneration.useInstructionFiles": true,
    "github.copilot.chat.codeGeneration.instructions": [
        {
            "file": ".github/copilot-instructions.md"
        }
    ]
}
```

### Profil Minimaliste (suggestions à la demande)

```json
{
    "github.copilot.enable": {
        "*": true
    },
    "editor.inlineSuggest.enabled": false,
    "github.copilot.editor.enableAutoCompletions": false
}
```

> Avec ce profil, déclenchez manuellement avec ++alt+backslash++

---

## Templates `.github/copilot-instructions.md`

### Template TypeScript/React

```markdown
---
applyTo: '**'
---

# GitHub Copilot — Instructions projet

## Stack technique
- TypeScript strict (noImplicitAny, strictNullChecks)
- React 18 avec hooks fonctionnels uniquement
- State: Zustand
- API: TanStack Query v5
- Styling: Tailwind CSS
- Tests: Jest + React Testing Library

## Conventions de code
- Composants: functional components, named exports
- Props: interface Props (jamais type Props)
- Fichier: un composant = un fichier du même nom
- Hooks custom: préfixe `use` obligatoire

## À éviter
- class components
- default exports pour les composants
- any sans justification dans un commentaire
- mutations directes du state
```

### Template Java/Spring Boot

```markdown
---
applyTo: 'src/**/*.java'
---

# Conventions Java

## Stack
- Java 21, Spring Boot 3.2
- Spring Data JPA, MapStruct
- Jakarta Validation
- JUnit 5 + Mockito + AssertJ

## Conventions
- Injection par constructeur (jamais @Autowired sur champ)
- DTOs sont des records Java
- Une interface + une implémentation par service
- Exceptions métier spécifiques (ex: UserNotFoundException)
- Jamais d'entité JPA retournée directement dans les controllers

## Nommage
- Controllers: UserController (suffixe Controller)
- Services: UserServiceImpl (suffixe Impl pour l'implémentation)
- Repositories: UserRepository (suffixe Repository)
- DTOs: CreateUserRequest, UserResponse, UpdateUserRequest
```

### Template Python/FastAPI

```markdown
---
applyTo: '**/*.py'
---

# Conventions Python

## Stack
- Python 3.11+, FastAPI, Pydantic v2
- SQLAlchemy 2.0 (style Mapped[])
- pytest avec pytest-asyncio
- mypy strict, Ruff, Black

## Conventions
- Annotations de type obligatoires sur toutes les fonctions publiques
- Pydantic v2 : utiliser model_validator et field_validator (pas v1 @validator)
- SQLAlchemy : Mapped[type] et mapped_column() (style 2.0)
- Routes FastAPI : toutes async
- HTTPException pour les erreurs HTTP

## Interdits
- import *
- except Exception sans re-raise ou log
- variables sans type hint (data, result, obj...)
```

---

## Template `.copilotignore`

```gitignore
# Secrets et configuration sensible
.env
.env.*
*.env
*secret*
*credential*
*password*

# Clés et certificats
*.pem
*.key
*.p12
*.pfx
*.crt

# Configuration de production
config/production.*
config/staging.*
infrastructure/

# Terraform tfstate
*.tfstate
*.tfstate.*
.terraform/

# Données sensibles
data/personal/
data/private/
exports/
dumps/

# Build outputs (optionnel)
# dist/
# build/
# target/
```

---

## Template `.code-workspace` multi-root

```json
{
    "folders": [
        {
            "name": "Frontend",
            "path": "./frontend"
        },
        {
            "name": "Backend",
            "path": "./backend"
        },
        {
            "name": "Infrastructure",
            "path": "./infrastructure"
        }
    ],
    "settings": {
        "github.copilot.enable": {
            "*": true,
            "terraform": false
        },
        "github.copilot.chat.codeGeneration.useInstructionFiles": true
    },
    "extensions": {
        "recommendations": [
            "GitHub.copilot",
            "GitHub.copilot-chat"
        ]
    }
}
```

---

## Template `SKILL.md` (agent customization)

```markdown
# [Nom du Skill] SKILL

## Rôle et domaine

Description concise de ce que ce skill active comme comportement.

## Quand invoquer ce skill

- Cas d'usage 1 : description précise
- Cas d'usage 2 : description précise
- Ne pas utiliser pour : cas exclus

## Comportements activés

1. **Comportement 1** : description
2. **Comportement 2** : description

## Exemples d'invocation

"Utilise le skill [nom] pour..."
"En tant que [rôle du skill], analyse..."

## Contraintes

- Contrainte 1
- Contrainte 2
```

---

## Template `.agent.md`

```markdown
# Nom de l'Agent

Description courte du rôle de cet agent.

## Comportement

Description détaillée de comment l'agent doit se comporter, quelles décisions il prend, quelle approche il suit.

## Outils autorisés

Listez les outils MCP ou VS Code que cet agent peut utiliser.

## Outils interdits

Listez les outils que cet agent ne doit pas utiliser.

## Exemples de tâches

- Tâche type 1
- Tâche type 2
```

---

## Template `.instructions.md` pour tests

```markdown
---
applyTo: '**/*.test.ts,**/*.spec.ts,**/__tests__/**'
---

# Conventions de tests

## Frameworks
- Jest + React Testing Library pour les composants
- MSW pour les mocks de requêtes HTTP
- user-event v14 (pas fireEvent pour les interactions utilisateur)

## Structure des tests
- describe: "ComponentName" ou "functionName"
- it/test: description en français, forme "devrait..."
- Pas de test qui dépend d'un autre test

## Assertions
- Préférer les matchers sémantiques : toBeInTheDocument(), toHaveValue()
- Éviter toMatchSnapshot() pour le markup (trop fragile)
- Chaque test a une seule assertion principale + assertions secondaires si nécessaire
```
