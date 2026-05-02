# 生物统计与生物信息引论

该仓库为清华大学统计与数据科学系 生物统计与生物信息引论 的官方仓库。持续更新中……

## AI使用指引
本课程鼓励大家使用AI工具辅助学习，特别鼓励使用Agent工具，比如Claude Code，Codex， Kimi Code等等，并在使用中了解其功能和局限性，以及如何融入自己日常的工作流中。

若想尝试Coding Agent，推荐使用Claude Code + DeepSeek V4， 价格非常便宜。Claude Code安装可以参见[这里](https://mp.weixin.qq.com/s/AA2NHww4jUBuAfi10EYICw)，然后调用[DeepSeek API](https://api-docs.deepseek.com/zh-cn/)。当然如果有ChatGPT Plus及以上的订阅，也可以直接使用[Codex](https://openai.com/codex/)，无需额外付费。其[官方文档](https://developers.openai.com/codex/learn/best-practices)非常值得一读。

然而，过度依赖AI会削弱个人的能力。本课程中，尽可能使用AI来帮助你理解问题和代码，而非将所有写代码、写报告的任务交给AI。AI仅仅是你的助手，你应当完全理解它所做的事情、所写的代码。

课程遇到问题鼓励求助AI（也可以找助教），但要注意核实AI内容的准确性。若使用搜索引擎，推荐使用Google和Bing，不推荐使用百度。在notebook和教程中内置了一些AI使用指引。初衷是无论教程写的多么详细，由于每个人的知识储备不同，总会有你不理解的地方。因此我们尝试将一些解释的工作交给你的大模型，告诉你需要理解到什么程度、回答什么问题。如果你对此有任何的意见和建议，欢迎反馈给老师和助教。


## 安装
请参照[Installation Guide](install.md)完成安装。

安装后，可以参照[Git tutorial](git_tutorial.md)学习git的基本用法。

## 推荐资源

### 3B1B 深度学习入门

建议优先观看前三个视频，它们对应本课程深度学习入门部分的核心概念：

| 主题 | 资源 |
| --- | --- |
| 神经网络结构 | [【官方双语】深度学习之神经网络的结构 Part 1 ver 2.0](https://www.bilibili.com/video/BV1bx411M7Zx/?share_source=copy_web&vd_source=abe71d796049463f4080c0b5fbc898dc) |
| 梯度下降 | [【官方双语】深度学习之梯度下降法 Part 2 ver 0.9 beta](https://www.bilibili.com/video/BV1Ux411j7ri/?share_source=copy_web&vd_source=abe71d796049463f4080c0b5fbc898dc) |
| 反向传播 | [【官方双语】深度学习之反向传播算法 上/下 Part 3 ver 0.9 beta](https://www.bilibili.com/video/BV16x411V7Qg/?share_source=copy_web&vd_source=abe71d796049463f4080c0b5fbc898dc) |

学有余力的同学可以继续了解 Transformer 和注意力机制：

| 主题 | 资源 |
| --- | --- |
| Transformer 直观解释 | [【官方双语】GPT是什么？直观解释Transformer \| 深度学习第5章](https://www.bilibili.com/video/BV13z421U7cs/?share_source=copy_web&vd_source=abe71d796049463f4080c0b5fbc898dc) |
| 注意力机制 | [【官方双语】直观解释注意力机制，Transformer的核心 \| 深度学习第6章](https://www.bilibili.com/video/BV1TZ421j7Ke/?share_source=copy_web&vd_source=abe71d796049463f4080c0b5fbc898dc) |

### 李沐 动手学深度学习

非常非常详细的课程，B站就有视频，跟着弹幕学习效果极佳 [动手学深度学习 PyTorch版](https://space.bilibili.com/1567748478/lists/358497?type=series). 推荐看1-40集，覆盖深度学习的基本概念、线性回归、softmax回归、CNN、VGG等内容并有非常详细的代码，也介绍很多硬件的知识。40集以后主要是目标检测等更注重计算机视觉的算法，可以等需要用的时候再学。

### Stanford课程

Stanford 有大量高质量公开课，同学们可以根据自己的兴趣选择。下面这些课程都和本课程的机器学习、深度学习、生成模型、生物信息方向有关。B 站视频多为搬运或字幕版，若链接失效，可以直接在 B 站搜索课程号，例如 `Stanford CS229`。Youtube上可能有较近年份的课程视频，大家也可自己搜索。

建议学习顺序：

```text
CS229 / CS230 机器学习与深度学习基础
        ↓
CS231N 视觉方向 / CS224N NLP方向 / CS224W 图学习方向
        ↓
CS236 生成模型 / CS336 大语言模型从零实现
```

#### CS229: Machine Learning

- 课程主页：[CS229: Machine Learning](https://cs229.stanford.edu/w24-index.html)
- B 站视频：[中文版-Stanford CS229: Machine Learning Full Course taught by Andrew Ng 2018版](https://www.bilibili.com/video/BV1nx42117r6/)
- 简要概述：机器学习经典基础课，覆盖线性回归、逻辑回归、广义线性模型、生成式/判别式模型、SVM、核方法、决策树、集成方法、EM、PCA、强化学习等。适合想系统理解机器学习数学基础的同学。
- 前置知识：Python/NumPy 编程，线性代数，多元微积分，概率论与统计基础。对低年级同学来说，这门课偏理论，建议配合本课程和李沐《动手学深度学习》学习。

#### CS230: Deep Learning

- 课程主页：[CS230 Deep Learning](https://cs230.stanford.edu/)
- B 站视频：[Stanford CS230 深度学习 Autumn 2018 中英双字幕](https://www.bilibili.com/video/BV1ex411X7pj/)
- 简要概述：深度学习入门到项目实践课程，覆盖神经网络、CNN、RNN/LSTM、Adam、Dropout、BatchNorm、初始化、项目策略和模型调试。相比 CS229 更偏应用和工程。
- 前置知识：Python 编程，矩阵/向量运算，基本概率统计，最好已经理解线性回归、softmax 回归、反向传播和 PyTorch 基本用法。

#### CS231N: Deep Learning for Computer Vision

- 课程主页：[CS231N: Deep Learning for Computer Vision](https://cs231n.stanford.edu/)
- B 站视频：[经典课程 计算机视觉 CS231n 中文字幕](https://www.bilibili.com/video/BV1Gb4y1X7Q5/)
- 简要概述：以图像分类、目标检测、分割等视觉任务为主线，讲解 CNN、训练技巧、可视化、迁移学习、视觉生成模型等。适合对医学影像、显微图像、病理图像分析感兴趣的同学。
- 前置知识：Python/NumPy，线性代数，微积分，概率统计，神经网络和反向传播基础。

#### CS224N: Natural Language Processing with Deep Learning

- 课程主页：[CS224N: Natural Language Processing with Deep Learning](https://web.stanford.edu/class/cs224n/index.html)
- B 站视频：[CS224N Stanford NLP with Deep Learning 2019冬季学期](https://www.bilibili.com/video/BV1Tb411K74n/)
- 简要概述：深度学习自然语言处理经典课程，覆盖词向量、RNN/LSTM、注意力机制、Transformer、预训练语言模型、Prompting、RLHF、多模态和代码生成等。适合理解语言模型和文本/序列数据建模。
- 前置知识：Python 和 PyTorch 基础，神经网络、反向传播、概率统计和线性代数。若直接看 Transformer 部分，建议先看 3B1B 的注意力机制视频。

#### CS224W: Machine Learning with Graphs

- 课程主页：[CS224W: Machine Learning with Graphs](https://web.stanford.edu/class/cs224w/)
- B 站视频：[图机器学习 CS224W 2021 中英字幕](https://www.bilibili.com/video/BV1vD4rePEiP/)
- 简要概述：图机器学习课程，覆盖节点嵌入、图神经网络、知识图谱、PageRank、社交网络、推荐系统等。对生物网络、蛋白互作网络、基因调控网络、药物-靶点关系等问题很有帮助。
- 前置知识：Python 编程，线性代数，概率统计，基本机器学习。熟悉图的基本概念会更好，例如节点、边、邻接矩阵、最短路。

#### CS236: Deep Generative Models

- 课程主页：[CS236: Deep Generative Models](https://deepgenerativemodels.github.io/)
- B 站视频：[斯坦福 CS236 深度生成模型 2023](https://www.bilibili.com/video/BV1o7421Z7tz/)
- 简要概述：生成模型系统课程，覆盖 VAE、GAN、自回归模型、normalizing flow、energy-based model、score-based model 和 diffusion model。适合本课程生成模型部分之后继续深入。
- 前置知识：机器学习基础，概率论，微积分，Python 编程。建议先理解最大似然、KL 散度、神经网络训练和 PyTorch，再学习 VAE/扩散模型。
- 该部分内容会在本课程内重点讲解。

#### CS336: Language Modeling from Scratch

- 课程主页：[CS336: Language Modeling from Scratch](https://cs336.stanford.edu/)
- B 站视频：[Stanford CS336 Language Modeling from Scratch Spring 2025](https://www.bilibili.com/video/BV1DMMuz7ELL/)
- 简要概述：从零实现语言模型的进阶课程，覆盖 tokenizer、Transformer、优化器、训练、GPU 计算、并行、scaling law、数据清洗、推理和对齐。课程**非常工程化**，第一个大作业就是从头进行大预言模型的预训练，适合想真正理解大模型训练流程的同学。
- 前置知识：熟练 Python，PyTorch，深度学习，Transformer，机器学习基础，基本系统知识。课程作业代码量较大，不建议作为第一门深度学习课。

### 自动求导与反向传播

如果想进一步理解 PyTorch 如何记录计算图、计算梯度，可以参考：

- [PyTorch Autograd Tutorial](https://docs.pytorch.org/tutorials/beginner/blitz/autograd_tutorial.html)
- [Dive into Deep Learning: Automatic Differentiation](https://d2l.ai/chapter_preliminaries/autograd.html)
