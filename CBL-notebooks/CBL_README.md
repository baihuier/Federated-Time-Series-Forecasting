
## CBL-notebooks 目录文件说明

### 数据探索阶段
- **00.EDA.ipynb**: 探索性数据分析（EDA），分析 LCL 电力数据集的基本特征
- **01.EDA_Lags.ipynb**: 时间滞后特征分析，探索时间序列的滞后特征

### 训练阶段（从简单到复杂）

#### 基础训练
- **02.Individual_Training.ipynb**: 独立训练
  - 每个客户仅使用自己的数据训练
  - 不共享数据，无协作

- **03.Centralized_Training_with_CarbonTracker.ipynb**: 集中式训练
  - 使用所有客户数据集中训练
  - 使用 CarbonTracker 测量能耗
  - 作为联邦学习的对比基线

#### 联邦学习基础
- **04.Federated_Training.ipynb**: 基础联邦训练
  - 每个客户使用私有数据
  - 协作训练全局模型
  - 不共享原始数据

- **05.Federated_Training_Inference.ipynb**: 联邦训练 + 推理
  - 在 04 基础上增加推理
  - 使用 flooring 和 capping 处理异常值
  - 使用全局模型进行预测

#### 联邦学习进阶
- **06.Federated_Learning_Custom_Model_Regularization_Aggregation.ipynb**: 自定义模型 + 正则化 + 聚合
  - 自定义模型架构（如 CNN）
  - 训练时应用 L1/L2 正则化
  - 使用不同的联邦聚合算法（如 FedNova）
  - 你刚修改的文件

- **07.Federated_Learning_with_exogenous_data.ipynb**: 带外生数据的联邦学习
  - 使用外生特征（时间特征、统计量等）
  - 增强模型输入信息

- **08.Federated_Learning_with_Testing_and_model_saving.ipynb**: 联邦学习 + 测试 + 模型保存
  - 包含测试集评估
  - 保存训练好的模型权重

### 预测和应用阶段
- **09.Make_Predictions.ipynb**: 使用保存的模型进行预测
  - 加载已保存的模型
  - 在测试集上生成预测结果

- **10.Final_Model_Training_and_Weights_Save.ipynb**: 最终模型训练和权重保存
  - 最终版本的模型训练
  - 保存模型权重供后续使用

- **11.Final_Model_Loading_and_csv_Gen.ipynb**: 最终模型加载和 CSV 生成
  - 加载最终模型
  - 生成预测结果的 CSV 文件

## 总结

这些文件构成了一个完整的实验流程：

1. 数据探索 (00-01) → 了解数据特征
2. 基础训练 (02-03) → 建立基线
3. 联邦学习基础 (04-05) → 实现基本联邦学习
4. 联邦学习进阶 (06-08) → 优化和增强
5. 模型应用 (09-11) → 预测和结果生成


---

跑图表时，用户太多，要跑很久。这里只跑02用户的
cids = ["MAC000002"] if "MAC000002" in client_X_train.keys() else []



---
{file} = 
请你修改这个{file}文件的代码，使其能够适配/CBL-dataset/LCL-June2015v2_0.csv 这个文件。具体的修改方式，已经写在了@CBL-notebooks/02.Individual_Training.ipynb 里面，下面叫他02文件。

你是一名专业的机器学习和深度学习代码专家，专门处理时间序列分析和联邦学习系统。当前任务是修改一个已有的集中式训练notebook，也就是{file} ，使其能够适配特定的电力消费数据集。

核心任务：
将{file}中的数据处理流程修改为与 02.Individual_Training.ipynb 相同的LCL电力数据集处理方式。并且能够成功运行最终的实验。

具体要求：

数据加载适配：
参考02文件中的 函数或类似的数据加载方法
将03文件的数据源修改为CBL-dataset/LCL-June2015v2_0.csv
确保使用相同的格式和解析参数
数据预处理对齐：
时间处理：按照02文件的方式解析时间列（可能是 DateTime 或 tstp 列）
缺失值处理：采用相同的填充/插值策略（如前向填充、线性插值等）
异常值处理：应用相同的阈值过滤或截断方法
数据归一化：使用相同的归一化方法（如 MinMaxScaler 或 StandardScaler）
特征工程一致性：

提取相同的时间特征：小时、星期几、月份、是否为周末等
创建相同的滞后特征（lag features）和滑动窗口统计量
保持相同的特征列命名和顺序

数据集划分：
采用相同的训练/验证/测试集比例
确保时间序列数据的时序连续性不被破坏
保持相同的序列长度和步长参数
验证数据形状和维度在预处理后的一致性
确保目标变量（如 KWH/hh）的处理方式相同

实验运行：
需要能够正确运行实验，能够正确进行训练和输出结果。