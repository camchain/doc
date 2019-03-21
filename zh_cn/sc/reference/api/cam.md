# Cam 命名空间

Cam 命名空间是 Cam 区块链所提供的 API，提供了访问区块链账本数据的和操作持久化存储区的方法。

注：本文中标记 `new` 和 ` 已弃用 ` 的地方是 2.0 版本相对 1.6 版本的更改之处。

从区块链查询数据的 API：

| API                           | 说明                   |
| ----------------------------- | -------------------- |
| Cam.Blockchain.GetHeight      | 获得当前区块高度             |
| Cam.Blockchain.GetHeader      | 通过区块高度或区块 Hash，查找区块头 |
| Cam.Blockchain.GetBlock       | 通过区块高度或区块 Hash，查找区块  |
| Cam.Blockchain.GetTransaction | 通过交易 ID 查找交易         |
| Cam.Blockchain.GetAccount     | 根据合约脚本的散列来获得一个账户     |
| Cam.Blockchain.GetValidators  | `new` 获得共识人的公钥       |
| Cam.Blockchain.GetAsset       | 根据资产 ID 查找资产         |
| Cam.Blockchain.GetContract    | `new` 根据合约散列获取合约内容   |

区块类 API：

| API                           | 说明                         |
| ----------------------------- | -------------------------- |
| Cam.Header.GetHash            | 获得该区块的散列                   |
| Cam.Header.GetVersion         | 获得区块版本号                    |
| Cam.Header.GetPrevHash        | 获得前一个区块的散列                 |
| Cam.Header.GetIndex           | 获得该区块的高度                   |
| Cam.Header.GetMerkleRoot      | 获得该区块中所有交易的 Merkle Tree 的根 |
| Cam.Header.GetTimestamp       | 获得区块的时间戳                   |
| Cam.Header.GetConsensusData   | 获得该区块的共识数据（共识节点生成的伪随机数）    |
| Cam.Header.GetNextConsensus   | 获得下一个记账合约的散列值              |
| Cam.Block.GetTransactionCount | 获得当前区块中交易的数量               |
| Cam.Block.GetTransactions     | 获得当前区块中所有的交易               |
| Cam.Block.GetTransaction      | 获得当前区块中指定的交易               |

交易类 API：

| API                           | 说明                                       |
| ----------------------------- | ---------------------------------------- |
| Cam.Transaction.GetHash       | 获得当前交易的 Hash                             |
| Cam.Transaction.GetType       | 获得当前交易的类型                                |
| Cam.Transaction.GetAttributes | 查询当前交易的所有属性                              |
| Cam.Transaction.GetInputs     | 查询当前交易的所有交易输入                            |
| Cam.Transaction.GetOutputs    | 查询当前交易的所有交易输出                            |
| Cam.Transaction.GetReferences | 查询当前交易的所有输入所引用的交易输出                      |
| Cam.Attribute.GetUsage        | 获得该交易特性中的用途                              |
| Cam.Attribute.GetData         | 获得该交易特性中用途之外的额外数据                        |
| Cam.Input.GetHash             | 所引用的交易的交易散列                              |
| Cam.Input.GetIndex            | 所引用的交易输出在其全部交易输出列表中的索引                   |
| Cam.Output.GetAssetId         | 获得资产 ID                                  |
| Cam.Output.GetValue           | 获得交易金额                                   |
| Cam.Output.GetScriptHash      | 获得脚本散列                                   |
| Cam.Enrollment.GetPublicKey   | ` 已弃用 ` 已用 Cam.Blockchain.GetValidators 替代 |

账户类 API：

| API                       | 说明                    |
| ------------------------- | --------------------- |
| Cam.Account.GetScriptHash | 获得该合约账户的脚本散列          |
| Cam.Account.GetVotes      | 获得该合约账户投给其它人的的投票信息    |
| Cam.Account.GetBalance    | 通过资产 ID 获得该账户中这种资产的余额 |

资产类 API：

| API                    | 说明                                    |
| ---------------------- | ------------------------------------- |
| Cam.Asset.GetAssetId   | 获得该资产的 ID                             |
| Cam.Asset.GetAssetType | 获得该资产的类别                              |
| Cam.Asset.GetAmount    | 获得该资产的总量                              |
| Cam.Asset.GetAvailable | 获得该资产的已经发行出去的数量                       |
| Cam.Asset.GetPrecision | 获得该资产的精度（最小分割数量），单位为小数点之后的位数          |
| Cam.Asset.GetOwner     | 获得该资产的所有人（公钥）                         |
| Cam.Asset.GetAdmin     | 获得该资产的管理员（合约地址），有权对资产的属性（如总量，名称等）进行修改 |
| Cam.Asset.GetIssuer    | 获得该资产的发行人（合约地址），有权进行资产的发行             |

合约类 API：

| API                    | 说明       |
| ---------------------- | -------- |
| Cam.Contract.GetScript | 获得该合约的脚本 |

存储类 API：

| API                    | 说明                              |
| ---------------------- | ------------------------------- |
| Cam.Storage.GetContext | `new` 获取当前存储区上下文                |
| Cam.Storage.Get        | 查询操作，在持久化存储区中通过 key 查询对应的 value |

运行时相关的 API：


| API                      | 说明                                  |
| ------------------------ | ----------------------------------- |
| Cam.Runtime.GetTrigger   | `new` 获得该智能合约的触发条件（应用合约 or 鉴权合约）    |
| Cam.Runtime.CheckWitness | `new` 验证调用该智能合约的交易 / 区块是否验证过所需的脚本散列 |
| Cam.Runtime.Notify       | `new` 在智能合约中向执行该智能合约的客户端发送通知        |
| Cam.Runtime.Log          | `new` 在智能合约中向执行该智能合约的客户端发送日志        |

参考：以上 API 的源码位于 Cam 项目中的 [src/Cam/SmartContract/StateReader.cs](https://github.com/Cam-project/Cam/blob/master/Cam/SmartContract/StateReader.cs) 文件。

------

此类 API 会对智能合约的状态进行修改

| API                            | 说明                               |
| ------------------------------ | -------------------------------- |
| Cam.Account.SetVotes           | 设置该合约账户投给其它人的的投票信息               |
| Cam.Validator.Register         | `new` 报名成为共识人                    |
| Cam.Asset.Create               | `new` 注册一种资产                     |
| Cam.Asset.Renew                | `new` 为资产续费                      |
| Cam.Contract.Create            | `new` 发布智能合约                     |
| Cam.Contract.Migrate           | `new` 迁移 / 更新智能合约                |
| Cam.Contract.Destroy           | `new` 销毁合约                       |
| Cam.Contract.GetStorageContext | `new` 获得合约的存储上下文                 |
| Cam.Storage.Put                | 插入操作，以 key-value 的形式向持久化存储区中插入数据 |
| Cam.Storage.Delete             | 删除操作，在持久化存储区中通过 key 删除对应的 value  |

参考：以上 API 的源码位于 Cam 项目中的 [src/Cam/SmartContract/StateMachine.cs](https://github.com/Cam-project/Cam/blob/master/Cam/SmartContract/StateMachine.cs) 文件。
