# getversion 方法

获取查询节点的版本信息。

## 调用示例

请求正文：

```json
{
  "jsonrpc": "2.0",
  "method": "getversion",
  "params": [],
  "id": 3
}
```

响应正文：

```json
{
    "jsonrpc":"2.0",
    "id":1,
    "result":
    {
        "port":16333,
        "nonce":444483942,
        "useragent":"\/CAM:1.0.0\/"
    }
}
```