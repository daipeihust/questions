# Fabric

## One

Peer节点; Committer记账节点; Client（客户端）; Fabric-CA客户端; Fabric客户端; 交易处理流程; Gossip消息协议; 组织（Organization）与联盟（Consortium）; 链码（Chaincode）; CSCC; ESCC; 账本（Ledger）

### 简单

1. 下面关于peer节点说法错误的是：D
    A.peer节点是区块链网络的基本元素
    B.peer节点储存了账本和智能合约
    C.一个peer节点可以维护多个账本
    D.一个peer节点只能维护一个智能合约

> 解析：一个peer节点可以同时维护多个账本和智能合约

2. 下面哪种节点是区块链网络中可以没有的：C
    A.提交节点
    B.背书节点
    C.锚节点
    D.主节点

> 解析：在实际情况中只有锚节点是可选的，一般都会有一个主节点，至少一个背书节点和一个提交节点。提交节点：通道中的每个 Peer 节点都是一个提交节点。他们会接收生成的区块，在这些区块被验证之后会以附加的方式提交到 Peer 节点的账本副本中。背书节点：每个安装了智能合约的 Peer 节点都可以作为一个背书节点。主节点：当组织在通道中具有多个 Peer 节点的时候，会有一个主节点，它负责将交易从排序节点分发到该组织中其他的提节点。锚节点：如果一个 Peer 节点需要同另一个组织的 Peer 节点通信的话，它可以使用对方组织通道配置中定义的锚节点；一个组织可以拥有 0 个或者多个锚节点，并且一个锚节点能够帮助很多不同的跨组织间的通信。故C项错误。

3. 下面关于联盟的说法正确的是：B
    A.一个联盟包含的组织数量是有限制的
    B.通道是一个联盟中的成员彼此进行通信的主要机制
    C.通道为联盟提供了一个公有的通信机制
    D.一个区块链网络中联盟的数量是有限制的

> 解析：一个联盟可以包含任意数量的组织，所以A项错误；通道为联盟提供了一个私有的通信机制，所以B项错误；一个区块链网络中联盟的数量没有限制，所以D项错误；通道是一个联盟中的成员彼此进行通信的主要机制，B项正确。

4. 下面关于智能合约说法错误的是：D
    A.智能合约用可执行的代码定义了不同组织之间的规则
    B.应用程序调用智能合约来生成被记录到账本上的交易
    C.通常来说，智能合约定义的是控制世界状态中业务对象生命周期的交易逻辑
    D.智能合约可以用任意编程语言开发

> 解析：Fabric是第一个支持通用编程语言编写智能合约（如 Java、Go 和 Node.js）的分布式账本平台，不受限于特定领域语言（Domain-Specific Languages，DSL），但是目前还不支持任意编程语言。其他选项都是智能合约的特性。

5. 下面哪项不是Hyperledger Fabric使用策略的理由：A
    A.策略可以让 Hyperledger Fabric 成为非许可区块链
    B.因为 Fabric 是授权区块链，用户由底层基础设施识别，所以用户可以在启动前决定网络的治理方式，以及改变正在运行的网络的治理方式
    C.策略决定了那些组织可以访问或者更新 Fabric 网络，并且提供了强制执行这些决策的机制
    D.策略能够评估交易和提案中的签名，并验证签名是否满足网络治理规则

> 解析：Hyperledger Fabric是许可区块链，接入Hyperledger Fabric区块链的用户都需要经过身份认证。故A项错误。

### 普通

1. 下面关于账本特性说法错误的是：A
    A.账本储存在节点上，通道上没有账本
    B.每个交易都会生成一组资产键值对，这些键值对以创建、更新或删除形式提交到账本
    C.账本是Fabirc中所有状态转换的有序的防篡改的记录
    D.每个节点为其所属的每个通道维护一个账本的副本

> 解析：账本由区块链（“链”）组成，用于以区块的形式存储不可变的顺序记录，以及用于维护当前Fabirc状态的状态数据库。每个通道有一个账本。每个节点为其所属的每个通道维护一个账本的副本。故A项错误。

2. 下面关于组织说法错误的是：C
    A.组织被定义在网络配置中
    B.一个新的组织想要加入一个通道或者一些已经存在的组织想要增加或减少他们的权限
    C.由CA颁发的证书不能用来为交易提供签名，来表明一个组织对交易的结果进行背书
    D.在大多数的额情况下，多个组织会聚集到一起作为一个联盟来形成一个网络
    
> 解析：证书颁发机构用来给管理者和网络节点颁发证书，在网络中扮演着重要的角色，它会分配X.509证书，这个证书能够用来识别属于组织的组件。由CA颁发的证书也可以用来为交易提供签名，来表明一个组织对交易的结果进行背书，背书是一笔交易可以被接受并记录到账本上的前提条件。故C项错误。

