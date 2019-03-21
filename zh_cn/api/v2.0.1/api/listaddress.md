# listaddress 方法

列出当前钱包内的所有地址。

> [!Note]
>
> 执行此命令前需要在 cam-server 节点中打开钱包。

## 调用示例

请求正文：

```json
{
  "jsonrpc": "2.0",
  "method": "listaddress",
  "params": [],
  "id": 1
}
```

响应正文：

```json
{
    "jsonrpc":"2.0",
    "id":3,
    "result":
    [
        {
            "address":"AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS",
            "haskey":true,
            "label":null,
            "watchonly":false
        },
        {
            "address":"AU4fgj8GkZ83U1KuonzVFDrDxp8dS3LBSn",
            "haskey":true,
            "label":null,
            "watchonly":false
        },
        {
            "address":"AS49yqDdrUXu1Hrcij7ykim7tzbFJTatTj",
            "haskey":true,
            "label":null,
            "watchonly":false
        }
    ]
}
```

响应说明：

address：钱包内的地址。

watchonly：该地址是否为监视地址。