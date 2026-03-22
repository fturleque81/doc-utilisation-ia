# Sécurité & Qualité du Code Généré

<span class="badge-intermediate">Intermédiaire</span>

## Principe de base : Copilot génère, vous validez

GitHub Copilot est entraîné sur des milliards de lignes de code public — code de qualité variable, parfois avec des bugs, parfois avec des problèmes de sécurité. **Vous êtes responsable de tout ce que vous committez**, qu'il soit généré par Copilot ou écrit manuellement.

---

## Checklist de vérification du code généré

### Vérification logique

- [ ] **Le code fait bien ce que le commentaire/prompt demandait ?** Pas d'interprétation erronée
- [ ] **Les cas limites sont gérés ?** (null, undefined, tableau vide, valeur max/min)
- [ ] **Les conditions d'erreur sont traitées ?** (try/catch, vérification des return codes)
- [ ] **La logique est-elle correcte ?** Pas d'erreur de comparaison (< vs <=, && vs ||)
- [ ] **Les boucles ont des conditions de sortie ?** Pas de boucle infinie possible

### Vérification de sécurité

- [ ] **Pas d'injection SQL** — les paramètres sont-ils paramétrisés, jamais concaténés ?
- [ ] **Pas de XSS** — le HTML généré est-il échappé ?
- [ ] **Pas de secrets hardcodés** — clés API, mots de passe, tokens ?
- [ ] **Validation des entrées** — les données utilisateur sont-elles validées *avant* utilisation ?
- [ ] **Pas d'exposition de données sensibles** — les logs/erreurs ne leakent pas de données privées ?

### Vérification de conformité

- [ ] **Respect des conventions du projet** ?
- [ ] **Imports corrects et complets** ?
- [ ] **Pas de dépendances inconnues** introduites sans raison ?
- [ ] **Pas de code déprécié** pour la version utilisée ?

---

## Risques de sécurité courants dans le code généré

### 1. Injection SQL

```python
# ❌ Code dangereux que Copilot peut parfois générer
def get_user(username: str):
    query = f"SELECT * FROM users WHERE username = '{username}'"
    return db.execute(query)  # Injection SQL possible !

# ✅ Correct — paramètres préparés
def get_user(username: str):
    query = "SELECT * FROM users WHERE username = ?"
    return db.execute(query, (username,))
```

!!! danger "Vérifiez tous les accès DB générés"
    Toute construction SQL générée par Copilot doit être inspectée. Si vous voyez une concaténation de chaîne dans une requête SQL, c'est un signal d'alarme immédiat.

### 2. Secrets hardcodés

```javascript
// ❌ Copilot peut compléter avec des valeurs d'exemple qui ressemblent à de vrais secrets
const config = {
    apiKey: "sk-1234567890abcdef",  // JAMAIS hardcoder
    dbPassword: "password123",       // JAMAIS hardcoder
    jwtSecret: "mysecretkey"         // JAMAIS hardcoder
};

// ✅ Toujours utiliser des variables d'environnement
const config = {
    apiKey: process.env.API_KEY!,
    dbPassword: process.env.DB_PASSWORD!,
    jwtSecret: process.env.JWT_SECRET!
};
```

### 3. Validation insuffisante des entrées

```typescript
// ❌ Copilot génère parfois du code sans validation suffisante
app.post('/users', (req, res) => {
    const user = req.body;  // Données non validées utilisées directement
    await createUser(user);
    res.json(user);
});

// ✅ Avec validation des entrées
import { z } from 'zod';

const CreateUserSchema = z.object({
    email: z.string().email(),
    name: z.string().min(2).max(100),
    role: z.enum(['USER', 'ADMIN'])
});

app.post('/users', (req, res) => {
    const validated = CreateUserSchema.parse(req.body);  // Lance une erreur si invalide
    await createUser(validated);
    res.json(validated);
});
```

### 4. Cryptographie faible

