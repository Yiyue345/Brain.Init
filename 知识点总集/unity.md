---
title: unity
---

# Unity

## L1 基础级

- 各种常用组件及其属性、方法
- MonoBehavior 脚本周期 Awake Start Update LateUpdate FixedUpdate
- 对象结构 Gameobject Component Transform

## L2 进阶级

- Gizmos
- AssetsBundle
- Cinemachine
- Timeline Animator Playable
- ScriptableObject 「资源」概念
- 程序化动画 (其实是3D动画的底层基础)
  - 骨骼绑定
  - 正向运动学 FK
  - 反向运动学 IK
- 还是编程那套设计模式 原则（能够不自觉的用了说明可能会了）

- 渲染管线概念 (有个概念和了解就行，L2不用深入)
  - 顶点着色器
  - 片段着色器
  - 图元数据
  - 光栅化
- Shader URP
- DrawCall 概念

- 程序化内容生成 Procedural Content Generation （感兴趣看看）

- Mirror 多人游戏框架 (看不看都行吧，并不是必要，只是觉得好用放在这里)
  - ClientRpc Command TargetRpc
  - NetworkManager
  - NetworkBehaviour
  - 其他
- Animancer

## L3 原理级 / 深层级
- IL2CPP 编译加速
- IL Weaving
- DOTS
  - ECS 架构
  - Burst 编译加速 HPC#
  - Job System