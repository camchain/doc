# Blockchain.GetHeader 方法 (byte[])

通过区块高度，在区块链中查找该区块头。

命名空间：[Cam.SmartContract.Framework.Services.Cam](../../Cam.md)

程序集：Cam.SmartContract.Framework

## 语法

```c#
public static extern Cam.SmartContract.Framework.Services.Cam.Header GetHeader(uint height)
```

参数：区块 Hash，32 字节的字节数组。

返回值：区块，[Header](../Header.md) 类型。

## 示例

```c#
public class Contract1 : FunctionCode
{
    public static void Main()
    {
        Header bl = Blockchain.GetHeader(997027);
    }
}
```



[返回上级](../Blockchain.md)