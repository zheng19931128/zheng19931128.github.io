---
layout: post
title: "政委 Training 秘笈 之 强化学习篇：(1) 简介"
categories:
- 政委Training秘笈 
- 强化学习
tags:
- 政委 
- 强化学习

---
<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

开篇说明
--

强化学习是一个很火的研究方向，很多人都讲“It‘s the future”。依我的拙见，那就是不需要太多数据，不想深度学习那样猛吃数据；同时也不需要先验的知识。强化学习是一个连续的决策问题，这个和人的学习方式较普通机器学习来讲更加接近。所以很有趣味和研究价值。

本篇这个Training秘笈，应该叫做Training（我）的苦逼纪录。事实上这是我的学习记录，我对强化学习的理解也是从最基础的认识开始的，因此难免会有一些错误。如果发生了错误，且将这些错误放在这里公布出来不断的鞭策自己。

希望随着时间的积累这个秘笈可以越来越多，不要给挂掉了（那真的太。。。说明我毅力不够）。


强化学习是什么
--

- 两句话说清楚强化学习

强化学习，即 Reinforcement Learning。在[Wikipedia](https://en.wikipedia.org/wiki/Reinforcement_learning)的解释为：是机器学习的一个领域，其问题关注的是如何让agent在与环境的交互中获得更多的累积奖励。

- 强化学习有什么特点

  + 强化学习和一般的机器学习有些不一样。首先一般机器学习面对的数据是feature和lable，但是RL问题中没有label，在一个决策执行之前甚至执行之后我们依然不知道这个决策是否真的应该这样做。而到一个周期（RL中称episode，如玩一个游戏从开始到游戏结束）结束，当我们知道最终的结果后，使用各种方法来评价当初做的动作会如何影响结果的。RL采用的是goal-directed的学习方式，再学习开始时没有既定的已有知识。
  
  + 强化学习中agent需要不断的和环境进行交互来获取经验（包括奖励reward，环境的状态state等），用来提升agent的行为。在交互中，agent可以影响到环境。一般机器学习不能和环境交互。
  
  + 强化学习关注的决策，而且是面对变化的环境连续的决策。

  + 强化学习的优化目标是提升在一个长时间段内的累积奖励来提升agent的行为。因此agent不仅需要能够根据当前的形势进行最优策略，还需具有一定“远见”能力。这是强化学习中的一个非常关键的问题：“exploration 和 exploitation”。

     - exploration是指探索，在强化学习中指agent对未知环境，未知状态的探索。
     - exploitation是指开发利用，在强化学习中指agent对以探索的经验的利用
     - exploration意味着agent尝试新的action，可能会得到更好的结果。exploitation则会在已知经验下达到最优。这二者之间存在一个平衡。目前尚没有很好的解决方法。


强化学习要素
--

为能够将现实的学习问题描述清楚，强化学习把实际的学习对象抽象为：环境，agent。agent和环境进行交互。这个学习过程的描述使用 policy， reward，value function 和环境模型。这4项被称为RL的要素。



名称|解释
---|:--
policy|决定agent的行为，什么环境下做出什么反应，是环境到动作的映射
reward signal| agent每做出一个action，会达到一个state。reward signal 是环境对agent做出的即时反应。
value function | reward signal是环境对agent的action作出即时的反馈，而value function是衡量agent整个生命周期内该行为的reward的累积。用来衡量action的好坏。
model|是对环境的模拟，用来预测环境对agent的action的反应。可以认为是agent对环境的认知。

**value function**

- 事实上，value function是agent自己对action价值的估计。在agent完成既定的任务之前很难知道某个时刻选择的action的value function是多少，根据reward signal的最大值作出反应并不能保证在value function上可以达到最大.
- 因此每当agent尝试一个action得到reward后会对value function进行更新，直至收敛。更新公式如下：


$$
V (s) ← V (s) + \alpha(V (s') − V (s))
$$

$V$ 是value function，$s$  是action之前state，$s'$  是action之后的state ，根据二者的差距来纠正$s$的value function，$\alpha$ 是更新率，可以认为是学习率。


本篇小节
--

本片主要讲了这么几个问题：

- 强化学习不同于一般的机器学习
- 强化学习的4个要素



