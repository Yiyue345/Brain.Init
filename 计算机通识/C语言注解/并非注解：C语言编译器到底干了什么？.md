# C语言编译器到底干了什么？

[参考视频链接]: https://www.bilibili.com/video/BV1mLpRzgEuR/

[^本文作者]: shiroe

所有的IDE都隐藏了你按下“ run ”后编译器所做的一切，如果你是一名对编译器的MAGIC感兴趣的C语言初学者，这篇文章希望可以初步解答你的疑惑。

C语言编译器的核心工作就是把你写的源代码（`.c` 文件）变成计算机可以直接运行的机器码（可执行文件）。这个过程大致分为 **四大阶段**：**预处理、编译、汇编、链接**。

## 一、预处理

- **输入**：源代码文件 `.c`，就是你自己写的部分

- **输出**：经过处理的源代码（扩展了头文件、宏等）

- **做什么**：

  - 处理 `#include`，把头文件内容直接拷贝进来。
  - 处理宏定义 `#define`，把宏替换为具体的代码。
  - 处理条件编译指令 `#if`、`#ifdef`、`#endif` 等，这个一般不怎么用。

  我们举个例子：

```c
#include <stdio.h>
#define PI 3.14

int main() {
    printf("%f\n", PI);
    return 0;
}
```

经过预处理，编译器会把 `<stdio.h>` 的内容和 `PI` 替换好，然后得到完整的 C 代码。

## 二、编译（Compilation）

- **输入**：预处理后的源代码

- **输出**：汇编代码（`.s` 文件）

- **步骤**：

  ### 1.**词法分析（Lexical Analysis）**：

  把代码分解成“单词”，称为 **token**，比如 `int`、`main`、`(` 等。

  ```c
  int main() {
      int x = 5 + 3;
      return x;
  }
  ```

  - 目标：把源代码拆成 **最小单元 token**
  - token 类型可以是关键字、标识符、运算符、常量等

  **分析结果示例：**

  | Token  | 类型     |
  | ------ | -------- |
  | int    | 关键字   |
  | main   | 标识符   |
  | (      | 左括号   |
  | )      | 右括号   |
  | {      | 左大括号 |
  | int    | 关键字   |
  | x      | 标识符   |
  | =      | 运算符   |
  | 5      | 常量     |
  | +      | 运算符   |
  | 3      | 常量     |
  | ;      | 分号     |
  | return | 关键字   |
  | x      | 标识符   |
  | ;      | 分号     |
  | }      | 右大括号 |

  

  ### 2.**语法分析（Parsing）**

  检查语法是否正确，把 token 组合成 **语法树**（AST）。

  - 目标：根据 C 语言语法，把 token 组合成 **语法树（AST, Abstract Syntax Tree）**
  - AST 反映程序的结构和逻辑

  **语法树大概就长下面这个样：**

  ```yaml
  FunctionDefinition
  ├── ReturnType: int
  ├── FunctionName: main
  └── Body
      ├── Declaration
      │   ├── Type: int
      │   ├── Name: x
      │   └── Init
      │       └── BinaryOp
      │           ├── Left: 5
      │           ├── Operator: +
      │           └── Right: 3
      └── ReturnStatement
          └── Variable: x
  ```

  解释：

  - `FunctionDefinition` 表示函数定义
  - `Declaration` 表示变量声明
  - `BinaryOp` 表示二元运算 `5 + 3`
  - `ReturnStatement` 表示返回语句

  ### 3.**语义分析（Semantic Analysis）**

  检查类型是否匹配，函数是否调用正确等。

  ### 4.**生成中间代码**

  一些编译器会生成与机器无关的中间表示（IR）。编译器可以通过这个阶段做优化，而不依赖具体 CPU 架构。

  ### 5.**优化（Optimization）**

  进行代码优化，比如消除冗余、循环优化等。

  ### 6.**生成汇编代码**

  把 IR 转换为汇编语言（与具体 CPU 架构有关）。

  这里拿x86平台的举个例子

  **6.1 赋值语句**

  ```c
  int x = 10;
  int y = 20;
  x = x + y;
  ```

  对应汇编代码，这里做了一点简化：

  ```asm
  mov DWORD PTR [rbp-4], 10    ; x = 10
  mov DWORD PTR [rbp-8], 20    ; y = 20
  mov eax, DWORD PTR [rbp-4]   ; eax = x
  add eax, DWORD PTR [rbp-8]   ; eax = eax + y
  mov DWORD PTR [rbp-4], eax   ; x = eax
  ```

  解释：

  - `mov`：数据传送（赋值）
  - `add`：加法运算
  - `[rbp-4]` 和 `[rbp-8]` 是栈上变量 x 和 y 的地址

  **6.2条件判断**

  ```C
  int x = 5;
  if (x > 0) {
      x = x - 1;
  }
  ```

  对应汇编（简化版）：

  ```asm
  mov eax, DWORD PTR [rbp-4]   ; eax = x
  cmp eax, 0                    ; 比较 x 和 0
  jle .L1                       ; 如果 x <= 0 跳到 .L1
  sub DWORD PTR [rbp-4], 1      ; x = x - 1
  .L1:
  ```

  解释：

  - `cmp`：比较两个数
  - `jle`：条件跳转（less or equal）
  - 条件成立时执行 `sub`，否则跳过

  **6.3循环**

  ```C
  int i;
  for (i = 0; i < 5; i++) {
      // 循环体，这里简单做 x = x + i;
      x = x + i;
  }
  ```

  对应汇编（简化版）：

  ```asm
  mov DWORD PTR [rbp-12], 0     ; i = 0
  .L2:
  cmp DWORD PTR [rbp-12], 5     ; 比较 i 和 5
  jge .L3                       ; i >= 5 跳出循环
  mov eax, DWORD PTR [rbp-4]    ; eax = x
  add eax, DWORD PTR [rbp-12]   ; eax = eax + i
  mov DWORD PTR [rbp-4], eax    ; x = eax
  add DWORD PTR [rbp-12], 1     ; i++
  jmp .L2                        ; 回到循环开始
  .L3:
  ```

  解释：

  - `.L2` / `.L3`：循环和跳转标签
  - `jmp`：无条件跳转
  - `cmp` + `jge`：循环条件判断

