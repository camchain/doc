# getbalance 方法

根据指定的资产编号，返回钱包中对应资产的余额信息。

> [!Note]
> 执行此命令前需要在 cam-server 节点中打开钱包。

## 参数说明

asset_id：资产 ID（资产标识符），即该资产在注册时的交易 ID。

如Cam为：0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec

Gas为：0x44c014a45d068d383422f6aa6131fe9fb3a3fc62ec5d01afe9c4e12ac2e46d02

其余资产 ID 可以通过 [CLI 命令](../../../node/console.html) 中的 `list asset` 命令查询，也可以在区块链浏览器中查询。

## 调用示例

请求正文：

```json
{
  "jsonrpc":"2.0",
  "method":"getbalance",
  "params":["0xceac4961fe81a783516519d263efe4b614777d427b2eccebd1bdb897b705edec"],
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
        "balance":"115",
        "confirmed":"115"
    }
}
```

响应说明：

balance：钱包中该资产的真实余额。

confirmed：钱包中该资产的已确认的金额，只有已确认的金额可以用来转账。

balance 和 confirmed 二者可能会不相等，仅在从钱包中转出一笔钱，而且有找零未确认时时，confirmed 值会小于balance。当这笔交易确定后，二者会变得相等。