```java
// ❌ Copilot peut suggérer des algorithmes dépréciés
MessageDigest md = MessageDigest.getInstance("MD5");  // MD5 est cassé
byte[] hash = md.digest(password.getBytes());

// ✅ Utiliser des algorithmes récents
// Pour les mots de passe, utilisez BCrypt, Argon2, ou PBKDF2
BCryptPasswordEncoder encoder = new BCryptPasswordEncoder(12);
String hashedPassword = encoder.encode(password);
```

---

## Problèmes de licence et droits d'auteur

### Le risque

Copilot est entraîné sur du code public, dont certains sont sous licence restrictive (GPL, AGPL, etc.). Des suggestions peuvent par inadvertance reproduire du code protégé.

### Mesures de protection

**1. Activer le filtrage de code dupliqué** dans les paramètres GitHub Copilot :

Sur [github.com/settings/copilot](https://github.com/settings/copilot) :
- Activez **"Block suggestions matching public code"** (Duplication Detection)

**2. Revue des séquences de code inhabituelles**

Si Copilot génère un algorithme très spécifique (tri, parsing complexe) qui semble trop parfait, vérifiez sa provenance potentielle.

**3. Pour les projets commerciaux**

Utilisez GitHub Copilot Business ou Enterprise qui incluent un engagement plus fort sur les protections IP via les politiques de GitHub.

---

## Tests : obligation non négociable

Tout code généré par Copilot **doit être testé**. Copilot peut générer du code qui compile et s'exécute mais qui produit des résultats incorrects dans certains cas.

### Stratégie de test minimal

```
Nouveau code généré par Copilot
    │
    ├── Test happy path (cas nominal)
    ├── Test edge cases (null, vide, limites)
    ├── Test error cases (exceptions attendues)
    └── Test intégration si dépendances externes
```

### Utiliser Copilot pour générer les tests

Ironiquement, Copilot est excellent pour générer les tests du code qu'il vient de créer :

```
Sur VS Code avec Inline Chat (++ctrl+i++) :
"Génère les tests unitaires Jest pour cette fonction.
Couvre : happy path, cas null, cas array vide, et les exceptions."
```

---

## Revue de code systématique

### Pour vous-même

Avant de committer du code avec des parties générées par Copilot :

1. **Lisez le diff entier** — pas seulement les parties que vous avez écrites manuellement
2. **Testez localement** — ne committez jamais de code non testé, même si c'est "juste du boilerplate"
3. **Cherchez les TODO/FIXME** générés — Copilot en crée parfois sans que vous les demandiez

### En équipe (Pull Request)

Signalez dans votre PR quelles parties ont été générées par IA si votre équipe a une politique là-dessus. De nombreuses équipes intègrent un point de revue spécifique pour le code IA.

---

## Désactiver Copilot pour les fichiers sensibles

Via `.vscode/settings.json` ou `.copilotignore` :

```json
// .vscode/settings.json
{
    "github.copilot.enable": {
        "*": true,
        "dotenv": false,          // .env files
        "properties": false,      // .properties files (Java)
        "yaml": false             // Si vos YAML contiennent des secrets
    }
}
```

!!! info "Syntaxe `.copilotignore`"
    Ce fichier utilise exactement la même syntaxe que `.gitignore` — motifs glob, wildcards `*` et `**`, chemins relatifs depuis la racine du dépôt. Il est lu par Copilot mais **ignoré par Git**.

```gitignore
# .copilotignore
.env
.env.*
*secrets*
*credentials*
config/production.yaml
infrastructure/terraform/
```

---

## Les 3 règles à ne jamais oublier

!!! danger "Règles d'or"
    1. **Validez toujours** — Copilot peut produire du code fonctionnel mais incorrect ou non sécurisé
    2. **Zéro secret hardcodé** — Clés API, mots de passe et tokens : toujours en variables d'environnement
    3. **Testez avant de committer** — Même le boilerplate généré doit passer par des tests

---

## Prochaines étapes

- [Performance & Ressources](performance.md) — Optimiser Copilot pour ne pas impacter l'IDE
- [Troubleshooting](../chapitre-5-troubleshooting/index.md) — Résoudre les problèmes courants