3. 下面关于账本描述错误的是：B
    A.Hyperledger Fabric中的账本由“世界状态“和”区块链“这两部分组成
    B.区块链数据结构与世界状态的数据结构是类似的
    C.世界状态是一个数据库，它存储了一组账本状态的当前值
    D.默认情况下，账本状态是以键值对的方式来表示的

> 解析：区块链数据结构与世界状态相差甚远，因为一旦把数据写入区块链，就无法修改，它是不可篡改的。故B项错误。

4. 下面关于世界状态说法错误的是：D
    A.世界状态将业务对象属性的当前值保存为唯一的账本状态
    B.账本世界状态记录了一组与特定业务对象有关的事实
    C.只有那些受到相关背书组织签名的交易才会更新世界状态
    D.首次创建账本时，世界状态不是空的

> 解析：首次创建账本时，世界状态是空的。因为区块链上记录了所有代表有效世界状态更新的交易，所以任何时候都可以从区块链中重新生成世界状态。这样一来就变得非常方便，例如，创建节点时会自动生成世界状态。此外，如果某个节点发生异常，重启该节点时能够在接受交易之前重新生成世界状态。故D项错误。

5. 下面关于账本中区块链部分说法错误的是：B
    A.区块链是一种历史记录
    B.经过所有的组织同意，可以修改历史区块
    C.区块链的结构是一群相互链接的区块的序列化日志
    D.每个区块的头部都包含区块交易的一个哈希，以及前一个区块头的哈希

> 解析：虽然与业务对象当前状态相关的事实可能会发生改变，但是与之相关的事实历史是不可变的，可以在事实历史上增加新的事实，但无法更改历史中已经存在的事实。如果把区块链看作是与业务对象有关的事实历史，且该历史是不可更改的，那么就能够很轻松、高效地理解区块链。

### 困难

1. 下面哪项是区块链网络交易流程的正确顺序：C
    A.提案、验证、排序、打包、提交
    B.打包、提案、排序、验证、提交
    C.提案、排序、打包、验证、提交
    D.打包、验证、提交、排序、提交

> 解析：区块链网络的交易流程分为三个阶段：提交、排序并打包、验证和提交。故C项正确。

2. 下面关于交易流程说法错误的是：A
    A.客户端应用程序可以自己生成账本更新提案
    B.已背书的交易提案在第二阶段经过排序生成区块
    C.已背书的交易提案在第三阶段分发给所有节点进行最终验证和提交
    D.排序服务创建交易区块，这些交易区块最终将分发给通道上的所有Peer节点

> 解析：在第一阶段，客户端应用程序将交易提案发送给一组节点，这些节点将调用智能合约来生成一个账本更新提案，然后背书该结果。客户端应用程序不能自己生成账本更新提案，故A项错误。

3. 下面关于排序服务说法错误的是：C
    A.排序服务节点同时接收来自许多不同应用程序客户端的交易
    B.排序服务的工作是将提交的交易按定义好的顺序安排成批次，并将它们打包成区块
    C.一个区块中交易的顺序与排序服务接收的顺序相同
    D.在Hyperledger Fabric中，由排序服务生成的区块是最终的

> 解析：一个区块中交易的顺序不一定与排序服务接收的顺序相同，因为可能有多个排序服务节点几乎同时接收交易。故C项错误。

4. 下面关于Gossip协议说法错误的是：D
    A.Peer节点通过gossip协议来传播账本和通道数据
    B.Gossip消息是持续的，通道中的每一个Peer节点不断地从多个节点接收当前一致的账本数据
    C.每一个Gossip消息都是带有签名的，因此拜占庭成员发送的伪造消息很容易就会被识别，并且非目标节点也不会接受与其无关的消息
    D.Gossip协议中，延迟、网络分区等其他影响不会丢失区块

> 解析：Peer 节点会受到延迟、网络分区或者其他原因影响而丢失区块，这时节点会通过从其他拥有这些丢失区块的节点处同步账本。故D项错误。

5. 下面关于主节点选举说法错误的是：B
    A.主节点的选举机制用于在每一个组织中选举出一个用于链接排序服务和开始分发新区块的节点
    B.在网络比较差有多个网络分区存在的情况下，组织中只会存在一个主节点保证网络稳定运行
    C.静态主节点选举允许你手动设置组织中的一个或多个节点节点为主节点
    D.动态选举出的主节点通过向其他节点发送心跳信息来证明自己处于存活状态

