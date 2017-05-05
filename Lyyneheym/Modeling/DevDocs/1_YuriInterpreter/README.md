﻿## Yuri Interpreter

在游戏逻辑没有被以游戏脚本的形式分离出来以前，它是以硬编码的形式结合到游戏的主程序之中，与游戏各部分运行时环境维护模块紧密耦合的。这种编码方式给通常只需使用可被封装的基本功能的AVG游戏开发带来不便：其一是开发调试需要重复编译整个工程，非常耗费时间；其二是演出、素材和程序内部类混杂在一起，可维护性低，代码重用性差，程序员和演出人员之间分工难以明确，降低了开发效率。

游戏脚本系统的引入就是为了解决上述问题，它将游戏运行时环境与游戏演出的业务逻辑分离开来，使得上层开发者不必考虑底层的实现，只需要从脚本里调用封装好的接口就可以实现相应的功能。游戏脚本的存在还有如下的好处：它降低了编译的时间成本，脚本虚拟机一旦完成就不需要在之后的游戏逻辑改变时重新编码和编译；降低了各模块耦合程度，底层的图形渲染、并行处理、消息队列等细节被隐藏起来，业余开发者只关心显示文本、显示图片、播放音效这些简单接口就可以进行开发，降低了开发门槛，有利于模块的复用；游戏引擎拓展脚本技术使得开发者在能够使用简单封装接口的情况下，仍可以通过脚本来自定义个性化的游戏系统。