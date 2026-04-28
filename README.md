# 生物统计与生物信息引论

该仓库为清华大学统计与数据科学系 生物统计与生物信息引论 的官方仓库。持续更新中……

## AI使用指引
本课程鼓励大家使用AI工具辅助学习，特别鼓励使用Agent工具，比如Claude Code，Codex， Kimi Code等等，并在使用中了解其功能和局限性，以及如何融入自己日常的工作流中。

然而，过度依赖AI会削弱个人的能力。本课程中，尽可能使用AI来帮助你理解问题和代码，而非将所有写代码、写报告的任务交给AI。AI仅仅是你的助手，你应当完全理解它所做的事情、所写的代码。

课程遇到问题鼓励求助AI（也可以找助教），但要注意核实AI内容的准确性。若使用搜索引擎，推荐使用Google和Bing，不推荐使用百度。

若想尝试Coding Agent，推荐使用Claude Code + DeepSeek V4， 价格非常便宜。Claude Code安装可以参见[这里](https://mp.weixin.qq.com/s/AA2NHww4jUBuAfi10EYICw)，然后调用[DeepSeek API](https://api-docs.deepseek.com/zh-cn/)。当然如果有ChatGPT Plus及以上的订阅，也可以直接使用[Codex](https://openai.com/codex/)，无需额外付费。其[官方文档](https://developers.openai.com/codex/learn/best-practices)非常值得一读。


## 安装
请参照[Installation Guide](install.md)完成安装。

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

### 自动求导与反向传播

如果想进一步理解 PyTorch 如何记录计算图、计算梯度，可以参考：

- [PyTorch Autograd Tutorial](https://docs.pytorch.org/tutorials/beginner/blitz/autograd_tutorial.html)
- [Dive into Deep Learning: Automatic Differentiation](https://d2l.ai/chapter_preliminaries/autograd.html)
