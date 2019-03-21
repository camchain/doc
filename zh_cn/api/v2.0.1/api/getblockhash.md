# getblockhash 方法

根据指定的索引，返回对应区块的散列值。

## 参数说明

index：区块索引。

## 调用示例

请求正文：

```json
{
  "jsonrpc": "2.0",
  "method": "getblockhash",
  "params": [10000],
  "id": 1
}
```

响应正文：

```json
{
    "jsonrpc":"2.0",
    "id":1,
    "result":"0x70c60597ddd3f811831bf51c61cd4718402a7bed27b2b44f48ebb0d0f65ae76b"
}
```



