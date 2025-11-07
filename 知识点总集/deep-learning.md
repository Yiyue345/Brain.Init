---
title: 深度学习(部分)
---
# 深度学习 （部分）

> [!WARNING]
> 因为深度学习领域很大，所以肯定没办法全部细节写完，学的时候需要自己看情况学细。
>
> L3 按需求选着看
>
> 顺便提一句，这不是圣经，读者需要自行看着用

## L1 基础级

- 多层感知机 MLP
- 神经网络基础 神经元(感知机) 层 前向传播 反向传播 链式求导
- 神经网络的数学原理 微积分 概率论 线性代数 (基本)
- 神经网络优化器 学习率 SGD momentum Adam 梯度下降
- 过拟合 overfitting 欠拟合 underfitting
- 数据集基本处理 归一化 标准化
- 训练集 验证集 测试集
- 激活函数
  - Sigmoid
  - Tanh
  - ReLU
- 损失函数 MSE 交叉熵损失函数
- 张量 Tensor
- 机器学习的一些概念
  - 监督学习
  - 无监督学习
  - 强化学习
  - 分类回归
  - 生成模型

## L2 入门级

- 正则化 Dropout L1/L2 正则化
- 卷积神经网络 CNN 感受野 下采样
- 神经网络框架的使用 Pytorch 自动微分 广播机制
- 经典 CNN (特别注意其创新点)
  - LeNet
  - AlexNet
  - VGGNet
  - GoogLeNet
  - ResNet
  - DenseNet

- 循环神经网络 RNN 隐状态
  - GRU
  - LSTM

- 训练相关
  - 梯度消失 梯度爆炸
  - Leaky ReLU
  - 数据增强 Data Augmentation (图像增广)
  - 批量归一化 Batch Normalization
  - K折交叉验证 K-Fold Cross Validation

- 非必要的工具
  - Pyplot 图绘制 (非必要，单纯工具)
  - Gradio
  - TensorBoard (没用过，不评价)

- 一些社区生态
  - HuggingFace
  - Kaggle

## L3 进阶级

- 上采样 转置卷积

- 视觉相关
  - EfficientNet
  - 锚框 非极大值抑制 NMS
  - Faster R-CNN 二阶段检测器
  - YOLO 单发多框检测器
  - U-net
  - Vision Transformer (ViT)
  - Swin Transformer

- 序列相关
  - 编码器-解码器架构 seq2seq
  - Attention 注意力
  - 自注意力机制 多头注意力
  - Transformer 位置编码

- 生成网络相关
  - 生成对抗网络 GAN
  - 变分自编码器 VAE 重参数化(数学警告)
  - 扩散模型 Diffusion

- 深度强化学习
  - 传统强化学习 价值函数 Q函数 SARSA Q-Learning PPO on-policy off-policy
  - DQN 经验回放
  - DDQN
  - DPPO

- LLM 开发
  - 全参微调 PEFT BERT LoRA
  - 分词器
  - 提示词工程 (不算深度学习)
    - RAG 知识库检索
    - 记忆机制
    - 链式提示
    - 思维树
    - 懒得写了，直接贴点链接
      - [Langchain 中文](https://docs.langchain.com.cn/docs/introduction/)
      - [Prompt Engineering Guide](https://www.promptingguide.ai/zh)
  - Agent
    - 工具调用

- 多模态

- 框架相关
  - 动态计算图 静态计算图

- 训练相关
  - AdamW 优化器
  - 层归一化
  - 微调
  - Focal Loss (解决图像分类中的类别样本不平衡问题)
  - 梯度裁剪 Gradient Clipping
  - 混合精度训练 Mixed Precision Training
  - 预热训练 Warmup
  - 早停 Early Stopping
  - 学习率 调度器 Scheduler 余弦退火 Cosine Annealing
  - 梯度累积 Gradient Accumulation

- 部署相关
  - 模型量化 Quantization
  - 模型剪枝 Pruning
  - 稀疏化 Sparsity
  - ONNX
  - TensorRT

- 神奇小网站
  - [活在时光机里面的 Papers with Code](https://web.archive.org/web/20250616051252/https://paperswithcode.com/)
  - [据说要接手 Paper with Code 的 HuggingFace Papers Trending](https://huggingface.co/papers/trending)
  - [arXiv](https://arxiv.org/)
  - [On the Biology of a Large Language Model](https://transformer-circuits.pub/2025/attribution-graphs/biology.html)
  - [Epoch AI](https://epoch.ai/)

## L4 前沿级 / 研究级

不懂。

pass