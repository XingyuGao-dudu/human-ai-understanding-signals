# Week2 相关文献及实验设计

## IDEA2

### Related work

<img width="5385" height="5006" alt="image" src="https://github.com/user-attachments/assets/3b8b8322-5de9-42dc-9e46-3baa3d493897" />


研究空白：AI已经能够生成丰富的verbal和nonverbal cues，现有研究也证明这些cue会影响empathy、naturalness、engagement和perceived understanding，back-channeling会让用户说得更久、更多，共同任务也能暴露AI的clarification和repair问题

但尚不清楚不同cue应如何表达AI的understanding、uncertainty和need for information，用户如何解释这些cue，以及这些解释是否会促进clarification、correction和repair，还是造成false common ground

### IDEA 2：通过多模态grounding cues外显AI的信息不足，支持用户repair并建立common ground

#### 研究问题

AI对当前共同理解表现出不同形式的grounding evidence，用户自行判断双方是否已经达成一致，以及是否需要继续询问、解释、修改或直接推进任务

RQ1：用户如何理解这些grounding cues？

RQ2：这些grounding condition如何影响用户的行为和common ground？

| Level | Evidence | Description |
| --- | --- | --- |
| 1 | Continued attention | H shows he/she is continuing to attend and therefore remains satisfied with S’s presentation. |
| 2 | Initiation of the relevant next contribution | H starts in on the next relevant contribution. |
| 3 | Acknowledgment | H nods or says ”uh huh” (backchannel). |
| 4 | Demonstration | H demonstrates all or part of what he/she has understood S to mean. |
| 5 | Display | H displays verbatim all or part of S’s presentation. |

#### 自变量-三种方案：

（1）比较同一grounding evidence level的不同模态。 固定语言内容和立场，只改变输出方式，比如动作，表情等，研究多模态是否影响用户理解、协商和common ground

（2）设计好不同的grounding evidence condition。 每个条件是一套完整策略，例如一般性回应、明确表达保留、复述加多模态提示，这些不同水平的evidence会本身就包含不同模态，研究哪种整体策略更有效，但无法区分效果来自语言内容还是表达模态

（3）grounding evidence level × 输出模态。 Factor A比较不同evidence，如acknowledgment与explicit reservation；Factor B：不同模态。既看两者各自作用，也看某类evidence是否更需要多模态表达

> 评论（2）
>
> 自变量-三种方案
>
> 高星宇 8月4日 09:23
>
> 如何控制AI 到这一步没有这些信息
>
> 高星宇 8月4日 09:30
>
> 筛选模态，
>
> 高星宇 8月4日 09:31
>
> 数字人，虚拟人，机器人，需要场景——所以这些cues 是重要的
>
> 高星宇 8月4日 09:34
>
> xxx 模态导致更好的common ground

#### 因变量：

（1）用户理解：用户是否意识到AI并未完全接受当前规则，以及能否正确判断AI的态度；（2）用户行为：用户是否询问证据、继续解释、验证、修改规则或直接提交，以及反应时间和互动轮数；（3）Common ground结果，最终规则是否正确，用户和AI是否接受同一规则，以及双方用该规则判断新物体时是否得到一致结果。一些问卷测量其他维度作为辅助

流程： 用户和AI分别获得部分证据 → 用户提出当前规则 → AI呈现一种grounding cue → 用户自由选择询问、解释、修改或直接提交 → 最多进行一次补充交流 → 用户与AI确认最终规则 → 使用该规则判断新的物体。这样既能观察用户是否主动协商，也能控制每个trial的长度和变量。

#### 实验流程

用户和AI分别获得同一分类规则下的不同示例，需要结合双方掌握的证据，共同推断“哪些物体属于X类”，并对最终分类规则形成共同理解

例子：真正的规则是“红色且有两个圆点的物体属于X类”。用户只看到部分示例，可能提出“有两个圆点的物体都属于X类”；AI看到另一组示例，其中“蓝色且有两个圆点”的物体不属于X类，因此对用户的假设有所保留。AI通过不同的自变量条件回应，用户可以自主行动，比如询问AI掌握的证据、修改规则或直接提交规则。（最后，双方使用共同确定的规则判断一组新物体？）

或共同推理一个微型谜题，各自掌握一部分线索，需要一起推理，或共同制定带隐藏约束的方案

> 实验流程
>
> 高星宇 8月4日 09:32
>
> Jigsaw，协作任务下可以去控制双方接收到的信息，可以去学习并结构化设计

#### 还需要确定的问题

选择哪一种任务，实验里怎么判断形成了common ground，自变量选择哪个方案

## IDEA3

<img width="3285" height="993" alt="image" src="https://github.com/user-attachments/assets/7e78f87c-9461-4cc4-92d9-5de08c681f91" />


目前没有在同一个真实、多轮human–AI任务中，系统比较older与younger adults：

何时发现AI没有理解，怎样解释breakdown原因，采用什么strategies，是否成功、付出多少effort，差异在控制AI experience、digital literacy和cognitive abilities后是否仍存在

### IDEA 3：不同年龄用户如何发现并修复human–AI common ground breakdown

#### 研究问题

RQ1：老年人与年轻人如何发现并解释AI对话中的grounding breakdown？

RQ2：不同年龄用户采用什么repair策略，这些策略是否有效？

RQ3：观察到的差异在多大程度上与年龄有关？

#### 实验设计

建议使用同一个物体指代与布局任务。参与者通过语言指导屏幕中的AI选择或移动相似物体，AI在部分trial中出现预设的理解错误或信息不足。所有年龄组面对相同任务、相同AI输出和相同breakdown时机，确保主要比较的是用户反应，而不是系统条件差异。

#### 自变量与因变量

主要自变量是年龄组：older adults与younger adults

控制条件：是否出现breakdown或breakdown类型作为控制条件

可能的因变量：是否发现breakdown、发现所需时间、repair策略、repair轮数、是否放弃、repair成功率，以及最终任务准确率。AI经验、digital literacy、任务熟悉度、听力或认知能力...

#### 原型与实验流程

开发一个规则控制或Woz的虚拟AI和布局界面。流程为：

用户指导AI → AI正确执行或出现预设breakdown → 用户自由决定是否及修正策略 → AI更新行动 → 必要时重复repair循环 → 完成任务。

实验后通过访谈了解参与者如何判断AI是否理解、为什么选择某种repair方式，以及他们何时决定继续或放弃

#### 数据分析与贡献

定量：比较年龄组在breakdown detection、repair行为和任务结果上的差异；定性上对repair sequence和访谈进行编码。

可能贡献是：说明不同年龄用户如何监测和修复human–AI common ground，区分年龄效应与技术经验等因素，并提出不依赖年龄刻板印象的adaptive repair design

#### 下周需要确定

重点确定三个问题：最终任务具体是？如何设置breakdown？需要测量哪些数据？
