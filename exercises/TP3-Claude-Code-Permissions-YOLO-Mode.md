# TP3: Claude Code Permissions and YOLO Mode
# TP3: Permissions Claude Code et Mode YOLO

**Duration / Durée**: 30 minutes
**Level / Niveau**: Beginner-Intermediate / Débutant-Intermédiaire
**Prerequisites / Prérequis**: Completed TP1, Claude Code installed / TP1 terminé, Claude Code installé

## Learning Objectives / Objectifs d'apprentissage

**English**: By the end of this practical exercise, you will be able to:
- Understand Claude Code's permission system and why it exists
- Configure permission rules for different operations
- Know the difference between allowlist and blocklist approaches
- Understand when and how to use YOLO mode safely
- Make informed decisions about security vs. convenience trade-offs

**Français**: À la fin de cet exercice pratique, vous serez capable de :
- Comprendre le système de permissions de Claude Code et pourquoi il existe
- Configurer les règles de permission pour différentes opérations
- Connaître la différence entre les approches allowlist et blocklist
- Comprendre quand et comment utiliser le mode YOLO en toute sécurité
- Prendre des décisions éclairées sur les compromis sécurité vs. commodité

## Introduction

### English

Claude Code operates with a **permission system** designed to protect you from unintended actions. By default, Claude will ask for your approval before performing potentially risky operations like:

- Writing or modifying files
- Executing shell commands
- Making network requests
- Accessing sensitive directories

This permission system exists because AI assistants can make mistakes or misinterpret instructions. Having a human in the loop for critical operations provides a safety net.

However, constantly approving every action can slow down your workflow, especially for repetitive or low-risk tasks. That's where **permission configuration** and **YOLO mode** come in.

### Français

Claude Code fonctionne avec un **système de permissions** conçu pour vous protéger des actions non intentionnelles. Par défaut, Claude vous demandera votre approbation avant d'effectuer des opérations potentiellement risquées comme :

- Écrire ou modifier des fichiers
- Exécuter des commandes shell
- Effectuer des requêtes réseau
- Accéder à des répertoires sensibles

Ce système de permissions existe parce que les assistants IA peuvent faire des erreurs ou mal interpréter les instructions. Avoir un humain dans la boucle pour les opérations critiques fournit un filet de sécurité.

Cependant, approuver constamment chaque action peut ralentir votre flux de travail, surtout pour les tâches répétitives ou à faible risque. C'est là que la **configuration des permissions** et le **mode YOLO** entrent en jeu.

## Part 1: Understanding the Permission System / Partie 1: Comprendre le système de permissions (10 minutes)

### Default Behavior / Comportement par défaut

**English**:
When you start Claude Code, it operates in a **safe mode** by default. This means:

1. **File Operations**: Claude asks before writing, editing, or deleting files
2. **Bash Commands**: Claude asks before running shell commands
3. **MCP Tools**: Claude asks before using Model Context Protocol tools

When Claude wants to perform an action, you'll see a prompt like:
```
Claude wants to run: npm install express
Allow? [y/n/a]
```

Response options:
- `y` (yes): Allow this specific action
- `n` (no): Deny this action
- `a` (always): Allow this type of action for the session

**Français**:
Quand vous démarrez Claude Code, il fonctionne en **mode sécurisé** par défaut. Cela signifie :

1. **Opérations de fichiers**: Claude demande avant d'écrire, modifier ou supprimer des fichiers
2. **Commandes Bash**: Claude demande avant d'exécuter des commandes shell
3. **Outils MCP**: Claude demande avant d'utiliser les outils Model Context Protocol

Quand Claude veut effectuer une action, vous verrez un prompt comme :
```
Claude veut exécuter : npm install express
Autoriser ? [y/n/a]
```

Options de réponse :
- `y` (yes/oui): Autoriser cette action spécifique
- `n` (no/non): Refuser cette action
- `a` (always/toujours): Autoriser ce type d'action pour la session

### Types of Permissions / Types de permissions

**English**:

