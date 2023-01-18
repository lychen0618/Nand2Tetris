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

## Week2
### Binary Numbers
二进制和十进制之间的转换
### Binary Arithmetic
* 加
* 减：由于使用补码表示，和加法一样
* 乘（软件部分）

### The Arithmetic Logic Unit (ALU)

### Project2
实现多个adder chip以及ALU chip

## Week3
### Clock
把连续的时间分解成一定大小的时间单元（0-1, tik-tok），这样做的目的有两点：
1. 使得系统的状态稳定：各组件状态的变化会有一定的延迟，在一个时间单元的后面，可以认为状态稳定了。
2. 同步计算机中各组件的工作

### Sequential Logic
* Sequential Logic和Combinatorial Logic的区别：前者在时间t的输入会依赖t-1的信息，而后者的输入只依赖于时间t时的信息。

### DFF Gate
在该课程中这个gate可以认为是primitive的。

At the beginning of each clock cycle, the outputs of all the DFFs in the computer commit to their inputs during the previous time unit. At all other times, the DFFs are ‘‘latched’’, meaning that changes in their inputs have no immediate effect on their outputs.

Hardware implementations achieve this time dependency by simultaneously feeding the master clock signal to all the DFF gates in the platform. Hardware simulators emulate the same effect in software. As far as the computer architect is concerned, the end result is the same: The inclusion of a DFF gate in the design of any chip ensures that the overall chip, as well as all the chips up the hardware hierarchy that depend on it, will be inherently time-dependent. These chips are called sequential, by definition.

### Register and RAM

### Project3
实现不同大小的RAM和一个程序计数器（PC）：完成了子目录03/a下的所有chip

## Week4
### 机器码和汇编语言（Hack Computer Platform）
* Machine language can be construed as both a programming tool and an integral part of the hardware platform. In fact, just as we say that the machine language is designed to exploit a given hardware platform, we can say that the hardware platform is designed to fetch, interpret, and execute instructions written in the given machine language.

* Hack汇编语言
    * 命令的类别：
        1. 算术和逻辑运算
        2. 内存访问操作：Direct addressing, Immediate addressing, Indirect addressing
        3. 流程控制：返回循环的开头（循环）、条件执行（分支）、子过程调用

### Project4
使用Hack的汇编语言实现mult和fill

#### 注意事项
* mult
    测试脚本会在一定的tick-tok后检查结果，所以如果代码需要的ticktok过多，无法通过测试。
* fill：注意下面的写法
    ```txt
    @SCREEN
    D=A
    @i
    A=D+M
    M=-1
    ```

## Week5
### Computer Architecture Fundamentals
* The Stored Program Concept -> 计算机功能的多样性
* 不同的计算机架构：
    1. Turing machine -> Theoretical Computer Science
    2. von Neumann machine -> Practical Computer Platform
    3. Harvard architecture: 和von Neumann架构不同的是，data memory and the instruction memory are kept in separate physical memory units that have 
    distinct address spaces
* CPU
    1. ALU
    2. a set of registers
    3. control unit: The instruction decoding is done by some control unit, which is also 
responsible for figuring out which instruction to fetch and execute next.
* fetch-execute cycle

### Project5
实现Memory、CPU和Computer chip
