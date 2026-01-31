# 课程构思

本文档包含课程内容的演进想法。

---

## 涵盖主题

### 1. 静态词嵌入 (Static Word Embeddings)

现代NLP的基础 - 将词表示为连续空间中的稠密向量。

- **Word2Vec**
  - Skip-gram和CBOW架构
  - 训练技术
  - 应用和局限性

- **GloVe (Global Vectors)**
  - 矩阵分解方法
  - 与Word2Vec的比较
  - 使用案例

**建议**:
- 包含在自定义数据集上训练embeddings的实践练习
- 使用t-SNE或UMAP可视化embeddings
- 讨论语义关系和类比

---

### 2. Transformers

通过attention机制彻底改变NLP的现代架构。

- **BERT (Bidirectional Encoder Representations from Transformers)**
  - Self-attention机制
  - 预训练和微调范式
  - Masked language modeling
  - 应用：分类、NER、QA

**建议**:
- 涵盖演进过程：从RNN到Transformers
- 使用Hugging Face Transformers库进行实践
- 探索变体（RoBERTa、DistilBERT等）
- 讨论计算成本和效率

---

### 3. UV（待澄清）

这个主题需要进一步明确。可能的解释：

- Universal Vectors？
- Uncertainty Visualization？
- 特定工具或框架？

**需要的操作**: 请澄清"uv"在本NLP课程中的含义。

---

### 4. CoT (Chain of Thought)

用于改善大语言模型推理能力的高级提示技术。

- Zero-shot和few-shot CoT
- 逐步推理
- 复杂问题解决中的应用
- 局限性和失败模式

**建议**:
- 用实际例子演示（数学、逻辑、常识推理）
- 与其他提示策略比较
- 探索变体（Self-Consistency、Tree of Thoughts）

---

## 其他待考虑主题

可以补充本课程的其他重要领域：

- 分词技术（BPE、WordPiece、SentencePiece）
- NLP任务的评估指标
- 微调策略和迁移学习
- NLP中的伦理考量
- 最新发展（LLMs、RAG、agents）

---

## 备注

这是一个持续更新的文档。随着课程成形，主题将被扩展和完善。
