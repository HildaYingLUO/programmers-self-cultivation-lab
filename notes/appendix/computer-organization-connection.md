# Connection with Computer Organization and Design / 与《计算机组成与设计》的联系

##  中文版

### 1. 总体关系

《程序员的自我修养：链接、装载与库》主要解释一个程序如何从源代码变成正在运行的进程，重点包括编译、链接、目标文件、装载、动态链接、运行库和系统调用。

《Computer Organization and Design》主要解释硬件和软件之间的接口，重点包括指令集、汇编语言、算术运算、处理器、流水线、内存层次结构和I/O。

因此，两本书可以放在同一条链条里理解：

```
source code -> complier -> assembly -> machine instructons -> object file -> executable -> loader -> process -> CPU execution

源代码 → 预处理 → 编译 → 汇编 → 目标文件 → 链接 → 可执行文件 → 装载 → 进程 → CPU 执行
```

>  程序从源代码开始，经过编译器处理后生成汇编代码，再被转换为机器指令并形成目标文件。多个目标文件和库经过链接后生成可执行文件。操作系统通过装载器将可执行文件装入内存，创建进程，最终由CPU取指、译码并执行机器指令。

《程序员的自我修养》更关注中间的 object file、linker、loader、runtime library 和 system call。

《Computer Organization and Design》更关注assembly, machine instructions, processor, cache, memory hierarchy 和I/O hardware。

### 2. 关键连接点

| 《程序员的自我修养》    | Computer Organization and Design | 连接方式                           |
| ----------------------- | -------------------------------- | ---------------------------------- |
| 编译生成汇编            | 指令集和汇编语言                 | C 代码最终会变成 CPU 能执行的指令  |
| 目标文件中的 `.text` 段 | 机器指令编码                     | `.text` 保存的是机器指令           |
| 函数调用和栈            | 寄存器、指令、调用过程           | 函数调用依赖指令、寄存器和栈       |
| 进程地址空间            | 内存层次结构                     | 程序地址最终要经过 cache 和 memory |
| 系统调用                | I/O 和中断                       | 应用请求 OS，OS 再和硬件交互       |
| 性能优化                | cache、流水线、局部性            | 程序性能受硬件结构影响             |

### 3. 我的理解

《程序员的自我修养》：程序如何被编译、链接、装载和运行。程序如何变成可执行文件并进入进程？

《Computer Organization and Design》: 这些程序最终如何被CPU和内存系统执行。这些指令进入CPU后，硬件如何执行它们？

这两本书是互补的，前者偏系统软件，后者偏计算机组成和体系结构。

### 4. 学习顺序

在学习过程中，按需补充《Computer Organization and Design》的相关章节。

| 当前学习内容         | 补充 COD 内容                           |
| -------------------- | --------------------------------------- |
| 本书 Ch02 编译和链接 | instructions, assembly language         |
| 本书 Ch03 目标文件   | machine instruction encoding            |
| 本书 Ch06 装载与进程 | memory hierarchy, virtual memory basics |
| 本书 Ch10 栈和堆     | registers, stack pointer, memory access |
| 本书 Ch12 系统调用   | I/O, interrupts, exceptions             |
| 性能优化             | cache, locality, pipelining             |

### 5. 代码实验想法

#### Experiment 1: C to Assembly

```bash
clang -S src/hello.c -o build/hello.s
```

观察 C 代码如何变成汇编代码。

#### Experiment 2: Assembly to Object File

```bash
clang -c src/hello.c -o build/hello.o
file build/hello.o
```

观察汇编/机器指令如何进入目标文件。

#### Experiment 3: Disassemble Object File on macOS

```bash
otool -tvV build/hello.o
```

观察目标文件中的机器指令。

#### Experiment 4: Memory Locality

写两个数组访问实验，对比顺序访问和跳跃访问，理解 cache locality。



---



## English Version

### 1. Overall Relationship

*Programmer's Self-Cultivation: Linking, Loading and Libraries* mainly explains how a program turns from source code into a running process. Its key topics  include compilation, linking, object files, loading, dynamic linking, runtime libraries, and system calls.

