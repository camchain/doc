# getnewaddress 方法

创建一个新的地址。

> [!Note]
> 执行此命令前需要在 cam-server 节点中打开钱包。

## 调用示例

请求正文：

```json
{
  "jsonrpc": "2.0",
  "method": "getnewaddress",
  "params": [],
  "id": 1
}
```

响应正文：

```json
{
    "jsonrpc":"2.0",
    "id":1,
    "result":"AU4fgj8GkZ83U1KuonzVFDrDxp8dS3LBSn"
}
```

响应说明：

返回新创建的地址。