> 解析：在网络比较差有多个网络分区存在的情况下，组织中会存在多个主节点以保证组织中节点的正常工作。在网络恢复正常之后，其中一个主节点会放弃领导权。在一个没有网络分区的稳定状态下，会只有唯一一个活动的主节点和排序服务相连。故B项错误。

## Two

Endorser背书节点; 共识（Consensus）; 交易（Transaction）和区块（Block）; LSCC; QSCC; VSCC; 策略管理（Policy）

### 简单

1. 下面哪一项不是区块的组成部分：C
    A.区块头
    B.区块数据
    C.区块尾
    D.区块元数据

> 解析：区块由三个部分组成：区块头、区块数据、区块元数据。区块头包含三个字段：区块编号、当前区块的哈希值、前一个区块头的哈希值；区块数据包含了一个有序的交易列表。区块数据是在排序服务创建区块时被写入的；区块元数据包含了区块被写入的时间，还有区块写入者的证书、公钥以及签名.故C项错误。

2. 下面关于策略说法错误的是：A
    A.策略在网络最初配置的时候由联盟成员一致同意，策略确定后就不可修改
    B.从根本上来说，策略是一组规则，用来定义如何做出决策和实现特定结果
    C.策略一般描述了谁和什么，比如一个人对资产访问或者权限
    D.在Hyperledger Fabric中，策略是基础设施的管理机制

> 解析：策略在网络最初配置的时候由联盟成员一致同意，但是在网络演化的过程中可以进行修改。例如，他们定义了从通道中添加或者删除成员的标准，改变区块格式或者指定需要给智能合约背书的组织数量。故A项错误。

3. 下面关于Hyperledger Fabric共识机制说法错误的是：B
    A.Hyperledger Fabric被设计为允许网络启动者选择最能代表参与者间存在的关系的共识机制
    B.Hyperledger Fabric提供多种可插拔选项，共识机制可以交换替换，但不支持不同的MSP
    C.保持账本在整个网络中同步的过程称为共识
    D.共识确保账本仅在交易被相应参与者批准时更新，并且当账本更新时，它们以相同的顺序更新相同的交易

> 解析：Hyperledger Fabric提供多种可插拔选项。账本数据可以以多种格式存储，共识机制可以交换替换，并且支持不同的MSP。故B项错误。

4. 下面关于应用程序和peer节点交互说法错误的是：C
    A.查询账本的操作涉及到应用程序和peer节点之间的一个简单的三步对话
    B.更新账本的操作会涉及到更多的步骤，需要额外的两步
    C.当应用程序需要访问账本和链码的时候，可以不连接到peer节点
    D.应用程序能够连接到一个或者多个peer节点来执行一个查询

> 解析：当应用程序需要访问账本和链码的时候，总是需要连接到peer节点。故B项错误。

5. 下面关于peer节点和通道说法错误的是：D
    A.概念上来说，可以把通道想象为类似于一个由朋友组成的群组一样
    B.通道允许区块链网络中特定的一些peer节点以及应用程序来彼此交互
    C.通道和peer节点是以不同的方式存在的，将通道理解为由物理的peer节点的组成的逻辑结构更合适一些
    D.因为通道提供了对peer节点访问和管理的控制

> 解释：peer节点提供了对通道访问和管理的控制。故D项错误。

### 普通

1. 下面关于peer节点和组织的说法错误的是：A
    A.如果组织不为区块链网络贡献他们的资源，这个网络仍然会存在
    B.区块链网络是由多个组织来管理的
    C.组织向区块链网络贡献资源，但是一个组织提供的资源不仅仅是peer节点
    D.区块链网络不依赖于任何一个单独的组织，只要还存在一个组织，区块链网络就会继续存在

> 解析：如果组织不为区块链网络贡献他们的资源，这个网络是不会存在的。更关键的是，这个网络会随着这些互相合作的组织提供的资源而增长或者萎缩。故A项错误。

2. 下面关于peer节点和身份说法错误的是：D
    A.peer节点会有一个身份信息被分给他们，这是通过一个特定的证书认证机构颁发的数字证书来实现的
    B.当peer节点连接到一个通道的时候，它的数字证书会通过通道MSP来识别它的所属组织
    C.一个peer节点只能被一个组织所有，因此也就只能被关联到一个单独的MSP
    D.peer节点物理上的位置对于其身份识别很重要

> 解析：peer节点物理上在哪真的不重要，它可以放在云中，或者是由一个组织所有的数据中心中，或者在一个本地机器中，是与它相关联的数字证书信息来识别出它是由哪个组织所有的。故D项错误。

