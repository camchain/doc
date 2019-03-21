# sendmany 方法

批量转账命令，并且可以指定找零地址。

> [!Note]
> 执行此命令前需要在 cam-server 节点中打开钱包。

## 参数说明

\<outputs_array> \[fee=0] \[change_address]

outputs_array：数组，数组中的每个元素的数据结构如下：

​	{"asset": \<asset>,"value": \<value>,"address": \<address>}

​	asset：资产 ID（资产标识符），即该资产在注册时的 RegistTransaction 的交易 ID。

如Cam为：0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec

Gas为：0x44c014a45d068d383422f6aa6131fe9fb3a3fc62ec5d01afe9c4e12ac2e46d02

​	其余资产 ID 可以通过 [CLI 命令](../../../node/console.html) 中的 `list asset` 命令查询，也可以在区块链浏览器中查询。

​	value：转账金额。

​	address：收款地址。

fee：手续费，可选参数，默认为 0。

change_address：找零地址，可选参数，默认为钱包中第一个标准地址。

## 调用示例

请求正文：

```json
{
    "jsonrpc": "2.0",
    "method": "sendmany",
    "params": [
        [
            {
                "asset": "0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec",
                "value": 1,
                "address": "AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS"
            },
            {
                "asset": "0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec",
                "value": 1,
                "address": "AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS"
            }
        ]
    ],
    "id": 1
}
```

请求正文（包含手续费和找零地址）：

```json
{
    "jsonrpc": "2.0",
    "method": "sendmany",
    "params": [
        [
            {
                "asset": "0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec",
                "value": 1,
                "address": "AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS"
            },
            {
                "asset": "0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec",
                "value": 1,
                "address": "AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS"
            }
        ],
        0,
        "AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS"
    ],
    "id": 1
}
```

响应正文：

```json
{
    "jsonrpc":"2.0",
    "id":1,
    "result":
    {
        "txid":"0x74bfac8e80b4f1a5c3566c2d647df8a078cc25267bf30d28a38209ebaf302660",
        "size":322,
        "type":"ContractTransaction",
        "version":0,
        "attributes":
        [
        ],
        "vin":
        [
            {
                "txid":"0xdc39101d0b6bf20431e01c5fc9a774f8ef5c58d32cf0324ce6555910c58eeb43",
                "vout":1
            }
        ],
        "vout":
        [
            {
                "n":0,
                "asset":"0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec",
                "value":"1",
                "address":"AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS"
            },
            {
                "n":1,
                "asset":"0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec",
                "value":"1",
                "address":"AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS"
            },
            {
                "n":2,
                "asset":"0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec",
                "value":"12",
                "address":"AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS"
            }
        ],
        "sys_fee":"0",
        "net_fee":"0",
        "scripts":
        [
            {
                "invocation":"40524af6c64a30aef4ced59643c88c80979f02893fa52cf2178188a27adf04dda19ebff5a9b7653b84dca0049a0f71af66ba0d859340159c0fd215dbdabf5090a8",
                "verification":"21035e822e49ec81f8f5b0543f7d8b6bebfd130ffb89df23051529da9839aef8d1cdac"
            }
        ]
    }
}
```

响应说明：

返回如上的交易详情说明交易发送成功，否则交易发送失败。

JSON 格式不正确，会返回 Parse error。                                                                                                                                         

如果签名不完整会返回待签名的交易。

如果余额不足会返回错误信息。
