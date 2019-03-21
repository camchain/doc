# getrawtransaction 方法

根据指定的散列值，返回对应的交易信息。

## 参数说明

txid：交易 ID。

verbose：可选参数，verbose 默认值为 0，verbose 为 0 时返回的是交易的序列化后的信息，用 16 进制字符串表示，如果从中获取详细信息需要调用 SDK 来进行反序列化。verbose 为 1 时返回的是对应交易的详细信息，用 Json 格式字符串表示。

## 调用示例

请求正文：

```json
{
  "jsonrpc":"2.0",
  "method":"getrawtransaction",
  "params":["0x7cfa1e22bb812f023a95ef7c67df92a2c417c89065481f166fef4b228348b65d"],
  "id":1
}
```

响应正文：

```json
{
    "jsonrpc":"2.0",
    "id":1,
    "result":"80000002b349d33673ea15e70baa8311e892e97a87ebd4ce8a853dd091232a85f130c7d60100afdab6cb512f1effef814943ef0e42e098aa4ffa0a94690a6e5feab66260d9f1010004eced05b797b8bdd1ebcc2e7b427d7714b6e4ef63d219655183a781fe6149acce002f685900000000f1957ac3f86e799ec9c2cbd74648c9078b354588026de4c22ae1c4e9af015dec62fca3b39ffe3161aaf62234388d065da414c04400a3e11100000000f1957ac3f86e799ec9c2cbd74648c9078b354588eced05b797b8bdd1ebcc2e7b427d7714b6e4ef63d219655183a781fe6149acce002f6859000000006ba9c8ed1c179f2de59bfe71f5264260e9992e28026de4c22ae1c4e9af015dec62fca3b39ffe3161aaf62234388d065da414c04408f1c17de46e00006ba9c8ed1c179f2de59bfe71f5264260e9992e28024140bf2190ea17e0a11a0cd64c296482fbe307b55a6c76efd5d19efbffdbf5eb36109e6dfa582d49dfb677193c01361be043c0bc3463c2a858e2868b364083723c26232103762ee6cd8ed0fc80152925c11f9050b4001bdc65ea7a47c1d25ba4f3b881adfcac4140047f78ae6a8f3daf29d2771d9b400bd110764803a6099b3dc3d80945433480f9dd52b26b12861d94287f1186945ca2ce265e4c7b69aa6cb681fcc8baa50276d5232102ebcae5333d911ef6f2975a4407a865412d722bf60376c77b9ec0126fe65c1f8eac"
}
```

请求正文：

verbose = 1，返回 JSON 格式的结果。

```json
{
  "jsonrpc":"2.0",
  "method":"getrawtransaction",
  "params":["0x7cfa1e22bb812f023a95ef7c67df92a2c417c89065481f166fef4b228348b65d",1],
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
        "txid":"0x7cfa1e22bb812f023a95ef7c67df92a2c417c89065481f166fef4b228348b65d",
        "size":518,
        "type":"ContractTransaction",
        "version":0,
        "attributes":
        [
        ],
        "vin":
        [
            {
                "txid":"0xd6c730f1852a2391d03d858aced4eb877ae992e81183aa0be715ea7336d349b3",
                "vout":1
            },
            {
                "txid":"0xf1d96062b6ea5f6e0a69940afa4faa98e0420eef434981efff1e2f51cbb6daaf",
                "vout":1
            }
        ],
        "vout":
        [
            {
                "n":0,
                "asset":"0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec",
                "value":"15",
                "address":"AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS"
            },
            {
                "n":1,
                "asset":"0x44c014a45d068d383422f6aa6131fe9fb3a3fc62ec5d01afe9c4e12ac2e46d02",
                "value":"3",
                "address":"AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS"
            },
            {
                "n":2,
                "asset":"0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec",
                "value":"15",
                "address":"ARb9LtCmNwBpwurXG73FR8ofvgoZywi5Nr"
            },
            {
                "n":3,
                "asset":"0x44c014a45d068d383422f6aa6131fe9fb3a3fc62ec5d01afe9c4e12ac2e46d02",
                "value":"1219276.41461",
                "address":"ARb9LtCmNwBpwurXG73FR8ofvgoZywi5Nr"
            }
        ],
        "sys_fee":"0",
        "net_fee":"0",
        "scripts":
        [
            {
                "invocation":"40bf2190ea17e0a11a0cd64c296482fbe307b55a6c76efd5d19efbffdbf5eb36109e6dfa582d49dfb677193c01361be043c0bc3463c2a858e2868b364083723c26",
                "verification":"2103762ee6cd8ed0fc80152925c11f9050b4001bdc65ea7a47c1d25ba4f3b881adfcac"
            },
            {
                "invocation":"40047f78ae6a8f3daf29d2771d9b400bd110764803a6099b3dc3d80945433480f9dd52b26b12861d94287f1186945ca2ce265e4c7b69aa6cb681fcc8baa50276d5",
                "verification":"2102ebcae5333d911ef6f2975a4407a865412d722bf60376c77b9ec0126fe65c1f8eac"
            }
        ],
        "blockhash":"0x71a45c169eae4c70ef18525822442b186fbdf0355fea6f06c690e13fd7880894",
        "confirmations":156,
        "blocktime":1534143637
    }
}
```



