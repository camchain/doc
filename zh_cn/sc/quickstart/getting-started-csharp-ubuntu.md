# 在 ubuntu 上如何用 C# 编写智能合约

在 ubuntu 中使用C#编写智能合约，需要进行如下操作：

   1. 创建 library 项目，编写代码，引入智能合约库。
   2. 编译 Cam-compiler/Camn 生成编译器。
   3. 执行命令运行 Camn 生成.avm 文件。

## 新建合约项目

1. 在 dotnet 命令行中创建 library 项目:

   ```c#
   mkdir CamContractDemo
   cd ./CamContractDemo/
   dotnet new library
   rm ./Class1.cs
   vim CamContractDemo.cs
   ```

   ![](../../../assets/create_Cam_contract.png)

2. 键入下面代码后按 `ESC`+`wq!` 保存退出。

   ```c#
   using Cam.SmartContract.Framework;
   using Cam.SmartContract.Framework.Services.Cam;

   public class CamContractDemo: SmartContract
   {
       public static bool Main()
       {
           return true;
       }
   }
   ```

3. 添加智能合约引用：

   ```
   dotnet add package Cam.SmartContract.Framework --version 1.0.0
   ```

   ![](../../../assets/Cam_addpackage.png)

4. 编译智能合约项目：

   ```
   dotnet publish -o ../testlib
   ```

   ![](../../../assets/build_Cam_contract_project.png)

## 生成编译器

    cd ..
    git clone https://github.com/camchain/Cam-compiler.git
    cd  ./Cam-compiler/Camn
    dotnet publish -o ../../testlib

## 生成 .avm 文件

    cd ../../testlib
    dotnet Camn.dll CamContractDemo.dll
    mkdir ../output
    cp CamContractDemo.avm ../output/CamContractDemo.avm

