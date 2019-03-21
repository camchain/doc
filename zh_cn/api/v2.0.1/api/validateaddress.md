# validateaddress 方法

验证地址是否是正确的 Cam 地址。

## 参数说明

address：地址。

## 调用示例

请求正文：

```json
{
  "jsonrpc": "2.0",
  "method": "validateaddress",
  "params": ["AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS"],
  "id": 1
}
```

响应正文：

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "address": "AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS",
        "isvalid": true
    }
}
```


