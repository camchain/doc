﻿# CLI 命令参考

打开命令行，定位到 cam-server 所在目录，输入下面代码即可启动 Cam 的命令行钱包（即 Cam 节点）。

`dotnet cam-server.dll`

本篇教程将介绍命令行钱包的所有命令，你可以通过输入命令的形式操作钱包，如创建打开钱包、导入导出私钥、转账、启动共识等。

首先我们先了解一下该命令行钱包有哪些命令，在命令行中输入 `help` ，回车，你会看到命令列表。

下面是所有命令的说明，命令中尖括号 `<>` 表示的是参数，方括号 `[]` 表示的是可选参数，或符号 `|` 表示所填的参数可以是其中任意一种，等号 `=` 表示可选参数在不输入情况下的默认值。

## 控制台指令

| 命令      | 功能说明      |
| ------- | --------- |
| version | 显示当前软件的版本 |
| help    | 帮助菜单      |
| clear   | 清除屏幕      |
| exit    | 退出程序      |

## 钱包操作

| 命令                                       | 功能说明                              | 备注     |
| ---------------------------------------- | --------------------------------- | ------ |
| create wallet \<path>                    | 创建钱包文件                            |        |
| open wallet \<path>                      | 打开钱包文件                            |        |
| upgrade wallet \<path>                   | 升级旧版钱包文件                          |        |
| rebuild index                            | 重建钱包索引                            | 需要打开钱包 |
| list address                             | 列出钱包中的所有账户                        | 需要打开钱包 |
| list asset                               | 列出钱包中的所有资产                        | 需要打开钱包 |
| list key                                 | 列出钱包中的所有公钥                        | 需要打开钱包 |
| show utxo [id\|alias]                    | 列出钱包中指定资产的 UTXO                   | 需要打开钱包 |
| show gas                                 | 列出钱包中的所有可提取及不可提取的 GAS             | 需要打开钱包 |
| claim gas                                | 提取钱包中的所有可提取的 GAS                  | 需要打开钱包 |
| create address [n=1]                     | 创建地址 / 批量创建地址                       | 需要打开钱包 |
| import key \<wif\|path>                  | 导入私钥 / 批量导入私钥                       | 需要打开钱包 |
| export key \[address] [path]             | 导出私钥                              | 需要打开钱包 |
| send \<id\|alias> \<address> \<value>\|all [fee=0] | 向指定地址转账 参数分别为：资产 ID，对方地址，转账金额，手续费 | 需要打开钱包 |
| import multisigaddress m pubkeys...      | 创建多方签名合约                              | 需要打开钱包 |
| sign \<jsonObjectToSign>            | 签名  参数为：记录交易内容的 json 字符串                            | 需要打开钱包 |
| relay \<jsonObjectToSign>                | 广播  参数为：记录交易内容的 json 字符串                            | 需要打开钱包 |

以下命令可能需要详细解释一下：


👉 `rebuild index` 

重建钱包索引。为什么要重建钱包索引，重建钱包索引有什么用？

钱包中有一个字段，记录了当前钱包同步的区块高度，每新增加一个区块，钱包客户端就会同步区块，将钱包中的资产和交易更新。假设当前记录的区块高度为 100，然后你执行了 import key 命令导入了私钥，这时钱包仍然是从区块高度为 100开始计算你的资产。如果导入的地址在区块高度小于 100的时候有一些交易，这些交易和对应的资产将不会体现在钱包中，所以要重建钱包索引，强制让钱包从区块高度为0开始计算你的资产。

假如由于种种原因，钱包中的某笔交易未确认，这时资产已经从钱包中扣除，但并未经过整个区块链网络的确认。如果想删掉这笔未确认的交易使钱包中的资产正常显示也需要重建钱包索引。

新创建的钱包不用重建钱包索引，只有要导入私钥或者钱包中资产显示异常时才需要重建钱包索引。

👉 `show utxo [id|alias]`

列出钱包中指定资产的 UTXO，示例如入输出如下所示：

```
Cam>show utxo Cam
0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec:2
total: 1 UTXOs
Cam>show utxo gas
0x44c014a45d068d383422f6aa6131fe9fb3a3fc62ec5d01afe9c4e12ac2e46d02:1
total: 1 UTXOs
Cam>show utxo 0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec
0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec:0
total: 1 UTXOs
```

