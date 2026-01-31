# TP2: Ralph Wiggum - Boucles autonomes avec Claude Code

**Durée**: 45 minutes
**Niveau**: Intermédiaire
**Prérequis**: TP1 terminé, Claude Code installé, compréhension de base des processus itératifs

## Objectifs d'apprentissage

À la fin de cet exercice pratique, vous serez capable de :
- Comprendre ce qu'est Ralph Wiggum et comment il permet l'itération autonome
- Installer et configurer le plugin Ralph Wiggum pour Claude Code
- Utiliser des boucles autonomes pour accomplir des tâches complexes en plusieurs étapes
- Comprendre les implications de coût et les considérations de sécurité
- Savoir quand utiliser des boucles autonomes par rapport à l'interaction manuelle

## Introduction

**Ralph Wiggum** est un plugin officiel de Claude Code qui permet des boucles d'itération autonomes. Nommé d'après le personnage des Simpson qui n'abandonne jamais, Ralph Wiggum permet à Claude de travailler de manière persistante sur des tâches complexes sans nécessiter d'intervention manuelle entre les étapes.

Traditionnellement, Claude Code s'arrête après avoir complété chaque réponse, vous obligeant à continuer manuellement la conversation. Ralph Wiggum change cela en interceptant le signal d'arrêt de Claude et en réinjectant automatiquement le prompt original, permettant à Claude d'itérer continuellement dans la même session jusqu'à ce que la tâche soit terminée ou qu'une limite d'itération maximale soit atteinte.

**Concept clé**: Pensez à Ralph Wiggum comme donnant à Claude de la "persistance" - la capacité de continuer à travailler sur un problème à travers plusieurs cycles de réflexion, tout comme un développeur pourrait itérer sur une solution plusieurs fois avant de la réussir.

## Partie 1: Comprendre Ralph Wiggum (10 minutes)

### Lecture de fond

Avant d'installer Ralph Wiggum, il est important de comprendre le concept et ses origines.

