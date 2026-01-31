# TP3: Permissions Claude Code et Mode YOLO

**Durée**: 30 minutes
**Niveau**: Débutant-Intermédiaire
**Prérequis**: TP1 terminé, Claude Code installé

## Objectifs d'apprentissage

À la fin de cet exercice pratique, vous serez capable de :
- Comprendre le système de permissions de Claude Code et pourquoi il existe
- Configurer les règles de permission pour différentes opérations
- Connaître la différence entre les approches allowlist et blocklist
- Comprendre quand et comment utiliser le mode YOLO en toute sécurité
- Prendre des décisions éclairées sur les compromis sécurité vs. commodité

## Introduction

Claude Code fonctionne avec un **système de permissions** conçu pour vous protéger des actions non intentionnelles. Par défaut, Claude vous demandera votre approbation avant d'effectuer des opérations potentiellement risquées comme :

- Écrire ou modifier des fichiers
- Exécuter des commandes shell
- Effectuer des requêtes réseau
- Accéder à des répertoires sensibles

Ce système de permissions existe parce que les assistants IA peuvent faire des erreurs ou mal interpréter les instructions. Avoir un humain dans la boucle pour les opérations critiques fournit un filet de sécurité.

Cependant, approuver constamment chaque action peut ralentir votre flux de travail, surtout pour les tâches répétitives ou à faible risque. C'est là que la **configuration des permissions** et le **mode YOLO** entrent en jeu.

## Partie 1: Comprendre le système de permissions (10 minutes)

### Comportement par défaut

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

### Types de permissions

| Type de permission | Défaut | Niveau de risque | Exemples |
|-------------------|--------|------------------|----------|
| Lire fichiers | ✅ Autorisé | Faible | Lire code source, configs |
| Écrire/Modifier fichiers | ⚠️ Demander | Moyen | Modifier code, créer fichiers |
| Supprimer fichiers | ⚠️ Demander | Élevé | Supprimer fichiers ou répertoires |
| Commandes Bash | ⚠️ Demander | Variable | Exécuter scripts, installer packages |
| Requêtes réseau | ⚠️ Demander | Moyen | Appels API, récupération web |
| Commandes système | ⚠️ Demander | Élevé | Changements configuration système |

## Partie 2: Configurer les permissions (10 minutes)

### Voir les paramètres actuels

Pour voir vos paramètres de permission actuels :

```bash
# Voir tous les paramètres
/config
```

### Approche allowlist

L'approche **allowlist** vous permet de pré-approuver des commandes ou patterns spécifiques. C'est l'approche recommandée pour la plupart des utilisateurs.

**Exemples de configuration**:

```bash
# Autoriser des commandes git spécifiques
/allowed-tools Bash(git status)
/allowed-tools Bash(git diff*)
/allowed-tools Bash(git add*)
/allowed-tools Bash(git commit*)

# Autoriser les commandes npm/yarn
/allowed-tools Bash(npm install*)
/allowed-tools Bash(npm run*)
/allowed-tools Bash(yarn*)

# Autoriser l'exécution Python
/allowed-tools Bash(python*)
/allowed-tools Bash(pytest*)
```

**Syntaxe des patterns**:
- `*` correspond à n'importe quels caractères
- Correspondance exacte : `git status` correspond exactement à `git status`
- Correspondance de préfixe : `git*` correspond à tout ce qui commence par `git`

### Paramètres de session vs. projet vs. utilisateur

Les permissions peuvent être configurées à trois niveaux :

