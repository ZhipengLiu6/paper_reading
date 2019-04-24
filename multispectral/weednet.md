# weedNet: Dense Semantic Weed Classification Using Multispectral, 2018
- 作者来自1. Autonomous Systems Lab; 2. Vision for Robotics Lab, Department of Mechanical and Process Engineering, 3. Crop Science, Department of Environmental Systems Science, ETH Zurich, Switzerland.
- 论文来自IEEE Robotics and Automation Letters, 2018
## Question
利用多光谱图像完成甜菜和杂草的分割区分，如下图所示

![GitHub](https://github.com/ZhipengLiu6/image_cloud/raw/master/paper/multispectural/weednet/method.png "GitHub,Social Coding")



## Contribution

1. 提出一个像素级别的植物、杂草分割数据集
2. 以多光谱图片作为输入，利用dense segmentation做植物、杂草的分类

## Method
Segnet作为分割网络，输入为近红外，红，NDVI多光谱图像作为输入，输出是土壤、植物和杂草分割结果。框架如下图所示：
![GitHub](https://github.com/ZhipengLiu6/image_cloud/raw/master/paper/multispectural/weednet/pipline.png "GitHub,Social Coding")

## Experiment result
### Datasets
- 可获取，手工标注和自动标注相结合。介绍如下：  
预先设计一块试验田，根据施药的分为三份，量大的都是甜菜，量中等是甜菜和杂草混合，量少的是杂草。如下图所示：  
![GitHub](https://github.com/ZhipengLiu6/image_cloud/raw/master/paper/multispectural/weednet/data_info.png "GitHub,Social Coding")    
根据NDVI(归一化植被指数)，可以自动区分植物和土壤。故对于只含有甜菜和杂草的土地可以自动提取标记出甜菜和杂草作为训练数据，测试集合由于混油杂草和甜菜，只能让植物专家手工标注，每张图片耗时60分钟。
### Code
- 可获取  
分割可视化结果如下图所示，植物和杂草混合区域分割结果不太理想。  
![GitHub](https://github.com/ZhipengLiu6/image_cloud/raw/master/paper/multispectural/weednet/result.png
 "GitHub,Social Coding")  
在不同地块的分割结果如下，可以看出将很多植物错误的分为杂草了  
![GitHub](https://github.com/ZhipengLiu6/image_cloud/raw/master/paper/multispectural/weednet/result1.png
 "GitHub,Social Coding")    
可能的原因：
1. 训练数据太少，造成泛化能力不足
2. 训练数据中杂草和植物没有相互混合出现在同一图片中，没有学习到植物和杂草的差异，而测试时杂草和植物相互混合的。

## 小结
杂草检测的总体流程：
1. 获取数据：试验田控制变量，得到有杂草和植物的干净数据。（耗时耗力）
2. 训练分割网络
3. 得到杂草和植物的分类结果。

不足之处：
1. 数据的多样性少，造成模型泛化能力不足
## Reference
1. Sa I, Chen Z, Popović M, et al. weednet: Dense semantic weed classification using multispectral images and mav for smart farming[J]. IEEE Robotics and Automation Letters, 2018, 3(1): 588-595.
