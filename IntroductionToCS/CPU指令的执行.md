# CPU指令的执行

## 指令集
在冯诺依曼结构体中的CPU只能执行CPU预先设计好的指令集中的指令。这个指令是在芯片设计之初就是设定对应电路逻辑的电信号指令。这个指令合集就是指令集。

## 分类
目前通常分为2大类指令集：
复杂指令集CISC（Complex Instruction Set Computer）
精简指令集RISC（Reduced Instruction Set Computer）

## 架构
指令集也有业内的统一规范和架构，目前常用的指令集架构
X86指令集：是属于复杂指令集，代表有Intel和AMD。
ARM指令集：是属于精简指令集，代表有骁龙和M1。


## 指令集的特点
1、所有的指令都是一串二进制数编码的。
2、这串二进制数就是指令码。
3、指令码操作的数据是操作数。
4、操作数是二进制计数形式。
5、指令码的操作数可以有1个可以有2个可以有3个甚至可以没有操作数。

## 性能
指令集也是CPU性能的重要指标

### 优劣势对比

| 类型 | 架构 | 优势 | 劣势 |
| :-- | :-- | :-- | :-- |
| RISC | ARM | 低能耗下的高性能 | 性能上限有局限性 |
| CISC | X86 | 高性能的上限较高 | 特定任务计算的性能提升瓶颈 |

> 这里补充一下，现在很多的CISC的很多指令就是将CISC解析成RISC执行来提升性能的，也可以理解成很多CISC指令是对RISC指令的封装。

## 指令执行流程

### 知识点关联关系
这个部分要结合[冯诺依曼体](./冯诺依曼式计算机)的知识点和[计算机结构](./计算机结构)的知识。

TODO未完待续
