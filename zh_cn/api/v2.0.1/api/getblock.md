# getblock 方法

根据指定的散列值，返回对应的区块信息。

## 参数说明

hash：区块散列值。

verbose：可选参数，verbose 默认值为 0，verbose 为 0 时返回的是区块的序列化后的信息，用 16 进制字符串表示，如果从中获取详细信息需要调用 SDK 来进行反序列化。verbose 为 1 时返回的是对应区块的详细信息，用 Json 格式字符串表示。

## 调用示例

请求正文：

```json
{
  "jsonrpc":"2.0",
  "method":"getblock",
  "params":["0x9e156ebc9b03039ed5029a6eb58c7eaffc2b57205067db3d8c039e9763a78b85"],
  "id":1
}

```

响应正文：

```json
{
    "jsonrpc":"2.0",
    "id":1,
    "result":"0000000067cd576630c5c5464cbec99f8532c04cc723ba6745ef1a4bd02ce22887b62fd2bc73865238532ee1d20d68c140a344f2dee2f8ba47607f02b44babae05acf0452336715bd16a090080ff1a76c417727d4b314a7020031c4a173bf92e906e920072f1a0f801fd4501409ac58b1151bcc13b95ec1c749d16b944de71974127dbf42e0b87606ecd4f2a69db85879e0d7ff1751a66c9ae958654e51a2b14fae424a34189a8247975bfa8e640bb471a1c46b147cec0b7817cf066b5a121b346a485e05d4efea7f9f83d1cc0df07d23257c3d63a478984576c2ce338c54a90c4f50c8f7f97691782a4e8c80e25406c8a3569ee5fbc88f70ae9c3db86d9dd1ab2a5a86c38f33fd90093f64fa07d7a6ef9b5adb78cf90b9446e775faacb7e22f514797a4fab1bbba16891a3bb7dfbf4081bde9d3c5fd9ba0e93fa3e71c858304cd172adc51fa5439e05ad71136e2dc24b9448751af0dc5406be874ff83e34df7332b8e539c8437438828f8aa5e7da52a40e4a6654ff365332c3756b782221bc4bba634305f3abea34d113018c3f8cf6464ea756129b5753388f63e83038efd0cf6fdc194e1f54f64fc9f38ef203c24cae5f15521035e822e49ec81f8f5b0543f7d8b6bebfd130ffb89df23051529da9839aef8d1cd21025e82b0d87946507bcfac71117b756640a136da6685aea4dc6828c6e6ca0d68832103681649df11f826afc16adceab7af57bc937e290da08323502fda7d1914ee18a0210275e022cb64dff870b9df068c3d928cd011655665e15432895158e064f44e9be5210298ff2c553a553f78042709658ca720eab8a48f902aebaae862f398845c15eb342103a905fe6b018eead29561567ba76267e22fd3549404091bacd243e74d99b816442103b515281957e6cda1e22489a95bc5d2090d0893c63bb40a438d84db4affc87bac57ae01000080ff1a7600000000"
}
```

请求正文：

verbose = 1，返回 JSON 格式的结果。

```json
{
  "jsonrpc":"2.0",
  "method":"getblock",
  "params":["0x9e156ebc9b03039ed5029a6eb58c7eaffc2b57205067db3d8c039e9763a78b85",1],
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
        "hash":"0x9e156ebc9b03039ed5029a6eb58c7eaffc2b57205067db3d8c039e9763a78b85",
        "size":686,
        "version":0,
        "previousblockhash":"0xd22fb68728e22cd04b1aef4567ba23c74cc032859fc9be4c46c5c5306657cd67",
        "merkleroot":"0x45f0ac05aeab4bb4027f6047baf8e2def244a340c1680dd2e12e5338528673bc",
        "time":1534146083,
        "index":617169,
        "nonce":"7d7217c4761aff80",
        "nextconsensus":"ANdTNfjNZjgtoJhontTuuboVCiUBhGwmx5",
        "script":
        {
            "invocation":"409ac58b1151bcc13b95ec1c749d16b944de71974127dbf42e0b87606ecd4f2a69db85879e0d7ff1751a66c9ae958654e51a2b14fae424a34189a8247975bfa8e640bb471a1c46b147cec0b7817cf066b5a121b346a485e05d4efea7f9f83d1cc0df07d23257c3d63a478984576c2ce338c54a90c4f50c8f7f97691782a4e8c80e25406c8a3569ee5fbc88f70ae9c3db86d9dd1ab2a5a86c38f33fd90093f64fa07d7a6ef9b5adb78cf90b9446e775faacb7e22f514797a4fab1bbba16891a3bb7dfbf4081bde9d3c5fd9ba0e93fa3e71c858304cd172adc51fa5439e05ad71136e2dc24b9448751af0dc5406be874ff83e34df7332b8e539c8437438828f8aa5e7da52a40e4a6654ff365332c3756b782221bc4bba634305f3abea34d113018c3f8cf6464ea756129b5753388f63e83038efd0cf6fdc194e1f54f64fc9f38ef203c24cae5",
            "verification":"5521035e822e49ec81f8f5b0543f7d8b6bebfd130ffb89df23051529da9839aef8d1cd21025e82b0d87946507bcfac71117b756640a136da6685aea4dc6828c6e6ca0d68832103681649df11f826afc16adceab7af57bc937e290da08323502fda7d1914ee18a0210275e022cb64dff870b9df068c3d928cd011655665e15432895158e064f44e9be5210298ff2c553a553f78042709658ca720eab8a48f902aebaae862f398845c15eb342103a905fe6b018eead29561567ba76267e22fd3549404091bacd243e74d99b816442103b515281957e6cda1e22489a95bc5d2090d0893c63bb40a438d84db4affc87bac57ae"
        },
        "tx":
        [
            {
                "txid":"0x45f0ac05aeab4bb4027f6047baf8e2def244a340c1680dd2e12e5338528673bc",
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
                "nonce":1981480832
            }
        ],
        "confirmations":6,
        "nextblockhash":"0x4f36d5e4154adc75149ef2e24b0350852bfccc183d76d6b00b3f07ffa54bbca9"
    }
}
```



