### 工业玻璃面板缺陷检测（语义分割）
数据集为四类玻璃面板缺陷，分别为气泡、划痕、灰尘、背景（背景为无缺陷）。本项目为像素级缺陷检测，也就是语义分割任务，语义分割为逐像素的分类，但是属于背景的像素点的数量往往远多于属于缺陷的数量，所以同样使用主流分类方法是无法正常完成缺陷检测。我使用Unet的思想，改进CycleGAN的生成器，将下采样和上采样的特征图拼合起来，进行进一步操作；同时也用TensorFlow2复现了deeplabV3+模型，作为对比。使用Diceloss作为损失函数，diceloss不受缺陷占比影响，也没有参数需要调整，十分切合本次项目。同时使用数据增强和重采样数据集训练，最终测试集mIoU为61.17%。
