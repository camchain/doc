# invoke 方法

使用给定的参数以散列值调用智能合约，并返回结果。

> [!Note]
>
> 此方法用于测试你的虚拟机脚本，如同在区块链上运行一样。这个RPC调用对区块链没有任何影响。

## 参数说明

scripthash：智能合约脚本散列值。

params：传递给智能合约的参数。

## 调用示例

请求正文：

```json
{
  "jsonrpc": "2.0",
  "method": "invoke",
  "params": [
"0xda891d3e87c835013b53cd96c3f68fa94c920e53",
[
  {
    "type": "String",
    "value": "name"
  },
  {
    "type":"Boolean",
    "value": false
  }
]
  ],
  "id": 1
}
```

响应正文：

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "state": "HALT, BREAK",
        "gas_consumed": "2.489",
        "stack": [
            {
                "type": "ByteArray",
                "value": "576f6f6c6f6e67"
            }
        ]
    }
}
```