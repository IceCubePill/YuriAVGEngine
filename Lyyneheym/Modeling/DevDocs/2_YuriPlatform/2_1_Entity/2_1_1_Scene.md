﻿## 场景（Scene）

### 定义
游戏由场景组成，每个场景定义了在一段时间内游戏的呈现方式，是一个Yuriri脚本文件在主调用堆栈上的解析实体。游戏的演绎、标题画面、鉴赏画面都可以使用场景来制作，制作游戏的本质就是编写各场景的逻辑。<br/>
由于场景描述的是一段时间的游戏业务逻辑，因此在同一时刻，Yuri Engine只允许有一个场景处于活跃状态。即在通常状况下场景只能**跳转**，不能**调用**。在使用`jump`指令进行跳转时，运行时环境会保存当前场景的**上下文**（详见下一章上下文相关内容），并将游戏场景切换到目标场景处，同时**恢复**目标场景的上下文。所以场景的上下文在游戏运行时环境中是**静态的**，如果进行场景切换时需要重新初始化目标场景中的上下文，请务必书写处理逻辑。<br/>

### 场景的组成
一个场景在运行时拥有以下的组成部分：
- **场景逻辑**
由场景同名的Yuri-IL文件所书写的场景业务逻辑，它将被运行时环境解析成场景包装Scene并被引擎按序执行。
- **场景上下文**
维护着场景内部的变量和变量值的包装，这些上下文可以被**序列化保存**，可以被**快照回滚**，详见“**运行时环境**”章节。
- **标签字典**
场景内定义的所有标签及其位置的字典，以支持运行时环境执行跳转指令。
- **函数向量**
场景内定义的函数对象的向量，以支持运行时环境做函数调用操作。关于函数相关的内容详见下一小节“**函数**”。
- **并行函数向量**
场景内定义的并行处理函数对象的向量，以支持运行时环境进行并行处理。关于并行相关的内容详见“**运行时环境**”章节。

### 程序集信息
| Property | Value |
| :-------- | :--------: |
| 命名空间   | Yuri.Yuriri.Scene |
| 最低版本   | 1.0 |
| 并行安全   | - |