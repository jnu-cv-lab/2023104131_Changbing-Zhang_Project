# 传统机器学习方法用于手写数字图像分类

## 项目简介

本项目使用 scikit-learn 内置的 `digits` 手写数字数据集，对比了六种传统机器学习分类器在图像分类任务上的性能。主要目标包括：

- 理解图像特征向量化过程
- 掌握训练/测试集划分
- 训练并评估多种分类器（KNN、朴素贝叶斯、逻辑回归、SVM、决策树、随机森林）
- 通过准确率、混淆矩阵、错误样本分析分类效果

## 环境要求

- Python 3.8+
- NumPy
- Matplotlib
- scikit-learn

安装依赖：

```bash
pip install numpy matplotlib scikit-learn
```

## 文件结构

```
.
├── 2023104131_张嫦炳_ML_CV_Assignment.py   # 主程序代码
├── README.md                  # 本文件
└── 2023104131_张嫦炳_ML_CV_Assignment.word   # 实验报告
```

## 运行方法

1. 将代码保存为 `digits_classification.py`。
2. 在终端中执行：
   ```bash
   python digits_classification.py
   ```
3. 程序将依次显示：
   - 若干张样本图像及其真实标签
   - 控制台输出训练集/测试集大小、各模型准确率表格
   - 最佳模型的混淆矩阵图形
   - 错误分类的样本图像

## 实验结果摘要  

| 模型               | 测试准确率 |
| ------------------ | ---------- |
| KNN (k=5)          | 98.44%     |
| 朴素贝叶斯         | 82.89%     |
| 逻辑回归           | 96.22%     |
| SVM (RBF核)        | **99.11%** |
| 决策树             | 82.44%     |
| 随机森林 (n=100)   | 96.00%     |

- **最佳模型**：SVM
- **最易混淆的数字对**：5→9，8→1，9→7
- **错误主要原因**：图像分辨率低（8x8），某些数字的局部形状相近，原始像素特征难以区分。

## 代码功能说明

- **数据加载**：`sklearn.datasets.load_digits()`
- **数据划分**：`train_test_split(test_size=0.25, stratify=y)`
- **特征向量**：每张 8×8 图像展平为 64 维
- **模型训练与评估**：初始化分类器 → `fit` → `predict` → `accuracy_score`
- **错误分析**：混淆矩阵（`ConfusionMatrixDisplay`）、错误样本可视化、统计常见混淆对