*Computer Organization and Design* mainly explains the hardware/software interface. Its key topics include instruction sets, assembly language, computer arithmetic, processors, pipelining, memory hierarchy, and I/O.

Therefore, the two books can be understood throught one continuous chain:

```
source code -> compiler -> assembly -> machine instructions -> object file -> executable -> loader -> process -> CPU execution
```

> A program starts from source code, which is processed by the compiler to generate assembly code. The assembly code is then converted into machine instructions and organized into object files. Multiple object files and libraries are linked together to produce an executable file. The operating system uses the loader to load the executable into memory and create a process. Finally, the CPU fetches, decodes, and executes the machine instructions.

*Programmer's Self-Cultivation* focuses more on oject files, linkers, loaders, runtime libraries, and system calls.

*Computer Organization and Design* focuses more on assembly, machine instructions, processors, caches, memory hierarchy, and I/O hardware.

### 2. Key Connections

| Programmer's Self-Cultivation   | Computer Organization and Design         | Connection                                                   |
| ------------------------------- | ---------------------------------------- | ------------------------------------------------------------ |
| compilation to assembly         | instruction set and assembly language    | C code eventually becomes CPU instructions                   |
| `.text` section in object files | machine instruction encoding             | `.text` stores machine instructions                          |
| function calls and stack        | registers, instructions, calling process | function calls depend on instructions, registers, and stack  |
| process address space           | memory hierarchy                         | program addresses are eventually served by cache and memory  |
| system calls                    | I/O and interrupts                       | applications request OS services, and the OS interacts with hardware |
| performance optimization        | cache, pipelining, locality              | program performance is affected by hardware organization     |

### 3. My Understanding

*Programmer's Self-Cultivation*  for understanding how a program is compiled, linked, loaded and executed.

> How does a program become an executable file and enter a process?

*Computer Organization and Design* for understanding how the CPU and memory system actually execute the instructions produced by the program.

> After instructions reach the CPU, how does the hardware execute them?

Therefore, the two books are complementary. The former is closer to system software, while the latter is closer to computer organization and architecture.

### 4. Reading Strategy

Supplement *Computer Organization and Design* when needed.

| Current Topic                | COD Topic to Supplement                 |
| ---------------------------- | --------------------------------------- |
| Ch02 Compilation and Linking | instructions, assembly language         |
| Ch03 Object Files            | machine instruction encoding            |
| Ch06 Loading and Processes   | memory hierarchy, virtual memory basics |
| Ch10 Stack and Heap          | registers, stack pointer, memory access |
| Ch12 System Calls            | I/O, interrupts, exceptions             |
| performance optimization     | cache, locality, pipelining             |

### 5. Code Experiment Ideas

#### Experiment 1: C to Assembly

```bash
clang -S src/hello.c -o build/hello.s
```

Observe how C code becomes assembly code.

#### Experiment 2: Assembly to Object File

```bash
clang -c src/hello.c -o build/hello.o
file build/hello.o
```

Observe how assembly or machine instructions enter an object file.

#### Experiment 3: Disassemble Oject File on macOS

```bash
otool -tvV build/hello.o
```

Observe machine instructions inside the object file.

#### Experiment 4: Memory Locality

Write two array access experiments and compare sequential access with strided access to understand cache locality.

---



## Key Terms / 关键词

| English                            | 中文           |
| ---------------------------------- | -------------- |
| computer organization              | 计算机组成     |
| computer architecture              | 计算机体系结构 |
| hardware/software interface        | 硬件/软件接口  |
| instruction set architecture / ISA | 指令集架构     |
| instruction                        | 指令           |
| assembly language                  | 汇编语言       |
| machine instruction                | 机器指令       |
| register                           | 寄存器         |
| program counter / PC               | 程序计数器     |
| stack pointer / SP                 | 栈指针         |
| arithmetic logic unit / ALU        | 算术逻辑单元   |
| datapath                           | 数据通路       |
| control unit                       | 控制单元       |
| pipelining                         | 流水线         |
| cache                              | 高速缓存       |
| memory hierarchy                   | 存储层次结构   |
| locality                           | 局部性         |
| I/O                                | 输入/输出      |
| interrupt                          | 中断           |
| exception                          | 异常           |















