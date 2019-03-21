# getstorage 方法

根据合约脚本散列和存储的 key，返回存储的 value。

## 参数说明

script_hash: 合约脚本散列。

key: 存储区的键。（需要转化为hex string）

## 调用示例

请求正文：

```json
{
	"jsonrpc": "2.0",
	"method": "getstorage",
	"params": ["0xda891d3e87c835013b53cd96c3f68fa94c920e53", "234892348"],
	"id": 1
}
```

响应正文：

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": "ab8239"
}
```