3. 下面关于peer节点和排序节点说法错误的是：C
    A.一个更新的交易和一个查询的交易区别很大，因为一个单独的peer节点不能够由它自己来更新账本
    B.交易流程的最后一个阶段是分发以及接下来的对于从排序节点发送给peer节点的区块的验证工作，这些区块最终会提交到账本中
    C.交易的三个阶段都涉及到了排序节点
    D.排序节点在交易流程中处于中心地位

> 解析：交易流程的第一阶段会引入在应用程序和一系列的peer节点之间的交互，它并没有涉及到排序节点。第一阶段只在乎应用程序询问不同组织的背书节点同意链码调用的提案结果。故C项错误。

4. 下面关于排序节点和共识说法错误的是：B
    A.整个交易处理流程被称为共识，因为所有peer节点在由排序节点提供的流程中对交易的排序及内容都达成了一致
    B.共识的流程在不同peer节点上同时发生
    C.共识是一个多步骤的流程，并且应用程序只会在这个流程结束的时候通知账本更新
    D.可以把排序节点理解为一个这样的节点，它为peer节点验证和写入账本从应用程序搜集和分发账本更新提案

> 解析：共识是一个多步骤的流程，并且应用程序只会在这个流程结束的时候通知账本更新，这个在不同的peer节点上可能在不同的时间会发生。故B错误。

5. 下面关于提案说法错误的是：D
    A.为了开始第一阶段，应用程序会生成一笔交易的提案，它会把这个提案发送给一系列的被要求的节点来获得背书
    B.每一个背书节点都会独立地使用交易提案来执行链码，以此来生成这个交易提案的响应
    C.peer节点通过向提案的响应添加自己的数字签名的方式提供背书，并且使用它的私钥为整个的负载提供签名
    D.当应用程序接收到1个被签过名的提案响应之后，交易流程中的第一个阶段就结束了

> 解析：当应用程序接收到有效数量的被签过名的提案响应之后，交易流程中的第一个阶段就结束了。故D错误。

### 困难

1. 下面关于背书策略说法错误的是：D
    A.每个链码都有一个背书策略与之相关联
    B.背书策略非常重要，它指明了区块链网络中哪些组织必须对一个给定的智能合约所生成的交易进行签名，以此来宣布该交易有效
    C.背书策略是Hyperledger Fabric与以太坊或比特币等其他区块链的区别所在
    D.只有经过背书的有效交易会被添加到分布式账本中，并更新世界状态

> 解析：所有的交易，无论是有效的还是无效的，都会被添加到分布式账本中，但只有有效交易会更新世界状态。故D项错误

2. 下面关于有效交易说法错误的是：C
    A.智能合约提取一组名为交易提案的输入参数，并将其与程序逻辑结合起来使用以读写账本
    B.一项交易被分发给网络中的所有节点，各节点通过两个阶段对其进行验证
    C.验证交易的第一步是检查交易在受到背书节点签名时它的交易读集与世界状态的当前值匹配，并且中间过程中没有被更新
    D.背书策略会检查交易，确保该交易已被足够的组织签署

> 解析：一项交易被分发给网络中的所有节点，各节点通过两个阶段对其进行验证。首先，根据背书策略检查交易，确保该交易已被足够的组织签署。其次，继续检查交易，以确保当该交易在受到背书节点签名时它的交易读集与世界状态的当前值匹配，并且中间过程中没有被更新。C选项中的验证是第二步，故C是错误的。

3. 下面关于系统通道配置说法错误的是：C
    A.每个网络都从排序服务系统通道开始
    B.排序系统通道配置区块中的策略治理着排序服务使用的共识
    C.系统通道配置不属于Fabric策略
    D.系统通道也治理着联盟中的哪些成员可以创建新通道

> 解析：系统通道配置属于策略的一种。故C项错误。

4. 下面关于隐元策略说法错误的是：A
    A.隐元策略不止在通道配置上下文中有效
    B.隐元策略聚合了由签名策略最终定义的配置树深层的结果
    C.隐元策略是隐藏的，因为它们基于通道配置中的当前组织隐式构建
    D.隐元策略是元信息，因为它们的评测不依赖于特定MSP规范，而是依赖于配置树中它们的其他子策略

> 解析：隐元策略只在通道配置上下文中有效，通道配置在配置树策略中是基于分层的层次结构。故A项错误。

5. 下面关于链码背书策略说法错误的是：B
    A.当使用fabric链码生命周期链码被批准并提交到通道时会指定一个背书策略
    B.基于状态的背书不能指定与默认链码级别背书策略不同的键的背书策略
    C.背书策略可以引用通道配置中的背书策略或者明确指定签名策略
    D.如果在批准阶段没有明确指明背书策略，就默认使用Endorsement策略
    
