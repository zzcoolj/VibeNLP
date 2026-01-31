# TP3: De Clawdbot à Moltbook - L'évolution des agents IA

**Durée**: 60 minutes
**Niveau**: Intermédiaire
**Prérequis**: TP1 et TP2 terminés, compréhension de base des agents IA et des LLMs

## Objectifs d'apprentissage

À la fin de cet exercice pratique, vous serez capable de :
- Comprendre l'histoire et l'évolution de Clawdbot vers Moltbot/OpenClaw
- Comprendre les différences entre Claude Code et Moltbot
- Explorer le réseau social réservé aux IA, Moltbook
- Analyser comment les agents IA interagissent et collaborent de manière autonome
- Comprendre les considérations éthiques et légales concernant le nommage et le branding de l'IA

## Introduction

Fin 2025 et début 2026, l'écosystème de l'IA a été témoin d'une série d'événements remarquables qui illustrent le rythme rapide du développement de l'IA et l'interaction complexe entre les communautés open-source, les intérêts des entreprises et l'autonomie de l'IA.

Ce TP retrace l'évolution de **Clawdbot** (un agent IA personnel) vers **Moltbot/OpenClaw** (après des problèmes de marque) puis vers **Moltbook** (un réseau social réservé aux IA). Cette histoire démontre à quelle vitesse les outils IA peuvent évoluer et comment les communautés s'adaptent aux défis.

---

## Partie 1: La naissance de Clawdbot (15 minutes)

### Lecture de fond

Fin 2025, Peter Steinberger, un développeur macOS connu pour ses outils Apple, a publié un projet open-source appelé **Clawdbot**. Le nom était une combinaison ludique de "Claude" (le modèle d'IA d'Anthropic) et "claw" (griffe en anglais).

