# getblock 方法

根据指定的索引，返回对应的区块信息。

## 参数说明

index：区块索引（区块高度） = 区块数 - 1。

verbose：可选参数，verbose 默认值为 0，verbose 为 0 时返回的是区块的序列化后的信息，用 16 进制字符串表示，如果从中获取详细信息需要调用 SDK 来进行反序列化。verbose 为 1 时返回的是对应区块的详细信息，用 Json 格式字符串表示。

## 调用示例

请求正文：

```json
{
  "jsonrpc": "2.0",
  "method": "getblock",
  "params": [10000],
  "id": 1
}
```

响应正文：

```json
{
    "jsonrpc":"2.0",
    "id":1,
    "result":"000000002cdfa400dccdfa8f3027fe56ec48144aa293c6161840478d0ae503fe060394ea3aeab7015f17c7b67166937b14c45005d94f0a68592b478db2fc61f6522366f69dea5f5a1027000014160ea536c43e0f78a180770083f58694ea82a9b635ccb20d45c5e101fd4501400ca32a853c8bf3344719e147f55208a5d7315c7ac378a10a5c9043af63ac19a118af6f6a8ec0c62e4e21e7c690e7afb547522bc8daeb41aeeb45e648ccce898640e7674effa50b032b948311b6e7d15ad8d7f2a6d8863f48440f99cac0bf5133f7934b524691638881c5d11ef8910f8b3af2b46c91851b18b2097522130258f33a4067b2403b181ed8caad9c1a35a24878195a8e4ba78ffa226d301c5e38c490a16196c591a66067fa85a47492491fa996788f01dfc436241cf974b4472601c6b0c240394c63bb1f8771b8ec1824b060a02ff1ca144b5f60de170b307792351a23f7e2db23d025e1c12133629d0274bd258e0e4e22177469556b1851a6ced3b27d6585408009e73e7a2405d0204b3b6c9fcc4988426b2676f7edf30d183be217ad03ff41566df57dd7f53ddeca1b3e0ec1c3a1633fd5dfbc85f63c5395c941972550a926f15521025e82b0d87946507bcfac71117b756640a136da6685aea4dc6828c6e6ca0d68832103681649df11f826afc16adceab7af57bc937e290da08323502fda7d1914ee18a0210275e022cb64dff870b9df068c3d928cd011655665e15432895158e064f44e9be5210298ff2c553a553f78042709658ca720eab8a48f902aebaae862f398845c15eb342103a905fe6b018eead29561567ba76267e22fd3549404091bacd243e74d99b816442103b515281957e6cda1e22489a95bc5d2090d0893c63bb40a438d84db4affc87bac2102d6d2032b4cd0e5b4c87675afb72234ee19ae6840bfc696e56adace062f7dda5157ae01000014160ea500000000"
}
```

请求正文：

verbose = 1，返回 JSON 格式的结果。

```json
{
  "jsonrpc": "2.0",
  "method": "getblock",
  "params": [10000, 1],
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
        "hash":"0xba2d61a356cff335b37cfb34c69fd20c5ec599e018319dfaff1722c40d72e476",
        "size":686,
        "version":0,
        "previousblockhash":"0xea940306fe03e50a8d47401816c693a24a1448ec56fe27308ffacddc00a4df2c",
        "merkleroot":"0xf6662352f661fcb28d472b59680a4fd90550c4147b936671b6c7175f01b7ea3a",
        "time":1516235421,
        "index":10000,
        "nonce":"0f3ec436a50e1614",
        "nextconsensus":"ASmiCrtCia2WnxuA18VautJ5de8z89hnU8",
        "script":
        {
            "invocation":"400ca32a853c8bf3344719e147f55208a5d7315c7ac378a10a5c9043af63ac19a118af6f6a8ec0c62e4e21e7c690e7afb547522bc8daeb41aeeb45e648ccce898640e7674effa50b032b948311b6e7d15ad8d7f2a6d8863f48440f99cac0bf5133f7934b524691638881c5d11ef8910f8b3af2b46c91851b18b2097522130258f33a4067b2403b181ed8caad9c1a35a24878195a8e4ba78ffa226d301c5e38c490a16196c591a66067fa85a47492491fa996788f01dfc436241cf974b4472601c6b0c240394c63bb1f8771b8ec1824b060a02ff1ca144b5f60de170b307792351a23f7e2db23d025e1c12133629d0274bd258e0e4e22177469556b1851a6ced3b27d6585408009e73e7a2405d0204b3b6c9fcc4988426b2676f7edf30d183be217ad03ff41566df57dd7f53ddeca1b3e0ec1c3a1633fd5dfbc85f63c5395c941972550a926",
            "verification":"5521025e82b0d87946507bcfac71117b756640a136da6685aea4dc6828c6e6ca0d68832103681649df11f826afc16adceab7af57bc937e290da08323502fda7d1914ee18a0210275e022cb64dff870b9df068c3d928cd011655665e15432895158e064f44e9be5210298ff2c553a553f78042709658ca720eab8a48f902aebaae862f398845c15eb342103a905fe6b018eead29561567ba76267e22fd3549404091bacd243e74d99b816442103b515281957e6cda1e22489a95bc5d2090d0893c63bb40a438d84db4affc87bac2102d6d2032b4cd0e5b4c87675afb72234ee19ae6840bfc696e56adace062f7dda5157ae"
        },
        "tx":
        [
            {
                "txid":"0xf6662352f661fcb28d472b59680a4fd90550c4147b936671b6c7175f01b7ea3a",
                "size":10,
                "type":"MinerTransaction",
                "version":0,
                "attributes":
                [
                ],
                "vin":
                [
                ],
                "vout":
                [
                ],
                "sys_fee":"0",
                "net_fee":"0",
                "scripts":
                [
                ],
                "nonce":2769163796
            }
        ],
        "confirmations":607179,
        "nextblockhash":"0x3725109fe999285c914ec1de43f628604daefe00a47aad68a189d1d8660bf7af"
    }
}
```



