# Week11

## ⛱️ 1

### User mental states｜用户心理状态

https://ceur-ws.org/Vol-4206/SOCIALIZE-01.pdf

user mental states, including beliefs, goals, intentions, emotions, and knowledge

用户心理状态，包括信念、目标、意图、情绪和知识

### Listening-related mental states｜与聆听相关的心理状态

https://www.techfak.uni-bielefeld.de/~hbuschme/publications/BuschmeierKopp-2018-AAMAS-preprint.pdf

listening-related mental states (contact, perception, understanding, acceptance, and agreement).”

### Latent states｜潜在状态

https://proceedings.mlr.press/v306/wu26k.html

These latent states correspond to a set of state dimensions which psychologically lead to how real users respond

### User thoughts / latent cognitive context｜用户想法／潜在认知背景

https://arxiv.org/html/2605.20087v1

Thoughts refer to the users’ latent cognitive context in human–AI conversations

指用户在人–AI 对话中未直接表达的认知背景。

## 2

Let Me Ask You This: How Can a Voice Assistant Elicit Explicit User Feedback?（CSCW 2021）

https://www.ziangxiao.com/pdf/%5Bp%5DXiao_2021_Let_Me_Ask_You_This-How_Can_A_Voice_Assistnat_Elicit_Explicit_User_Feedback.pdf

“Generally, there are two types of user signals: implicit and explicit.”

一般来说，用户信号分为两类：隐式信号和显式信号。 作者举的例子是：停留时长、滚动、跳过等交互日志可以提供隐式线索；用户通过评分或回答调查问题主动表达偏好或意图，则提供显式信号

## 1. 场景

研究者在设计和分析人–AI 多轮任务互动研究时，需要确定如何采集、解释和使用与用户心理状态有关的证据

## 2. 定义

本文关注人–AI 任务互动中，研究者如何建立、验证或使用用户心理状态与证据之间的对应关系

## 3. 困难

人和人对话时，说话者会留意听者的简短回应、表情和动作，据此判断对方是否听懂、是否同意，再决定继续说、换个说法，还是停下来确认。这个过程也给人–AI 对话提出了一个问题：用户和 AI 交流时会发出哪些信号？这些信号能反映什么心理状态？AI 能否据此调整回应？ 已有研究从不同角度探索这些问题，比如用视线判断用户是否同意 AI 的回答，或用文字、语音和表情识别用户的情绪

已有部分研究发现，人的某些信号与某种心理状态的对应关系，但这些发现分散在不同任务和场景中，信号和心理状态都不止一种，两者也不是一一对应的。

同一个信号可能和多种状态有关，同一种状态也可能通过不同信号表现出来

因此，做这类研究时，需要确定：研究想判断什么、信号是在什么任务和时点采集的、作者凭什么把它和该状态联系起来，以及这些依据能不能用到自己的场景

## 4. RQ

在不同的人–AI 对话场景中，哪些用户信号可以作为判断心理状态的依据？这些对应关系是如何采集和验证的，又在什么条件下适用？

如何将这套 mapping 做成工具，帮助研究者在设计新实验时选择信号、确定采集时机，并找到合适的验证依据？

（1）建立mapping

（2）设计工具

## 5 mapping

### 心理状态

| 类别 | 文献中出现的具体词 |
| --- | --- |
| 信念 Beliefs | 对自己理解的判断：主观理解（subjective understanding / subjective comprehension，#01、#02）。<br>对 AI 的认识和预期：心理模型变化（mental model shifts，#20）、用户对语音助手如何接话和办事的预期（user expectations，#30）、相信访谈者由电脑还是真人控制（#17；这是实验中告知的身份）。<br>对 AI 或互动的评价：用户满意度（user satisfaction，#08）、对回复的不满意（user dissatisfaction，#21）、用户意见（user opinions，#23）、对助手或代理的评价与接受度（user perception / user acceptance，#31、#32、#39）、信任及失败后的信任（trust / trust after failure，#14、#15、#42）、感知同理心／感知共情（perceived empathy，#12、#43）、被倾听感（feeling heard，#43）。这些词保留各自的测量，不合成一个「好感」分数。 |
| 目标 Goals | 想在对话里达成什么：对话目标（conversational goals，#35）。<br>想得到什么：情感支持需求（emotional support needs，#16）、信息需求（information needs，#41）。<br>希望得到哪种回答或选择：回答偏好（preference，#27）、当场确认的用户选择偏好（user preferences，#36）。这里保留「需求」「偏好」原名；#35 的目标进度（goal progress）另记，它是对进度的表示或评价。 |
| 意图 Intentions | 这一轮想让系统做什么：用户任务意图（user intent，#34），包括想操作的对象或参数。论文记录的 slot value 是用于核对的具体参数，不是意图本身。<br>当时想了但没说出来的内容：未表达的认知背景（unspoken cognitive context，#24）中的目的、动机及对回复的反应。这里有用户的补记作为依据。 |
| 情绪 Emotions | 本人报告的情绪维度：愉快程度（valence）、激活程度（arousal）、控制感（dominance，#11）；任务后情绪（emotion，#15）；场景情绪与心境（affect / emotion / mood，#44）。<br>披露时的感受：披露顾虑（fear of disclosure，#17）。<br>文献也研究了情绪表达：听得出的烦躁、挫败（annoyance / frustration，#13），可见的悲伤（visible sadness，#17），面部基准的情绪类别（affective states，#12）。这些是外部观察标签，不能和本人感受合并。 |
| 知识 Knowledge | 对内容的掌握：客观内容理解（objective comprehension，#02）；能否应用：情境应用能力（enabledness，#02）。<br>用于核对知识的表现词：回忆、定义题、概念题（recall / definition probe / concept inventory，#01）、学习变化（student learning，#06、#08）。这些是测量结果。<br>与理解困难或把握有关的词：困惑（confusion，#04，本人自报）、有把握／困惑／犹豫（confidence / puzzlement / hesitation，#05，人工标注）、学生不确定性（student uncertainty，#06，幕后人工标注）。这些词放在理解相关文献下查找；它们不等于知识不足，也不等于答错。 |

