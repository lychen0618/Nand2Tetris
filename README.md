# Nand2Tetris

## Week1
### Boolean Functions
* 布尔运算符：and, or, not等
* 运算定律：交换律、结合律、德摩根定律等
* 布尔方程
    * 两种表达方式
        * 真值表
        * 布尔表达式
    * **任何布尔方程都可以只使用and, or, not来表示**
    * 使用德摩根定律，可以通过and和not得到or
* 布尔表达式的简化：通过运算定律；通过观察真值表
* Nand: 这门课定义的一个布尔操作
    * ```x Nand y = Not(x And y)```
    * 任何布尔方程都可以用一个只包含这个操作的布尔表达式来表示


### Gate Logic
关于如何使用逻辑门来实现布尔方程
* 逻辑门
    * 基本：nand, and等
    * 复合

### Hardware Description Language
A gate is a simple chip. (只不过提供的功能比较简单)
* 一个逻辑门接口（例如三个输入，一个输出，提供```a And b And c```功能）可能有很多不同的实现。HDL是一种用来描述逻辑门接口具体实现的语言。
* 常用的HDL语言
    * VHDL
    * Verilog
* A **hardware simulator** is a software system that enables building and simulating logic gates and chips before actually committing them to silicon. This is exactly what hardware engineers do in practice: they build and test computers in simulation, using HDL and hardware simulators.
* 基于Simulator和现有硬件模拟出来的chip的性能肯定是不如实际硬件

### Project1
使用HDL实现15个chip：目前实现了Not, And, Or, Not16
#### 注意事项
* 使用Hardware Simulator时要安装较高版本的jdk，否则会显示找不到Nand.class。因为Nand.class是java13编译的，低版本的jdk不能使用高版本的.class文件。