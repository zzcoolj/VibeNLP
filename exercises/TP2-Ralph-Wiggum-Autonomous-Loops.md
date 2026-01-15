# TP2: Ralph Wiggum - Autonomous Loops with Claude Code
# TP2: Ralph Wiggum - Boucles autonomes avec Claude Code

**Duration / Durée**: 45 minutes
**Level / Niveau**: Intermediate / Intermédiaire
**Prerequisites / Prérequis**: Completed TP1, Claude Code installed, basic understanding of iterative processes / TP1 terminé, Claude Code installé, compréhension de base des processus itératifs

## Learning Objectives / Objectifs d'apprentissage

**English**: By the end of this practical exercise, you will be able to:
- Understand what Ralph Wiggum is and how it enables autonomous iteration
- Install and configure the Ralph Wiggum plugin for Claude Code
- Use autonomous loops to complete complex multi-step tasks
- Understand the cost implications and safety considerations
- Know when to use autonomous loops vs. manual interaction

**Français**: À la fin de cet exercice pratique, vous serez capable de :
- Comprendre ce qu'est Ralph Wiggum et comment il permet l'itération autonome
- Installer et configurer le plugin Ralph Wiggum pour Claude Code
- Utiliser des boucles autonomes pour accomplir des tâches complexes en plusieurs étapes
- Comprendre les implications de coût et les considérations de sécurité
- Savoir quand utiliser des boucles autonomes par rapport à l'interaction manuelle

## Introduction

### English

**Ralph Wiggum** is an official Claude Code plugin that enables autonomous iteration loops. Named after the Simpson's character who never gives up, Ralph Wiggum allows Claude to work persistently on complex tasks without requiring manual intervention between steps.

Traditionally, Claude Code stops after completing each response, requiring you to manually continue the conversation. Ralph Wiggum changes this by intercepting Claude's "stop" signal and automatically re-injecting the original prompt, allowing Claude to iterate continuously within the same session until the task is complete or a maximum iteration limit is reached.

**Key Concept**: Think of Ralph Wiggum as giving Claude "persistence" - the ability to keep working on a problem through multiple thinking cycles, just like a developer might iterate on a solution multiple times before getting it right.

### Français

**Ralph Wiggum** est un plugin officiel de Claude Code qui permet des boucles d'itération autonomes. Nommé d'après le personnage des Simpson qui n'abandonne jamais, Ralph Wiggum permet à Claude de travailler de manière persistante sur des tâches complexes sans nécessiter d'intervention manuelle entre les étapes.

Traditionnellement, Claude Code s'arrête après avoir complété chaque réponse, vous obligeant à continuer manuellement la conversation. Ralph Wiggum change cela en interceptant le signal d'arrêt de Claude et en réinjectant automatiquement le prompt original, permettant à Claude d'itérer continuellement dans la même session jusqu'à ce que la tâche soit terminée ou qu'une limite d'itération maximale soit atteinte.

**Concept clé**: Pensez à Ralph Wiggum comme donnant à Claude de la "persistance" - la capacité de continuer à travailler sur un problème à travers plusieurs cycles de réflexion, tout comme un développeur pourrait itérer sur une solution plusieurs fois avant de la réussir.

## Part 1: Understanding Ralph Wiggum / Partie 1: Comprendre Ralph Wiggum (10 minutes)

### Background Reading / Lecture de fond

**English**: Before installing Ralph Wiggum, it's important to understand the concept and its origins.

**Français**: Avant d'installer Ralph Wiggum, il est important de comprendre le concept et ses origines.

