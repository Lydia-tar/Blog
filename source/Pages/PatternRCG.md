# Pattern recognition

k-means

### python 读取 .mat 文件

.mat数据格式是Matlab的数据存储的标准格式。在Matlab中主要使用load()函数导入一个mat文件，使用save()函数保存一个mat文件。

在python中,使用scipy.io, 读取出来的是字典。
``` python
import scipy.io as scio 
dataFile = 'C://data.mat'
data = scio.loadmat(dataFile) 
```

## 无监督学习 （ unsupervised learning)

### 聚类方法

#### 基本概念

##### 样本之间的距离（distance）或相似度（similarity）

样本集合 （假设有n个样本，每个样本有m个属性的特征向量组成，则可以用矩阵X表示）:
$X=[X_{ij}]_{m \times n}= \left[ \begin{matrix} x_{11} & x_{11} & ... & x_{1n} \\ x_{21} & x_{22} & ... & x_{2n} \\ . &. &. &. \\. &. &. &. \\. &. &. &. \\ x_{m1} & x_{m2} & ... & x_{mn}\end{matrix} \right ]
$

1. 闵可夫斯基距离

2. 马哈拉诺比斯距离（Mahalanobis distance）

3. 相关系数 （correlation coefficient）

4. 夹角余弦 (cosine)

##### 类或簇 （cluster）

通过聚类得到的类或簇，本质是样本的子集。如果一个聚类方法规定一个样本只能属于一个类，则是硬聚类方法（hard clustering）。反之，称为软聚类方法（soft clustering）。



聚类算法

层次聚类（hierarchical clustering）

k均值聚类（k-means clustering）