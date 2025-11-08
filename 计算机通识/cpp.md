---
title: C++ 神秘清单
---

# C++ 标准语法神秘清单

显然是现代 C++ 语法而不是 C++ 98 或者更远古的 C++

C++98 大脑的现代化之路。

全列肯定写不完而且也不会，所以写感觉有用的。

会边学边写。

## L1 初窥门径

*最开始时往往是看起来美好的。*

基本语法，主要是 C++ 98 就有的。

- C 语法

- 指针、数组、引用

- class 和 struct
  
  - public
  
  - private
  
  - 构造函数 / 析构函数
  
  - 操作符重载 operator
  
  - 友元函数 friend

- 内联函数 inline

- constexpr consteval

- enum / enum class

## L2 渐入佳境

*为什么不说话了？*

一些更高级的语法。

- 模块化
  
  - 分离编译 翻译单元
    
    - `#include`
    
    - cpp20 的现代模块化 `export` `import` 命名单元
  
  - 命名空间

- cpp11 auto 自动类型推导

- 类
  
  - 具体类
  
  - 抽象类
  
  - 类的层次

- 类的基本函数
  
  - 默认化 删除化
  * 普通构造函数
  
  * 默认构造函数 X()
  
  * 拷贝构造函数 X(const X&)
  
  * 移动构造函数 X(X&&)
  
  * 拷贝赋值函数 operator=(const X&)
  
  * 移动赋值函数 operator=(X&&)
  
  * 析构函数 ~X()

* 用户自定义类型 用户定义字面量

* typedef using 类型别名

- cpp11 统一初始化 初始化列表 窄化类型转换

- cpp11 移动语义
  
  - 移动构造
  
  - std::move
  
  - 函数返回移动
  
  - 左值引用 右值引用
  
  - 省略复制优化

- cpp11 智能指针 shared_ptr weak_ptr unique_ptr

- cpp11 范围 for 循环

- cpp17 初始化 if / switch 语句

- cpp17 variant

- cpp17 结构化绑定

- cpp17 属性 `[[nodiscard]]`

- cpp20 三向比较运算符

## L3 略有小成

*甚至还没能算是会用，勉强是看神仙吵架的基础……也许吧。*

- RAII 资源获取即初始化 生命周期

- PIMPL SFINAE

- 接口和实现分离 声明和实现分离

- 错误处理
  
  - throw 异常，还是错误码？
  
  - 函数的约束条件
  
  - 断言 编译时断言 运行时断言

- 多态
  
  - 运行时多态 编译时多态
  
  - override final
  
  - 虚函数 虚析构函数
  
  - 虚表 继承 多继承

- 模板
  
  - 参数化类型
  
  - 模板参数推导 推导指引
  
  - 参数化操作技巧
    
    - 模板函数
    
    - 函数对象（用对象包装函数）
    
    - 匿名函数表达式 闭包 捕获变量
  
  - 函数使用 auto 作为参数产生的模板函数
    
    - cpp14 匿名函数支持 auto
    
    - cpp20 缩写函数模板 非函数支持 auto
  
  - 编译期判断 `if constexpr`
  
  - 模板特化
  
  - 可变参数模板

- 泛型编程

- 元编程 编译期编程 metaprogramming

- cpp17 折叠表达式 左折叠 右折叠

- cpp11 并发 多线程 thread 互斥量 RAII锁

- cpp20 协程 co_await co_yield co_return

- cpp20 Ranges 库 Views Adapters

- cpp20 概念 concept
  
  - requires 表达式 requirements 字句
  
  - 有效代码

## L4 我也不会

多学多写。


