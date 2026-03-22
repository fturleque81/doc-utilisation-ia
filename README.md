# documentation-ia

Centralisation de la documentation issue de mon apprentissage IA.

## Lancer le site en local

Ce projet utilise MkDocs avec le thème Material.

### Pré-requis

- Windows avec Python 3.11+
- Lanceur Python `py` disponible

### Installation des dépendances

Depuis la racine du projet :

```powershell
py -m pip install --upgrade pip
py -m pip install mkdocs-material
```

### Démarrage en local

```powershell
py -m mkdocs serve
```

> **Note** : Lance cette commande depuis la racine du repo (dossier où est `mkdocs.yml`)

Ensuite ouvre l'URL affichée dans le terminal (par défaut : <http://127.0.0.1:8000>). 

### Build statique

```powershell
py -m mkdocs build
```

> **Note** : Lance cette commande depuis la racine du repo (dossier où est `mkdocs.yml`)

Le site généré sera dans le dossier `site/`.

## Dépannage rapide (Windows)

Si `pip` ou `mkdocs` n'est pas reconnu, c'est normal si les scripts Python ne sont pas dans le PATH.
Dans ce cas, utilise toujours :

- `py -m pip ...`
- `py -m mkdocs ...`

Commandes de vérification utiles :

```powershell
py --version
py -m pip --version
py -m mkdocs --version
```
