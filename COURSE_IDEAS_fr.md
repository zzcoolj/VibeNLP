# Idées de cours

Ce document contient des idées en évolution pour le contenu du cours.

---

## Sujets à couvrir

### 1. Plongements de mots statiques (Static Word Embeddings)

Fondement du NLP moderne - représenter les mots comme des vecteurs denses dans un espace continu.

- **Word2Vec**
  - Architectures Skip-gram et CBOW
  - Techniques d'entraînement
  - Applications et limitations

- **GloVe (Global Vectors)**
  - Approche par factorisation matricielle
  - Comparaison avec Word2Vec
  - Cas d'usage

**Suggestions**:
- Inclure des exercices pratiques pour entraîner des plongements sur des ensembles de données personnalisés
- Visualiser les plongements avec t-SNE ou UMAP
- Discuter des relations sémantiques et des analogies

---

### 2. Transformeurs (Transformers)

Architecture moderne qui a révolutionné le NLP grâce aux mécanismes d'attention.

- **BERT (Bidirectional Encoder Representations from Transformers)**
  - Mécanisme d'auto-attention
  - Paradigme de pré-entraînement et d'affinement
  - Modélisation de langage masqué
  - Applications: classification, NER, QA

**Suggestions**:
- Couvrir l'évolution: des RNN aux Transformeurs
- Pratique avec la bibliothèque Hugging Face Transformers
- Explorer les variantes (RoBERTa, DistilBERT, etc.)
- Discuter des coûts computationnels et de l'efficacité

---

### 3. UV (à clarifier)

Ce sujet nécessite une spécification supplémentaire. Interprétations possibles:

- Vecteurs universels?
- Visualisation de l'incertitude?
- Un outil ou framework spécifique?

**Action requise**: Veuillez clarifier ce que "uv" signifie dans le contexte de ce cours NLP.

---

### 4. CoT (Chain of Thought)

Technique de prompting avancée pour améliorer le raisonnement dans les grands modèles de langage.

- CoT zero-shot et few-shot
- Raisonnement étape par étape
- Applications dans la résolution de problèmes complexes
- Limitations et modes d'échec

**Suggestions**:
- Démontrer avec des exemples pratiques (math, logique, raisonnement de bon sens)
- Comparer avec d'autres stratégies de prompting
- Explorer les variantes (Self-Consistency, Tree of Thoughts)

---

## Sujets supplémentaires à considérer

Autres domaines importants qui pourraient compléter ce cours:

- Techniques de tokenisation (BPE, WordPiece, SentencePiece)
- Métriques d'évaluation pour les tâches NLP
- Stratégies d'affinement et apprentissage par transfert
- Considérations éthiques en NLP
- Développements récents (LLMs, RAG, agents)

---

## Notes

Ceci est un document évolutif. Les sujets seront développés et affinés à mesure que le cours prend forme.
