# getassetstate 方法

根据指定的资产编号，查询资产信息。

## 参数说明

asset_id：资产 ID（资产标识符），即该资产在注册时的交易 ID。

如Cam为：0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec

Gas为：0x44c014a45d068d383422f6aa6131fe9fb3a3fc62ec5d01afe9c4e12ac2e46d02

其余资产 ID 可以通过 [CLI 命令](../../../node/console.html) 中的 `list asset` 命令查询，也可以在区块链浏览器中查询。

## 调用示例

请求正文：

```json
{
  "jsonrpc":"2.0",
  "method":"getassetstate",
  "params":["0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec"],
  "id":1
}
```

响应正文：

```json
{
    "jsonrpc":"2.0",
    "id":1,
    "result":
    {
        "version":0,
        "id":"0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec",
        "type":"GoverningToken",
        "name":
        [
            {
                "lang":"zh-CN",
                "name":"CAM"
            },
            {
                "lang":"en",
                "name":"CAM"
            }
        ],
        "amount":"200000000",
        "available":"200000000",
        "precision":0,
        "owner":"00",
        "admin":"Abf2qMs1pzQb8kYk9RuxtUb9jtRKJVuBJt",
        "issuer":"Abf2qMs1pzQb8kYk9RuxtUb9jtRKJVuBJt",
        "expiration":4000000,
        "frozen":false
    }
}
```

