# API 参考

每个 Cam 节点 cam-server 都可选的提供了一套 API 接口，用于从节点获取区块链数据，使得开发区块链应用变得十分方便。接口通过 [JSON-RPC](http://wiki.geekdream.com/Specification/json-rpc_2.0.html) 的方式提供，底层使用 HTTP/HTTPS 协议进行通讯。要启动一个提供 RPC 服务的节点，可运行以下命令：

`dotnet cam-server.dll /rpc`

若要通过 HTTPS 的方式访问 RPC 服务器，需要在启动节点前修改配置文件 `config.json`，并设置域名、证书和密码：

```json
{
  "ApplicationConfiguration": {
    "Paths": {
      "Chain": "Chain"
    },
    "P2P": {
      "Port": 18333,
      "WsPort": 18334
    },
    "RPC": {
      "Port": 18331,
      "SslCert": "YourSslCertFile.xxx",
      "SslCertPassword": "YourPassword"
    }
  }
}
```

JSON-RPC 服务器启动后，会监听 TCP 端口，默认端口如下。P2P 和 WebSocket 的端口详见 [Cam 节点介绍](../../node/introduction.html)。

|                | 主网（Main Net） | 测试网（Test Net） |
| -------------- | ------------ | ------------- |
| JSON-RPC HTTPS | 18331        | 16331         |
| JSON-RPC HTTP  | 18332        | 16332         |

## 命令列表

| 方法                                       | 参数                                       | 说明                           | 备注       |
| ---------------------------------------- | ---------------------------------------- | ---------------------------- | -------- |
| [dumpprivkey](api/dumpprivkey.html)        | \<address>                               | 导出指定地址的私钥                    | 需要打开钱包   |
| [getaccountstate](api/getaccountstate.html) | \<address>                               | 根据账户地址，查询账户资产信息              |          |
| [getapplicationlog](api/getapplicationlog.html) | \<txid> [verbose=0]                      | 根据指定的交易 ID 获取合约日志            | 需要启动日志记录 待开发 |
| [getassetstate](api/getassetstate.html) | \<asset_id>                              | 根据指定的资产编号，查询资产信息             |          |
| [getbalance](api/getbalance.html)          | \<asset_id>                              | 根据指定的资产编号，返回钱包中对应资产的余额信息     | 需要打开钱包   |
| [getbestblockhash](api/getbestblockhash.html) |                                          | 获取主链中高度最大的区块的散列              |          |
| [getblock](api/getblock.html)              | \<hash> [verbose=0]                      | 根据指定的散列值，返回对应的区块信息           |          |
| [getblock](api/getblock2.html)             | \<index> [verbose=0]                     | 根据指定的索引，返回对应的区块信息            |          |
| [getblockcount](api/getblockcount.html)    |                                          | 获取主链中区块的数量                   |          |
| [getblockhash](api/getblockhash.html)      | \<index>                                 | 根据指定的索引，返回对应区块的散列值           |          |
| [getblocksysfee](api/getblocksysfee.html)  | \<index>                                 | 根据指定的索引，返回截止到该区块前的系统手续费      |          |
| [getconnectioncount](api/getconnectioncount.html) |                                          | 获取节点当前的连接数                   |          |
| [getcontractstate](api/getcontractstate.html) | \<script_hash>                           | 根据合约脚本散列，查询合约信息              |          |
| [getnewaddress](api/getnewaddress.html)    |                                          | 创建一个新的地址                     | 需要打开钱包   |
| [getrawmempool](api/getrawmempool.html)    |                                          | 获取内存中未确认的交易列表                |          |
| [getrawtransaction](api/getrawtransaction.html) | \<txid> [verbose=0]                      | 根据指定的散列值，返回对应的交易信息           |          |
| [getstorage](api/getstorage.html)          | \<script_hash>  \<key>                   | 根据合约脚本散列和存储的 key，返回存储的 value |          |
| [gettxout](api/gettxout.html)              | \<txid> \<n>                             | 根据指定的散列和索引，返回对应的交易输出（零钱）信息   |          |
| [getpeers](api/getpeers.html)              |                                          | 获得该节点当前已连接/未连接的节点列表          |          |
| [getversion](api/getversion.html)          |                                          | 获取查询节点的版本信息                  |          |
| [invoke](api/invoke.html)                  | \<script_hash>  \<params>                | 使用给定的参数以散列值调用智能合约            |          |
| [invokefunction](api/invokefunction.html)  | \<script_hash>  \<operation>  \<params>  | 以指定的脚本散列值调用智能合约，传入操作及参数      |          |
| [invokescript](api/invokescript.html)      | \<script>                                | 通过虚拟机运行脚本并返回结果               |          |
| [listaddress](api/listaddress.html)        |                                          | 列出当前钱包内的所有地址                 | 需要打开钱包   |
| [sendrawtransaction](api/sendrawtransaction.html) | \<hex>                                   | 广播交易                         |          |
| [sendfrom](api/sendfrom.html)              | \<asset_id> \<from>\<to> \<value> [fee=0] | 从指定地址，向指定地址转账                | 需要打开钱包   |
| [sendtoaddress](api/sendtoaddress.html)    | \<asset_id> \<address> \<value> [fee=0]  | 向指定地址转账                      | 需要打开钱包   |
| [sendmany](api/sendmany.html)              | \<outputs_array> \[fee=0] \[change_address] | 批量转账命令                       | 需要打开钱包   |
| [validateaddress](api/validateaddress.html) | \<address>                               | 验证地址是否是正确的 Cam 地址            |          |


## GET 请求示例

一次典型的 JSON-RPC GET 请求格式如下：

下面以获取主链中区块的数量方法为例。

请求 URL：

```
http://somewebsite.com:18332?jsonrpc=2.0&method=getblockcount&params=[]&id=1
```

发送请求后，将会得到如下的响应：

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": 616975
}
```

## POST 请求示例

一次典型的 JSON-RPC Post 请求的格式如下：

下面以获取主链中区块的数量方法为例。

请求 URL：

```
http://somewebsite.com:18332
```

请求 Body：

```json
{
  "jsonrpc": "2.0",
  "method": "getblockcount",
  "params": [],
  "id": 1
}
```

发送请求后，将会得到如下的响应：

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": 616975
}
```

## 其它

[C# JSON-RPC 使用方法](https://github.com/chenzhitong/CSharp-JSON-RPC/blob/master/json_rpc/Program.cs)
