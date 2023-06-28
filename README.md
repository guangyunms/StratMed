# Drug-recommendations

在MIMIC-III数据集上的药物推荐，框架改变来自SafeDrug2021

目前最高分0.0.5316  SOTA得分(MoleRec2023):0.5305

使用方法：

1.配置环境lx.yml

2.运行src/SafeDrug.py

相对上一版本的改动：

1.将药物和诊断映射到同一个图谱中训练（将所有药物映射到知识图谱中，将部分诊断映射到知识图谱中，不能映射的部分用普通的嵌入表示）。

![image](https://github.com/lixiang-222/Drug-recommendations/assets/98081667/2a954f5e-3709-4794-a77c-ecd9a3e8b32d)



目前已有提升的操作：

1.把原作者对于分子理论的部分全部去掉，在患者表示之后直接过MLP输出；

2.在患者表示中加入药物历史表示；

3.不要考虑患者历史诊断和程序的信息，只使用当次的结果；


※目前存在的问题:

1.效果不是很高，估计是药物和诊断构图之中存在问题

2.跑到一半会有bug，结果会骤降，且一动不动

3.好像从知识图谱中抽小图谱的哪一步，对编号对错了


※目前的计划：

1.重新查查小编号对标的问题

2.把同构图换成异构图的训练方式

3.把transE的结果当做预训练结果

4.把药物通过nn.Embeding的结果当做预训练的嵌入
