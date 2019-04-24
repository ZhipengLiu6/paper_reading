# Datasets of remote sensing  
| Dataset | Year | Size | Introduction  | Link |
| ---- | --- | --- | --- | --- | 
| Dstl | 2017 | 20.2G | satellite image segmentation | [kaggle](https://www.kaggle.com/c/dstl-satellite-imagery-feature-detection/data)| 
|MtS-WH| 2009 | 448M | 卫星遥感图像，分辨率为1m，包含4个波段（蓝，绿，红和近红外波段）| [WH-sigma](http://sigma.whu.edu.cn/resource.php)|
| Multispectral-sugar-beet | 2018 | 1.1G | crop and weed segmentation | [google_drive](https://drive.google.com/file/d/1moUzw39CEp3kXBzRfFcHEOEi4D4WRmZM/view?usp=drive_open)|



1. Dstl: the training data set includes 25 images, each with 20 channels (3 band (3 channels, RGB) + A band (8 channels) + M band (8 channels) + P band (1 channel)), and the corresponding labels of objects. There are 10 types of overlapping objects labeled with contours, including 0. Buildings, 1. Misc, 2. Road, 3. Track, 4. Trees, 5. Crops, 6. Waterway, 7. Standing water, 8. Vehicle Large, 9. Vehicle Small
2. Mts-WH: 武汉多时相场景数据集(Multi-temporal Scene Dataset, MtS-WH)数据集主要用于进行场景变化检测的方法理论研究与验证。MtS-WH主要包含两幅7200 x 6000像素大小的高分辨率遥感影像，覆盖范围为中国武汉市汉阳区。影像分别获取于2002年2月和2009年6月，分辨率为1m，包含4个波段（蓝，绿，红和近红外波段）。每个时相训练集包括190张影像，测试集包括1920张影像。
3. Multispectral-sugar-beet: 甜菜、杂草和土地三类，信息如下图所示：![GitHub](https://github.com/ZhipengLiu6/image_cloud/raw/master/paper/multispectural/weednet/label_info.png "GitHub,Social Coding")

# Data acquisition method
## 1. Mts-WH
给遥感图像的每个点格进行类别标记，此处点格的大小可以调整，标注截图如下图所示：
![GitHub](https://github.com/ZhipengLiu6/image_cloud/raw/master/dataset/Mts-WH/data_label_mts_wh.png "GitHub,Social Coding")
详细标注过程参考网址：http://sigma.whu.edu.cn/resource.php

## 2.  Multispectral-sugar-beet
预先设计一块试验田，根据施药的分为三份，量大的都是甜菜，量中等是甜菜和杂草混合，量少的是杂草。如下图所示：
![GitHub](https://github.com/ZhipengLiu6/image_cloud/raw/master/paper/multispectural/weednet/data_info.png "GitHub,Social Coding")  
根据NDVI(归一化植被指数)，可以自动区分植物和土壤。故对于只含有甜菜和杂草的土地可以自动提取标记出甜菜和杂草作为训练数据，测试集合由于混油杂草和甜菜，只能让植物专家手工标注，每张图片耗时60分钟。
