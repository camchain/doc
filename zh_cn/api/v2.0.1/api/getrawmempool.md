# getrawmempool 方法

获取内存中未确认的交易列表。

## 调用示例

请求正文：

```json
{
  "jsonrpc": "2.0",
  "method": "getrawmempool",
  "params": [],
  "id": 1
}
```

响应正文：

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    "b0c36f0500bea671e38dd7ac9a9bf2887ef98d3359737bd7aa8a4efbbe0e6fe6"
  ]
}
```

这些是节点收到的未确定的交易，即零确认的交易。