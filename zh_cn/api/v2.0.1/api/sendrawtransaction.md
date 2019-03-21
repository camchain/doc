# sendrawtransaction 方法

广播交易。

## 参数说明

hex：在程序中构造的已签名的交易序列化后的 16 进制字符串。

## 调用示例

请求正文：

```json
{
  "jsonrpc": "2.0",
  "method": "sendrawtransaction",
  "params": ["146ba9c8ed1c179f2de59bfe71f5264260e9992e2851c10962616c616e63654f6667530e924ca98ff6c396cd533b0135c8873e1d89da"],
  "id": 1
}
```

响应正文：

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": false
}
```

响应说明：

当 result 为 true 时表明当前交易广播成功，

当 result 为 false 时表示当前交易广播失败，原因可能有双重花费、签名不完整等。

本示例中广播了一个已经确认的交易，因为双重花费所以广播失败。

