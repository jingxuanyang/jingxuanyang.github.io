---
layout: post
title:  "HITSZMealRecognition: 饭盒中菜品的识别与计价"
date:   2020-07-15
categories: convolutional-neural-network
tags: CNN meal-recognition YOLO
author: Jingxuan Yang
---

* content
{:toc}

## 引言

HITSZMealRecognition是一个自动识别菜品并给出价格的MATLAB程序，采用YOLO神经网络实现。来源是人工智能课程的大作业，去年我们的题目是人脸识别，今年改为了菜品识别，感觉很有意思，要来了示例文件，便上手试试。






## 软件准备

工欲善其事必先利其器，软件需要使用MATLAB R2020a或更高版本，还需要额外安装`Deep Learning Toolbox Model for ResNet-50 Network`工具箱。

* 安装方法1：在线安装

打开MATLAB，点击Home->Add-Ons->Get Add-Ons

![安装步骤1](https://imgkr.cn-bj.ufileos.com/5164fb0b-39e1-49db-8660-4fefd9eeb0a2.png)

进入之后，搜索`Deep Learning Toolbox Model for ResNet-50 Network`，下载并安装，我这里已经安装。

![安装步骤2](https://imgkr.cn-bj.ufileos.com/cdca436f-ca91-4362-9d0a-440ef47042d7.png)

* 安装方法2：离线安装

下载`Deep Learning Toolbox Model for ResNet-50 Network`工具箱压缩文件，下面是百度网盘链接。

> 链接：https://pan.baidu.com/s/1Wmzcm3WNUqnugyjrjuU6Wg 

> 提取码：91er

解压之后得到`R2020a`文件夹：

![R2020a文件夹](https://imgkr.cn-bj.ufileos.com/73a97095-32fb-4ccd-9771-222557e98c21.png)

按`Win`+`R`输入`cmd`回车进入命令行：

![进入命令行](https://imgkr.cn-bj.ufileos.com/ac5e3309-9781-4c4f-a5ab-c9ab5c7e5db3.png)

键入以下命令，注意下面的路径需要根据实际情况**替换**。

```bash
# 进入MATLAB安装路径bin文件夹中的win64文件夹
cd C:\MATLAB\R2020a\bin\win64
# 下面路径为解压之后R2020a文件夹所在路径
install_supportsoftware.exe -archives C:\Users\jsmith\Downloads\MathWorks\SupportPackages\R2020a\
```

然后，`install_supportsoftware`软件会自动安装工具箱。

![install_supportsoftware.exe软件位置](https://imgkr.cn-bj.ufileos.com/ab3157ec-b3c8-4191-927e-eebaae8a461b.png)


## 图片标记

图片标记使用`labelImg`软件，百度网盘链接如下。

> 链接：https://pan.baidu.com/s/1a-pojlR93-CSX6-_IKmv-Q 

> 提取码：91er

解压之后，无需安装，直接双击`labelImg.exe`使用。

![labelImg.exe软件](https://imgkr.cn-bj.ufileos.com/9208d2fe-10d1-4149-b2da-6f0559d2fc6a.png)

图片标记主要包含**两个步骤**：

* 步骤1：用矩形把每个菜品框选，并添加标签

![框选并添加标签](https://imgkr.cn-bj.ufileos.com/7c2b18d8-3ee3-434f-af6c-68c8f276952a.png)

* 步骤2：保存xml文件

![保存xml文件](https://imgkr.cn-bj.ufileos.com/5550b8f8-0f67-47e1-bbce-10c543bbeaeb.png)

以此类推，把数据集中的所有图片都进行标记即可。

最后形成的标签共51个，如下表所示。

| 变量 | 描述 |
| :- | :- |
| rice | 米饭 |
| jrtd | 鸡肉土豆 |
| dg | 豆干 |
| ymc | 油麦菜 |
| cjd | 炒鸡蛋 |
| nrm | 牛肉面 |
| sqz | 烧茄子 |
| jt | 鸡腿 |
| cqj | 炒青椒 |
| df | 豆腐 |
| jdxhs | 鸡蛋西红柿 |
| st | 蒜苔 |
| bc | 菠菜 |
| wz | 丸子 |
| j2 | 鸡2 |
| gdf | 干豆腐 |
| yr | 鸭肉 |
| cm | 炒面 |
| j1 | 鸡1 |
| csp | 炒笋片 |
| cch | 炒菜花 |
| r2 | 肉2 |
| r1 | 肉1 |
| cyc | 炒油菜 |
| tdnr | 土豆牛肉 |
| xmz | 小米粥 |
| jdhg | 鸡蛋黄瓜 |
| krbf | 烤肉拌饭 |
| szrp | 水煮肉片 |
| r3 | 肉3 |
| cst | 炒笋条 |
| cct | 炒菜头 |
| czch | 炒紫菜花 |
| r4 | 肉4 |
| jdg | 鸡蛋糕 |
| r5 | 肉5 |
| mlt | 麻辣烫 |
| jdjc | 鸡蛋韭菜 |
| cdfp | 炒豆腐片 |
| csh | 炒蒜毫 |
| r6 | 肉6 |
| j3 | 鸡3 |
| jcdp | 韭菜豆片 |
| bcnf | 白菜闹粉 |
| gbjd | 宫保鸡丁 |
| cmg | 炒蘑菇 |
| lm | 拉面 |
| jp | 鸡排 |
| jt2 | 鸡腿2 |
| yt | 鸭腿 |
| hd | 海带 |
| yd | 鱼段 |

原谅粗犷豪放的命名方式，除了拼音就是12345/笑哭。另，白菜**闹**粉的闹读一声，找不到那个字，或许是方言吧~

## 生成标记数据文件

这一步把图片标记生成的xml文件经过一系列处理生成数据集标记（Ground Truth）文件，主要代码如下：

```matlab
%% saveGroundTruth.m
% Author:  Jingxuan Yang
% E-mail:  yangjingxuan@stu.hit.edu.cn
% Date:    2020.07.13
% Project: HITSZ Meal Recognition
% Purpose: save ground truth file
% Note   :

clc;
clear;

%% load label data
labelDataLoaded = load('HITSZMealLabel');

% set file extention
extendXML = '.xml';
extendJPG = '.jpg';

% initialize filename and label
imageFilenames = {};
labelData = cell(0, size(labelDataLoaded.labelDefs, 1));

%% obtain label data
i = 1;
numImages = 242;
while i <= numImages
    
    % obtain xml file name
    stri = num2str(i, '%d');
    filenameXML = strcat(stri, extendXML);
    
    % show iteration progress
    fprintf('searching for: %s\n', filenameXML);
    
    % obtain jpg file name
    filenameJPG = strcat(stri, extendJPG);
    
    % if filename does not exist, jump out
    if ~exist(filenameXML, 'file')
        continue;
    end
    
    % obtain image path
    imageFile = fullfile(pwd, filenameJPG);
    imageFilenames = [imageFilenames; imageFile]; %# ok
    
    % obtain xml file content
    xmlFile = xmlRead(filenameXML);
    labelLine = cell(0, size(labelDataLoaded.labelDefs, 1));

    for j = 1:length(xmlFile.object)
        
        % obtain label name
        labelName = xmlFile.object(j).name;

        % seems do nothing
        for k = 1:size(labelDataLoaded.labelDefs, 1)
            if labelName == string(labelDataLoaded.labelDefs{k, 1})
                break;
            end
        end
        
        % obtain x and y limits
        xmin = xmlFile.object(j).bndbox.xmin;
        ymin = xmlFile.object(j).bndbox.ymin;
        xmax = xmlFile.object(j).bndbox.xmax;
        ymax = xmlFile.object(j).bndbox.ymax;
        
        % calculate label range: xmin, ymin, width and height
        labelLine(1, k) = {[xmin, ymin, xmax - xmin, ymax - ymin]};

    end % w.r.t. for j

    % add new label line to existing label data
    labelData = [labelData; labelLine]; %# ok
    
    % enter next iteration
    i = i + 1;
    
end % w.r.t. while i

% obtain ground truth data source
dataSource = groundTruthDataSource(imageFilenames);

% obtain label data as table format
labelDataTable = cell2table(labelData);

% set label definitions to label data table
for i = 1:size(labelDataLoaded.labelDefs, 1)
    labelDataTable.Properties.VariableNames(1, i) = table2cell(labelDataLoaded.labelDefs(i, 1));
end

%% save ground truth
% obtain ground truth of dataset
mealGroundTruth = groundTruth(dataSource, labelDataLoaded.labelDefs, labelDataTable);

% save ground truth as mat file
save('HITSZMealGroundTruth.mat', 'mealGroundTruth');
```

以`mealGroundTruth`为变量名保存在`HITSZMealGroundTruth.mat`文件中的图片标记具体内容如下，主要包含图片地址 (DataSource)，标签定义 (LabelDefinitions) 以及每张图片的标记信息 (LabelData)。

![HITSZMealGroundTruth.mat保存的mealGroundTruth变量](https://imgkr.cn-bj.ufileos.com/0cac9d92-67a7-44de-8389-faab28ef4208.png)


## 数据集训练

准备工作已经完成，下面就是见证奇迹的时刻！使用YOLO神经网络进行训练，MATLAB代码如下：

```matlab
%% mealRecognition.m
% Author:  Jingxuan Yang
% E-mail:  yangjingxuan@stu.hit.edu.cn
% Date:    2020.07.14
% Project: HITSZ Meal Recognition
% Purpose: train meal neual network
% Note   :

clc;
clear;

%% load data
% set traning flag
doTraining = true;

% load ground truth data
load('HITSZMealGroundTruth.mat');

% obtain meal dataset
hitMealDataset = mealGroundTruth.LabelData;
hitMealDataset(1:4, :);

% obtain path of image files
hitMealDataset.imageFilename = fullfile(mealGroundTruth.DataSource.Source);

%% set data tables
% set training data table, 70% of total dataset
rng(0);
shuffledIndices = randperm(height(hitMealDataset));
idx = floor(0.7 * length(shuffledIndices));
trainingIdx = 1:idx;
trainingDataTbl = hitMealDataset(shuffledIndices(trainingIdx), :);

% set validation data table
validationIdx = idx + 1:idx + 1 + floor(0.1 * length(shuffledIndices));
validationDataTbl = hitMealDataset(shuffledIndices(validationIdx), :);

% set test data table, 10% of total dataset
testIdx = validationIdx(end) + 1:length(shuffledIndices);
testDataTbl = hitMealDataset(shuffledIndices(testIdx), :);

%% construct data sources
% get training data source
imdsTrain = imageDatastore(trainingDataTbl{:, 'imageFilename'});
bldsTrain = boxLabelDatastore(trainingDataTbl(:, mealGroundTruth.LabelDefinitions.Name));
trainingData = combine(imdsTrain, bldsTrain);

% get validation data source
imdsValidation = imageDatastore(validationDataTbl{:, 'imageFilename'});
bldsValidation = boxLabelDatastore(validationDataTbl(:, mealGroundTruth.LabelDefinitions.Name));
validationData = combine(imdsValidation, bldsValidation);

% get test data source
imdsTest = imageDatastore(testDataTbl{:, 'imageFilename'});
bldsTest = boxLabelDatastore(testDataTbl(:, mealGroundTruth.LabelDefinitions.Name));
testData = combine(imdsTest, bldsTest);

%% train network
% draw figure
data = read(trainingData);
I = data{1};
bbox = data{2};
annotatedImage = insertShape(I, 'Rectangle', bbox);
annotatedImage = imresize(annotatedImage, 2);
figure;
imshow(annotatedImage);

% set training parameters
inputSize = [224 224 3];
numClasses = width(hitMealDataset) - 1;
trainingDataForEstimation = transform(trainingData, @(data)preprocessData(data, inputSize));
numAnchors = 7;
[anchorBoxes, meanIoU] = estimateAnchorBoxes(trainingDataForEstimation, numAnchors);
featureExtractionNetwork = resnet50;
featureLayer = 'activation_40_relu';
lgraph = yolov2Layers(inputSize, numClasses, anchorBoxes, featureExtractionNetwork, featureLayer);

% data augmentation
augmentedTrainingData = transform(trainingData, @augmentData);

% draw augmented images
augmentedData = cell(4, 1);
for k = 1:4
    data = read(augmentedTrainingData);
    augmentedData{k} = insertShape(data{1}, 'Rectangle', data{2});
    reset(augmentedTrainingData);
end
figure
montage(augmentedData, 'BorderSize', 2);
fprintf('augmentedData\n');

% preprocess training and validation data
preprocessedTrainingData = transform(augmentedTrainingData, @(data)preprocessData(data, inputSize));
preprocessedValidationData = transform(validationData, @(data)preprocessData(data, inputSize));

% draw preprocessed training data
data = read(preprocessedTrainingData);
I = data{1};
bbox = data{2};
annotatedImage = insertShape(I, 'Rectangle', bbox);
annotatedImage = imresize(annotatedImage, 2);
figure
imshow(annotatedImage);

% set training options
options = trainingOptions('sgdm',                    ...
                          'MiniBatchSize',    16,    ...
                          'InitialLearnRate', 1e-3,  ...
                          'MaxEpochs',        300,   ...
                          'CheckpointPath',  'temp', ...
                          'ValidationData',   preprocessedValidationData);

% check whether train or not
if doTraining
    % if train from last check point
    % pretrained = load('yolov2_checkpoint__2100__2020_06_26__20_12_13.mat');
    % [detector, info] = trainYOLOv2ObjectDetector(preprocessedTrainingData, pretrained.detector, options);

    % if train from the very initial point
    [detector,info] = trainYOLOv2ObjectDetector(preprocessedTrainingData, lgraph, options);
else
    % if do not train, load pretrained detector
    pretrained = load('yolov2_checkpoint__2786__2020_06_26__18_57_21.mat'); %# ok
    detector = pretrained.detector;
end

%% verify training results
% verify training dataset
% mealTrainingDatasetRecognition;

% verify test dataset
mealTestDatasetRecognition;

%% obtain test results
fprintf('Test result:\n');
preprocessedTestData = transform(testData, @(data)preprocessData(data, inputSize));
detectionResults = detect(detector, preprocessedTestData);
[ap, recall, precision] = evaluateDetectionPrecision(detectionResults, preprocessedTestData);
```

主要步骤包含：

* 载入Ground Truth数据文件
* 设置训练集、验证集与测试集数据
* 进行数据增强以及预处理
* 设置训练选项
* 开始训练

最后几行程序对训练结果进行验证。

## 训练结果

历时约**两个小时**，训练完成。

```matlab
*************************************************************************
Training on single GPU.
Initializing input data normalization.
|======================================================================================================================|
|  Epoch  |  Iteration  |  Time Elapsed  |  Mini-batch  |  Validation  |  Mini-batch  |  Validation  |  Base Learning  |
|         |             |   (hh:mm:ss)   |     RMSE     |     RMSE     |     Loss     |     Loss     |      Rate       |
|======================================================================================================================|
|       1 |           1 |       00:00:12 |         6.04 |         2.89 |      36.4648 |       8.3261 |          0.0010 |
|       5 |          50 |       00:02:08 |         1.70 |         1.68 |       2.9017 |       2.8259 |          0.0010 |
|      10 |         100 |       00:04:14 |         1.30 |         1.56 |       1.7015 |       2.4322 |          0.0010 |
|      15 |         150 |       00:06:19 |         1.19 |         1.60 |       1.4222 |       2.5474 |          0.0010 |
|      20 |         200 |       00:08:24 |         1.11 |         1.63 |       1.2372 |       2.6486 |          0.0010 |
|      25 |         250 |       00:10:28 |         1.09 |         1.63 |       1.1945 |       2.6467 |          0.0010 |
|      30 |         300 |       00:12:32 |         1.07 |         1.63 |       1.1550 |       2.6604 |          0.0010 |
|      35 |         350 |       00:14:37 |         0.95 |         1.65 |       0.9035 |       2.7259 |          0.0010 |
|      40 |         400 |       00:16:41 |         0.96 |         1.67 |       0.9282 |       2.7757 |          0.0010 |
|      45 |         450 |       00:18:46 |         1.02 |         1.61 |       1.0330 |       2.6045 |          0.0010 |
|      50 |         500 |       00:20:48 |         0.91 |         1.56 |       0.8285 |       2.4478 |          0.0010 |
|      55 |         550 |       00:22:45 |         0.91 |         1.66 |       0.8258 |       2.7571 |          0.0010 |
|      60 |         600 |       00:24:41 |         0.90 |         1.74 |       0.8162 |       3.0429 |          0.0010 |
|      65 |         650 |       00:26:38 |         0.98 |         1.66 |       0.9628 |       2.7391 |          0.0010 |
|      70 |         700 |       00:28:35 |         0.92 |         1.70 |       0.8434 |       2.8811 |          0.0010 |
|      75 |         750 |       00:30:32 |         0.89 |         1.64 |       0.7837 |       2.6788 |          0.0010 |
|      80 |         800 |       00:32:29 |         0.85 |         1.73 |       0.7217 |       3.0060 |          0.0010 |
|      85 |         850 |       00:34:26 |         0.80 |         1.71 |       0.6447 |       2.9223 |          0.0010 |
|      90 |         900 |       00:36:23 |         0.79 |         1.81 |       0.6216 |       3.2707 |          0.0010 |
|      95 |         950 |       00:38:19 |         0.79 |         1.66 |       0.6245 |       2.7580 |          0.0010 |
|     100 |        1000 |       00:40:16 |         0.80 |         1.71 |       0.6352 |       2.9196 |          0.0010 |
|     105 |        1050 |       00:42:12 |         0.77 |         1.71 |       0.5860 |       2.9217 |          0.0010 |
|     110 |        1100 |       00:44:09 |         0.75 |         1.77 |       0.5618 |       3.1404 |          0.0010 |
|     115 |        1150 |       00:46:06 |         0.75 |         1.79 |       0.5622 |       3.2177 |          0.0010 |
|     120 |        1200 |       00:48:03 |         0.75 |         1.93 |       0.5571 |       3.7390 |          0.0010 |
|     125 |        1250 |       00:49:59 |         0.72 |         1.71 |       0.5192 |       2.9271 |          0.0010 |
|     130 |        1300 |       00:51:56 |         0.70 |         1.81 |       0.4967 |       3.2754 |          0.0010 |
|     135 |        1350 |       00:53:53 |         0.72 |         1.88 |       0.5133 |       3.5208 |          0.0010 |
|     140 |        1400 |       00:55:49 |         0.71 |         1.84 |       0.5047 |       3.3997 |          0.0010 |
|     145 |        1450 |       00:57:46 |         0.69 |         1.81 |       0.4773 |       3.2823 |          0.0010 |
|     150 |        1500 |       00:59:42 |         0.69 |         1.79 |       0.4759 |       3.1913 |          0.0010 |
|     155 |        1550 |       01:01:39 |         0.66 |         1.78 |       0.4292 |       3.1606 |          0.0010 |
|     160 |        1600 |       01:03:36 |         0.63 |         1.74 |       0.4024 |       3.0253 |          0.0010 |
|     165 |        1650 |       01:05:33 |         0.67 |         1.77 |       0.4504 |       3.1407 |          0.0010 |
|     170 |        1700 |       01:07:29 |         0.66 |         1.87 |       0.4394 |       3.5100 |          0.0010 |
|     175 |        1750 |       01:09:26 |         0.59 |         1.72 |       0.3476 |       2.9637 |          0.0010 |
|     180 |        1800 |       01:11:23 |         0.65 |         1.80 |       0.4166 |       3.2458 |          0.0010 |
|     185 |        1850 |       01:13:19 |         0.54 |         1.91 |       0.2931 |       3.6658 |          0.0010 |
|     190 |        1900 |       01:15:16 |         0.81 |         1.80 |       0.6628 |       3.2433 |          0.0010 |
|     195 |        1950 |       01:17:12 |         0.78 |         1.66 |       0.6019 |       2.7468 |          0.0010 |
|     200 |        2000 |       01:19:09 |         0.66 |         1.70 |       0.4379 |       2.8963 |          0.0010 |
|     205 |        2050 |       01:21:06 |         0.58 |         1.69 |       0.3384 |       2.8453 |          0.0010 |
|     210 |        2100 |       01:23:03 |         0.57 |         1.72 |       0.3237 |       2.9709 |          0.0010 |
|     215 |        2150 |       01:24:59 |         0.54 |         1.81 |       0.2898 |       3.2773 |          0.0010 |
|     220 |        2200 |       01:26:56 |         0.52 |         1.78 |       0.2684 |       3.1785 |          0.0010 |
|     225 |        2250 |       01:28:53 |         0.59 |         1.71 |       0.3457 |       2.9146 |          0.0010 |
|     230 |        2300 |       01:30:50 |         0.50 |         1.86 |       0.2476 |       3.4739 |          0.0010 |
|     235 |        2350 |       01:32:48 |         0.48 |         1.86 |       0.2311 |       3.4490 |          0.0010 |
|     240 |        2400 |       01:34:44 |         0.48 |         1.71 |       0.2317 |       2.9211 |          0.0010 |
|     245 |        2450 |       01:36:41 |         0.50 |         1.87 |       0.2543 |       3.5030 |          0.0010 |
|     250 |        2500 |       01:38:38 |         0.55 |         2.04 |       0.3066 |       4.1628 |          0.0010 |
|     255 |        2550 |       01:40:35 |         0.46 |         1.87 |       0.2144 |       3.4843 |          0.0010 |
|     260 |        2600 |       01:42:32 |         0.59 |         1.88 |       0.3496 |       3.5158 |          0.0010 |
|     265 |        2650 |       01:44:29 |         0.52 |         1.78 |       0.2728 |       3.1686 |          0.0010 |
|     270 |        2700 |       01:46:26 |         0.45 |         1.72 |       0.2048 |       2.9435 |          0.0010 |
|     275 |        2750 |       01:48:23 |         0.40 |         1.79 |       0.1591 |       3.2040 |          0.0010 |
|     280 |        2800 |       01:50:19 |         0.45 |         1.75 |       0.1985 |       3.0679 |          0.0010 |
|     285 |        2850 |       01:52:16 |         0.35 |         1.89 |       0.1256 |       3.5809 |          0.0010 |
|     290 |        2900 |       01:54:13 |         0.34 |         1.76 |       0.1189 |       3.0899 |          0.0010 |
|     295 |        2950 |       01:56:10 |         0.39 |         1.80 |       0.1485 |       3.2481 |          0.0010 |
|     300 |        3000 |       01:58:07 |         0.39 |         1.93 |       0.1506 |       3.7139 |          0.0010 |
|======================================================================================================================|
Detector training complete.
*************************************************************************
```

测试结果差强人意，有部分菜品没有识别出来，还有极少部分菜品识别错误。一部分原因是训练用的数据集较小，另一部原因是部分菜品没有录入到标签里（罕见菜品，标记的时候就直接忽略了）。图片左上角为根据识别结果自动计算的价格（虚拟价格并非学校食堂真实价格）。

![验证测试集](https://imgkr.cn-bj.ufileos.com/85e58f43-56d9-4c56-82f7-081d3c78dc7f.png)

![验证测试集](https://imgkr.cn-bj.ufileos.com/97f4d2ed-bf60-4565-a1c4-64b358c03e50.png)

![验证测试集](https://imgkr.cn-bj.ufileos.com/a758f635-f7c2-4b96-b2d5-6cebaa485a01.png)

![验证测试集](https://imgkr.cn-bj.ufileos.com/416dc940-4404-47ec-9ea8-813f78ba7e11.png)

![验证测试集](https://imgkr.cn-bj.ufileos.com/832e995e-9157-4207-99e2-bd1a4094807c.png)


## 后记

此次菜品识别与上次人脸识别的最大区别在于这次需要在**一张图片上识别多个物体**，而上次人脸识别只是针对单个人的照片进行识别。主要学习到了图片标记的方法，制作数据集制作到凌晨两点，点鼠标点到手疼，深刻体会到了一个好的数据集是多么的珍贵！可惜的是训练结果不太理想，都是数据集太小的锅/傲娇。

全部代码与数据集已上传GitHub，欢迎star，也可下载下来在自己电脑上跑着玩一玩~

> https://github.com/jingxuanyang/HITSZMealRecognition

