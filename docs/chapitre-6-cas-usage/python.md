# Python — Cas d'Usage

## Stack couverte

- **Langage** : Python 3.10+
- **Frameworks** : FastAPI, Django, Flask
- **Qualité** : mypy, Ruff, Black
- **Tests** : pytest avec fixtures et parametrize
- **IDE** : VS Code + Pylance (recommandé) ou PyCharm

---

## Pourquoi les annotations de type transforment Copilot

Sans type hints, Copilot génère du code Python générique. Avec des annotations de type complètes, il génère du code précis et adapté à votre domaine.

```python
# Sans type hints — Copilot génère quelque chose de générique
def get_users(db, filters):
    ...

# Avec type hints — Copilot comprend les types et génère du code précis
from sqlalchemy.orm import Session
from .models import User
from .schemas import UserFilter, UserResponse

def get_users(
    db: Session,
    filters: UserFilter,
    skip: int = 0,
    limit: int = 100,
) -> list[UserResponse]:
    ...
```

---

## Structure de projet recommandée

```
mon-projet-python/
├── .github/
│   ├── copilot-instructions.md
│   └── instructions/
│       ├── fastapi-routes.instructions.md
│       └── tests.instructions.md
├── src/
│   └── mon_package/
│       ├── __init__.py
│       ├── models/
│       │   ├── __init__.py
│       │   ├── user.py          # SQLAlchemy models
│       │   └── product.py
│       ├── schemas/
│       │   ├── __init__.py
│       │   ├── user.py          # Pydantic schemas
│       │   └── product.py
│       ├── api/
│       │   ├── __init__.py
│       │   ├── routes/
│       │   └── dependencies.py
│       ├── services/
│       └── repositories/
├── tests/
│   ├── conftest.py
│   ├── unit/
│   └── integration/
├── pyproject.toml
└── mypy.ini
```

---

## Configuration Copilot pour Python

### `.github/copilot-instructions.md`

```markdown
---
applyTo: '**/*.py'
---

# Conventions Python du projet

## Versions et outils
- Python 3.11+
- Framework: FastAPI avec Pydantic v2
- ORM: SQLAlchemy 2.0 (style déclaratif avec Mapped[])
- Tests: pytest avec fixtures de scope function par défaut
- Linting: Ruff, formatting: Black, type checking: mypy strict

## Conventions de code
- Annotations de type obligatoires sur toutes les fonctions publiques
- Pydantic: utiliser `model_validator` et `field_validator` de Pydantic v2 (pas v1)
- SQLAlchemy: utiliser `Mapped[type]` et `mapped_column()` (style 2.0)
- Async: toutes les routes FastAPI sont async
- Erreurs: lever des exceptions HTTP avec `raise HTTPException(status_code=..., detail=...)`

## Patterns interdits
- Pas d'import `*`
- Pas de variables `data`, `result`, `obj` sans contexte de type
- Pas de `except Exception` sans re-raise ou logging
```

### `.github/instructions/fastapi-routes.instructions.md`

```markdown
---
applyTo: 'src/**/api/routes/*.py'
---

## Pattern des routes FastAPI

- Chaque route utilise un service injecté via Depends()
- Retourner toujours un schéma Pydantic, jamais un modèle SQLAlchemy
- Status codes explicites: 201 pour création, 204 pour suppression
- Tags fournis pour la documentation OpenAPI automatique

## Template de route

```python
@router.post(
    "/",
    response_model=UserResponse,
    status_code=status.HTTP_201_CREATED,
    summary="Créer un nouvel utilisateur",
    tags=["users"],
)
async def create_user(
    user_data: CreateUserRequest,
    service: UserService = Depends(get_user_service),
) -> UserResponse:
    return await service.create(user_data)
```
```

---

## Cas d'usage pratiques

### 1. Modèle SQLAlchemy 2.0

```python
# Modèle User avec SQLAlchemy 2.0
# Relations: un User a plusieurs Orders
# Champs: id, email (unique), username, created_at, is_active
from sqlalchemy.orm import Mapped, mapped_column, relationship

class User(Base):
    __tablename__ = "users"
    # Copilot génère les champs avec les bons types Mapped[]
```

### 2. Schéma Pydantic v2

```python
# Schéma de validation pour la création d'un utilisateur
# email: format email, validé
# password: min 8 chars, au moins 1 majuscule, 1 chiffre
# username: 3-50 chars, alnum + underscores
from pydantic import BaseModel, EmailStr, field_validator

class CreateUserRequest(BaseModel):
    # Copilot génère les champs et les validators
```

### 3. Service avec injection de dépendances

```python
# Service de gestion des utilisateurs
# Dépend du UserRepository (injecté)
# Méthodes: create, get_by_id, get_by_email, update, delete
class UserService:
    def __init__(self, repository: UserRepository) -> None:
        self.repository = repository
    
    async def create(self, data: CreateUserRequest) -> UserResponse:
        # Copilot complète la logique avec hash du mot de passe, vérification unicitié
```

### 4. Tests pytest avec fixtures

Dans Copilot Chat :
```
Génère les tests pytest pour UserService.create().
Utilise des fixtures:
- mock_repository: mocke UserRepository avec pytest-mock
- Couvre: création réussie, email déjà utilisé (UserAlreadyExistsError), 
  email invalide, et mot de passe trop faible
Utilise pytest.mark.asyncio pour les tests async.
```

---

## Configuration `pyproject.toml` orientée qualité

```toml
[tool.mypy]
python_version = "3.11"
strict = true
warn_return_any = true
warn_unused_configs = true

[tool.ruff]
select = ["E", "F", "I", "UP", "ANN"]  # ANN = vérification annotations de type
ignore = ["ANN101"]  # self n'a pas besoin d'annotation

[tool.pytest.ini_options]
asyncio_mode = "auto"
testpaths = ["tests"]
```

---

## Configuration IDE

=== ":material-microsoft-visual-studio-code: VS Code"
    ```json
    // .vscode/settings.json
    {
        "python.defaultInterpreterPath": "${workspaceFolder}/.venv/bin/python",
        "python.analysis.typeCheckingMode": "strict",
        "python.analysis.autoImportCompletions": true,
        "editor.formatOnSave": true,
        "[python]": {
            "editor.defaultFormatter": "ms-python.black-formatter",
            "editor.codeActionsOnSave": {
                "source.organizeImports": "explicit"
            }
        },
        "github.copilot.enable": {
            "python": true
        }
    }
    ```
    
    Extensions recommandées :
    - `ms-python.python` — Python Language Server
    - `ms-python.pylance` — Pylance (type checking)
    - `ms-python.black-formatter` — Black formatter
    - `charliermarsh.ruff` — Ruff linter

=== "PyCharm"
    - **Settings → Python Interpreter** : configurez le venv
    - **Settings → Editor → Inspections → Python** : activez les warnings de type
    - Plugin GitHub Copilot : utilise le type inference de PyCharm pour enrichir le contexte
    - Le support des annotations de type est aussi bon qu'avec Pylance

---

## Utiliser Copilot pour les migrations de base de données

```python
# Migration Alembic pour ajouter la table 'products' 
# Champs: id (UUID), name (VARCHAR 255), price (DECIMAL 10,2), 
#         category_id (FK vers categories), created_at (TIMESTAMP DEFAULT NOW())
def upgrade() -> None:
    # Copilot génère le op.create_table() complet
```

---

## Prochaines étapes

- [Java — Cas d'Usage](java.md)
- [Node.js & React — Cas d'Usage](nodejs-react.md)
