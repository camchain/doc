# Transaction.GetOutputs 方法 ()

查询当前交易的所有交易输出。

命名空间：[Cam.SmartContract.Framework.Services.Cam](../../Cam.md)

程序集：Cam.SmartContract.Framework

## 语法

```c#
public extern Cam.SmartContract.Framework.Services.Cam.TransactionOutput[] GetOutputs()
```

返回值：当前交易的所有交易输出，[TransactionOutput](../TransactionOutput.md) 数组。

## 示例

```c#
public class Contract1 : FunctionCode
{
    public static void Main()
    {
        byte[] transaction = new byte[] { 88, 114, 160, 206, 130, 137, 41, 94, 119, 120, 242, 71, 232, 244, 3, 20, 165, 69, 182, 232, 106, 185, 119, 239, 183, 65, 174, 220, 157, 251, 28, 215 };
        Transaction tx = Blockchain.GetTransaction(transaction);
        TransactionOutput[] outputs = tx.GetOutputs();
    }
}
```



[返回上级](../Transaction.md)