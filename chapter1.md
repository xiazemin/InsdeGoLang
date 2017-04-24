# 环境搭建

1. **准备**

   查看goPath

   $ echo $GOPATH

   /Users/didi/goLang

2. 获取源码

   ```
   git clone https://github.com/golang/go
   ```

3. 查看源码目录结构

   ```
    find . -print \| sed -e 's;\[^/\]\*/;\|\_\_\_\_;g;s;\_\_\_\_\|; \|;g'
   ```

   文件夹

|  | 描述 |
| :--- | :--- |
| [/src/cmd/](https://github.com/golang/go/tree/release-branch.go1.4/src/cmd) | 包含不同的命令行工具。 |
| [/src/cmd/go/](https://github.com/golang/go/tree/release-branch.go1.4/src/cmd/go) | 该目录下包含一个 Go 工具的源代码文件。此工具用于下载编译 Go 的源文件，以及安装 Go 语言的包。在完成上述工作中，它会收集所有源文件并调用 Go 链接器与编译器。 |
| [/src/cmd/dist/](https://github.com/golang/go/tree/release-branch.go1.4/src/cmd/dist) | 此目录下也包含一个工具。此工具用于编译生成所有其它命令行工具。同时，它会由标准库生成所有的包。要想搞明白每个工具或者包到底用到了哪些库，你就需要分析这里的源代码。 |
| [/src/cmd/gc/](https://github.com/golang/go/tree/release-branch.go1.4/src/cmd/gc) | 包含 Go 编译器与系统架构无关的部分。 |
| [/src/cmd/ld/](https://github.com/golang/go/tree/release-branch.go1.4/src/cmd/ld) | 包含 Go 链接器与系统架构无关的部分。与系统架构相关的部分被放在以 l 开头的目录中。这些目录的命名规则与编译器部分的命名规则相同。 |
| [/src/cmd/5a/](https://github.com/golang/go/tree/release-branch.go1.4/src/cmd/5a), 6a, 8a, and 9a | 此目录下存放针对不同架构的 Go 语言汇编编译器。Go 汇编程序的语言并不能一一对应地映射到下层机器的汇编语言。不过，对于每种不同的架构都存在一个将 Go 汇编程序翻译为机器汇编程序的编译器。你可以这[这里](https://golang.org/doc/asm)找到更多内容。 |
| [/src/lib9/](https://github.com/golang/go/tree/release-branch.go1.4/src/lib9),[/src/libbio](https://github.com/golang/go/tree/release-branch.go1.4/src/libbio),[/src/liblink](https://github.com/golang/go/tree/release-branch.go1.4/src/liblink) | 在编译器、链接器、以及运行时中用到的不同库。 |
| [/src/runtime/](https://github.com/golang/go/tree/release-branch.go1.4/src/runtime) | 这部分包含了 Go 语言最重要的包，所有程序都默认导入这些包。其中包括所有的运行时功能，比如内存管理、垃圾回收、Go 协程（goroutine）等等。 |