> 解析：基于状态的背书可以指定与默认链码级别背书策略不同的键的背书策略。故B项错误。

## Three

Committer记账节点; Orderer排序节点; 交易处理流程; Gossip消息协议; 共识（Consensus）; 成员关系服务提供者（MSP）; 组织（Organization）与联盟（Consortium）; 交易（Transaction）和区块（Block）; 链码（Chaincode）; CSCC; ESCC; LSCC; QSCC; VSCC; 策略管理（Policy）

### 简单

1. 下面关于智能合约说法错误的是：A
    A.当智能合约被安装在peer节点之后，它就可以被客户端应用调用了
    B.交易的响应会和交易的提案打包到一起形成一个完整的经过背书的交易，他们会被分发到整个网络
    C.客户端应用是通过发送交易提案给智能合约背书策略所指定的peer的节点方式来调用智能合约的
    D.交易的提案会作为智能合约的输入，智能合约会使用它来生成一个背书交易响应

> 解析：当智能合约被安装在 Peer 节点并且在通道上定义之后，它就可以被客户端应用调用了。故A项错误。

2. 关于主节点下面说法错误的是：C
    A.在动态选举主节点中，如果一个主节点出错了，那么剩下的节点将会重新选举一个主节点
    B.一个节点可以选择参与静态或者动态的领导选举
    C.一个组织的节点只有一个主节点连接到排序服务
    D.从管理者的角度来考虑的话会有两套节点，一套是静态选择的主节点，另一套是动态选举的主节点

> 解析：一个组织的节点可以有一个或者多个主节点连接到排序服务。故C项错误。

3. 在区块链网络中，MSP出现在哪两个位置：D
    A.参与者节点本地、排序节点
    B.通道配置、网络配置
    C.通道配置、排序节点
    D.参与者节点本地、通道配置
    
> 解析：在区块链网络中，MSP 出现在两个位置：参与者节点本地（本地 MSP）、通道配置（通道 MSP）。故D项正确。

4. 下面关于身份说法错误的是：B
    A.MSP将可验证的身份转变为区块链网络的成员
    B.身份验证不要求确保交换消息的各方创建特定消息的身份
    C.数字证书是包含与证书持有者相关的属性的文档，它允许在其结构中编码一些用于身份识别的信息
    D.身份验证和消息完整性是安全通信中的重要概念

> 解析：身份验证要求确保交换消息的各方创建特定消息的身份。故B项错误。

5. 下面哪项不是PKI四个关键要素中的一项：A
    A.交易数据
    B.数字证书
    C.公钥和私钥
    D.证书授权中心

> 解析：PKI有四个关键要素：数字证书、公钥和私钥、证书颁发机构、证书吊销列表。故A项错误。

### 普通

1. 下面关于排序服务说法错误的是：A
    A.排序服务是一个中心化的组件
    B.一个排序服务可以包含很多单独的由不同组织所有的节点
    C.排序节点使交易有序
    D.除了排序角色之外，排序节点还维护着允许创建通道的组织列表

> 解析：排序服务看起来像是一个中心化的组件，它最初被用来创建网络，然后连接到了网络中的每个通道，事实上，排序服务本身可以是完全去中心化的。跟作为网络的管理点一样，排序服务同样提供了另外一个关键的设施 —— 交易的分发点。排序服务是一个从应用程序搜集背书过的交易的组件，然后它会把这些交易进行排序并放进区块中，这些区块会被分发到通道中的每个 Peer 节点。在每个这样的提交节点中，交易不管是有效的还是无效的都会被记录下来，并且他们本地账本副本也会更新。故A项错误。

2. 下面关于链码说法错误的是：C
    A.链码是定义单项或多项资产的软件和能修改资产的交易指令
    B.链码是业务逻辑
    C.链码执行会写入一组键值，会被提交给网络并应用于当前节点的账本
    D.链码函数针对账本的当前状态数据库执行，并通过交易提案启动

> 解析：链码执行会写入一组键值（写集），会被提交给网络并应用于所有节点的账本。故C项错误。

3. 下面关于共识说法错误的是：B
    A.最近，在分布式账本技术中，共识已成为单个函数内特定算法的同义词
    B.共识就是简单地就交易顺序达成一致
    C.共识被定义为包含区块的一组交易的正确性的闭环验证
    D.当区块中交易的订单和结果满足明确的策略标准检查时，最终会达成共识

> 解析：共识不仅包括简单地就交易顺序达成一致，Hyperledger Fabric通过其在整个交易流程中的基本角色，从提案和背书到排序、验证和提交，突出了这种区别。故B项错误。