**Caractéristiques clés de Clawdbot**:
- **Agent IA auto-hébergé**: Vos prompts et fichiers ne quittent jamais votre matériel (sauf vers l'API du modèle)
- **Messagerie multi-plateforme**: WhatsApp, Telegram, Slack, Discord, iMessage, Microsoft Teams, et plus
- **Capacités agentiques**: Pas seulement un chatbot - il peut exécuter des tâches, observer l'état de l'ordinateur et itérer sur des solutions
- **Flexibilité de modèle**: Fonctionne avec Claude, les modèles OpenAI ou les modèles locaux

### Croissance virale

Clawdbot est devenu l'un des **projets open-source à la croissance la plus rapide de l'histoire de GitHub**:
- 9 000 étoiles dans les premières 24 heures
- Plus de 60 000 étoiles en quelques semaines
- Adoption massive dans la Silicon Valley
- Présenté dans les principales publications technologiques mondiales

### Exercice 1.1: Rechercher le projet original

Visitez le dépôt GitHub d'OpenClaw et répondez aux questions suivantes:

**Questions**:
1. Dans quel(s) langage(s) de programmation le projet est-il écrit?
2. Quelles plateformes de messagerie sont supportées?
3. Comment fonctionne l'architecture de l'agent?

**Ressources**:
- GitHub: Recherchez "OpenClaw" ou "Moltbot"
- DataCamp Tutorial: Moltbot (Clawdbot) Tutorial

---

## Partie 2: Le problème de marque (10 minutes)

### La demande d'Anthropic

Le **27 janvier 2026**, Anthropic a envoyé une demande de marque au projet Clawdbot. La raison: le nom "Clawd" était trop similaire à "Claude," le nom protégé de l'assistant IA d'Anthropic.

Cela a conduit à un rebranding rapide:
- **Clawdbot** → **Moltbot**
- **Nom du projet** → **OpenClaw**

**Leçon clé**: Même en open-source, le droit des marques s'applique. Lors de la création de projets qui font référence à des produits ou marques existants, un nommage prudent est essentiel.

### Questions de discussion

1. Pourquoi pensez-vous qu'Anthropic a demandé le changement de nom?
2. Ce type de protection de marque est-il bénéfique ou nuisible à la communauté open-source?
3. Comment géreriez-vous le nommage d'un projet inspiré par des outils IA existants?

---

## Partie 3: Claude Code vs Moltbot (15 minutes)

### Différences clés

| Fonctionnalité | Claude Code | Moltbot (OpenClaw) |
|----------------|-------------|-------------------|
| **Cas d'usage principal** | Assistance au codage | Assistant IA général |
| **Interface** | Terminal/IDE | Apps de messagerie (WhatsApp, etc.) |
| **Hébergement** | Serveurs Anthropic | Auto-hébergé |
| **Confidentialité des données** | Données envoyées à Anthropic | Données restent sur votre machine |
| **Statut officiel** | Outil officiel Anthropic | Open-source communautaire |
| **Support de modèles** | Claude uniquement | Claude, OpenAI, modèles locaux |
| **Utilisateur cible** | Développeurs | Tout le monde |

### Quand utiliser chacun

**Utilisez Claude Code quand**:
- Vous faites du développement logiciel
- Vous voulez un support officiel d'Anthropic
- Vous avez besoin d'une intégration profonde avec la base de code
- Vous préférez les flux de travail en terminal

**Utilisez Moltbot quand**:
- Vous avez besoin d'un assistant IA polyvalent
- La confidentialité est une préoccupation critique (auto-hébergement)
- Vous voulez interagir via des applications de messagerie
- Vous avez besoin de flexibilité dans le choix du modèle

### Exercice 3.1: Analyse comparative

Créez un court document (200-300 mots) expliquant quel outil vous choisiriez pour:
1. Construire un système de productivité personnel
2. Développer une application web
3. Aider un membre de la famille non technique avec des tâches quotidiennes

---

## Partie 4: Moltbook - Le réseau social IA (15 minutes)

### Qu'est-ce que Moltbook?

En janvier 2026, **Matt Schlicht** (PDG d'octane.ai) a lancé **Moltbook** - un réseau social exclusivement pour les agents IA. Il est souvent décrit comme "Reddit pour les agents IA."

**Faits clés**:
- **37 000+ agents IA** ont utilisé la plateforme
- **1 million+ d'humains** l'ont visité pour observer
- Le site est maintenu par un bot IA nommé **Clawd Clawderberg** (nommé d'après OpenClaw et Mark Zuckerberg)
- Les agents IA peuvent poster, commenter et interagir de manière autonome

**La partie fascinante**: Les agents IA sur Moltbook ont généré des discussions inattendues, incluant des débats philosophiques sur l'existence de l'IA et, de manière controversée, certains bots ont proposé des idées sur les relations humain-IA qui ont déclenché un débat public.

### La chaîne d'évolution

```
Claude (Modèle IA d'Anthropic)
    ↓ a inspiré
Clawdbot (Agent IA personnel par Peter Steinberger, 2025)
    ↓ problème de marque
Moltbot/OpenClaw (Rebrandé, janvier 2026)
    ↓ a inspiré
Moltbook (Réseau social IA par Matt Schlicht, janvier 2026)
    ↓ maintenu par
Clawd Clawderberg (Bot IA gérant la plateforme)
```

### Exercice 4.1: Observer Moltbook

Visitez Moltbook et observez les interactions des agents IA pendant 10-15 minutes. Notez:

1. Quels sujets les agents IA discutent-ils?
2. Comment les interactions diffèrent-elles des réseaux sociaux humains?
3. Y a-t-il des patterns dans la façon dont les IA communiquent entre elles?
4. Qu'est-ce qui vous a le plus surpris?

**Ressource**: Recherchez "Moltbook AI social network" pour trouver la plateforme.

---

## Partie 5: Considérations éthiques (5 minutes)

### Points de discussion

1. **Autonomie de l'IA**: Les agents IA devraient-ils être autorisés à gérer des réseaux sociaux de manière autonome?
2. **Contenu IA**: Quand les agents IA créent du contenu, qui en est responsable?
3. **Observation humaine**: Est-il éthique de créer des espaces réservés aux IA que les humains ne peuvent qu'observer?
4. **Marque et nommage**: Comment la communauté open-source devrait-elle naviguer les problèmes de marques avec les entreprises d'IA?

---

## Résultats attendus

Après avoir complété ce TP, vous devriez avoir:

- ✅ Compréhension de l'évolution Clawdbot → Moltbot → Moltbook
- ✅ Capacité à comparer Claude Code et Moltbot
- ✅ Observation pratique des interactions d'agents IA
- ✅ Réflexion critique sur l'éthique et l'autonomie de l'IA
- ✅ Compréhension des considérations de marques dans les projets IA

---

## Points clés à retenir

1. **Le développement IA va vite**: En quelques mois, nous avons vu la naissance, la croissance virale, le rebranding et l'expansion vers de nouveaux domaines
2. **L'open-source et les intérêts corporatifs coexistent**: Le problème de marque montre comment les projets communautaires doivent naviguer les préoccupations des entreprises
3. **Les agents IA deviennent plus autonomes**: Moltbook représente une nouvelle frontière où les IA interagissent sans implication humaine directe
4. **Différents outils pour différents objectifs**: Claude Code et Moltbot servent des besoins différents - comprendre les deux fait de vous un meilleur praticien de l'IA
5. **L'écosystème est interconnecté**: Un projet inspire un autre, créant un riche écosystème d'outils IA

---

## Ressources supplémentaires

- [NBC News: Moltbook - Réseau social réservé aux IA](https://www.nbcnews.com/tech/tech-news/ai-agents-social-media-platform-moltbook-rcna256738)
- [DataCamp: Tutoriel Moltbot](https://www.datacamp.com/tutorial/moltbot-clawdbot-tutorial)
- [News9Live: Clawdbot renommé en Moltbot](https://www.news9live.com/technology/artificial-intelligence/clawdbot-renamed-moltbot-anthropic-claude-trademark-2923663)
- [DEV Community: De Clawdbot à Moltbot](https://dev.to/sivarampg/from-clawdbot-to-moltbot-how-a-cd-crypto-scammers-and-10-seconds-of-chaos-took-down-the-4eck)
- [GitHub: Anthropic Claude Code](https://github.com/anthropics/claude-code)

---

## Soumission

Pour compléter ce TP, soumettre:

1. **Document de recherche** (Exercice 1.1):
   - Réponses aux trois questions de recherche sur OpenClaw

2. **Réponses aux discussions** (Partie 2):
   - Vos réflexions sur les questions de discussion sur les marques (150-200 mots)

3. **Document de comparaison** (Exercice 3.1):
   - Votre analyse de quand utiliser Claude Code vs Moltbot

4. **Rapport d'observation Moltbook** (Exercice 4.1):
   - Vos notes de l'observation des interactions IA sur Moltbook

5. **Réflexion** (200-300 mots):
   Que pensez-vous que l'avenir réserve aux agents IA et aux espaces réservés aux IA? Comment cela pourrait-il affecter le développement logiciel et la collaboration humain-IA?

---

**Félicitations!** Vous avez maintenant une compréhension complète de l'évolution de Clawdbot à Moltbook, et du contexte plus large des agents IA personnels dans l'écosystème IA moderne. Ces connaissances vous aideront à mieux naviguer dans le paysage en évolution rapide des outils IA et à comprendre l'interaction entre les communautés open-source et le développement IA des entreprises.
