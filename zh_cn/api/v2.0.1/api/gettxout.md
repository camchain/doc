# gettxout 方法

根据指定的散列和索引，返回对应的unspent交易输出（零钱）信息。如果交易输出已经花费，返回结果为空。

## 参数说明

txid：交易 ID。

n：要获取的交易输出在该交易中的索引（从 0 开始）。

## 调用示例

请求正文：

```json
{
  "jsonrpc":"2.0",
  "method":"gettxout",
  "params":["0x7cfa1e22bb812f023a95ef7c67df92a2c417c89065481f166fef4b228348b65d",1],
  "id":1
}

```

响应正文：

```json
{
    "jsonrpc":"2.0",
    "id":1,
    "result":
    {
        "n":1,
        "asset":"0x44c014a45d068d383422f6aa6131fe9fb3a3fc62ec5d01afe9c4e12ac2e46d02",
        "value":"3",
        "address":"AdoFZkWAJoMTJ4MkdRrtBDAbWyrRhEF8cS"
    }
}
```