4. 下面关于交易检查说法错误的是：A
    A.交易检查和平衡发生在交易的生命周期结束后，包括使用背书策略来指定哪些特定成员必须背书某个交易类以及系统链码，以确保强制执行和维护这些策略
    B.在交易提交之前，节点将使用这些系统链码来确保存在足够的背书，并且它们来自适当的实体
    C.在包含交易的任何区块附加到账本之前，将进行版本控制检查，在此期间，账本的当前状态为同意
    D.最终检查可防止双重花费操作和可能危及数据完整性的其他威胁，并允许针对非静态变量执行功能

> 解析：交易检查和平衡发生在交易的生命周期中，并包括使用背书策略来指定哪些特定成员必须背书某个交易类以及系统链码，以确保强制执行和维护这些策略。故A项错误。

5. 下面关于Hyperledger Fabric说法错误的是：B
    A.Hyperledger Fabric是一个开源的企业级许可分布式账本技术平台
    B.Fabric平台也是许可的，这意味着它与公共非许可网络不同，Fabric的参与者可以是匿名的
    C.Fabric具有高度模块化和可配置的架构，可为各行各业的业务提供创新性、多样性和优化
    D.Fabric是第一个支持通用编程语言编写智能合约的分布式账本平台

> 解析：Fabric平台也是许可的，这意味着它与公共非许可网络不同，参与者彼此了解而不是匿名的或完全不信任的。故B项错误。


### 困难

1. 私有数据的交易流程正确的是：B
    A.提案、背书节点将提案响应发回、应用程序将交易提交给排序服务、模拟交易、提交区块
    B.提案、模拟交易、背书节点将提案响应发回、应用程序将交易提交给排序服务、提交区块
    C.提案、背书节点将提案响应发回、模拟交易、应用程序将交易提交给排序服务、提交区块
    D.模拟交易、提案、背书节点将提案响应发回、应用程序将交易提交给排序服务、提交区块

> 解析：当在链码中引用私有数据集合时，交易流程略有不同，以便在交易被提案、背书并提交到账本时保持私有数据的机密性。正确的顺序是：1.客户端应用程序提交一个提案请求，让属于授权集合的背书节点执行链码函数；2.背书节点模拟交易，并将私有数据存储在 瞬态数据存储中；3.背书节点将提案响应发送回客户端；4.客户端应用程序将交易提交给排序服务；5.在区块提交的时候，授权节点会根据集合策略来决定它们是否有权访问私有数据。故B项正确。

2. 下面关于Fabric平台说法错误的是：B
    A.Fabric平台支持可插拔的共识协议
    B.Fabric平台在企业应用中不能使用崩溃容错共识协议
    C.Fabric平台在去中心化的场景中，可能需要更传统的拜占庭容错共识协议
    D.Fabric可以利用不需要原生加密货币的共识协议来激励昂贵的挖矿或推动智能合约执行

> 解析：当部署在单个企业内或由可信任的权威机构管理时，完全拜占庭容错的共识可能是不必要的，并且大大降低了性能和吞吐量。在这种的情况下，崩溃容错（Crash Fault-Tolerant，CFT）共识协议可能就够了，而在去中心化的场景中，可能需要更传统的拜占庭容错（Byzantine Fault Tolerant，BFT）共识协议。故B项错误。

3. 下面哪项不是Fabric模块化组件：D
    A.可插拔的排序服务对交易顺序建立共识，然后向节点广播区块
    B.可插拔的成员服务提供者负责将网络中的实体与加密身份相关联
    C.可选的P2P gossip服务通过排序服务将区块发送到其他节点
    D.中心化组件

> 解析：总体来看，Fabric由以下模块化的组件组成：1.可插拔的排序服务对交易顺序建立共识，然后向节点广播区块；2.可插拔的成员服务提供者负责将网络中的实体与加密身份相关联；3.可选的P2P gossip服务通过排序服务将区块发送到其他节点；4.智能合约（“链码”）隔离运行在容器环境（例如Docker）中。它们可以用标准编程语言编写，但不能直接 访问账本状态；5.账本可以通过配置支持多种DBMS；6.可插拔的背书和验证策略，每个应用程序可以独立配置。故D项错误。

4. 下面哪项不适用于智能合约：B
    A.多个智能合约在网络中同时运行
    B.它们可以动态部署
    C.智能合约使用AOP方式编程
    D.应用代码应视为不被信任的，甚至可能是恶意的

> 解析：有三个关键点适用于智能合约，尤其是应用于平台时：1.多个智能合约在网络中同时运行；2.它们可以动态部署（很多情况下任何人都可以部署）；3.应用代码应视为不被信任的，甚至可能是恶意的。AOP是面向切片编程，跟智能合约没有必然联系。故B项错误。

