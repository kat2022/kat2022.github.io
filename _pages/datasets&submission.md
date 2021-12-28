---
layout: page
title: Datasets & Submission
permalink: /datasets&submission/
---

<style>

    .more img{
        width:90%;
        height:auto;
    }
</style>

### Datasets

#### 数据简介
数据集中的问题涵盖常识知识和事实知识两大类型，涉及音乐、影视、军事、历史、化学、物理、生物、法律、医学领域。
注：本赛题要求使用预训练模型进行评测，在模型预训练阶段允许使用外部数据集，但在知识量测评阶段不允许引入外部知识，入围团队后期需提供模型代码、运行脚本、模型说明文件供评测结果复现。

#### 数据说明
数据集包含3个文件，依次为：

| 文件类别 |        文件名        |      文件内容     |
|:--------:|:--------------------:|:-----------------:|
|  训练集  | KCT_train_public.txt | 训练集问题-答案对 |
|  测试集  |  KCT_test_public.txt |     测试集问题    |
| 评测脚本 |      evaluate.py     |   评测指标的计算  |

在训练集中，每行数据即为一个问题，包含5个字段
qid：问题ID
query：待填充的句子，[MASK]标识符代表要填充的位置；
answer: [MASK]处正确答案(不定长的字符串)的列表（可能不止一个正确答案）
domain: 问题类型（Facts代表事实知识，Common Sense代表常识知识）
NeedReasoning: False代表简单问题（单条知识）、True代表复杂问题（多条知识组合）
示例：
<p style='text-align: center'>
<img class='img' src="/assets/img/datasets_example.png">
</p>

##### 注
- 对于数值类问题，答案格式统一为阿拉伯数字；日期类问题，月份用英文表达，年和日用数字表达，评定与年月日顺序无关；常识类问题，答案限制为单个词语。
<p style='text-align: center'>
<img class='img' src="/assets/img/answer_example.png">
</p>
- 测试集提供qid和 query。
qid：问题ID
query：待填充的句子，[MASK]标识符代表要填充的位置;

提交示例
按行输出各问题预测结果，输出文件编码为 “无 BOM-UTF8”、分隔符为英文半角逗号“,”的标准 csv 格式文件，包含id以及ret字段。
id: 问题ID
ret: 包含K个预测答案的列表,本赛题 K取5, 将列表存储为json字符串
样例：
<p style='text-align: center'>
<img class='img' src="/assets/img/output_example.png">
</p>

#### 评测标准
本赛题使用F1指标衡量预测答案与正确答案的重合程度，公式如下：
<p style='text-align: center'>
<img class='img' src="/assets/img/formula.png">
</p>
- NumSame: 预测字符串和正确字符串重复token的个数
- len(prediction): 预测答案token的个数
- len(gold)：正确答案token的个数
- 对topK预测结果与答案列表中字符串依次计算F1，每个问题的分数取F1最大值，最终得分为所有问题得分的平均值, 具体代码可参见评测脚本。

#### 数据评测示例
样例及评分规则如下，假定K取3：
<p class='more' style='text-align: center'>
<img src="/assets/img/predict.png">
</p>
根据F1计算公式：
columbia university与答案完全匹配，F1值为1;
ucla 和答案没有重合token，F1值为0；
Columbia city与答案有1个重复token(columbia)，F1值为0.5
最终该条数据取预测结果中最大F1值，得分为1。



#### 数据下载

| 2021/07/19   12:22:35         赛题数据      测试集 - MD5                                                               （报名后可下载数据） |
|---------------------------------------------------------------------------------------------------------------------------------------------|
| 2021/07/19   12:22:35         赛题数据      测试集 - MD5                                                               （报名后可下载数据） |
| 2021/07/19   12:22:35         提交样例      提交样例 - MD5                                                           （报名后可下载数据）   |
| 2021/07/19   12:22:35         提交样例      baseline - MD5                                                             （报名后可下载数据） |
| 2021/07/19   12:22:35         示例程序      评测脚本 - MD5                                                           （报名后可下载数据）   |


<h3>Submission</h3>

<form th:action="@{/file/upload}" method="post" enctype="multipart/form-data">
    <table>
        <tr>
            <td><input type="file" title=' ' name="file" multiple="multiple" /></td>
        </tr>
        <tr>
            <td><input type="submit" value="Submit"/></td>
        </tr>
         <hr>
     </table>
 </form>