| Permission Type | Default | Risk Level | Examples |
|----------------|---------|------------|----------|
| Read files | ✅ Allowed | Low | Reading source code, configs |
| Write/Edit files | ⚠️ Ask | Medium | Modifying code, creating files |
| Delete files | ⚠️ Ask | High | Removing files or directories |
| Bash commands | ⚠️ Ask | Variable | Running scripts, installing packages |
| Network requests | ⚠️ Ask | Medium | API calls, web fetches |
| System commands | ⚠️ Ask | High | System configuration changes |

**Français**:

| Type de permission | Défaut | Niveau de risque | Exemples |
|-------------------|--------|------------------|----------|
| Lire fichiers | ✅ Autorisé | Faible | Lire code source, configs |
| Écrire/Modifier fichiers | ⚠️ Demander | Moyen | Modifier code, créer fichiers |
| Supprimer fichiers | ⚠️ Demander | Élevé | Supprimer fichiers ou répertoires |
| Commandes Bash | ⚠️ Demander | Variable | Exécuter scripts, installer packages |
| Requêtes réseau | ⚠️ Demander | Moyen | Appels API, récupération web |
| Commandes système | ⚠️ Demander | Élevé | Changements configuration système |

## Part 2: Configuring Permissions / Partie 2: Configurer les permissions (10 minutes)

### Viewing Current Settings / Voir les paramètres actuels

**English**: To see your current permission settings:

**Français**: Pour voir vos paramètres de permission actuels :

```bash
# View all settings / Voir tous les paramètres
/config
```

### Allowlist Approach / Approche allowlist

**English**:
The **allowlist** approach lets you pre-approve specific commands or patterns. This is the recommended approach for most users.

**Français**:
L'approche **allowlist** vous permet de pré-approuver des commandes ou patterns spécifiques. C'est l'approche recommandée pour la plupart des utilisateurs.

**Example configurations / Exemples de configuration**:

```bash
# Allow specific git commands / Autoriser des commandes git spécifiques
/allowed-tools Bash(git status)
/allowed-tools Bash(git diff*)
/allowed-tools Bash(git add*)
/allowed-tools Bash(git commit*)

# Allow npm/yarn commands / Autoriser les commandes npm/yarn
/allowed-tools Bash(npm install*)
/allowed-tools Bash(npm run*)
/allowed-tools Bash(yarn*)

# Allow Python execution / Autoriser l'exécution Python
/allowed-tools Bash(python*)
/allowed-tools Bash(pytest*)
```

**Pattern Syntax / Syntaxe des patterns**:
- `*` matches any characters / correspond à n'importe quels caractères
- Exact match: `git status` only matches exactly `git status` / correspond exactement à `git status`
- Prefix match: `git*` matches anything starting with `git` / correspond à tout ce qui commence par `git`

### Session vs. Project vs. User Settings / Paramètres de session vs. projet vs. utilisateur

**English**:
Permissions can be configured at three levels:

1. **Session**: Only lasts for the current Claude Code session (temporary)
2. **Project**: Saved in `.claude/settings.json` in your project (shared with team)
3. **User**: Saved in `~/.claude/settings.json` (personal, all projects)

**Français**:
Les permissions peuvent être configurées à trois niveaux :