#### Required Reading / Lecture obligatoire
**English**: Read the original article about Ralph Wiggum:
- Article: [Ralph Wiggum - Autonomous Loops](https://ghuntley.com/ralph/)

**Français**: Lisez l'article original sur Ralph Wiggum :
- Article : [Ralph Wiggum - Boucles autonomes](https://ghuntley.com/ralph/)

#### Understanding the Third-Party Implementation / Comprendre l'implémentation tierce

**English**:
The community repo at [github.com/frankbria/ralph-claude-code](https://github.com/frankbria/ralph-claude-code) was an early third-party implementation that provided additional features like rate limiting and circuit breakers.

**IMPORTANT NOTE**: You do NOT need to follow the setup instructions from this repository. Ralph Wiggum is now officially integrated into Claude Code, and we'll use the official plugin instead.

The third-party repo is useful for:
- Understanding the conceptual evolution
- Seeing example use cases
- Learning about additional features (rate limiting, circuit breakers)

**Français**:
Le dépôt communautaire sur [github.com/frankbria/ralph-claude-code](https://github.com/frankbria/ralph-claude-code) était une implémentation tierce précoce qui fournissait des fonctionnalités supplémentaires comme la limitation de débit et les disjoncteurs.

**NOTE IMPORTANTE**: Vous n'avez PAS besoin de suivre les instructions d'installation de ce dépôt. Ralph Wiggum est maintenant officiellement intégré dans Claude Code, et nous utiliserons le plugin officiel à la place.

Le dépôt tiers est utile pour :
- Comprendre l'évolution conceptuelle
- Voir des exemples de cas d'usage
- Apprendre sur les fonctionnalités supplémentaires (limitation de débit, disjoncteurs)

### How Ralph Wiggum Works / Comment fonctionne Ralph Wiggum

**English**:
Ralph Wiggum uses a **Stop hook** mechanism to intercept Claude's exit attempts:

1. You start a task with `/ralph-loop "your task" --max-iterations 20`
2. Claude begins working on the task
3. When Claude would normally stop, the Stop hook intercepts it
4. The original prompt is re-injected into the session
5. Claude continues iterating with full context from previous iterations
6. This continues until:
   - The completion condition is met (e.g., "DONE" is output)
   - Maximum iterations are reached
   - You manually cancel with `/cancel-ralph`

**Français**:
Ralph Wiggum utilise un mécanisme de **Stop hook** pour intercepter les tentatives de sortie de Claude :

1. Vous démarrez une tâche avec `/ralph-loop "votre tâche" --max-iterations 20`
2. Claude commence à travailler sur la tâche
3. Quand Claude s'arrêterait normalement, le Stop hook l'intercepte
4. Le prompt original est réinjecté dans la session
5. Claude continue à itérer avec le contexte complet des itérations précédentes
6. Cela continue jusqu'à ce que :
   - La condition de complétion soit remplie (ex: "DONE" est affiché)
   - Les itérations maximales soient atteintes
   - Vous annulez manuellement avec `/cancel-ralph`

## Part 2: Installation / Partie 2: Installation (5 minutes)

### Step 1: Add the Official Plugin Marketplace / Étape 1: Ajouter le marché de plugins officiel

**English**: First, ensure you have access to the Anthropic official plugin marketplace.

**Français**: D'abord, assurez-vous d'avoir accès au marché de plugins officiel d'Anthropic.

```bash
# English: Add Anthropic official plugin marketplace
# Français: Ajouter le marché de plugins officiel d'Anthropic
/plugin marketplace add anthropics/claude-code
```

### Step 2: Install Ralph Wiggum Plugin / Étape 2: Installer le plugin Ralph Wiggum

**English**: Install the official Ralph Wiggum plugin.

**Français**: Installez le plugin Ralph Wiggum officiel.

```bash
# English: Install Ralph Wiggum plugin
# Français: Installer le plugin Ralph Wiggum
/plugin install ralph-wiggum@claude-plugins-official
```

### Verification / Vérification

**English**: Verify the installation by listing your installed plugins:

**Français**: Vérifiez l'installation en listant vos plugins installés :

```bash
# English: List installed plugins
# Français: Lister les plugins installés
/plugin list
```

**English**: You should see `ralph-wiggum` in the output.

**Français**: Vous devriez voir `ralph-wiggum` dans la sortie.

## Part 3: Basic Usage / Partie 3: Utilisation de base (15 minutes)

### Starting an Autonomous Loop / Démarrer une boucle autonome

**English**: The basic syntax for starting a Ralph loop is:

**Français**: La syntaxe de base pour démarrer une boucle Ralph est :

```bash
/ralph-loop "your task description" --max-iterations <number> --completion-promise "DONE"
```

**Parameters / Paramètres**:
- `"your task description"` / `"description de votre tâche"`: The task you want Claude to complete / La tâche que vous voulez que Claude accomplisse
- `--max-iterations <number>`: Safety limit (ALWAYS SET THIS) / Limite de sécurité (TOUJOURS DÉFINIR CECI)
- `--completion-promise "DONE"`: The keyword Claude should output when finished / Le mot-clé que Claude devrait afficher quand il a terminé

### Exercise A: Simple Multi-Step Task / Exercice A: Tâche simple en plusieurs étapes

**English**: Let's try a simple autonomous loop task.

**Français**: Essayons une tâche de boucle autonome simple.

**Task / Tâche**:
```bash
/ralph-loop "Create a Python function to calculate fibonacci numbers, write tests for it, run the tests, and fix any issues until all tests pass. Output DONE when complete." --max-iterations 10 --completion-promise "DONE"
```

**What to Observe / Ce qu'il faut observer**:

**English**:
1. Claude will create the function
2. Claude will write tests
3. Claude will run the tests
4. If tests fail, Claude will fix the code automatically
5. Claude will iterate until tests pass or max iterations reached
6. Claude will output "DONE" when successful

**Français**:
1. Claude créera la fonction
2. Claude écrira les tests
3. Claude exécutera les tests
4. Si les tests échouent, Claude corrigera le code automatiquement
5. Claude itérera jusqu'à ce que les tests passent ou que les itérations max soient atteintes
6. Claude affichera "DONE" en cas de succès

### Canceling a Running Loop / Annuler une boucle en cours

**English**: If you need to stop a running loop:

**Français**: Si vous devez arrêter une boucle en cours :

```bash
/cancel-ralph
```

## Part 4: Cost Awareness & Safety / Partie 4: Conscience des coûts et sécurité (10 minutes)

### Cost Implications / Implications de coût

**English**:
⚠️ **CRITICAL WARNING**: Autonomous loops consume tokens rapidly!

**Cost Examples**:
- A 50-iteration loop on a medium codebase: **$50-100+ in API costs**
- Each iteration includes full context from previous iterations
- Costs scale with: codebase size, iteration count, task complexity

**ALWAYS**:
- Set `--max-iterations` to a reasonable limit
- Start with small values (5-10) for testing
- Monitor your API usage
- Use on smaller, focused tasks first

**Français**:
⚠️ **AVERTISSEMENT CRITIQUE**: Les boucles autonomes consomment des tokens rapidement !

**Exemples de coûts**:
- Une boucle de 50 itérations sur un codebase moyen : **50-100$+ en coûts d'API**
- Chaque itération inclut le contexte complet des itérations précédentes
- Les coûts évoluent avec : la taille du codebase, le nombre d'itérations, la complexité de la tâche

**TOUJOURS**:
- Définir `--max-iterations` à une limite raisonnable
- Commencer avec de petites valeurs (5-10) pour les tests
- Surveiller votre utilisation d'API
- Utiliser sur des tâches plus petites et ciblées d'abord

### Best Practices for Cost Management / Meilleures pratiques pour la gestion des coûts

**English**:
1. **Start Small**: Test with `--max-iterations 5` first
2. **Be Specific**: Clear task descriptions reduce wasted iterations
3. **Use Completion Promises**: Help Claude know when to stop
4. **Monitor Progress**: Watch the first few iterations to ensure Claude is on track
5. **Cancel Early**: Use `/cancel-ralph` if things go off track

**Français**:
1. **Commencer petit**: Tester avec `--max-iterations 5` d'abord
2. **Être spécifique**: Des descriptions de tâches claires réduisent les itérations gaspillées
3. **Utiliser les promesses de complétion**: Aider Claude à savoir quand s'arrêter
4. **Surveiller les progrès**: Observer les premières itérations pour s'assurer que Claude est sur la bonne voie
5. **Annuler tôt**: Utiliser `/cancel-ralph` si les choses déraillent

### When to Use Ralph Wiggum vs. Manual Interaction / Quand utiliser Ralph Wiggum vs. interaction manuelle

**English**:

**✅ Good Use Cases for Ralph Wiggum**:
- Multi-step tasks with clear completion criteria
- Test-driven development cycles (write tests → implement → fix → verify)
- Iterative refinement tasks
- Tasks requiring multiple file changes
- Debugging complex issues that need multiple attempts

**❌ Poor Use Cases**:
- Exploratory work (unclear end goal)
- Tasks requiring human judgment at each step
- Simple one-step tasks
- Tasks where you want to review each change

**Français**:

**✅ Bons cas d'usage pour Ralph Wiggum**:
- Tâches en plusieurs étapes avec des critères de complétion clairs
- Cycles de développement dirigés par les tests (écrire tests → implémenter → corriger → vérifier)
- Tâches de raffinement itératif
- Tâches nécessitant des changements dans plusieurs fichiers
- Débogage de problèmes complexes nécessitant plusieurs tentatives

**❌ Mauvais cas d'usage**:
- Travail exploratoire (objectif final peu clair)
- Tâches nécessitant un jugement humain à chaque étape
- Tâches simples en une étape
- Tâches où vous voulez réviser chaque changement

## Part 5: Practical Exercises / Partie 5: Exercices pratiques (15 minutes)

### Exercise B: Test-Driven Development Loop / Exercice B: Boucle de développement dirigée par les tests

**English**: Create a task that requires multiple iterations to get right.

**Français**: Créez une tâche qui nécessite plusieurs itérations pour être réussie.

**Task / Tâche**:
```bash
/ralph-loop "Create a Python class for a simple calculator with add, subtract, multiply, and divide methods. Write comprehensive unit tests including edge cases (division by zero, large numbers, negative numbers). Run the tests and fix any failures. Output DONE when all tests pass." --max-iterations 15 --completion-promise "DONE"
```

### Exercise C: Documentation Generation / Exercice C: Génération de documentation

**English**: Use Ralph to create comprehensive documentation.

**Français**: Utilisez Ralph pour créer une documentation complète.

**Task / Tâche**:
```bash
/ralph-loop "Analyze all Python files in the src/ directory and create a comprehensive README.md with: project description, installation instructions, usage examples for each module, and API documentation. Verify the markdown formatting is correct. Output DONE when complete." --max-iterations 8 --completion-promise "DONE"
```

### Exercise D: Debugging Challenge / Exercice D: Défi de débogage

**English**: Let Ralph debug and fix a problematic piece of code.

**Français**: Laissez Ralph déboguer et corriger un morceau de code problématique.

**Task / Tâche**:
```bash
/ralph-loop "Find and fix all bugs in the file utils.py. For each bug found: identify it, explain why it's a bug, fix it, and add a test case to prevent regression. Continue until no more bugs are found or all tests pass. Output DONE when complete." --max-iterations 12 --completion-promise "DONE"
```

## Expected Outcomes / Résultats attendus

**English**: After completing this TP, you should have:

**Français**: Après avoir complété ce TP, vous devriez avoir :

- ✅ Understanding of what Ralph Wiggum is and how it works / Compréhension de ce qu'est Ralph Wiggum et comment il fonctionne
- ✅ Successfully installed the Ralph Wiggum plugin / Plugin Ralph Wiggum installé avec succès
- ✅ Completed at least one autonomous loop task / Complété au moins une tâche de boucle autonome
- ✅ Understanding of cost implications / Compréhension des implications de coût
- ✅ Ability to judge when to use autonomous loops / Capacité à juger quand utiliser des boucles autonomes

## Troubleshooting / Dépannage

### Problem / Problème: Ralph loop doesn't stop at completion promise / La boucle Ralph ne s'arrête pas à la promesse de complétion

**English - Solutions**:
- Ensure your completion promise is clear and distinctive (e.g., "TASK_COMPLETE", "DONE", "FINISHED")
- Check that Claude is actually outputting the promise string
- Verify the promise string matches exactly (case-sensitive)

**Français - Solutions**:
- Assurez-vous que votre promesse de complétion est claire et distinctive (ex: "TASK_COMPLETE", "DONE", "FINISHED")
- Vérifiez que Claude affiche réellement la chaîne de promesse
- Vérifiez que la chaîne de promesse correspond exactement (sensible à la casse)

### Problem / Problème: Loop exceeds max iterations without completing / La boucle dépasse les itérations max sans se terminer

**English - Solutions**:
- Task may be too complex - break it into smaller sub-tasks
- Task description may be unclear - be more specific
- Increase `--max-iterations` if task is legitimately complex
- Review the first few iterations to see if Claude is making progress

**Français - Solutions**:
- La tâche peut être trop complexe - la diviser en sous-tâches plus petites
- La description de la tâche peut être peu claire - être plus spécifique
- Augmenter `--max-iterations` si la tâche est légitimement complexe
- Réviser les premières itérations pour voir si Claude fait des progrès

### Problem / Problème: High API costs / Coûts d'API élevés

**English - Solutions**:
- Reduce `--max-iterations` for testing
- Use more specific task descriptions
- Start with smaller codebases
- Monitor first iteration to catch issues early
- Cancel loops that go off track immediately

**Français - Solutions**:
- Réduire `--max-iterations` pour les tests
- Utiliser des descriptions de tâches plus spécifiques
- Commencer avec des codebases plus petits
- Surveiller la première itération pour détecter les problèmes tôt
- Annuler immédiatement les boucles qui déraillent

## Key Takeaways / Points clés à retenir

**English**:
1. **Ralph Wiggum enables persistence**: Claude can work through multi-step tasks autonomously
2. **Always set max-iterations**: This is your safety net against runaway costs
3. **Start small and test**: Use low iteration counts for testing before production use
4. **Clear completion criteria help**: Well-defined tasks converge faster
5. **Cost awareness is critical**: Monitor token usage and start with small tasks
6. **It's a power tool**: Great for complex tasks, overkill for simple ones

**Français**:
1. **Ralph Wiggum permet la persistance**: Claude peut travailler sur des tâches en plusieurs étapes de manière autonome
2. **Toujours définir max-iterations**: C'est votre filet de sécurité contre les coûts incontrôlés
3. **Commencer petit et tester**: Utiliser de faibles nombres d'itérations pour les tests avant l'usage en production
4. **Des critères de complétion clairs aident**: Les tâches bien définies convergent plus rapidement
5. **La conscience des coûts est critique**: Surveiller l'utilisation des tokens et commencer avec de petites tâches
6. **C'est un outil puissant**: Excellent pour les tâches complexes, exagéré pour les simples

## Additional Resources / Ressources supplémentaires

**English**:
- [Original Ralph Wiggum Article by Geoffrey Huntley](https://ghuntley.com/ralph/)
- [Community Implementation (for reference)](https://github.com/frankbria/ralph-claude-code)
- [Claude Code Official Documentation](https://github.com/anthropics/claude-code)
- [Claude Code Plugin Marketplace](https://github.com/anthropics/claude-code-plugins)

**Français**:
- [Article original sur Ralph Wiggum par Geoffrey Huntley](https://ghuntley.com/ralph/)
- [Implémentation communautaire (pour référence)](https://github.com/frankbria/ralph-claude-code)
- [Documentation officielle de Claude Code](https://github.com/anthropics/claude-code)
- [Marché des plugins Claude Code](https://github.com/anthropics/claude-code-plugins)

## Submission / Soumission

**English**: To complete this TP, submit:

**Français**: Pour compléter ce TP, soumettre :

1. **Screenshots / Captures d'écran**:
   - Ralph plugin installation confirmation / Confirmation d'installation du plugin Ralph
   - At least one successful Ralph loop completion / Au moins une complétion réussie d'une boucle Ralph

2. **Code Repository Link / Lien vers le dépôt de code**:
   - Repository showing work completed by autonomous loops / Dépôt montrant le travail complété par les boucles autonomes

3. **Reflection / Réflexion** (5-7 sentences / phrases):
   - **English**: Describe your experience using Ralph Wiggum. What task did you give it? How many iterations did it take? Were you surprised by anything? What are the advantages and disadvantages compared to manual interaction with Claude? Would you use this for real projects?
   - **Français**: Décrivez votre expérience avec Ralph Wiggum. Quelle tâche lui avez-vous donnée ? Combien d'itérations ont été nécessaires ? Avez-vous été surpris par quelque chose ? Quels sont les avantages et inconvénients par rapport à l'interaction manuelle avec Claude ? Utiliseriez-vous ceci pour de vrais projets ?

4. **Cost Analysis / Analyse des coûts**:
   - **English**: Estimate the token usage for your Ralph loops. How much would this cost at current API rates?
   - **Français**: Estimez l'utilisation des tokens pour vos boucles Ralph. Combien cela coûterait-il aux tarifs actuels de l'API ?

---

**English**: **Congratulations!** You now understand how to use Ralph Wiggum to enable Claude Code to work autonomously on complex multi-step tasks. Use this power wisely, always with cost awareness and appropriate safety limits.

**Français**: **Félicitations !** Vous comprenez maintenant comment utiliser Ralph Wiggum pour permettre à Claude Code de travailler de manière autonome sur des tâches complexes en plusieurs étapes. Utilisez ce pouvoir avec sagesse, toujours avec une conscience des coûts et des limites de sécurité appropriées.
