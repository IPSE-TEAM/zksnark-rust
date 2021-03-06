### 零知识证明运用

零知识证明的工作流程主要分为4步：

首先将欲证明的计算性问题，转换成门电路 Circuit
然后将门电路 Circuit 转换成 R1CS
再将 R1CS 转变成 QAP
最后，基于 QAP 实现 zkSNARK 的算法


### 参与方

- 数据提供方Alice（花钱存储）
- 数据存储方Bob（矿工）
- 区块链主网
- 数据索引方（IPSE搜索引擎）

### 流程

- 数据提供方存储数据，本地加密或者不加密，向链上提交存储数据请求（出价）。
    - 订单要说明数据存储周期，数据冷热，备份数量，数据提取次数。
    - 数据提供方支付定金，锁定在链上合约里。
- 数据存储方接单，提供存储。接单矿工需要有公网ip，要能远程接收数据提供方的数据。
    - 如果是多个备份，多个数据存储方可以一起接单。
    - 如果是热数据，就必须在矿工保存一份准备随时提取，如果是冷数据，可以让其他存储节点保存。
- Alice向Bob推送数据，BoB存储完毕后，做出一个数据存储零知识证明上链。
- 区块链主网验证后，按照合约发放一定比例的Token给Bob。
- 区块链主网定时验证Bob提供的数据存储零知识证明，逐渐释放Token给Bob。
- Alice需要提取数据时，需要在链上记录一次，然后向Bob提取数据。