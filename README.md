# ICDM 2023 基于预训练模型的社区发现和团伙挖掘

## ComDetector: 节点-子结构判别能力是社区发现预训练任务的关键

### About
本文档关注如何将预训练技术应用于社区发现任务，并详细阐述了一种切实可行的方案***ComDetector***。在本方案中，我们发现让模型学会判别图中的节点与其对应子结构（社区）是解决社区发现预训练任务的关键。具体的，我们在预训练阶段采用互信息最大化的方式让模型学会将开源数据集ogbn-arxiv中的节点与其对应子结构绑定的知识，并通过微调将这个能力泛化到其他数据集上。

### Setup
该脚本在`python 3.9.17`上运行，并需要安装以下第三方库以及他们的依赖：

    dgl==0.6.1

    networkx==3.1

    numpy==1.26.0

    ogb==1.3.6

    pandas==2.1.0

    scikit-learn==1.0.2

    scipy==1.11.2

    torch==1.13.1

    torchaudio==0.13.1

    torchvision==0.14.1
    
### Script
· 在 ogbn-arxiv (in dataset folder) 上预训练，并在 icdm2023_session1_test (将icdm数据放在`./icdm2023_session1_test/`路径下)上测试，结果见result文件夹

(1) 预训练数据预处理

`python ./ogbn_preprocess.py`

(2) 预训练以及测试

`sh ./script/pretrain.sh`

· 在 Cora / Citeseer (in data folder) 上进行本地测试 

`sh ./script/local_ft.sh`
