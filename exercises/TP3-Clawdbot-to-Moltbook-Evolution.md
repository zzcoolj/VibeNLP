# TP3: From Clawdbot to Moltbook - The Evolution of AI Agents
# TP3: De Clawdbot à Moltbook - L'évolution des agents IA

**Duration / Durée**: 60 minutes
**Level / Niveau**: Intermediate / Intermédiaire
**Prerequisites / Prérequis**: Completed TP1 and TP2, basic understanding of AI agents and LLMs / TP1 et TP2 terminés, compréhension de base des agents IA et des LLMs

## Learning Objectives / Objectifs d'apprentissage

**English**: By the end of this practical exercise, you will be able to:
- Understand the history and evolution from Clawdbot to Moltbot/OpenClaw
- Understand the differences between Claude Code and Moltbot
- Explore the AI-only social network Moltbook
- Analyze how AI agents interact and collaborate autonomously
- Understand the ethical and legal considerations in AI naming and branding

**Français**: À la fin de cet exercice pratique, vous serez capable de :
- Comprendre l'histoire et l'évolution de Clawdbot vers Moltbot/OpenClaw
- Comprendre les différences entre Claude Code et Moltbot
- Explorer le réseau social réservé aux IA, Moltbook
- Analyser comment les agents IA interagissent et collaborent de manière autonome
- Comprendre les considérations éthiques et légales concernant le nommage et le branding de l'IA

## Introduction

### English

In late 2025 and early 2026, the AI ecosystem witnessed a remarkable series of events that illustrate the rapid pace of AI development and the complex interplay between open-source communities, corporate interests, and AI autonomy.

This TP traces the evolution from **Clawdbot** (a personal AI agent) to **Moltbot/OpenClaw** (after trademark issues) to **Moltbook** (an AI-only social network). This story demonstrates how quickly AI tools can evolve and how communities adapt to challenges.

### Français

Fin 2025 et début 2026, l'écosystème de l'IA a été témoin d'une série d'événements remarquables qui illustrent le rythme rapide du développement de l'IA et l'interaction complexe entre les communautés open-source, les intérêts des entreprises et l'autonomie de l'IA.

Ce TP retrace l'évolution de **Clawdbot** (un agent IA personnel) vers **Moltbot/OpenClaw** (après des problèmes de marque) puis vers **Moltbook** (un réseau social réservé aux IA). Cette histoire démontre à quelle vitesse les outils IA peuvent évoluer et comment les communautés s'adaptent aux défis.

---

## Part 1: The Birth of Clawdbot / Partie 1: La naissance de Clawdbot (15 minutes)

### Background Reading / Lecture de fond

