# Topic-Visualization

>  **基于主题表示和对齐的观点挖掘平台**

### 背景

自然语言处理任务中中，一篇文档是由多个词汇组成的，LDA主题模型将“文档与词”之间的关系描述为 “文档-主题”和“主题-词”，可以理解为一篇文档是由不同概率下的主题维度组成、一个主题是由不同词汇出现频率构成。这导致两个问题：由主题概率表示的文档向量具有稀疏性不利于探索主题的多维度信息、每个主题下的主题词相互独立没有包含任何语义信息，这两点决定了传统主题模型在更加精确的主题信息提取存在不足。

### 方法

本平台使用Cemoody提出的[LDA2Vec](https://github.com/cemoody/lda2vec)主题表示模型，将主题向量和词向量嵌入同一语义空间联合训练。实验表明（数据集见图1描述），通过LDA2Vec训练，由主题向量线性组成的文档向量相比于LDA主题模型（文档由各主题维度下概率表示）在文档表示方面效果更好（可参考下图1中在文档分类中实验结果）；由于主题向量和词向量具有类似的形式（维度和稠密向量），使得不同主题向量间可以通过余弦相似度进行很好地量化，同时主题向量和词向量进行相似度计算也可以获得每个主题下最相关的主题词（相比于LDA主题词根据词频得出效果更好，参见图2）；由于主题向量和词向量是在同一语义空间联合训练的，所以生成的词向量必然包含主题成分（可以理解为词汇的领域信息），这有利于进行词推理学习（参见图3）。上述部分代码后期给出。

- 图0-[双语新闻数据集](https://github.com/cbxs123/news-comment-spider/tree/master/0-data/双语新闻集)

<img src="./img/0.png" style="zoom:60%" align=center />

- 图1

<img src="./img/1.png" style="zoom:60%" align=center />

- 图2

<img src="./img/2.png" style="zoom:60%" align=center />

- 图3

<img src="./img/3.png" style="zoom:60%" align=center />


可视化平台基于[jasonhavenD](https://github.com/jasonhavenD/DJH-NLPIE)开源的框架，以“中美贸易战”中英双语新闻集为语料，使用[LDA2Vec(pytorch版)](https://github.com/TropComplique/lda2vec-pytorch)进行主题表示的观点信息可视化展示（图4和图5为主题-词分布情况，图6和图7为主题演化情况），主题对齐尚在开发中。


- 图4-中文27号主题（美国商会态度）的主题-词分布情况

<img src="./img/4.png" style="zoom:60%" align=center />


- 图5-英文27号主题（Military）的主题-词分布情况

<img src="./img/5.png" style="zoom:60%" align=center />


- 图6-中文其中两个主题的演化情况

<img src="./img/6.png" style="zoom:60%" align=center />


- 图7-英文其中两个主题的演化情况

<img src="./img/7.png" style="zoom:60%" align=center />