## 三、汇编

- **输入**：汇编代码 `.s`

- **输出**：目标文件 `.o`（机器码，但尚未链接）

- **做什么**：

  - 把汇编代码转成机器码（二进制指令）。
  - 为变量、函数生成符号表，但**还不确定地址**（地址由链接器决定）。

  在 **汇编阶段**，每个变量和函数都会生成一个 **符号（symbol）**，记录在符号表里：

  名称（变量名、函数名）、类型（int、函数等）、大小（4字节、8字节…）、相对位置/段名（比如栈偏移、.data段偏移），此时符号只是**一个标签或占位符**，而不是确切的物理地址。

- **特点**：

  - 每个 `.c` 文件会生成一个对应的 `.o` 文件。
  - `.o` 文件可以独立编译，不需要完整项目。

## 四、 链接（Linking）

- **输入**：多个 `.o` 文件 + 库文件（比如 `stdio`）
- **输出**：可执行文件（就是你电脑最后能运行的文件，windows就是.exe）
- **做什么**：
  - 把不同 `.o` 文件中的符号（函数、全局变量）对应起来。
  - 给函数和变量分配实际地址。
  - 将需要的库函数（比如 `printf`）的代码加入到最终可执行文件。
- **结果**：
  - 生成最终可执行文件，可以直接运行。

## 小结

至此，我们大概梳理了一遍 C 编译器在幕后做的事情：从源代码的预处理、编译、汇编，到链接器生成可执行文件，再到运行时栈和堆上的内存布局。

需要注意的是，这里只是一个 比较粗浅的讲解，省略了许多底层优化、指令集差异和复杂的链接过程。如果你希望深入理解 C 编译器的工作原理和内存管理机制，可以试着阅读下面这些书籍：

1. 《编译原理（龙书）》——Alfred V. Aho
2. 《深入理解计算机系统（CS:APP）》——Randal E. Bryant & David R. O’Hallaron