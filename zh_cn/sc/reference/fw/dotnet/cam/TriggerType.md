# TriggerType 枚举

用来表示智能合约触发器类型的枚举，通过 [Runtime.Trigger](Runtime/Trigger.md) 可以获得当前智能合约的触发器类型是 **验证合约（Verification）** 还是以 **应用合约（Application）** 。

更多关于触发器的知识，请点击 [智能合约的触发器](../../../../trigger.md)

命名[Cam.SmartContract.Framework.Services.Cam](../Cam.md)

程序集：Cam.SmartContract.Framework

## 语法

```c#
public enum TriggerType : byte
{
    Verification = 0x00,
    Application = 0x10
}
```

