---
title: c#
---

# C#

## L1 基础级

- 变量声明 赋值 类型转换
- 各种流程语句if for while等等 运算符
- Enum
- List Array Dictionary
- struct class interface
- 面向对象编程（封装继承多态）
- 元组
- 字符串格式化 $内插字符串

- readonly const static
- 装箱拆箱 （实际上不常用，但是也不难理解）
- 属性 getter setter
- 析构函数 Dispose Close IDispose

- 懒得写了

## L2 进阶级


- 设计模式 SOLID原则
- 运算符重载
- 泛型<> 泛型约束 where
- 委托 事件 Func<> Action<> Predicate<>(实际上是Func<T, bool>的语法糖)
- 多线程 Async Await lock语法 Parallel PLINQ Task
- LINQ 延迟执行
- 反射 Attribute
- 注解
- 函数式编程 闭包 lambda表达式 链式调用(柯里化) 匿名方法
- 迭代器 yield return
- 异常处理 Exception try catch finnaly

- 引用参数 in out ref
  - [C#.NET in、out、ref详解](https://www.cnblogs.com/TangQF/articles/18943640)
- 泛型逆变协变 in T / out T (逆变协变听个名得了，in T out T怎么用更重要点)

- 模式匹配 is switch

- 其他基础语法的部分语法糖
  - ? 判空 ?? 空合并 ? 调用 ??= 空赋值
  - => lambda表达式
  - => 表达式主体成员
  - using var
  - 文件作用域命名空间

- .NET 生态 (除了包，其他大概听说了解就行，深度了解能到 L3 级)
  - C# 标准
  - 常见平台 (可以搜 .NET 历史)
    - .NET framework
    - Mono
    - .NET Core / .NET
  - 编译原理
    - IL (Intermediate Language)
    - CLR (Common Language Runtime)
    - JIT (Just In Time)
    - AOT (Ahead Of Time)
    - GC (Garbage Collection)
  - 包
    - NuGet

## L3 原理级

- IL Weaving
- GC 垃圾回收
  - 分代回收（代际假说）
  - 标记清除