# getbestblockhash 方法

获取主链中高度最大的区块的散列。

## 调用示例

请求正文：

```json
{
  "jsonrpc": "2.0",
  "method": "getbestblockhash",
  "params": [],
  "id": 1
}
```

响应正文：

```json
{
    "jsonrpc":"2.0",
    "id":1,
    "result":"0x9e156ebc9b03039ed5029a6eb58c7eaffc2b57205067db3d8c039e9763a78b85"
}
```

响应说明：

result：主链中高度最大的区块的散列。