#### Lecture obligatoire
Lisez l'article original sur Ralph Wiggum :
- Article : [Ralph Wiggum - Boucles autonomes](https://ghuntley.com/ralph/)

#### Comprendre l'implémentation tierce

Le dépôt communautaire sur [github.com/frankbria/ralph-claude-code](https://github.com/frankbria/ralph-claude-code) était une implémentation tierce précoce qui fournissait des fonctionnalités supplémentaires comme la limitation de débit et les disjoncteurs.

**NOTE IMPORTANTE**: Vous n'avez PAS besoin de suivre les instructions d'installation de ce dépôt. Ralph Wiggum est maintenant officiellement intégré dans Claude Code, et nous utiliserons le plugin officiel à la place.

Le dépôt tiers est utile pour :
- Comprendre l'évolution conceptuelle
- Voir des exemples de cas d'usage
- Apprendre sur les fonctionnalités supplémentaires (limitation de débit, disjoncteurs)

### Comment fonctionne Ralph Wiggum

Ralph Wiggum utilise un mécanisme de **Stop hook** pour intercepter les tentatives de sortie de Claude :

1. Vous démarrez une tâche avec `/ralph-wiggum:ralph-loop "votre tâche" --completion-promise "DONE" --max-iterations 20`
2. Claude commence à travailler sur la tâche
3. Quand Claude s'arrêterait normalement, le Stop hook l'intercepte
4. Le prompt original est réinjecté dans la session
5. Claude continue à itérer avec le contexte complet des itérations précédentes
6. Cela continue jusqu'à ce que :
   - La condition de complétion soit remplie (ex: "DONE" est affiché)
   - Les itérations maximales soient atteintes
   - Vous annulez manuellement avec `/cancel-ralph`

## Partie 2: Installation (5 minutes)

### Étape 1: Ajouter le marché de plugins officiel

D'abord, assurez-vous d'avoir accès au marché de plugins officiel d'Anthropic.

```bash
# Ajouter le marché de plugins officiel d'Anthropic
/plugin marketplace add anthropics/claude-code
```

### Étape 2: Installer le plugin Ralph Wiggum

Installez le plugin Ralph Wiggum officiel.

```bash
# Installer le plugin Ralph Wiggum
/plugin install ralph-wiggum@claude-plugins-official
```

### Vérification

Vérifiez l'installation en listant vos plugins installés :

```bash
# Lister les plugins installés
/plugin list
```

Vous devriez voir `ralph-wiggum` dans la sortie.

## Partie 3: Utilisation de base (15 minutes)

### Démarrer une boucle autonome

La syntaxe de base pour démarrer une boucle Ralph est :

```bash
/ralph-wiggum:ralph-loop "description de votre tâche" --completion-promise "DONE" --max-iterations <nombre>
```

**Paramètres**:
- `"description de votre tâche"`: La tâche que vous voulez que Claude accomplisse
- `--max-iterations <nombre>`: Limite de sécurité (TOUJOURS DÉFINIR CECI)
- `--completion-promise "DONE"`: Le mot-clé que Claude devrait afficher quand il a terminé

### Exercice A: Tâche simple en plusieurs étapes

Essayons une tâche de boucle autonome simple.

**Tâche**:
```bash
/ralph-wiggum:ralph-loop "Créer une fonction Python pour calculer les nombres de Fibonacci, écrire des tests pour elle, exécuter les tests et corriger tout problème jusqu'à ce que tous les tests passent. Afficher DONE quand c'est terminé." --completion-promise "DONE" --max-iterations 10
```

**Ce qu'il faut observer**:
1. Claude créera la fonction
2. Claude écrira les tests
3. Claude exécutera les tests
4. Si les tests échouent, Claude corrigera le code automatiquement
5. Claude itérera jusqu'à ce que les tests passent ou que les itérations max soient atteintes
6. Claude affichera "DONE" en cas de succès

### Annuler une boucle en cours

Si vous devez arrêter une boucle en cours :

```bash
/cancel-ralph
```

## Partie 4: Conscience des coûts et sécurité (10 minutes)

### Implications de coût

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

### Meilleures pratiques pour la gestion des coûts

1. **Commencer petit**: Tester avec `--max-iterations 5` d'abord
2. **Être spécifique**: Des descriptions de tâches claires réduisent les itérations gaspillées
3. **Utiliser les promesses de complétion**: Aider Claude à savoir quand s'arrêter
4. **Surveiller les progrès**: Observer les premières itérations pour s'assurer que Claude est sur la bonne voie
5. **Annuler tôt**: Utiliser `/cancel-ralph` si les choses déraillent

### Quand utiliser Ralph Wiggum vs. interaction manuelle

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

## Partie 5: Exercices pratiques (15 minutes)

### Exercice B: Boucle de développement dirigée par les tests

Créez une tâche qui nécessite plusieurs itérations pour être réussie.

**Tâche**:
```bash
/ralph-wiggum:ralph-loop "Créer une classe Python pour une calculatrice simple avec des méthodes add, subtract, multiply et divide. Écrire des tests unitaires complets incluant les cas limites (division par zéro, grands nombres, nombres négatifs). Exécuter les tests et corriger tout échec. Afficher DONE quand tous les tests passent." --completion-promise "DONE" --max-iterations 15
```

### Exercice C: Génération de documentation

Utilisez Ralph pour créer une documentation complète.

**Tâche**:
```bash
/ralph-wiggum:ralph-loop "Analyser tous les fichiers Python dans le répertoire src/ et créer un README.md complet avec : description du projet, instructions d'installation, exemples d'utilisation pour chaque module, et documentation API. Vérifier que le formatage markdown est correct. Afficher DONE quand c'est terminé." --completion-promise "DONE" --max-iterations 8
```

### Exercice D: Défi de débogage

Laissez Ralph déboguer et corriger un morceau de code problématique.

**Tâche**:
```bash
/ralph-wiggum:ralph-loop "Trouver et corriger tous les bugs dans le fichier utils.py. Pour chaque bug trouvé : l'identifier, expliquer pourquoi c'est un bug, le corriger, et ajouter un cas de test pour prévenir la régression. Continuer jusqu'à ce qu'aucun bug ne soit trouvé ou que tous les tests passent. Afficher DONE quand c'est terminé." --completion-promise "DONE" --max-iterations 12
```

## Résultats attendus

Après avoir complété ce TP, vous devriez avoir :

- ✅ Compréhension de ce qu'est Ralph Wiggum et comment il fonctionne
- ✅ Plugin Ralph Wiggum installé avec succès
- ✅ Complété au moins une tâche de boucle autonome
- ✅ Compréhension des implications de coût
- ✅ Capacité à juger quand utiliser des boucles autonomes

## Dépannage

### Problème: La boucle Ralph ne s'arrête pas à la promesse de complétion

**Solutions**:
- Assurez-vous que votre promesse de complétion est claire et distinctive (ex: "TASK_COMPLETE", "DONE", "FINISHED")
- Vérifiez que Claude affiche réellement la chaîne de promesse
- Vérifiez que la chaîne de promesse correspond exactement (sensible à la casse)

### Problème: La boucle dépasse les itérations max sans se terminer

**Solutions**:
- La tâche peut être trop complexe - la diviser en sous-tâches plus petites
- La description de la tâche peut être peu claire - être plus spécifique
- Augmenter `--max-iterations` si la tâche est légitimement complexe
- Réviser les premières itérations pour voir si Claude fait des progrès

### Problème: Coûts d'API élevés

**Solutions**:
- Réduire `--max-iterations` pour les tests
- Utiliser des descriptions de tâches plus spécifiques
- Commencer avec des codebases plus petits
- Surveiller la première itération pour détecter les problèmes tôt
- Annuler immédiatement les boucles qui déraillent

## Points clés à retenir

1. **Ralph Wiggum permet la persistance**: Claude peut travailler sur des tâches en plusieurs étapes de manière autonome
2. **Toujours définir max-iterations**: C'est votre filet de sécurité contre les coûts incontrôlés
3. **Commencer petit et tester**: Utiliser de faibles nombres d'itérations pour les tests avant l'usage en production
4. **Des critères de complétion clairs aident**: Les tâches bien définies convergent plus rapidement
5. **La conscience des coûts est critique**: Surveiller l'utilisation des tokens et commencer avec de petites tâches
6. **C'est un outil puissant**: Excellent pour les tâches complexes, exagéré pour les simples

## Ressources supplémentaires

- [Article original sur Ralph Wiggum par Geoffrey Huntley](https://ghuntley.com/ralph/)
- [Implémentation communautaire (pour référence)](https://github.com/frankbria/ralph-claude-code)
- [Documentation officielle de Claude Code](https://github.com/anthropics/claude-code)
- [Marché des plugins Claude Code](https://github.com/anthropics/claude-code-plugins)

## Soumission

Pour compléter ce TP, soumettre :

1. **Captures d'écran**:
   - Confirmation d'installation du plugin Ralph
   - Au moins une complétion réussie d'une boucle Ralph

2. **Lien vers le dépôt de code**:
   - Dépôt montrant le travail complété par les boucles autonomes

3. **Réflexion** (5-7 phrases):
   Décrivez votre expérience avec Ralph Wiggum. Quelle tâche lui avez-vous donnée ? Combien d'itérations ont été nécessaires ? Avez-vous été surpris par quelque chose ? Quels sont les avantages et inconvénients par rapport à l'interaction manuelle avec Claude ? Utiliseriez-vous ceci pour de vrais projets ?

4. **Analyse des coûts**:
   Estimez l'utilisation des tokens pour vos boucles Ralph. Combien cela coûterait-il aux tarifs actuels de l'API ?

---

**Félicitations !** Vous comprenez maintenant comment utiliser Ralph Wiggum pour permettre à Claude Code de travailler de manière autonome sur des tâches complexes en plusieurs étapes. Utilisez ce pouvoir avec sagesse, toujours avec une conscience des coûts et des limites de sécurité appropriées.
