### 设计目标和应用场景

#### 设计目标：

Shy语言旨在实现一个简单、易学的汇编语言，帮助学习计算机原理的学生更好地了解汇编语言。其简洁性也适用于承担一些轻量级任务。
(目前正在考虑基于Shy语言实现一个简易高级语言，见[这里](https://github.com/Shyliuli/shy_language/blob/main/Shy_C.md) )

#### 主要应用场景：

1. **教学课堂**：Shy语言可以帮助学生更好地理解指针等概念，同时加深对计算机原理的理解。
2. **极端低性能场景**：在必须编写汇编语言的情况下，Shy语言提供了一种更加简洁易写的选择。

#### 与x86汇编相比：

Shy语言更加精简，共有19组（共42个，每组两个命令，对应不同的参数类型，out和in由于考虑是否为ascii,有四种）基础指令。它包含了如小于、小于等于这样的语法糖，尽管理论上只需要大于和等于即可实现所有功能。所有的指令命名结构均为 `<基础指令>+<参数类型（addr/num）>`。Shy语言仅有一种16位字节数据表示，使得开发时无需考虑数据类型，简化了开发过程。

### 环境准备

[参考这里](https://github.com/Shyliuli/shy_language/blob/main/README.md)

### 语言基础

#### 地址表：

- Shy语言运行在 `Shy_hardware`（尚未实现）或 `Shyemu`上。
- 拥有 `0x00-0xFFFF`的内存地址可用空间，其中一部分是保留的，如下所示：
  - `0x00-0x0F`：寄存器（`ax`, `bx`, `cx`, `dx`, `ex`, `fx`, `gx`, `hx`, `ix`, `jx`, `kx`, `lx`, `mx`（程序计数器，保存运行位置），`nx`（改变此寄存器则程序退出），`ox`（保存 `equ`等指令的判断结果）），‘px’。
  - `0x10-0x4F`：保留空间（用于命令等）。
  - `0x50-0xFFFF`：内存，其中 `0x36-0x1FFF`为变量存储，`0x2000-0xFFFF`为程序。

#### 基础语法规则：

- Shy语言文件包含数据和代码两部分，格式如下：
  ```
  _datastart_
  数据
  _dataend_
  _codestart_
  代码
  _codeend_
  ```
- 数据部分直接使用地址（`0x`开头的16进制数）+数据（可以是 `0x`开头的16进制数，纯数字，也可以是字符或字符串，如果是后者则会以所写地址为开头自动向下顺延。请注意，如果需要写0x开头的字符串，请写两个字符0和x”）。

#### 代码部分：

- 绝大多数命令都有两个参数，少部分仅有一个。
- 格式为 `<命令> <参数1> <参数2>`。
- 命令部分可以[参考这里](https://github.com/Shyliuli/shy_language/blob/main/CommandGuide.md)
- 参数部分可以[参考这里](https://github.com/Shyliuli/shy_language/blob/main/ParameterGuide.md)

##### 一个例子

```
_datastart_
0x0060 shy
_dataend_
_codestart_
outaasc 0x0060 0x00
outaasc 0x0061 0x00
outaasc 0x0062 0x00
_codeend_

```
