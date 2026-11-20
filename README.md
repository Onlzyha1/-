
##基于朴素贝叶斯的乳腺癌分类研究——基于WDBC数据集的探索性分析与三种分类模型比较


## 一、项目简介

  本研究以Wisconsin Diagnostic Breast Cancer（WDBC）公开数据集为对象
  使用Python 完成数据检查、统计描述、相关性分析和可视化
  建立高斯朴素贝叶斯、逻辑回归与随机森林三种二分类模型。
  研究采用80%/20%分层训练测试划分，并在训练集内部进行5折交叉验证。
  结果表明，三种模型在固定测试集上均有较强的判别能力：
  逻辑回归取得最高测试集ROC AUC（0.9960），
  随机森林取得最高恶性类别F1（0.9630），
  而高斯朴素贝叶斯虽然简洁、便于理解，但恶性类别召回率相对较低。
  
## 二、数据来源

  UCI 原始来源：https://archive.ics.uci.edu/dataset/17/breast+cancer+wisconsin+diagnostic
  scikit-learn 文档：https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_breast_cancer.html
  数据：569条记录，30个特征；`malignant=1` 表示恶性，`malignant=0` 表示良性。

## 三、项目结构

```
张峻珲2026104383期末大作业.pdf     完整报告
张峻珲2026104383期末大作业.ipynb   带运行结果的Notebook
data.csv                           数据
/results/model_comparison.csv      模型绩效
/results/hyperparameter_search.csv 网格搜索全部记录
/results/summary.json              结果统计
/figures                           可视化图片
```

## 四、运行环境与复现

运行环境：
Python 3.10+

使用包的版本：
numpy==2.3.5
pandas==2.2.3
matplotlib==3.10.8
scikit-learn==1.8.0
notebook
nbformat
nbclient

复现步骤：
执行Notebook：
```bash
jupyter notebook 张峻珲2026104383期末大作业.ipynb
```
随机种子为42，80%/20%分层划分，训练集中5折分层交叉验证。
ROC AUC 用于选择最优参数；
每个模型仅在最终未参与调参的测试集上评估一次。
标准化放在Pipeline里以避免交叉验证数据泄漏。
