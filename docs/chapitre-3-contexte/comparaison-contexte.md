# Comparaison — Contexte & Personnalisation VS Code vs IntelliJ

## Présentation
Cette page compare les capacités de contextualisation et de personnalisation de Copilot entre VS Code et IntelliJ IDEA. Les deux approches sont complémentaires et donnent des résultats différents selon les langages et les besoins.

---

## Tableau comparatif complet

| Mécanisme | VS Code | IntelliJ | Notes |
|-----------|:-------:|:--------:|-------|
| **Fenêtre de contexte** | Fichiers ouverts | Analyse complète PSI | IntelliJ analyse plus en profondeur |
| **Instructions globales** | ✅ `.github/copilot-instructions.md` | ❌ | Exclusif VS Code |
| **Instructions ciblées** | ✅ `.github/instructions/*.instructions.md` | ❌ | Exclusif VS Code |
| **Prompt files** | ✅ `.github/prompts/*.prompt.md` | ❌ | Exclusif VS Code |
| **Agents custom** | ✅ `.github/agents/*.agent.md` | ❌ | Exclusif VS Code |
| **Skills** | ✅ `SKILL.md` + `copilot-skill://` | ❌ | Exclusif VS Code |
| **Hooks** | ✅ (limités, en évolution) | ❌ | Exclusif VS Code |
| **Exclusion de fichiers** | ✅ `.copilotignore` | ✅ Dossiers "Excluded" | Mécanismes différents |
| **Contexte de dépendances** | ✅ package.json, requirements.txt | ✅ pom.xml, build.gradle | Les deux lisent les manifests |
| **Analyse sémantique** | Via Language Server (LSP) | Via PSI (analyse native) | IntelliJ plus profond pour JVM |
| **Settings par projet** | ✅ `.vscode/settings.json` | ✅ `.idea/` (partageable) | Deux approches |
| **Workspace multi-dossiers** | ✅ `.code-workspace` | ✅ Multi-module natif | IntelliJ meilleur pour Maven/Gradle |

---

## Qualité du contexte par langage

| Langage | VS Code | IntelliJ |
|---------|:-------:|:--------:|
| Java | ⭐⭐⭐⭐ (Extension Pack for Java) | ⭐⭐⭐⭐⭐ natif |
| Kotlin | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ natif |
| TypeScript | ⭐⭐⭐⭐⭐ natif | ⭐⭐⭐⭐ (WebStorm) |
| JavaScript | ⭐⭐⭐⭐⭐ natif | ⭐⭐⭐⭐ (WebStorm) |
| Python | ⭐⭐⭐⭐⭐ avec Pylance | ⭐⭐⭐⭐⭐ (PyCharm) |
| Go | ⭐⭐⭐⭐⭐ natif | ⭐⭐⭐⭐ (GoLand) |
| Rust | ⭐⭐⭐⭐⭐ natif | ⭐⭐⭐ (plugin) |
| C# | ⭐⭐⭐⭐ avec C# Dev Kit | ⭐⭐⭐⭐⭐ (Rider) |

---

## L'avantage de VS Code : personnalisation profonde

VS Code permet une personnalisation du comportement de Copilot impossible sur IntelliJ :

```
Équipe utilisant VS Code peut avoir :

.github/
├── copilot-instructions.md              → "Ce projet utilise Vue 3 + Pinia + TypeScript 5"
├── instructions/
│   ├── vue.instructions.md              → Règles composants Vue (applyTo: **/*.vue)
│   └── stores.instructions.md           → Règles Pinia (applyTo: **/stores/**) 
├── prompts/
│   ├── create-component.prompt.md       → Template création de composant Vue
│   └── write-e2e-test.prompt.md         → Cypress E2E tests standards
└── agents/
    └── vue-expert.agent.md              → Agent spécialisé Vue 3
```

Résultat : Copilot se comporte comme s'il avait été formé spécifiquement pour ce projet.

---

## L'avantage d'IntelliJ : analyse sémantique native

IntelliJ connaît votre code en profondeur **sans configuration** :

```java
// Exemple : IntelliJ comprend que orderService est un
// OrderService et connaît toutes ses méthodes disponibles
// sans avoir besoin d'onglets ouverts

@Autowired
private OrderService orderService;

public void process() {
    // Copilot sur IntelliJ suggère exactement les bonnes
    // méthodes de orderService avec les bons types de paramètres
    orderService.
    //           ↑ Suggestions précises car IntelliJ connaît
    //             le type exact et toutes ses méthodes
}
```

Sur VS Code, la même précision nécessiterait que le fichier `OrderService.java` soit ouvert dans un onglet.

---

## Stratégie recommandée selon le contexte

### Vous travaillez sur un projet Java/Spring Boot

```
Recommandation : IntelliJ IDEA en IDE principal
                 VS Code optionnel pour les fichiers de personnalisation

Pourquoi : L'analyse PSI d'IntelliJ donne un contexte Java exceptionnel.
           Si vous avez besoin d'instructions custom, créez-les sur VS Code
           et committez-les dans .github/ — elles bénéficieront à toute l'équipe.
```

### Vous travaillez sur un projet full-stack TypeScript

```
Recommandation : VS Code avec workspace multi-dossiers

Pourquoi : VS Code + Pylance/TypeScript Language Server = contexte TS 
           excellent + personnalisation .instructions.md possible + 
           .copilotignore pour exclure les fichiers générés.
```

### Vous avez les deux IDEs et alternez selon les projets

```
Recommandation : 
- Créez les fichiers .github/ dans votre projet (instructions, agents)
- Ces fichiers bénéficient à VS Code automatiquement
- IntelliJ ignore ces fichiers mais bénéficie de la structure propre 
  et du README bien écrit
- Win-win pour les deux IDEs !
```

---

## Migration de contexte : d'IntelliJ vers VS Code

Si vous souhaitez passer d'IntelliJ à VS Code pour un projet :

1. **Exportez votre connaissance projet** vers un `copilot-instructions.md`
2. **Créez des instructions** pour les conventions Java/Kotlin de votre équipe
3. **Installez les extensions** : Extension Pack for Java, Spring Boot Extension Pack
4. **Configurez le workspace** avec un `.code-workspace` si multi-module

```markdown
<!-- .github/copilot-instructions.md pour un projet Spring Boot -->
# Instructions — MonApp Spring Boot

Ce projet est une API REST Spring Boot 3.2 avec Java 21.

Architecture (packages) :
- `controller` : @RestController, validation des entrées, mapping DTOs
- `service` : @Service, logique métier, @Transactional pour les ops write
- `repository` : interfaces JpaRepository, queries JPQL dans @Query
- `model` : entités JPA, enums, DTOs (record Java 16+)
- `config` : @Configuration, beans, sécurité Spring Security
- `exception` : @ControllerAdvice, hiérarchie d'exceptions

Conventions Java :
- Java 21 features : Records, Pattern Matching, Sealed Classes bienvenues
- Lombok : @Data, @Builder, @RequiredArgsConstructor, @Slf4j
- Validation : @Valid sur les DTOs d'entrée, annotations javax.validation
- Tests : JUnit 5, Mockito, AssertJ, @SpringBootTest pour les IT
```

---

## Prochaines étapes

- [Bonnes Pratiques](../chapitre-4-bonnes-pratiques/index.md) — Comment tirer le meilleur des deux IDEs
- [Cas d'usage Java](../chapitre-6-cas-usage/java.md) — Configuration complète pour un projet Java
- [Cas d'usage Node.js/React](../chapitre-6-cas-usage/nodejs-react.md) — Configuration complète pour un projet TypeScript

