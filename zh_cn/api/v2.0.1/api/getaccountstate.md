# getaccountstate 方法

根据账户地址，查询账户资产信息。

## 参数说明

address：账户地址，以 A 开头的 34 位长度的字符串，如 AJBENSwajTzQtwyJFkiJSv7MAaaMc7DsRz。

## 调用示例

请求正文：

```json
{
  "jsonrpc":"2.0",
  "method":"getaccountstate",
  "params":["AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS"],
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
        "script_hash":"0x8845358b07c94846d7cbc2c99e796ef8c37a95f1",
        "frozen":false,
        "votes":
        [
        ],
        "balances":
        [
            {
                "asset":"0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec",
                "name":"CAM",
                "value":"115"
            },
            {
                "asset":"0x44c014a45d068d383422f6aa6131fe9fb3a3fc62ec5d01afe9c4e12ac2e46d02",
                "name":"Gas",
                "value":"19114"
            }
        ]
    }
}
```

响应说明：

script_hash：合约脚本散列，在 Cam 中所有账户都是合约账户。

frozen：该账户是否冻结。

votes：查询该地址用于投票的 Cam

balance：该地址的资产余额。

asset：资产 ID

name: 资产简称

value：资产金额。

