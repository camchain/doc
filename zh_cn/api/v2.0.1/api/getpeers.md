# getpeers 方法

获得该节点当前已连接/未连接的节点列表。

## 调用示例

请求正文：

```json
{
  "jsonrpc": "2.0",
  "method": "getpeers",
  "params": [],
  "id": 1
}
```

响应正文：

```json
{
    "jsonrpc":"2.0",
    "id":1,
    "result":
    {
        "unconnected":
        [
        ],
        "bad":
        [
        ],
        "connected":
        [
            {
                "address":"::ffff:110.88.129.56",
                "port":16333
            },
            {
                "address":"::ffff:110.88.129.54",
                "port":16333
            },
            {
                "address":"::ffff:110.88.129.51",
                "port":16333
            },
            {
                "address":"::ffff:110.88.129.52",
                "port":16333
            },
            {
                "address":"::ffff:110.88.129.53",
                "port":16333
            },
            {
                "address":"::ffff:110.88.129.55",
                "port":16333
            }
        ]
    }
}
```

响应说明：

unconnected：当前未连接到的节点。

bad：不再连接（拉黑）的节点。

connected：当前已连接到的节点。

