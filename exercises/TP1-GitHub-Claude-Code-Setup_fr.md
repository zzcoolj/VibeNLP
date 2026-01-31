# TP1: Configuration de GitHub avec Claude Code

**Durée**: 30 minutes
**Niveau**: Débutant
**Prérequis**: Compte GitHub, connaissances de base de Git

## Objectifs d'apprentissage

À la fin de cet exercice pratique, vous serez capable de :
- Configurer l'intégration GitHub de Claude Code dans votre dépôt
- Déclencher Claude Code via les issues GitHub
- Comprendre le workflow de base pour travailler avec Claude Code

## Introduction

Claude Code est un assistant IA qui peut vous aider avec des tâches de codage directement via GitHub. Une fois configuré, vous pouvez mentionner `@claude` dans les issues ou les pull requests, et Claude répondra automatiquement pour vous aider avec votre demande.

## Partie 1: Configuration du dépôt (10 minutes)

### Étape 1: Fork ou créer un dépôt

1. Allez sur GitHub et soit :
   - Forkez un dépôt existant, OU
   - Créez un nouveau dépôt pour cet exercice

2. Assurez-vous que votre dépôt est :
   - Public OU privé (si vous avez accès aux GitHub Apps pour les dépôts privés)
   - Contient au moins un fichier (comme un README.md)

### Étape 2: Installer l'application GitHub Claude Code

Ouvrez Claude Code dans le terminal et exécutez ```/install-github-app```, suivez les instructions
[Référence](https://code.claude.com/docs/en/github-actions)

## Partie 2: Configuration de base (5 minutes)

### Étape 3: Créer un fichier CLAUDE.md (optionnel mais recommandé)

Créez un fichier nommé `CLAUDE.md` à la racine de votre dépôt. Ce fichier donne à Claude le contexte de votre projet.

Exemple de contenu :
```markdown
# CLAUDE.md

## Aperçu du projet

Ceci est un dépôt d'entraînement pour apprendre à utiliser Claude Code avec GitHub.

## Directives de développement

- Garder le code simple et bien commenté
- Suivre le guide de style Python PEP 8
- Écrire des messages de commit clairs
```

**Pourquoi c'est important**: Le fichier CLAUDE.md aide Claude à comprendre le contexte de votre projet, les standards de codage et les préférences.

## Partie 3: Test de l'intégration (10 minutes)

### Étape 4: Créer votre première issue

1. Allez dans l'onglet **Issues** de votre dépôt
2. Cliquez sur **"New Issue"**
3. Entrez un titre : `Test de l'intégration Claude Code`
4. Dans la description, tapez :
   ```
   @claude Bonjour ! Pouvez-vous m'aider à créer une fonction Python simple qui additionne deux nombres ?
   ```
5. Cliquez sur **"Submit new issue"**

### Étape 5: Observer la réponse de Claude

1. Attendez quelques instants (généralement 10-30 secondes)
2. Claude publiera automatiquement un commentaire sur votre issue
3. Claude affichera une liste de tâches sur lesquelles il travaille
4. Observez Claude :
   - Créer le code demandé
   - Commiter les changements dans une nouvelle branche
   - Fournir un lien pour créer une pull request

### Étape 6: Réviser le travail de Claude

1. Cliquez sur le lien de la branche fourni par Claude
2. Révisez le code créé par Claude
3. Si Claude a créé un lien PR, cliquez dessus pour créer une pull request
4. Révisez la pull request et fusionnez-la si tout semble correct

## Partie 4: Scénarios de pratique (5 minutes)

Maintenant que vous comprenez les bases, essayez ces exercices supplémentaires :

### Exercice A: Revue de code
Créez une nouvelle issue et demandez :
```
@claude Pouvez-vous revoir ce code et suggérer des améliorations ?
[collez du code simple]
```

### Exercice B: Correction de bug
Créez une issue avec :
```
@claude J'ai un bug dans mon code à la ligne X. Pouvez-vous m'aider à le corriger ?
```

### Exercice C: Documentation
Demandez à Claude :
```
@claude Pouvez-vous ajouter de la documentation à mon fichier Python principal ?
```

## Résultats attendus

Après avoir complété ce TP, vous devriez avoir :
- ✅ Une intégration Claude Code fonctionnelle dans votre dépôt
- ✅ Au moins une issue résolue avec succès grâce à l'aide de Claude
- ✅ Une compréhension du workflow de base : Issue → Réponse Claude → Branche → PR → Fusion
- ✅ Un fichier CLAUDE.md avec le contexte du projet

## Dépannage

### Problème: Claude ne répond pas à mon issue
**Solutions**:
- Assurez-vous d'avoir tapé `@claude` (pas @Claude ou @CLAUDE)
- Vérifiez que l'application GitHub est correctement installée
- Vérifiez que l'issue est dans un dépôt où Claude est installé
- Attendez un peu plus longtemps (parfois cela prend jusqu'à une minute)

### Problème: Claude crée du code mais je ne le vois pas
**Solution**:
- Claude crée automatiquement une nouvelle branche
- Cherchez le nom de la branche dans le commentaire de Claude
- Cliquez sur le lien de la branche pour voir le code

### Problème: Je veux donner des instructions plus spécifiques à Claude
**Solution**:
- Utilisez le fichier CLAUDE.md pour définir les préférences au niveau du projet
- Soyez spécifique dans la description de votre issue
- Incluez des extraits de code, des chemins de fichiers et des exigences claires

## Meilleures pratiques

1. **Soyez spécifique**: Plus vous fournissez de détails, mieux Claude peut vous aider
2. **Utilisez CLAUDE.md**: Configurez des directives de projet pour des résultats cohérents
3. **Révisez tout**: Révisez toujours le code de Claude avant de fusionner
4. **Itérez**: Si la première tentative de Claude n'est pas parfaite, demandez des améliorations dans un commentaire de suivi
5. **Commencez petit**: Commencez par des tâches simples pour comprendre le workflow

## Ressources supplémentaires

- [Documentation Claude Code](https://github.com/anthropics/claude-code)
- [Claude Code GitHub Action](https://github.com/anthropics/claude-code-action)
- [Exemples de fichiers CLAUDE.md](https://github.com/search?q=filename%3ACLAUDE.md)

## Soumission

Pour compléter ce TP, soumettez :
1. Lien vers votre dépôt avec Claude Code installé
2. Lien vers au moins une issue où Claude vous a aidé avec succès
3. Capture d'écran de votre pull request fusionnée
4. Brève réflexion (2-3 phrases) : Quelle tâche pensez-vous que Claude Code serait le plus utile pour vos projets ?

---

**Félicitations !** Vous avez configuré et testé avec succès Claude Code avec GitHub. Vous pouvez maintenant utiliser cet outil puissant pour vous aider avec les tâches de codage, les revues de code, la documentation, et plus encore.
