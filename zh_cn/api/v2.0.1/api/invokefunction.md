# invokefunction 方法

使用给定的操作和参数，以散列值调用智能合约之后返回结果。

> [!Note]
>
> 此方法用于测试你的虚拟机脚本，如同在区块链上运行一样。这个RPC调用对区块链没有任何影响。

## 参数说明

scripthash：智能合约脚本散列值。

operation：操作名称（字符串）。

params：传递给智能合约操作的参数。

## 调用示例

请求正文：

```json
{
  "jsonrpc": "2.0",
  "method": "invokefunction",
  "params": [
    "0xda891d3e87c835013b53cd96c3f68fa94c920e53",
    "balanceOf",
    [
      {
        "type": "Hash160",
        "value": "0x282e99e9604226f571fe9be52d9f171cedc8a96b"
      }
    ]
  ],
  "id": 3
}

```

响应正文：

```json
{
    "jsonrpc":"2.0",
    "id":3,
    "result":
    {
        "script":"146ba9c8ed1c179f2de59bfe71f5264260e9992e2851c10962616c616e63654f6667530e924ca98ff6c396cd533b0135c8873e1d89da",
        "state":"HALT, BREAK",
        "gas_consumed":"0.308",
        "stack":
        [
            {
                "type":"ByteArray",
                "value":"00c69398ef8623"
            }
        ],
        "tx":"d10136146ba9c8ed1c179f2de59bfe71f5264260e9992e2851c10962616c616e63654f6667530e924ca98ff6c396cd533b0135c8873e1d89da000000000000000000000000"
    }
}
```
