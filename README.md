# Shy语言

Shy语言是一个开源的汇编语言项目，专为教学目的设计。它通过提供一个简化版的汇编语言，旨在帮助初学者轻松地掌握汇编语言的基本概念。项目包括一个编译器（shycc）和一个运行模拟器（shyemu），以支持用户编写和测试Shy语言程序。

## 关于Shy语言

Shy语言努力降低汇编语言学习的门槛，通过简化的语法和直观的操作，使得初学者能够无压力地掌握关键概念。该项目适合教育工作者、学生，以及任何对汇编语言感兴趣的个人。

## 安装过程

要安装Shy语言的编译器和运行模拟器，请遵循以下步骤：

1. **下载源代码**：从GitHub仓库下载 [shycc](https://github.com/Shyliuli/shycc)和 [shyemu](https://github.com/Shyliuli/shyemu)的源代码。
2. **编译工具**：使用您选择的C++编译器编译 `main.cpp`。例如，使用g++编译器时的命令如下：

```
g++ main.cpp -o shycc
g++ main.cpp -o shyemu
```

> 目前，我正在学习如何有效使用Makefile，不能保证其当前的可用性。

## 编译Shy语言程序

使用 `shycc`编译您的Shy语言程序：

```
shycc /path/to/your/file/test.shy
```

这将生成一个 `.sfs`文件（硬盘镜像，可以被视为可执行程序）。

## 运行Shy语言程序

显然Shy硬件目前不存在（创建文件夹ing）。因此，我们使用 `shyemu`来模拟Shy程序的运行环境：

```
shyemu /path/to/your/file/test.sfs
```

这允许您启动并运行用Shy语言编写的程序，便于测试和调试。

## 许可证

Shy语言是在GPLv3许可证下发布的。这意味着任何人都可以自由地使用、修改和分发该软件，但任何基于Shy语言的衍生作品也必须在相同的许可证下发布。