5. 下面关于网络和通道配置说法错误的是：D
    A.网络和通道配置封装了网络成员同意的策略，提供了对网络资源访问控制的共享参考
    B.网络和通道配置也包含了有关网络和通道组成的一些情况，比如联盟的名字以及它所包含的组织
    C.在排序服务中的每个节点都记录着网络配置中的每个通道
    D.与peer节点同样的概念不能应用到通道配置

> 解析：与Peer节点同样的概念也可以应用到通道配置。故D项错误。

# 应用

## One

协作; 治理; 数字资产; NFT; 治理模式; 设计原则; Fabric智能合约独立运行生命周期; GO高级用法; Fabric GO智能合约接口; Fabric JAVA智能合约接口; solidity高级用法; 智能合约升级过程; AI（联邦学习等）; 物联网; 隐私计算
普通：15

### 简单

1. 区块链在企业应用中，下面哪项是不需要考虑的要求：D
    A.参与者必须是已认证或者可识别的
    B.网络需要获得许可
    C.高交易吞吐量性能和交易确认低延迟
    D.根据企业要求定制中心化特性

> 解析：对于企业应用，我们需要考虑以下要求：1.参与者必须是已认证的或者可识别的；2.网络需要获得许可；3.高交易吞吐量性能；4.交易确认低延迟；5.与商业交易有关的交易和数据的隐私和机密性。故D项错误。

2. 下面哪项属于区块链应用：D
    A.支付宝转账
    B.购买福利彩票
    C.查看自己的健康码
    D.使用以太坊转账

> 解析：A B C三项都是中心化的服务，D项以太坊是区块链2.0的平台，是去中心化的区块链应用。故D项正确。

3. 下面关于NFT说法错误的是：C
    A.NFT是一种加密代币
    B.NFT文件本身可以无限复制
    C.NFT可以互换
    D.NFT使用了区块链的技术

> 解析：非同质化代币一种存储在区块链（数位账本）上的数据单位，它可以代表艺术品等独一无二的数字物品。其是一种加密代币，但与比特币等加密货币不同，其不可互换。故C项错误。

4. 下面关于数字资产说法错误的是：B
    A.数字资产是指企业或个人拥有或控制的，以电子数据形式存在的，在日常活动中持有以备出售或处于生产过程中的非货币性资产
    B.数字资产就是NFT
    C.数字资产是可定义的
    D.数字资产信息的揭示具有可靠性

> 解析：NFT是非同质化代币，是一种数字资产，但是数字资产不等同于NFT。故B项错误。

5. 下面关于Solidity说法错误的是：A
    A.Solidity是动态类型语言，支持继承、库和复杂的用户定义类型等特性
    B.Solidity是一门面向合约的、为实现智能合约而创建的高级编程语言
    C.Solidity的设计目的是能在以太坊虚拟机上运行
    D.目前尝试Solidity编程的最好的方式是使用Remix

> 解析：Solidity是静态类型语言，支持继承、库和复杂的用户定义类型等特性。故A项错误。

6. 下面关于智能合约Go接口说法正确的是：C
    A.GetTxID是获取节点ID
    B.GetTransient是获取交易附属信息
    C.GetSignedProposal是获取交易提案所有相关数据
    D.GetQueryResult是分页查询匹配局部复合键的所有键值

> 解析：GetTxID是获取交易的交易ID；GetTransient是获取交易的临时信息，这类信息主要用于应用在程序级，并不写入账本数据；GetQueryResult是使用富查询方式查询状态数据库，状态数据库需要能够支持富查询功能；GetSignedProposal是获取交易提案所有相关数据。故C项正确。

7. 下面关于只能合约JAVA接口说法错误的是：C
    A.createCompositeKey功能是组合属性，形成复合键
    B.splitCompositeKey功能是将复合键拆分成一系列属性
    C.invokeChaincode功能是调用当前链码的Invoke方法
    D.delState功能是在账本中删除一对键值

> 解析：invokeChaincode功能是调用其它链码的Invoke方法。故C项错误。

8. 下面关于智能合约升级说法错误的是：A
    A.只能升级控制器合约，不能对数据合约进行升级
    B.对于多链场景，只需根据业务的需要来判断链与链之间的灰度策略，重复单链场景的升级即可
    C.对于跨链场景，需要根据跨链两端的具体情况来制定升级方法
    D.如果需要回退版本，只需要发布一个普通交易，将代理控制器合约的“Bank”映射到原版本的合约地址上即可

> 解析：智能合约的升级包括控制器合约和数据合约，二者都可以的升级。故A项错误。