👉 `show gas` 

列出钱包中的所有可提取及不可提取的 GAS，输出结果如下：

```
unavailable: 0.0015
  available: 0.004
```

其中 unavailable 表示不可提取的 GAS，available 表示可提取（待提取）的 GAS。

* 注：这里不包含已提取的 GAS，查看已提取的 GAS 请用 list asset 命令。

什么是可提取的 GAS，什么是不可提取的 GAS？

每一个 Cam 都有两种状态：unspent 和 spent。每一个未提取的 GAS 也有两种状态，available 和 unavailable。一个 Cam 的生命周期以转入地址起始，转出地址截止，转入时状态变为 unspent，转出时状态变为 spent。当 Cam 处于 unspent 状态时，所产生的 Gas 为 unavailable 状态，即不可提取。当 Cam 处于 spent 状态时，期间所产生的 GAS 变为 available，用户可以提取。

如何将钱包中的所有 unavailable GAS 转为 available GAS 呢，很简单，将钱包中的所有 Cam 转到钱包中的任意一个地址即可。

👉 `claim gas` 

提取钱包中的所有可提取的 GAS，该过程是通过一个特殊的交易 Claim Transaction 完成的，输入命令后，客户端会输出 Claim Transaction 的 ID（提取 GAS 这笔交易的 ID）。

执行完 claim gas 命令后，再执行 list asset 会显示 GAS 有增加。

👉 `create address [n=1]` 

可以输入 create address  来创建一个地址，也可以输入 create address 100 来批量创建 100个地址，批量创建的地址会自动导出到 address.txt 文件中。

👉 `export key [address] [path]`

你可以指定导出哪个地址对应的私钥，也可以指定导出至指定的文件中，例如下面的命令都是合法的。该命令需要验证钱包密码。

export key

export key AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS

export key key.txt

export key AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS key.txt

👉  `import key <wif|path>`

导入私钥，你可以指定导入一个私钥，或者是导入一个文件中的多个私钥，例如下面的命令都是合法的。

import key L2woGn**************************************WzZ4vd

import key key.txt

如果是指定文件的话，文件里的私钥格式请参考 export key key.txt 的输出。

👉 `send <id|alias> <address> <value>|all [fee=0]`

转账，一共有 4 个参数，第一个参数是资产 ID，第二个参数是收款地址，第三个参数是转账金额（当输入 all 即为钱包中该资产的全部数量），第四个参数是手续费（这个参数可不填，默认为0）。该命令需要验证钱包密码。假如我想转 100 Cam 转到这个地址“AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS”，我需要输入以下命令。

send 0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS 100

因为第二个参数除了资产 ID，还可以填写资产缩写，如 Cam，gas，所以以上命令可以写成：

send Cam AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS 100

不知道资产 ID 怎么办？请输入 list asset 命令查看钱包中的所有资产。

👉 `import multisigaddress m pubkeys...`

以 m 个最小签名数量来创建多方签名的合约地址，例如两个公钥创建的多方签名地址， m 可以为 1 或 2， 后面的参数就是两方的公钥。

👉 `sign <jsonObjectToSign>` 

从签名数量为 1 以上的多方签名合约中提取资产时，需要多方进行签名，参数为记录这段交易的 json 字符串。 签名完整后才能广播出去。

👉 `relay <jsonObjectToSign>` 

签名完整后，可以将这段交易信息进行广播。参数同样为记录这段交易的 json 字符串。


## 查看节点信息

| 命令                             | 功能说明                    |
| ------------------------------ | ----------------------- |
| show state                     | 显示当前区块链同步状态             |
| show node                      | 显示当前已连接的节点地址和端口         |
| show pool                      | 显示内存池中的交易（这些交易处于零确认的状态） |
| export blocks [path=chain.acc] | 导出全部区块数据，导出的结果可以用作离线同步  |
| export blocks \<start> [count] | 从指定区块高度导出指定数量的区块数据，导出的结果可以用作离线同步  |
## 高级指令

| 命令              | 功能说明 |
| --------------- | ---- |
| start consensus | 启动共识 |
启动共识的前提是该钱包有共识的权限，在 Cam 主网上可以通过投票选举获得共识的权限，如果自己部署的私有链可以在 `protocol.json` 中设置共识节点的公钥，详情可参考 [私链搭建](../network/private-chain.html)。

