# Cas d'Usage par Technologie

GitHub Copilot s'adapte à chaque écosystème technologique. Ce chapitre présente des configurations et workflows optimisés pour les stacks les plus courants, avec des exemples concrets pour IntelliJ et VS Code.

---

## Technologies couvertes

<div class="grid cards" markdown>

-   :simple-nodedotjs: **Node.js & React**
    
    ---
    
    TypeScript, Express, React, Jest — configuration optimale pour l'écosystème JavaScript moderne.
    
    [Voir le guide →](nodejs-react.md)

-   :simple-python: **Python**
    
    ---
    
    FastAPI, Django, pytest, type hints — Copilot avec Pylance et les annotations de type.
    
    [Voir le guide →](python.md)

-   :simple-java: **Java**
    
    ---
    
    Spring Boot, Maven/Gradle, JUnit — IntelliJ comme IDE principal avec Copilot.
    
    [Voir le guide →](java.md)

</div>

---

## Principes communs à tous les projets

Quel que soit le langage, ces principes améliorent la qualité des suggestions Copilot :

| Principe | Impact |
|----------|--------|
| Types explicites partout | ++ Élevé — Copilot utilise les types pour inférer l'intention |
| Noms de variables descriptifs | ++ Élevé — `activeUserList` >> `data` |
| Fichiers liés ouverts dans les onglets | + Moyen — enrichit le contexte |
| Commentaires de fonction avant implémentation | ++ Élevé — guide directement la génération |
| Conventions cohérentes dans tout le projet | + Moyen — Copilot apprend le style |

---

## Choisir son IDE par technologie

| Technologie | IDE recommandé | Raison |
|-------------|---------------|--------|
| Java / Kotlin | **IntelliJ IDEA** | PSI natif, refactoring avancé, Maven/Gradle intégré |
| JavaScript / TypeScript | **VS Code** | TS Language Service natif, écosystème extensions |
| Python | **VS Code** (Pylance) ou **PyCharm** | Pylance = meilleure inférence type que PyCharm |
| React / Vue / Angular (SPA) | **VS Code** | Extensions JSX/TSX, CSS modules, React DevTools |
| Spring Boot | **IntelliJ IDEA** | Bean navigation, auto-configuration, run configs |
| FastAPI / Django | **VS Code** ou **PyCharm** | Les deux sont excellents |
| Fullstack (Java + React) | **IntelliJ ou VS Code** | IntelliJ Ultimate gère les deux ; VS Code également |

---

## Prochaines étapes

- [Appendices](../appendices/raccourcis-clavier.md) — Référence complète des raccourcis et templates
