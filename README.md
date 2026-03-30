# Nemotron3 Super (2026.03.11)

报告：https://developer.nvidia.com/blog/introducing-nemotron-3-super-an-open-hybrid-mamba-transformer-moe-for-agentic-reasoning/
论文：https://research.nvidia.com/labs/nemotron/files/NVIDIA-Nemotron-3-Super-Technical-Report.pdf
权重：https://huggingface.co/nvidia/NVIDIA-Nemotron-3-Super-120B-A12B-FP8

### 完整训练流程

https://github.com/NVIDIA-NeMo/Nemotron/tree/main/src/nemotron/recipes

Raw Data → Data Prep → Tokenized Data (Artifact)
                            ↓
                       Pretraining → Checkpoint (Artifact)
                            ↓
                          SFT → Checkpoint (Artifact)
                            ↓
                          RL → Final Model (Artifact)

### 1. Pre-Training

数据集：
 - 25T tokens https://huggingface.co/collections/nvidia/nemotron-pre-training-datasets
训练软件：
 - Megatron-LM https://github.com/NVIDIA/Megatron-LM
输出模型：
 - https://huggingface.co/nvidia/NVIDIA-Nemotron-3-Super-120B-A12B-Base-BF16

### 2. Supervised Fine-Tuning

数据集：
 - 4000万个样本 https://huggingface.co/collections/nvidia/nemotron-post-training-v3
 - 数据预处理工具：https://github.com/NVIDIA-NeMo/DataDesigner

### 3. Reinforcement Learning

数据集：
 - 21 种环境配置和 37 个数据集
训练软件：
 - https://github.com/NVIDIA-NeMo/RL
 - https://github.com/NVIDIA-NeMo/Gym
