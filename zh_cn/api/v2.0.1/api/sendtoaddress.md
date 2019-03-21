# sendtoaddress 方法

向指定地址转账。

> [!Note]
> 执行此命令前需要在 cam-server 节点中打开钱包。

## 参数说明

asset_id：资产 ID（资产标识符），即该资产在注册时的 RegistTransaction 的交易 ID。

如Cam为：0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec

Gas为：0x44c014a45d068d383422f6aa6131fe9fb3a3fc62ec5d01afe9c4e12ac2e46d02

其余资产 ID 可以通过 [CLI 命令](../../../node/console.html) 中的 `list asset` 命令查询，也可以在区块链浏览器中查询。

address：收款地址。

value：转账金额。

fee：手续费，可选参数，默认为 0。

## 调用示例

请求正文：

```json
{
  "jsonrpc": "2.0",
  "method": "sendtoaddress",
  "params": ["0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec","AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS",1],
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
        "txid":"0x3de4410f3cda67154a9ea2a7b9d5879be0b4c50936b532f184359f147fecdd0e",
        "size":202,
        "type":"ContractTransaction",
        "version":0,
        "attributes":
        [
        ],
        "vin":
        [
            {
                "txid":"0x74bfac8e80b4f1a5c3566c2d647df8a078cc25267bf30d28a38209ebaf302660",
                "vout":0
            }
        ],
        "vout":
        [
            {
                "n":0,
                "asset":"0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec",
                "value":"1",
                "address":"AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS"
            }
        ],
        "sys_fee":"0",
        "net_fee":"0",
        "scripts":
        [
            {
                "invocation":"40b90c22adf04e74d14a13f854947e3156bc109a1c28f02aea06cb414791c2822b8e7139bf6474bddc21bda35a168bce617fb41517716d16e9154cc15ead57b541",
                "verification":"21035e822e49ec81f8f5b0543f7d8b6bebfd130ffb89df23051529da9839aef8d1cdac"
            }
        ]
    }
}
```

响应说明：

返回如上的交易详情说明交易发送成功，否则交易发送失败。

如果签名不完整会返回待签名的交易。

如果余额不足会返回错误信息。