9. 下面关于联邦学习说法错误的是：B
    A.联邦学习是在保障大数据交换时的信息安全、保护终端数据和个人数据隐私、保证合法合规的前提下，在多参与方或多计算节点之间开展高效率的机器学习的一种新兴人工智能基础技术
    B.与分布式机器学习相同，联邦学习需要一种去中心化分布系统来保证用户的隐私安全，在保障数据安全和交换、训练效率前提下进行有效的机器学习
    C.区块链作为一个去中心化、数据加密、不可篡改的分布式共享数据库，可以为联邦学习的数据交换提供数据保密性来对用户隐私进行保障，保证各参与方之间的数据安全，也可以保证多参与方提供数据进行模型训练的数据一致性区块链的价值驱动激励机制也能够增加各参与方之间提供数据、更新网络模型参数的积极性
    D.基于区块链的应用优点，目前已经有一些应用区块链的联邦学习系统提出

> 解析：与分布式机器学习不同的是联邦学习需要一种去中心化分布系统来保证用户的隐私安全，在保障数据安全和交换、训练效率前提下进行有效的机器学习。故B项错误。

10. 下面关于隐私计算说法错误的是：A
    A.隐私计算可以实现在聚合海量数据的前提下利用分散在多方的数据完成聚合计算和模型训练
    B.隐私计算保证整个过程中每一方的数据都不会暴露出来，是大数据时代解决隐私问题的关键
    C.隐私计算是一类技术的统称，其中包括安全多方计算、零知识证明、联邦学习等
    D.计算过程的可信性保证，仍然是目前的一个开放问题

> 解析：目前的人工智能模型大多依赖海量数据的训练，对于海量数据的需求导致了数据隐私问题的泛滥。而隐私计算可以实现在不聚合海量数据的前提下利用分散在多方的数据完成聚合计算和模型训练，保证整个过程中每一方的数据都不会暴露出来，是大数据时代解决隐私问题的关键。故A项错误。

11. 下面关于成员服务提供者说法错误的是：A
    A.因为一个私钥可能会被公开，所以引入了一种可以证实身份的机制即成员服务提供者
    B.成员服务提供者是一个可让身份被信任和被网络中其他参与者公认的，而不需要暴露成员的私钥的机制
    C.将可验证身份转换为角色的能力是Fabric网络功能的基础
    D.成员服务提供者是一种机制，使您能够加入一个需要许可的区块链网络

> 解析：证书机构通过生成可以用来证实身份的由公钥和私钥形成的键值对来发放认证信息。因为一个私钥永远不会被公开，所以引入了一种可以证实身份的机制即成员服务提供者（MSP）。故A项错误。

12. 下面关于通道MSP说法错误的是：D
    A.通道MSP在通道层面上定义了管理权和参与权
    B.通道MSP识别谁在通道层次拥有权限
    C.每个参与通道的组织都必须为其定义一个MSP
    D.系统通道MSP不包括参与排序服务的所有组织的MSP

> 解析：系统通道MSP包括参与排序服务的所有组织的MSP。故D项错误。

13. 下面关于本地MSP说法错误的是：C
    A.本地MSP是为客户端和节点定义的
    B.每个节点都必须定义一个本地MSP
    C.排序节点的本地MSP不在节点的文件系统上定义
    D.MSP定义了组织管理员。组织、组织的管理员、节点的管理员以及节点本身都应该具有相同的信任根

> 解析：排序节点的本地MSP也在节点的文件系统上定义。故C项错误。

14. 下面关于组织与MSP说法错误的是：B
    A.关于组织最重要的是他们在单个MSP下管理其成员
    B.MSP不允许将标识链接到组织
    C.组织和它的MSP之间的专属关系使得以组织的名字为前缀命名MSP是合乎情理的
    D.一个组织也可以被划分为多个组织单元，每个单元都有一定的职责，也称为affiliations

> 解析：MSP允许将标识链接到组织。故B项错误。

15. 下面关于MSP结构说法错误的是：C
    A.config.yaml:通过启用“Node OUs”和定义可接受的角色来配置Fabric中的身份分类特性
    B.cacerts:此文件夹包含此MSP代表的组织所信任的根CA的自签名X.509证书列表
    C.intermediatecerts:此文件夹包含一个身份列表，这些身份定义了具有此组织管理员角色的参与者
    D.signcert:此文件夹包含CA发行的节点签名密钥

> 解析：intermediatecerts:此文件夹包含该组织所信任的中间CA的X.509证书列表。每个证书必须由MSP中的一个根CA或者其本身颁发的CA链最终会指向一个受信任的根CA的任何中间CA进行签名。故C项错误。

