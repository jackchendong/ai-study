# CSA：Cross Self-Attention（交叉自注意力）

**核心意思：** 在“自注意力”的基础上，引入“跨输入”的信息交互

**通俗理解：**

- 普通 Self-Attention：一句话自己内部互相看
- CSA：不仅看自己，还可以“看别人”

**举个例子：**

假设你有两个输入：

- 文本 A（问题）
- 文本 B（上下文 / 文档）

CSA 会让：

- A 里的 token 可以关注 B
- B 里的 token 也可以关注 A

👉 本质：不同序列之间的信息融合

**长见于：**

- Encoder-Decoder（比如机器翻译）
- 多模态模型（图文）
- RAG（检索增强生成）

理解: 

CSA：让不同输入“互相看”

HCA：让不同层级 + 不同输入“分层互相看”

# HCA：Hierarchical Cross-Attention（层级交叉注意力）

**核心意思：** 在不同“层级/粒度”上做 Cross-Attention

**为什么需要它：**

长文本 or 多模态任务中：

- 信息是分层的（词 → 句 → 段 → 文档）
- 一次性全 attention 成本太高

**HCA 的做法：**

分层处理：

1. 低层（token级）

    - 细粒度信息（词与词）

2. 高层（chunk / sentence级）

    - 结构信息（段落与段落）

然后：

👉 在不同层之间做 Cross-Attention

**HCA 常见于：**
- 长上下文模型（Long Context LLM）
- 文档级 QA
- 分块检索 + 汇总（Chunk → Summary）

理解: 

CSA：让不同输入“互相看”

HCA：让不同层级 + 不同输入“分层互相看”