### 用户信号

| 类别 | 文献中出现的具体词 |
| --- | --- |
| 显式信号 Explicit user signals | A．说出要求或选择：说出正确对象或参数（#34）、提出或修订对话目标（#35）、回答代理的澄清问题并选定选项（#36）、提出具体信息需求（#41）。<br>B．明确给出评价：指认不满意的回复并评分（#21）、明确提交反馈（#22）、点赞／点踩作为正负反馈记录（#40）。<br>C．回答自评或问卷：理解自评（#01、#02）、困惑自评（#04）、辅导满意度（#08）、情绪评分（#11、#15、#44）、信任问卷（#14、#15、#42）、感知同理心或被倾听感评价（#12、#43）。<br>D．主动补记或被问后说明：解释失败后为何继续使用（#14）、说明支持需求（#16）、谈对回复的意见（#23）、补记没说出来的想法（#24）、说明原本预期或采纳理由（#30、#39）、解释实际生活需求（#41）。互动时表达、结束即访、事后回看要保留时间区别。 |
| 隐式信号 Implicit user signals | A．文字和对话行为：简短听者反馈（#03）、措辞变化（#20）、重说、改写、追问、澄清、更正（#21、#25–#30、#37）、双方称呼是否趋同（#38）、实际披露的内容（#10、#18）。<br>B．声音与时序：音高、能量、语速、停顿、话语时长等（#05、#07、#13、#29、#42）；对话持续时间、发言量和反馈量（#09、#10、#22、#32）。<br>C．视线、表情与动作：注视位置及阅读眼动（#01）、面部表情、头部和视线（#04）、视频与面部特征（#11、#12、#33、#42）、可见悲伤与面试动作（#17、#19）、共同看向物体或互看（#45）。<br>D．交互日志：是否继续使用功能（#14）、查看或编辑目标（#35）、采纳或修改建议（#39、#42）。这些行为能直接记录；背后的原因需要额外证据。<br>E．来自用户的被动测量：皮电、脉搏、心搏间隔、加速度、皮温（#44）。这是本表纳入的测量材料，不是 Xiao 原文列举的子类，也未被验证为可以单独识别特定情绪。 |

### 信号和判断对象之间，文献发现了哪几种关系？

| 主类 | 概念 |
| --- | --- |
| 有关系 | 数据支持信号与目标状态之间存在关系。在研究覆盖的范围内，没有发现这种关系明显依赖某个特定条件。 |
| 有条件的关系 | 关系只在某些人群、任务、对话情境或时间窗口里成立，或者关系的强度、方向会随条件改变。 |
| 关系不明确 | 研究检验了信号和状态，但证据不足，或者结果彼此不一致，暂时判断不了有没有关系。 |
| 没有实质关系 | 数据足以排除达到预设重要程度的关系。这比「没发现显著关系」要求更高。 |
| 未验证 | 研究没有检验这条具体的「信号—状态」关系。这是证据缺口，不是分析得出的关系。 |

| 类别 | 文献中可以填入的关系与结果 |
| --- | --- |
| 1．有证据支持信号与状态有关 | #11：在该人机聊天数据中，用户的聊天文本可以预测本人给出的情绪自评分数。这里支持的是「文本与自报情绪有关」，结论的范围是该研究的任务和测量。 |
| 2．有关系，但信号单独使用时信息有限 | #11：同一研究中，仅用视频预测情绪自评的表现有限。可以写「视频单独使用的预测表现有限」，不能因此写「表情与情绪无关」。 |
| 3．关系的适用范围有限，或信号的含义随语境变化 | #08：有些对话特征在原语料中能解释会话满意度，换到另一批语料后解释力下降。#25、#30：重说、改写、追问的含义取决于上一轮回复和当前任务；它们可以是修复，也可以是正常推进对话。因此，这些动作不能固定对应「不满」或「困惑」。 |
| 4．直接检验了信号与状态，但没有得到明确结论 | 这一类只收直接检验了具体信号和具体状态、却没有得到明确支持的结果。原表中的 #04 和 #12 都不能填进来：#04 比较的是诱发条件，#12 比较的是不同 AI 输入条件下的共情评分。「没发现明确关系」也不等于「证实没有关系」。 |
| 5．没有验证这条信号与状态的关系 | #04：面部、头部和视线特征在诱发条件之间有差异，但没有验证这些特征能否判断本人困惑。#05、#13：模型预测的是观察者评定的犹豫、烦躁或挫败，不是本人报告的感受。#33、#42：预测的是助手事件或用户采纳行为，不是困惑或信任。#12、#44：分别研究了改变 AI 输入后的效果和不同材料能否对齐，都没有直接验证对应的信号与心理状态之间的关系。 |
