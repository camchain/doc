# invokescript 方法

通过虚拟机传递脚本之后返回结果。

> [!Note]
>
> 此方法用于测试你的虚拟机脚本，如同在区块链上运行一样。这个RPC调用对区块链没有任何影响。

## 参数说明

script：一个由虚拟机运行的脚本，与 InvocationTransaction 中携带的脚本相同。

## 调用示例

请求正文：

```json
{
  "jsonrpc": "2.0",
  "method": "invokescript",
  "params": ["00046e616d656711c4d1f4fba619f2628870d36e3a9773e874705b"],
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