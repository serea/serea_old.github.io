---
title: "Works during PHD"
image: 
  path: /images/recipes/DOCTOR/image1.png
  thumbnail: /images/recipes/DOCTOR/image1.png
  caption: "Works during PHD"
categories:
  - My Work
---

## 博士期间工作介绍

主要的研究分为两个方向：

### 网络流量中恶意行为分析与发现研究

已发表相关学术论文7篇(IIE-B类2篇，IIE-C类5篇)，其中一作3篇，目前思考如何积累。

#### 1.Hierarchical Clustering Based Network Traffic Data Reduction for Improving Suspicious Flow Detection，已发表，TrustCom 2018会议（CCF C类会议），一作；

![image-center]({{ '/images/recipes/DOCTOR/image-20191122094850298.png' | absolute_url }}){: .align-center}

![image-center]({{ '/images/recipes/DOCTOR/image-20191122094937223.png' | absolute_url }}){: .align-center}


**问题描述：**网络中的流量数据非常庞大，及时处理依旧会保留大量的数据集；

**启发点：**大事化小，小事化了，先找到重点部分，再套用复杂的方法。

**因此，**我们提出希望通过简单处理先去掉大部分非异常数据，再对可能异常数据做集中精准的分析的方法。

先处理一部分的主要思路：通过基于特征的聚类将数据划分为多个类簇，再通过类簇中随机采样判断类簇是否可能包含恶意流量，如果采样数据中未发现恶意流量则认为该类簇不包含恶意流量，对于采样中发现恶意流量的类簇做进一步的判断分析。

#### 2.DeepGFL: Deep Feature Learning via Graph for Attack Detection on Flow-based Network Traffic，已发表，MilCom 2018会议（IIE B类会议），二作；

**问题描述：**网络流中的部分节点存在特征比较少，比如网络攻击中的跳板等节点，仅包含控制命令的转换，或者低强度的dos攻击，包含少量的低频率的网页访问等情况；

**启发点：**沿着网络流作为一种信息流的传递，使用相邻节点，多跳节点增加对当前节点的认识。

![image-center]({{ '/images/recipes/DOCTOR/image-20191122095038734.png' | absolute_url }}){: .align-center}


**因此，**我们提出了深度特征学习的方法来提高对异常流量的发现。在获取每条流量初始特征的基础上，按照网络流的方向即如果是s的考虑流入的flow，与d考虑流出的flow共同运算，s流出发flow与d流入的flow共同运算。主要是原始特征的迭代运算，将运算结果使用决策树模型判断特征的有效性，去掉有效性score < λ的特征。

#### 3.Marrying Graph Kernel with Deep Neural Network: A Case Study for Network Anomaly Detection，已发表，ICCS 2019会议（IIE B类会议），共同一作;

**问题描述：**根据上一篇论文中发现将网络拓扑图表达成graph可以发现更高维度的特征与信息，因此想了解不同流量在短时间内产生的网络拓扑图对于流量的分类是否有影响。

**启发点：**每个flow考虑短时间内构建的网络拓扑图，发现同类型攻击flow构建的拓扑图具有相似性，graph kernel是一种通过子图的相似性来表达图相似性的方法，因此我们考虑通过graph kernel来表达这种相似性。


![image-center]({{ '/images/recipes/DOCTOR/image-20191122075606342.png' | absolute_url }}){: .align-center}

**因此，**我们提出将图核与深度神经网络相结合的异常检测方法。考虑两种将图核特征和原始流量特征在深度神经网络训练过程中的方法，一种在深度神经网络输入端与原始流量特征直接链接输入到深度神经网络中，另一种单独将图核特征和原始特征输入到深度神经网络中训练图核特征的分类能力，在softmax层叠加两个模型的分类结果。

![image-center]({{ '/images/recipes/DOCTOR/image-20191122080038661.png' | absolute_url }}){: .align-center}

#### 4.Understanding the Influence of Graph Kernels on Deep Learning Architecture: A Case Study of Flow-Based Network Attack Detection，已发表，TrustCom 2019会议（CCF C类会议），一作;

进一步理解图核方法在深度学习中所起的作用，从Multi-step Attack 和 Low-intensity Attack两类攻击分析，发现图核有利于捕捉攻击行为在拓扑的空间上的结构一致性和相似性特征。为了增加时间维度上流量的一致性和相关性，尝试将flow按照时间顺序输入到LSTM中，结合kernel做流量异常发现。

![image-center]({{ '/images/recipes/DOCTOR/image-20191122101927385.png' | absolute_url }}){: .align-center}

![image-center]({{ '/images/recipes/DOCTOR/image-20191122101857509.png' | absolute_url }}){: .align-center}

#### 5.STDeepGraph: Spatial-Temporal Deep Learning on Communication Graphs for Long-Term Network Attack Detection，已发表，TrustCom 2019会议（CCF C类会议），二作;

#### 6.A Novel Approach for Identifying Lateral Movement Attacks Based on Network Embedding，已发表，ISPA 2018会议（CCF C类会议），五作;

#### 7.An improved method to unveil malware's hidden behavior，已发表，Inscript 2017会议（IIE C类会议），三作。

### 大规模的恶意行为分析与测量

#### 1.在Ethereum大规模发现dapp的中存在的恶意攻击交易

基于对区块链游戏（DApp）上恶意行为描述的report的观察，我们发现存在针对以太坊DApp的恶意攻击行为，以及不规范甚至是恶意的DApp。

**为什么解决此问题：**

由于涉及巨大的经济利益，加上试探漏洞成本低于攻击成功的收益，区块链上的攻击者有很大动力去挖DApp的漏洞。攻击、做空、投机等行为将极大地毁灭信任，打击生态。

DApp本质是智能合约，拥有去中心化、透明、不可篡改的特性，也可以接受/发送虚拟货币。DApp无法调试更改的特性，以及与区块链上其他合约之间的交互和虚拟货币传递行为，一旦发生攻击，非法获取虚拟货币无法追回。

DApp和智能合约不要求公开源代码，通常只在区块链上留存字节码，从执行代码角度分析DApp和智能合约行为比较困难。

**此方法的优势：**

![image-center]({{ '/images/recipes/DOCTOR/image2.png' | absolute_url }}){: .align-center}

提出基于序列交易图的检测方法。DApp上的攻击行为往往存在着多次试探过程后再攻击成功的流程，而且此类试探过程与成功攻击的行为在交易图上很相似。对于所有需要尝试和试探的攻击类型，都无法逃逸本方法的检测，并且本方法具备在实际攻击成功前通过检测攻击试探过程预测即将发生的攻击的能力。由于用户与智能合约间交易图包含虚拟货币传递过程和智能合约交易过程，本方法借助交易图可以充分分析与利用区块链公开交易信息。

**后续的工作：**

后续有一部分人在测试链上进行大规模攻击分析的进一步工作，Ethereum提供一个测试平台，通过测试平台有希望能更快速早期的发现新攻击甚至是新类型的攻击方式。

还有一部分人关注溢出，重入等攻击，从执行代码中“币”的转移逻辑和实际交易发生后“币”的转移结果相比较的工作。

我目前刚刚提交完第二次的论文投稿，目前的想法是后面关注EOS上的攻击行为，以及关注区块链货币的交易异常两个方向。

### 其他工作

"VPN"恶意行为分析项目：了解VPN数据存储情况，设计建设方案以及分析模型，并采用异常图检测方法对账号行为建模。

网络空间安全态势感知课程教材样章撰写，填写教材编辑相关申请材料。 