1. **Session**: Dure uniquement pour la session Claude Code actuelle (temporaire)
2. **Projet**: Sauvegardé dans `.claude/settings.json` dans votre projet (partagé avec l'équipe)
3. **Utilisateur**: Sauvegardé dans `~/.claude/settings.json` (personnel, tous les projets)

```bash
# Ajouter aux paramètres du projet
/allowed-tools --project Bash(npm run build)

# Ajouter aux paramètres utilisateur
/allowed-tools --user Bash(git*)
```

### Exercice A: Configurer vos permissions

Configurez une configuration de permissions sensée pour un projet Node.js typique.

**Étapes**:
1. Ouvrez Claude Code dans un répertoire de projet
2. Autorisez les opérations git courantes
3. Autorisez les commandes npm/yarn
4. Autorisez l'exécution des tests
5. Vérifiez avec `/config`

```bash
# Votre configuration
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

## Partie 3: Mode YOLO (10 minutes)

### Qu'est-ce que le mode YOLO ?

Le **Mode YOLO** (You Only Live Once / On ne vit qu'une fois) est la fonctionnalité de commodité ultime qui **approuve automatiquement toutes les opérations** sans demander de permission. Quand il est activé, Claude exécutera toute action immédiatement sans vous solliciter.

⚠️ **AVERTISSEMENT**: Le mode YOLO est puissant mais potentiellement dangereux. Utilisez-le uniquement quand vous faites entièrement confiance à la tâche et à l'environnement.

### Activer le mode YOLO

Il y a plusieurs façons d'activer le mode YOLO :

**Méthode 1: Option en ligne de commande**
```bash
# Démarrez Claude Code en mode YOLO
claude --dangerously-skip-permissions
```

**Méthode 2: Pendant la session**
```bash
# Activer le mode YOLO pour la session actuelle
/dangerously-skip-permissions
```

### Quand utiliser le mode YOLO

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

### Précautions de sécurité

Si vous décidez d'utiliser le mode YOLO, suivez ces directives de sécurité :

1. **Utilisez Git**: Ayez toujours les changements non commités sauvegardés ou soyez sur une branche propre
2. **Définissez des limites**: Utilisez `--max-turns` pour limiter le nombre d'actions
3. **Travaillez en isolation**: Utilisez des conteneurs ou VMs quand possible
4. **Révisez après**: Révisez toujours quels changements ont été faits
5. **Ayez une stratégie de sortie**: Sachez comment arrêter (Ctrl+C) et annuler (git checkout .)

### Exercice B: Expérimentation YOLO sécurisée

Pratiquez l'utilisation du mode YOLO dans un environnement sécurisé.

**Étapes**:

1. Créez un nouveau répertoire de test:
```bash
mkdir ~/yolo-test && cd ~/yolo-test
git init
echo "# YOLO Test" > README.md
git add . && git commit -m "Initial commit"
```

2. Démarrez Claude Code en mode YOLO:
```bash
claude --dangerously-skip-permissions
```

3. Donnez à Claude une tâche en plusieurs étapes:
```
Créer un module Python simple de calculatrice avec des fonctions add, subtract, multiply et divide.
Ensuite créer un fichier de test et exécuter les tests.
```

4. Observez comment Claude exécute sans invites

5. Révisez les changements:
```bash
git diff
git status
```

6. Nettoyez:
```bash
cd ~ && rm -rf ~/yolo-test
```

### Combiner YOLO avec Ralph Wiggum

Le mode YOLO est souvent utilisé avec Ralph Wiggum (TP2) pour des sessions de codage entièrement autonomes :

```bash
# Démarrez Claude Code en mode YOLO
claude --dangerously-skip-permissions

# Puis utilisez Ralph Wiggum pour des boucles autonomes
/ralph-wiggum:ralph-loop "implémenter la fonctionnalité X avec des tests" --completion-promise "DONE" --max-iterations 10
```

Cette combinaison permet à Claude de travailler de manière complètement autonome, itérant jusqu'à ce que la tâche soit terminée.

## Résumé des meilleures pratiques

### Configuration des permissions

| Situation | Recommandation |
|-----------|----------------|
| Développement quotidien | Allowlist des commandes sûres courantes |
| Projet d'équipe | Utiliser paramètres niveau projet dans `.claude/settings.json` |
| Outils personnels | Utiliser paramètres niveau utilisateur pour la cohérence |
| Travail sensible | Garder le défaut (demander pour tout) |
| Apprentissage/tutoriels | Mode YOLO dans environnement isolé |

### Organigramme de décision

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

## Résultats attendus

Après avoir complété ce TP, vous devriez avoir :

- ✅ Compréhension du système de permissions de Claude Code
- ✅ Configuré une allowlist pour les opérations courantes
- ✅ Expérimenté le mode YOLO en toute sécurité
- ✅ Capacité à prendre des décisions de sécurité éclairées

## Dépannage

### Problème: Permission demandée pour une commande autorisée

**Solutions**:
- Vérifiez que la syntaxe exacte de la commande correspond à votre pattern allowlist
- Vérifiez que le paramètre a été sauvegardé (utilisez `/config` pour vérifier)
- Rappelez-vous que les patterns sont sensibles à la casse

### Problème: Le mode YOLO semble avoir arrêté

**Solutions**:
- Le mode YOLO est limité à la session par défaut
- Redémarrez avec l'option `--dangerously-skip-permissions`
- Vérifiez si vous avez atteint une limite dure (comme des erreurs réseau)

### Problème: Vouloir désactiver le mode YOLO en cours de session

**Solution**: Redémarrez simplement Claude Code sans l'option, ou appuyez sur Ctrl+C pour quitter.

## Ressources supplémentaires

- [Documentation Claude Code - Permissions](https://docs.anthropic.com/claude-code/permissions)
- [Meilleures pratiques de sécurité Claude Code](https://docs.anthropic.com/claude-code/security)
- [TP2: Ralph Wiggum - Pour les boucles autonomes](./TP2-Ralph-Wiggum-Autonomous-Loops_fr.md)

## Soumission

Pour compléter ce TP, soumettre :

1. **Capture d'écran**:
   - Votre sortie `/config` montrant votre configuration allowlist

2. **Fichier de configuration**:
   - Votre `.claude/settings.json` si vous avez créé des paramètres niveau projet

3. **Réflexion** (3-5 phrases):
   Quelle est votre philosophie sur la configuration des permissions ? Préférez-vous demander pour tout, créer une allowlist des commandes courantes, ou utiliser le mode YOLO ? Pourquoi ? Quels scénarios changeraient votre approche ?

---

**Félicitations !** Vous comprenez maintenant comment équilibrer sécurité et commodité en utilisant Claude Code. Rappelez-vous : un grand pouvoir implique de grandes responsabilités. Utilisez le mode YOLO avec sagesse !
