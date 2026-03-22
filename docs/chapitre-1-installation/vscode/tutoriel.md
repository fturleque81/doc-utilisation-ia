# :material-microsoft-visual-studio-code: Tutoriel — Installer GitHub Copilot sur Visual Studio Code

<span class="badge-vscode">VS Code</span> <span class="badge-beginner">Débutant</span>

## Présentation
Ce tutoriel vous guide pas à pas pour installer et configurer GitHub Copilot sur Visual Studio Code. Durée estimée : **3 à 5 minutes**.

---

## Prérequis

Avant de commencer, vérifiez :

- [ ] Visual Studio Code version **1.80 ou supérieure** (vérifiable via *Help → About*)
- [ ] Un compte GitHub avec un abonnement **Copilot actif** ([vérifier ici](https://github.com/settings/copilot))
- [ ] Une connexion internet active

!!! warning "Version VS Code"
    Les versions antérieures à 1.80 ne supportent pas toutes les fonctionnalités de Copilot. La mise à jour est fortement recommandée.
    
    Pour mettre à jour VS Code : *Help → Check for Updates* (ou téléchargez la dernière version sur [code.visualstudio.com](https://code.visualstudio.com))

---

## Étape 1 — Ouvrir le panneau Extensions

1. Lancez Visual Studio Code
2. Ouvrez le panneau **Extensions** via l'une de ces méthodes :
   - Cliquer sur l'icône Extensions dans la barre latérale gauche (icône de carrés)
   - Raccourci : ++ctrl+shift+x++ (Windows/Linux) / ++cmd+shift+x++ (macOS)
   - Menu : *View → Extensions*

<div class="img-placeholder">
📸 Capture d'écran : Icône Extensions dans la barre latérale VS Code
</div>

---

## Étape 2 — Rechercher et installer GitHub Copilot

1. Dans la barre de recherche du panneau Extensions, tapez : **GitHub Copilot**
2. Vous verrez deux extensions principales :
   - **GitHub Copilot** — autocomplétion inline (à installer en premier)
   - **GitHub Copilot Chat** — interface de chat IA
3. Cliquez sur **GitHub Copilot** (le premier résultat, publié par *GitHub*)
4. Cliquez sur le bouton **Install** bleu

<div class="img-placeholder">
📸 Capture d'écran : Résultats de recherche "GitHub Copilot" dans les extensions VS Code
</div>

!!! danger "Vérifiez l'éditeur"
    Assurez-vous que l'extension est publiée par **GitHub** (insigne de vérification). L'identifiant exact est `GitHub.copilot`. Il existe des extensions tierces imitatrices — installez uniquement l'officielle.

---

## Étape 3 — Installer GitHub Copilot Chat

L'extension Copilot Chat n'est pas incluse automatiquement — installez-la pour bénéficier du chat IA :

1. Dans le panneau Extensions, cherchez **GitHub Copilot Chat**
2. Cliquez sur **Install**

!!! info "Depuis VS Code 1.90+"
    À partir de VS Code 1.90, GitHub Copilot et Copilot Chat sont souvent proposés ensemble et peuvent être installés d'un seul clic via une notification dans VS Code.

---

## Étape 4 — Authentification avec GitHub

Après installation, VS Code déclenche automatiquement le processus d'authentification :

1. Une **notification pop-up** apparaît en bas à droite : *"Sign in to use GitHub Copilot"*
2. Cliquez sur **Sign In to GitHub**
3. VS Code ouvre votre navigateur sur la page d'autorisation GitHub
4. Si vous n'êtes pas connecté à GitHub, connectez-vous
5. Cliquez sur **Authorize Visual-Studio-Code**

<div class="img-placeholder">
📸 Capture d'écran : Page d'autorisation GitHub dans le navigateur
</div>

6. Une fois autorisé, VS Code affiche un message de confirmation : *"GitHub authentication was successful"*
7. Sélectionnez **Open** quand VS Code demande de rouvrir l'application

!!! tip "La notification n'apparaît pas ?"
    Ouvrez la palette de commandes avec ++ctrl+shift+p++ (++cmd+shift+p++ sur macOS), tapez **"GitHub Copilot: Sign In"** et appuyez sur ++enter++.

---

## Étape 5 — Vérifier le fonctionnement

**Vérification visuelle :**

Regardez la barre d'état en bas de VS Code (la barre colorée tout en bas) :

- L'icône Copilot (ressemblant à un casque/logo Copilot) devrait apparaître
- Si elle est accompagnée d'un point vert, Copilot est actif

<div class="img-placeholder">
📸 Capture d'écran : Icône Copilot dans la barre de statut VS Code (en bas à droite)
</div>

**Vérification par un test pratique :**

1. Créez un nouveau fichier : ++ctrl+n++ ou *File → New File*
2. Choisissez le langage JavaScript (ou n'importe quel autre langage)
3. Tapez ce commentaire :

```javascript
// Fonction qui retourne la somme de tous les nombres dans un tableau
function
```

4. Attendez 1 à 2 secondes après avoir tapé `function`
5. Une suggestion grisée devrait apparaître automatiquement

```javascript
// Suggestion exemple (en gris dans votre éditeur) :
function sumArray(arr) {
    return arr.reduce((acc, val) => acc + val, 0);
}
```

6. Appuyez sur ++tab++ pour accepter la suggestion

!!! success "Ça fonctionne !"
    Si vous voyez la suggestion apparaître en gris et pouvez l'accepter avec ++tab++, GitHub Copilot est opérationnel.

---

## Étape 6 — Tester Copilot Chat

1. Ouvrez le panneau Copilot Chat via l'icône dans la barre latérale gauche (bulle de chat avec logo Copilot)
2. Ou utilisez le raccourci ++ctrl+alt+i++ (++cmd+alt+i++ macOS)
3. Tapez une question comme : *"Comment créer une fonction qui trie un tableau d'objets par date en JavaScript ?"*
4. Copilot répond avec du code et des explications

!!! info "Modes de Copilot Chat"
    - **Chat panel** (panneau latéral) : conversations longues et contextuelles
    - **Inline Chat** (++ctrl+i++ / ++cmd+i++) : directement dans l'éditeur, sur le code sélectionné
    - **Quick Chat** (++ctrl+shift+i++) : fenêtre flottante rapide

---

## Pièges à éviter

!!! danger "Pièges courants lors de l'installation"

    **1. VS Code trop ancien**
    L'extension s'installe mais les fonctionnalités avancées ne fonctionnent pas.
    ✅ Solution : mettez à jour VS Code via *Help → Check for Updates*

    **2. Authentification bloquée par un proxy d'entreprise**
    Le navigateur s'ouvre mais la redirection vers VS Code échoue.
    ✅ Solution : vérifiez les paramètres réseau, ou configurez un proxy dans les settings VS Code (`http.proxy`)

    **3. Pas de suggestion malgré une installation réussie**
    Copilot est peut-être désactivé pour le langage actuel.
    ✅ Vérifiez `github.copilot.enable` dans les settings (voir [Paramétrage VS Code](../../chapitre-2-parametrage/vscode-parametrage.md))

    **4. Suggestions confondues avec l'autocomplétion IntelliSense**
    Les suggestions Copilot apparaissent en gris italique et légèrement décalées, différentes des suggestions IntelliSense classiques.
    ✅ Voir les [raccourcis clavier](reference.md) pour les distinguer et les contrôler

    **5. Extension installée mais icône absente dans la barre de statut**
    Parfois VS Code nécessite un rechargement de fenêtre.
    ✅ *Developer → Reload Window* (ou ++ctrl+shift+p++ → "Reload Window")

---

## Prochaines étapes

- [Guide de référence VS Code](reference.md) — settings.json, raccourcis complets, extensions recommandées
- [Paramétrage VS Code](../../chapitre-2-parametrage/vscode-parametrage.md) — Configurer Copilot finement
- [Comparaison IntelliJ vs VS Code](../comparaison.md) — Différences clés entre les deux IDEs