1. **Session**: Dure uniquement pour la session Claude Code actuelle (temporaire)
2. **Projet**: Sauvegardé dans `.claude/settings.json` dans votre projet (partagé avec l'équipe)
3. **Utilisateur**: Sauvegardé dans `~/.claude/settings.json` (personnel, tous les projets)

```bash
# Add to project settings / Ajouter aux paramètres du projet
/allowed-tools --project Bash(npm run build)

# Add to user settings / Ajouter aux paramètres utilisateur
/allowed-tools --user Bash(git*)
```

### Exercise A: Configure Your Permissions / Exercice A: Configurer vos permissions

**English**: Set up a sensible permission configuration for a typical Node.js project.

**Français**: Configurez une configuration de permissions sensée pour un projet Node.js typique.

**Steps / Étapes**:
1. Open Claude Code in a project directory / Ouvrez Claude Code dans un répertoire de projet
2. Allow common git operations / Autorisez les opérations git courantes
3. Allow npm/yarn commands / Autorisez les commandes npm/yarn
4. Allow test execution / Autorisez l'exécution des tests
5. Verify with `/config` / Vérifiez avec `/config`

```bash
# Your configuration / Votre configuration
/allowed-tools Bash(git status)
/allowed-tools Bash(git diff*)
/allowed-tools Bash(git add*)
/allowed-tools Bash(git commit*)
/allowed-tools Bash(git push*)
/allowed-tools Bash(git pull*)
/allowed-tools Bash(npm*)
/allowed-tools Bash(yarn*)
/allowed-tools Bash(npx jest*)
/allowed-tools Bash(npx prettier*)
/allowed-tools Bash(npx eslint*)
```

## Part 3: YOLO Mode / Partie 3: Mode YOLO (10 minutes)

### What is YOLO Mode? / Qu'est-ce que le mode YOLO ?

**English**:
**YOLO Mode** (You Only Live Once) is the ultimate convenience feature that **auto-approves all operations** without asking for permission. When enabled, Claude will execute any action immediately without prompting you.

⚠️ **WARNING**: YOLO mode is powerful but potentially dangerous. Use it only when you fully trust the task and environment.

**Français**:
Le **Mode YOLO** (You Only Live Once / On ne vit qu'une fois) est la fonctionnalité de commodité ultime qui **approuve automatiquement toutes les opérations** sans demander de permission. Quand il est activé, Claude exécutera toute action immédiatement sans vous solliciter.

⚠️ **AVERTISSEMENT**: Le mode YOLO est puissant mais potentiellement dangereux. Utilisez-le uniquement quand vous faites entièrement confiance à la tâche et à l'environnement.

### Enabling YOLO Mode / Activer le mode YOLO

**English**: There are several ways to enable YOLO mode:

**Français**: Il y a plusieurs façons d'activer le mode YOLO :

**Method 1: Command Line Flag / Méthode 1: Option en ligne de commande**
```bash
# Start Claude Code in YOLO mode
claude --dangerously-skip-permissions
```

**Method 2: During Session / Méthode 2: Pendant la session**
```bash
# Enable YOLO mode for current session
/dangerously-skip-permissions
```

### When to Use YOLO Mode / Quand utiliser le mode YOLO

**English**:

**✅ Safe scenarios for YOLO mode**:
- Working in a disposable development container (Docker)
- Testing in a sandboxed environment
- Running well-understood, repetitive tasks
- Personal projects where mistakes are easily reversible
- Following along with tutorials in isolated environments
- Using with Ralph Wiggum for autonomous loops (TP2)

**❌ Dangerous scenarios - NEVER use YOLO mode**:
- Production environments
- Repositories with sensitive data
- Shared team repositories (without team consent)
- When working with credentials or secrets
- Unfamiliar codebases
- When you haven't clearly defined the task

**Français**:

**✅ Scénarios sûrs pour le mode YOLO**:
- Travailler dans un conteneur de développement jetable (Docker)
- Tester dans un environnement sandboxé
- Exécuter des tâches répétitives bien comprises
- Projets personnels où les erreurs sont facilement réversibles
- Suivre des tutoriels dans des environnements isolés
- Utiliser avec Ralph Wiggum pour des boucles autonomes (TP2)

**❌ Scénarios dangereux - NE JAMAIS utiliser le mode YOLO**:
- Environnements de production
- Dépôts avec des données sensibles
- Dépôts d'équipe partagés (sans consentement de l'équipe)
- Quand vous travaillez avec des credentials ou secrets
- Codebases non familiers
- Quand vous n'avez pas clairement défini la tâche

### Safety Precautions / Précautions de sécurité

**English**:
If you decide to use YOLO mode, follow these safety guidelines:

1. **Use Git**: Always have uncommitted changes backed up or be on a clean branch
2. **Set boundaries**: Use `--max-turns` to limit the number of actions
3. **Work in isolation**: Use containers or VMs when possible
4. **Review after**: Always review what changes were made
5. **Have an exit strategy**: Know how to stop (Ctrl+C) and revert (git checkout .)

**Français**:
Si vous décidez d'utiliser le mode YOLO, suivez ces directives de sécurité :

1. **Utilisez Git**: Ayez toujours les changements non commités sauvegardés ou soyez sur une branche propre
2. **Définissez des limites**: Utilisez `--max-turns` pour limiter le nombre d'actions
3. **Travaillez en isolation**: Utilisez des conteneurs ou VMs quand possible
4. **Révisez après**: Révisez toujours quels changements ont été faits
5. **Ayez une stratégie de sortie**: Sachez comment arrêter (Ctrl+C) et annuler (git checkout .)

### Exercise B: Safe YOLO Experimentation / Exercice B: Expérimentation YOLO sécurisée

**English**: Practice using YOLO mode in a safe environment.

**Français**: Pratiquez l'utilisation du mode YOLO dans un environnement sécurisé.

**Steps / Étapes**:

1. Create a new test directory / Créez un nouveau répertoire de test:
```bash
mkdir ~/yolo-test && cd ~/yolo-test
git init
echo "# YOLO Test" > README.md
git add . && git commit -m "Initial commit"
```

2. Start Claude Code in YOLO mode / Démarrez Claude Code en mode YOLO:
```bash
claude --dangerously-skip-permissions
```

3. Give Claude a multi-step task / Donnez à Claude une tâche en plusieurs étapes:
```
Create a simple Python calculator module with add, subtract, multiply, and divide functions.
Then create a test file and run the tests.
```

4. Observe how Claude executes without prompts / Observez comment Claude exécute sans invites

5. Review the changes / Révisez les changements:
```bash
git diff
git status
```

6. Clean up / Nettoyez:
```bash
cd ~ && rm -rf ~/yolo-test
```

### Combining YOLO with Ralph Wiggum / Combiner YOLO avec Ralph Wiggum

**English**:
YOLO mode is often used together with Ralph Wiggum (TP2) for fully autonomous coding sessions:

```bash
# Start Claude Code in YOLO mode
claude --dangerously-skip-permissions

# Then use Ralph Wiggum for autonomous loops
/ralph-wiggum:ralph-loop "implement feature X with tests" --completion-promise "DONE" --max-iterations 10
```

This combination allows Claude to work completely autonomously, iterating until the task is complete.

**Français**:
Le mode YOLO est souvent utilisé avec Ralph Wiggum (TP2) pour des sessions de codage entièrement autonomes :

```bash
# Démarrez Claude Code en mode YOLO
claude --dangerously-skip-permissions

# Puis utilisez Ralph Wiggum pour des boucles autonomes
/ralph-wiggum:ralph-loop "implémenter la fonctionnalité X avec des tests" --completion-promise "DONE" --max-iterations 10
```

Cette combinaison permet à Claude de travailler de manière complètement autonome, itérant jusqu'à ce que la tâche soit terminée.

## Best Practices Summary / Résumé des meilleures pratiques

### Permission Configuration / Configuration des permissions

**English**:
| Situation | Recommendation |
|-----------|----------------|
| Daily development | Allowlist common safe commands |
| Team project | Use project-level settings in `.claude/settings.json` |
| Personal tools | Use user-level settings for consistency |
| Sensitive work | Keep default (ask for everything) |
| Learning/tutorials | YOLO mode in isolated environment |

**Français**:
| Situation | Recommandation |
|-----------|----------------|
| Développement quotidien | Allowlist des commandes sûres courantes |
| Projet d'équipe | Utiliser paramètres niveau projet dans `.claude/settings.json` |
| Outils personnels | Utiliser paramètres niveau utilisateur pour la cohérence |
| Travail sensible | Garder le défaut (demander pour tout) |
| Apprentissage/tutoriels | Mode YOLO dans environnement isolé |

### Decision Flowchart / Organigramme de décision

**English**:
```
Is this a production environment?
  → YES: Never use YOLO mode, use conservative allowlist

Is this a sandboxed/disposable environment?
  → YES: YOLO mode is acceptable

Do I fully understand what Claude will do?
  → NO: Don't use YOLO mode
  → YES: Consider YOLO for efficiency

Am I using version control?
  → NO: Don't use YOLO mode
  → YES: YOLO is safer (can revert)
```

**Français**:
```
Est-ce un environnement de production ?
  → OUI: Ne jamais utiliser le mode YOLO, utiliser une allowlist conservatrice

Est-ce un environnement sandboxé/jetable ?
  → OUI: Le mode YOLO est acceptable

Est-ce que je comprends entièrement ce que Claude va faire ?
  → NON: Ne pas utiliser le mode YOLO
  → OUI: Considérer YOLO pour l'efficacité

Est-ce que j'utilise le contrôle de version ?
  → NON: Ne pas utiliser le mode YOLO
  → OUI: YOLO est plus sûr (peut annuler)
```

## Expected Outcomes / Résultats attendus

**English**: After completing this TP, you should have:

**Français**: Après avoir complété ce TP, vous devriez avoir :

- ✅ Understanding of Claude Code's permission system / Compréhension du système de permissions de Claude Code
- ✅ Configured allowlist for common operations / Configuré une allowlist pour les opérations courantes
- ✅ Experimented with YOLO mode safely / Expérimenté le mode YOLO en toute sécurité
- ✅ Ability to make informed security decisions / Capacité à prendre des décisions de sécurité éclairées

## Troubleshooting / Dépannage

### Problem / Problème: Permission keeps getting asked for allowed command

**English - Solutions**:
- Check exact command syntax matches your allowlist pattern
- Verify the setting was saved (use `/config` to check)
- Remember that patterns are case-sensitive

**Français - Solutions**:
- Vérifiez que la syntaxe exacte de la commande correspond à votre pattern allowlist
- Vérifiez que le paramètre a été sauvegardé (utilisez `/config` pour vérifier)
- Rappelez-vous que les patterns sont sensibles à la casse

### Problem / Problème: YOLO mode seems to have stopped

**English - Solutions**:
- YOLO mode is session-only by default
- Restart with `--dangerously-skip-permissions` flag
- Check if you hit a hard limit (like network errors)

**Français - Solutions**:
- Le mode YOLO est limité à la session par défaut
- Redémarrez avec l'option `--dangerously-skip-permissions`
- Vérifiez si vous avez atteint une limite dure (comme des erreurs réseau)

### Problem / Problème: Want to disable YOLO mode mid-session

**English - Solution**: Simply restart Claude Code without the flag, or press Ctrl+C to exit.

**Français - Solution**: Redémarrez simplement Claude Code sans l'option, ou appuyez sur Ctrl+C pour quitter.

## Additional Resources / Ressources supplémentaires

**English**:
- [Claude Code Documentation - Permissions](https://docs.anthropic.com/claude-code/permissions)
- [Claude Code Security Best Practices](https://docs.anthropic.com/claude-code/security)
- [TP2: Ralph Wiggum - For autonomous loops](./TP2-Ralph-Wiggum-Autonomous-Loops.md)

**Français**:
- [Documentation Claude Code - Permissions](https://docs.anthropic.com/claude-code/permissions)
- [Meilleures pratiques de sécurité Claude Code](https://docs.anthropic.com/claude-code/security)
- [TP2: Ralph Wiggum - Pour les boucles autonomes](./TP2-Ralph-Wiggum-Autonomous-Loops.md)

## Submission / Soumission

**English**: To complete this TP, submit:

**Français**: Pour compléter ce TP, soumettre :

1. **Screenshot / Capture d'écran**:
   - Your `/config` output showing your allowlist configuration / Votre sortie `/config` montrant votre configuration allowlist

2. **Configuration file / Fichier de configuration**:
   - Your `.claude/settings.json` if you created project-level settings / Votre `.claude/settings.json` si vous avez créé des paramètres niveau projet

3. **Reflection / Réflexion** (3-5 sentences / phrases):
   - **English**: What is your philosophy on permission configuration? Do you prefer asking for everything, allowlisting common commands, or using YOLO mode? Why? What scenarios would change your approach?
   - **Français**: Quelle est votre philosophie sur la configuration des permissions ? Préférez-vous demander pour tout, créer une allowlist des commandes courantes, ou utiliser le mode YOLO ? Pourquoi ? Quels scénarios changeraient votre approche ?

---

**English**: **Congratulations!** You now understand how to balance security and convenience when using Claude Code. Remember: with great power comes great responsibility. Use YOLO mode wisely!

**Français**: **Félicitations !** Vous comprenez maintenant comment équilibrer sécurité et commodité en utilisant Claude Code. Rappelez-vous : un grand pouvoir implique de grandes responsabilités. Utilisez le mode YOLO avec sagesse !