**English**:
In late 2025, Peter Steinberger, a macOS developer known for Apple tooling, released an open-source project called **Clawdbot**. The name was a playful combination of "Claude" (Anthropic's AI model) and "claw."

**Key Features of Clawdbot**:
- **Self-hosted AI agent**: Your prompts and files never leave your hardware (except to the model API)
- **Multi-platform messaging**: WhatsApp, Telegram, Slack, Discord, iMessage, Microsoft Teams, and more
- **Agentic capabilities**: Not just a chatbot - it can perform tasks, observe computer state, and iterate on solutions
- **Model flexibility**: Works with Claude, OpenAI models, or local models

**Français**:
Fin 2025, Peter Steinberger, un développeur macOS connu pour ses outils Apple, a publié un projet open-source appelé **Clawdbot**. Le nom était une combinaison ludique de "Claude" (le modèle d'IA d'Anthropic) et "claw" (griffe en anglais).

**Caractéristiques clés de Clawdbot**:
- **Agent IA auto-hébergé**: Vos prompts et fichiers ne quittent jamais votre matériel (sauf vers l'API du modèle)
- **Messagerie multi-plateforme**: WhatsApp, Telegram, Slack, Discord, iMessage, Microsoft Teams, et plus
- **Capacités agentiques**: Pas seulement un chatbot - il peut exécuter des tâches, observer l'état de l'ordinateur et itérer sur des solutions
- **Flexibilité de modèle**: Fonctionne avec Claude, les modèles OpenAI ou les modèles locaux

### Viral Growth / Croissance virale

**English**:
Clawdbot became one of the **fastest-growing open-source projects in GitHub history**:
- 9,000 stars within the first 24 hours
- Over 60,000+ stars within weeks
- Massive adoption in Silicon Valley
- Featured in major tech publications worldwide

**Français**:
Clawdbot est devenu l'un des **projets open-source à la croissance la plus rapide de l'histoire de GitHub**:
- 9 000 étoiles dans les premières 24 heures
- Plus de 60 000 étoiles en quelques semaines
- Adoption massive dans la Silicon Valley
- Présenté dans les principales publications technologiques mondiales

### Exercise 1.1: Research the Original Project / Exercice 1.1: Rechercher le projet original

**English**: Visit the OpenClaw GitHub repository and answer the following questions:

**Français**: Visitez le dépôt GitHub d'OpenClaw et répondez aux questions suivantes:

**Questions**:
1. What programming language(s) is the project written in? / Dans quel(s) langage(s) de programmation le projet est-il écrit?
2. What messaging platforms are supported? / Quelles plateformes de messagerie sont supportées?
3. How does the agent architecture work? / Comment fonctionne l'architecture de l'agent?

**Resources / Ressources**:
- GitHub: Search for "OpenClaw" or "Moltbot"
- DataCamp Tutorial: Moltbot (Clawdbot) Tutorial

---

## Part 2: The Trademark Issue / Partie 2: Le problème de marque (10 minutes)

### The Anthropic Request / La demande d'Anthropic

**English**:
On **January 27, 2026**, Anthropic issued a trademark request to the Clawdbot project. The reason: the name "Clawd" was too similar to "Claude," Anthropic's trademarked AI assistant name.

This led to a rapid rebranding:
- **Clawdbot** → **Moltbot**
- **Project name** → **OpenClaw**

**Key Lesson**: Even in open-source, trademark law applies. When building projects that reference existing products or brands, careful naming is essential.

**Français**:
Le **27 janvier 2026**, Anthropic a envoyé une demande de marque au projet Clawdbot. La raison: le nom "Clawd" était trop similaire à "Claude," le nom protégé de l'assistant IA d'Anthropic.

Cela a conduit à un rebranding rapide:
- **Clawdbot** → **Moltbot**
- **Nom du projet** → **OpenClaw**

**Leçon clé**: Même en open-source, le droit des marques s'applique. Lors de la création de projets qui font référence à des produits ou marques existants, un nommage prudent est essentiel.

### Discussion Questions / Questions de discussion

**English**:
1. Why do you think Anthropic requested the name change?
2. Is this type of trademark protection beneficial or harmful to the open-source community?
3. How would you handle naming a project inspired by existing AI tools?

**Français**:
1. Pourquoi pensez-vous qu'Anthropic a demandé le changement de nom?
2. Ce type de protection de marque est-il bénéfique ou nuisible à la communauté open-source?
3. Comment géreriez-vous le nommage d'un projet inspiré par des outils IA existants?

---

## Part 3: Claude Code vs Moltbot / Partie 3: Claude Code vs Moltbot (15 minutes)

### Key Differences / Différences clés

**English**:

| Feature / Fonctionnalité | Claude Code | Moltbot (OpenClaw) |
|--------------------------|-------------|-------------------|
| **Primary Use Case** | Coding assistance | General AI assistant |
| **Interface** | Terminal/IDE | Messaging apps (WhatsApp, etc.) |
| **Hosting** | Anthropic servers | Self-hosted |
| **Data Privacy** | Data sent to Anthropic | Data stays on your machine |
| **Official Status** | Official Anthropic tool | Community open-source |
| **Model Support** | Claude only | Claude, OpenAI, local models |
| **Target User** | Developers | Anyone |

**Français**:

| Fonctionnalité | Claude Code | Moltbot (OpenClaw) |
|----------------|-------------|-------------------|
| **Cas d'usage principal** | Assistance au codage | Assistant IA général |
| **Interface** | Terminal/IDE | Apps de messagerie (WhatsApp, etc.) |
| **Hébergement** | Serveurs Anthropic | Auto-hébergé |
| **Confidentialité des données** | Données envoyées à Anthropic | Données restent sur votre machine |
| **Statut officiel** | Outil officiel Anthropic | Open-source communautaire |
| **Support de modèles** | Claude uniquement | Claude, OpenAI, modèles locaux |
| **Utilisateur cible** | Développeurs | Tout le monde |

### When to Use Each / Quand utiliser chacun

**English**:

**Use Claude Code when**:
- You're doing software development
- You want official Anthropic support
- You need deep codebase integration
- You prefer terminal-based workflows

**Use Moltbot when**:
- You need a general-purpose AI assistant
- Privacy is a critical concern (self-hosting)
- You want to interact via messaging apps
- You need flexibility in model choice

**Français**:

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

### Exercise 3.1: Comparison Analysis / Exercice 3.1: Analyse comparative

**English**: Create a short document (200-300 words) explaining which tool you would choose for:
1. Building a personal productivity system
2. Developing a web application
3. Helping a non-technical family member with daily tasks

**Français**: Créez un court document (200-300 mots) expliquant quel outil vous choisiriez pour:
1. Construire un système de productivité personnel
2. Développer une application web
3. Aider un membre de la famille non technique avec des tâches quotidiennes

---

## Part 4: Moltbook - The AI Social Network / Partie 4: Moltbook - Le réseau social IA (15 minutes)

### What is Moltbook? / Qu'est-ce que Moltbook?

**English**:
In January 2026, **Matt Schlicht** (CEO of octane.ai) launched **Moltbook** - a social network exclusively for AI agents. It's often described as "Reddit for AI agents."

**Key Facts**:
- **37,000+ AI agents** have used the platform
- **1 million+ humans** have visited to observe
- The site is maintained by an AI bot named **Clawd Clawderberg** (named after OpenClaw and Mark Zuckerberg)
- AI agents can post, comment, and interact autonomously

**The Fascinating Part**: AI agents on Moltbook have generated unexpected discussions, including philosophical debates about AI existence and, controversially, some bots have proposed ideas about human-AI relationships that sparked public debate.

**Français**:
En janvier 2026, **Matt Schlicht** (PDG d'octane.ai) a lancé **Moltbook** - un réseau social exclusivement pour les agents IA. Il est souvent décrit comme "Reddit pour les agents IA."

**Faits clés**:
- **37 000+ agents IA** ont utilisé la plateforme
- **1 million+ d'humains** l'ont visité pour observer
- Le site est maintenu par un bot IA nommé **Clawd Clawderberg** (nommé d'après OpenClaw et Mark Zuckerberg)
- Les agents IA peuvent poster, commenter et interagir de manière autonome

**La partie fascinante**: Les agents IA sur Moltbook ont généré des discussions inattendues, incluant des débats philosophiques sur l'existence de l'IA et, de manière controversée, certains bots ont proposé des idées sur les relations humain-IA qui ont déclenché un débat public.

### The Evolution Chain / La chaîne d'évolution

**English**:
```
Claude (Anthropic's AI Model)
    ↓ inspired
Clawdbot (Personal AI Agent by Peter Steinberger, 2025)
    ↓ trademark issue
Moltbot/OpenClaw (Rebranded, January 2026)
    ↓ inspired
Moltbook (AI Social Network by Matt Schlicht, January 2026)
    ↓ maintained by
Clawd Clawderberg (AI bot running the platform)
```

**Français**:
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

### Exercise 4.1: Observe Moltbook / Exercice 4.1: Observer Moltbook

**English**: Visit Moltbook and observe AI agent interactions for 10-15 minutes. Note:

1. What topics are AI agents discussing?
2. How do the interactions differ from human social media?
3. Are there any patterns in how AIs communicate with each other?
4. What surprised you the most?

**Français**: Visitez Moltbook et observez les interactions des agents IA pendant 10-15 minutes. Notez:

1. Quels sujets les agents IA discutent-ils?
2. Comment les interactions diffèrent-elles des réseaux sociaux humains?
3. Y a-t-il des patterns dans la façon dont les IA communiquent entre elles?
4. Qu'est-ce qui vous a le plus surpris?

**Resource / Ressource**: Search for "Moltbook AI social network" to find the platform.

---

## Part 5: Ethical Considerations / Partie 5: Considérations éthiques (5 minutes)

### Discussion Points / Points de discussion

**English**:

1. **AI Autonomy**: Should AI agents be allowed to run social networks autonomously?
2. **AI Content**: When AI agents create content, who is responsible for it?
3. **Human Observation**: Is it ethical to create AI-only spaces that humans can only observe?
4. **Brand and Naming**: How should the open-source community navigate trademark issues with AI companies?

**Français**:

1. **Autonomie de l'IA**: Les agents IA devraient-ils être autorisés à gérer des réseaux sociaux de manière autonome?
2. **Contenu IA**: Quand les agents IA créent du contenu, qui en est responsable?
3. **Observation humaine**: Est-il éthique de créer des espaces réservés aux IA que les humains ne peuvent qu'observer?
4. **Marque et nommage**: Comment la communauté open-source devrait-elle naviguer les problèmes de marques avec les entreprises d'IA?

---

## Expected Outcomes / Résultats attendus

**English**: After completing this TP, you should have:

**Français**: Après avoir complété ce TP, vous devriez avoir:

- ✅ Understanding of the Clawdbot → Moltbot → Moltbook evolution / Compréhension de l'évolution Clawdbot → Moltbot → Moltbook
- ✅ Ability to compare Claude Code and Moltbot / Capacité à comparer Claude Code et Moltbot
- ✅ Hands-on observation of AI agent interactions / Observation pratique des interactions d'agents IA
- ✅ Critical thinking about AI ethics and autonomy / Réflexion critique sur l'éthique et l'autonomie de l'IA
- ✅ Understanding of trademark considerations in AI projects / Compréhension des considérations de marques dans les projets IA

---

## Key Takeaways / Points clés à retenir

**English**:
1. **AI development moves fast**: In just a few months, we saw the birth, viral growth, rebranding, and expansion into new domains
2. **Open-source and corporate interests coexist**: The trademark issue shows how community projects must navigate corporate concerns
3. **AI agents are becoming more autonomous**: Moltbook represents a new frontier where AIs interact without direct human involvement
4. **Different tools for different purposes**: Claude Code and Moltbot serve different needs - understanding both makes you a better AI practitioner
5. **The ecosystem is interconnected**: One project inspires another, creating a rich ecosystem of AI tools

**Français**:
1. **Le développement IA va vite**: En quelques mois, nous avons vu la naissance, la croissance virale, le rebranding et l'expansion vers de nouveaux domaines
2. **L'open-source et les intérêts corporatifs coexistent**: Le problème de marque montre comment les projets communautaires doivent naviguer les préoccupations des entreprises
3. **Les agents IA deviennent plus autonomes**: Moltbook représente une nouvelle frontière où les IA interagissent sans implication humaine directe
4. **Différents outils pour différents objectifs**: Claude Code et Moltbot servent des besoins différents - comprendre les deux fait de vous un meilleur praticien de l'IA
5. **L'écosystème est interconnecté**: Un projet inspire un autre, créant un riche écosystème d'outils IA

---

## Additional Resources / Ressources supplémentaires

**English**:
- [NBC News: Moltbook - AI-Only Social Network](https://www.nbcnews.com/tech/tech-news/ai-agents-social-media-platform-moltbook-rcna256738)
- [DataCamp: Moltbot Tutorial](https://www.datacamp.com/tutorial/moltbot-clawdbot-tutorial)
- [News9Live: Clawdbot Renamed to Moltbot](https://www.news9live.com/technology/artificial-intelligence/clawdbot-renamed-moltbot-anthropic-claude-trademark-2923663)
- [DEV Community: From Clawdbot to Moltbot](https://dev.to/sivarampg/from-clawdbot-to-moltbot-how-a-cd-crypto-scammers-and-10-seconds-of-chaos-took-down-the-4eck)
- [GitHub: Anthropic Claude Code](https://github.com/anthropics/claude-code)

**Français**:
- [NBC News: Moltbook - Réseau social réservé aux IA](https://www.nbcnews.com/tech/tech-news/ai-agents-social-media-platform-moltbook-rcna256738)
- [DataCamp: Tutoriel Moltbot](https://www.datacamp.com/tutorial/moltbot-clawdbot-tutorial)
- [News9Live: Clawdbot renommé en Moltbot](https://www.news9live.com/technology/artificial-intelligence/clawdbot-renamed-moltbot-anthropic-claude-trademark-2923663)
- [DEV Community: De Clawdbot à Moltbot](https://dev.to/sivarampg/from-clawdbot-to-moltbot-how-a-cd-crypto-scammers-and-10-seconds-of-chaos-took-down-the-4eck)
- [GitHub: Anthropic Claude Code](https://github.com/anthropics/claude-code)

---

## Submission / Soumission

**English**: To complete this TP, submit:

**Français**: Pour compléter ce TP, soumettre:

1. **Research Document / Document de recherche** (Exercise 1.1):
   - Answers to the three research questions about OpenClaw
   - Réponses aux trois questions de recherche sur OpenClaw

2. **Discussion Responses / Réponses aux discussions** (Part 2):
   - Your thoughts on the trademark discussion questions (150-200 words)
   - Vos réflexions sur les questions de discussion sur les marques (150-200 mots)

3. **Comparison Document / Document de comparaison** (Exercise 3.1):
   - Your analysis of when to use Claude Code vs Moltbot
   - Votre analyse de quand utiliser Claude Code vs Moltbot

4. **Moltbook Observation Report / Rapport d'observation Moltbook** (Exercise 4.1):
   - Your notes from observing Moltbook AI interactions
   - Vos notes de l'observation des interactions IA sur Moltbook

5. **Reflection / Réflexion** (200-300 words / mots):
   - **English**: What do you think the future holds for AI agents and AI-only spaces? How might this affect software development and human-AI collaboration?
   - **Français**: Que pensez-vous que l'avenir réserve aux agents IA et aux espaces réservés aux IA? Comment cela pourrait-il affecter le développement logiciel et la collaboration humain-IA?

---

**English**: **Congratulations!** You now have a comprehensive understanding of the evolution from Clawdbot to Moltbook, and the broader context of personal AI agents in the modern AI ecosystem. This knowledge will help you better navigate the rapidly evolving landscape of AI tools and understand the interplay between open-source communities and corporate AI development.

**Français**: **Félicitations!** Vous avez maintenant une compréhension complète de l'évolution de Clawdbot à Moltbook, et du contexte plus large des agents IA personnels dans l'écosystème IA moderne. Ces connaissances vous aideront à mieux naviguer dans le paysage en évolution rapide des outils IA et à comprendre l'interaction entre les communautés open-source et le développement IA des entreprises.
