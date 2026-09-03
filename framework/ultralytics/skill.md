## 数据标注

[数据集概览 - Ultralytics YOLO 文档](https://docs.ultralytics.com/zh/datasets/)

[Datasets — Torchvision 0.24 documentation](https://docs.pytorch.org/vision/stable/datasets.html)

[深度学习数据集有没有规范或指导意见，数据集的建立都需要做哪些研究工作？ - 知乎](https://www.zhihu.com/question/8784947770)

数据标注的平台有很多，但是我需要的，应该是能够导入“已经标了一半甚至全部标完的”数据集并在此基础上修改。

[计算机视觉领域的最好用的图像标注工具数据标注工具随着模型能力不断升级，经久不衰的Labelme推陈出新，也有 T-Rex - 掘金](https://juejin.cn/post/7412702063677472795)

[LabelImg、VoTT、Labelme、CVAT四个图像标注工具的优缺点 - 管道工人刘博 - 博客园](https://www.cnblogs.com/liuyajun2022/p/18371287)

[10个最流行的开源机器视觉标注工具_开源标注工具-CSDN博客](https://blog.csdn.net/shebao3333/article/details/133982003)

| **平台** | **功能表** | **导入教程** |
| --- | --- | --- |
| LabelImg (is now part of the Label Studio community) | [Label Studio Enterprise Pricing | HumanSignal]([Pricing \\| HumanSignal](https://humansignal.com/pricing/)) |
| Labelme | [Products - Labelme](https://labelme.io/products) | Labelme转向收费，仅Pro版可以Import YOLO format |
| CVAT | [CVAT Enterprise Pricing | Data Annotation for Enterprises]([CVAT Enterprise Pricing \\| CVAT](https://www.cvat.ai/pricing/enterprise)) |
| VoTT is no longer being maintained! | [microsoft/VoTT: Visual Object Tagging Tool: An electron app for building end to end Object Detection Models from Images and Videos.](https://github.com/microsoft/VoTT) | 不再维护 |
| MakeSense |     | [将标注好的YOLO标签导入MakeSense中_makesense导入标签-CSDN博客](https://blog.csdn.net/weixin_43491146/article/details/135475082) |
| X-Anylabeling |     | [【YOLO】X-Anylabeling 数据集标注-CSDN博客](https://blog.csdn.net/AbaAbaxxx_/article/details/146176323) |
|     |     |     |

对于计算机视觉，看来可用的只剩CVAT和Label Studio了？还有T-Rex

[CVAT vs LabelStudio: Which One is Better? | by Mariia Krasavina | CVAT.ai | Medium](https://medium.com/cvat-ai/cvat-vs-labelstudio-which-one-is-better-b1a0d333842e)

## 格式规范

[Pytorch - DSDL中文文档](https://opendatalab.github.io/dsdl-docs/tutorials/train_test/pytorch/)

[OpenMMLab 2.0数据集格式规范 | 张星的博客](https://zhangxingai.github.io/2023/10/16/openmmlab_BaseDataset.html)