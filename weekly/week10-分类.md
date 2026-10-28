# Week 10：文献分类

## 一、现在文章在研究什么问题？

- A：用户怎样反馈，代理怎样接收和回应？用户反馈如何影响代理？
- B：能否从用户信号判断用户的某种状态或情况？
- C：用户理解AI内容的过程，怎样被记录和判断？

我们的scope可能是(人–AI互动中的用户状态与反馈)

### 这些文章遇到的问题是

同一个行为，意思可能不同。

用户不一定把状态表现出来。

缺少可以核对的证据

证据需要不上具体内容和时刻。

取证可能会改变互动

不同证据可能互相矛盾

### 为了回答这些问题，收集了什么数据？

用户怎么表现：录音、视频、视线、表情、头部动作、点击和操作

用户怎么说：对话原文、即时自评、结束后的回看说明

用户实际会什么：解释题、判断题、应用题和操作结果

AI做了什么：讲了什么、何时追问、何时补充、显示了什么

当时是什么情况：任务内容、实验条件、当前知识点和事件时间

### 其中哪些需求反复出现？

设置AI：用什么模型、收到什么输入、怎样回应

记录双方：用户说了什么、AI说了什么，发生在什么时候

中途收报告：在指定内容或事件后，问用户当时怎么想

取得表现证据：让用户答题、解释或操作，保存答案及理由

对齐材料：把某次点头、某句话、自评和答题结果放回同一段互动

回看和标注：找到片段，补充解释，记录研究者的判断

区分证据：用户说“懂了”、研究者认为他懂了、实际答对

### 这些需求可以怎样归类？

#### A．实验怎么搭

设置任务、AI、输入输出、实验条件和测量时机。

#### B．数据怎么收

连续记录对话和行为；在需要的时候收自评、答案、操作及回看报告。

#### C．材料怎么对应和分析

按时间、具体内容和事件找到相关材料；分别标注，再比较行为、自评和实际表现

## A 用户怎样反馈，代理怎样接收和回应？

### 1 Communicative Listener Feedback in Human–Agent Interaction: Artificial Speakers Need to Be Attentive and Adaptive

AAMAS 2018

https://www.ifaamas.org/Proceedings/aamas2018/pdfs/p1213.pdf
<img width="1434" height="396" alt="image" src="https://github.com/user-attachments/assets/8e5d7266-07a5-4171-b06d-02f7c08cb8c0" />

<img width="1462" height="562" alt="image" src="https://github.com/user-attachments/assets/3b71ec8c-f175-4f19-a06f-e0f416cf1054" />
<img width="1280" height="380" alt="image" src="https://github.com/user-attachments/assets/3975ce82-3d0d-4c9a-8469-d85272d67846" />


#### 1．背景

已有研究多研究代理怎样给人反馈。本文研究：代理关注并回应人的反馈后，人会不会继续反馈，能不能感觉到代理在配合自己。

#### 2．RQ

1：Are human interlocutors willing to provide natural communicative listener feedback to artificial conversational agents?

2：Do human interlocutors notice that they are interacting with an agent that makes a collaborative effort in the joint project of making itself understood?

#### 假设

1 We expected that participants provide more feedback in the target condition AS than in the two control condition EA and NA

预期AS组比EA、NA组提供更多反馈

2 In general we expected that participants in the target condition AS would provide higher ratings than participants in both control conditions EA and NA.

AS组对代理的评价高于EA、NA组。

3 We also expected that participants who interacted with the agent that explicitly asked whether it should repeat or continue (EA) would be rated higher than the agent that did not adapt at all (NA) — at least for some of the questionnaire items.

预期至少部分问卷项目中，EA组评价高于NA组

#### 3．实验设置

系统：使用同类代理配置三种行为策略，接入一个具身虚拟代理，日程助手

| 条件 | |
| --- | --- |
| AS：关注反馈 | 根据用户反馈判断继续或重复，不确定时询问用户 |
| EA：明确询问 | 不处理自然反馈，每个信息单元后都问继续还是重复 |
| NA：不调整 | 不处理反馈，说完当前单元就继续 |

36人分三组，听虚拟人介绍日程：一组由幕后研究者实时输入用户反馈、模型决定继续或重复，一组每讲完一条都问用户是否重复，一组直接继续，最后比较用户反馈和问卷评价

任务：不能自由聊天，但可以点头、发出“嗯”等反馈。共六个对话阶段，每阶段2—3个信息单元，安排纸质日历回忆填写，互动后填写问卷。

#### 4．数据采集

| 收啥数据 | 怎么收 | 何时收 | 用途 |
| --- | --- | --- | --- |
| 用户声音 | 摄像头录像中的音轨 | 全程 | 标注发声反馈，回答RQ1 |
| 用户头部动作 | 摄像头录像中的视频轨 | 全程 | 标注头动反馈，回答RQ1 |
| 代理行为记录 | 分析中记录呈现次数、引出反馈提示及用户回应 | 互动中 | 计算反馈率、提示效果 |
| 主观评价 | 20项七点问卷，本文分析其中6项 | 互动后 | 回答RQ2 |
| 日程回忆 | 用户填写纸质日历 | 回忆阶段 | 安排了采集，本文未分析其有效性结果 |

36次互动中，33次音视频可用

#### 5．数据—分析—结果Mapping

| 对应问题 | 数据怎样对应 | 具体分析 | 结果 |
| --- | --- | --- | --- |
| RQ1：有没有反馈、有哪些形式 | 声音与头动分别标注，时间重叠的归为双模态反馈 | Praat转写发声，ELAN标注头动。排除回答代理明确问题时的反馈。统计类型和比例 | 共734个反馈：仅发声17.3%，仅头动40.3%，双模态42.4% |
| 假设：AS是否反馈更多 | 每人的反馈数对应其信息呈现次数，包括重复呈现 | 反馈率＝反馈数÷呈现次数，贝叶斯方差分析及组间比较 | AS反馈率高于EA、NA |
| AS反馈多是否仅因代理经常提示 | 将代理提示与其后4秒内的反馈对应 | 统计有效提示比例，另算没有提示的主动反馈 | 61%的提示引出反馈，46%的用户反馈为主动反馈，差异不能只用提示次数解释 |
| RQ2及评价假设 | 每人六项问卷评分对应实验条件 | 逐题比较中位数，用贝叶斯因子比较条件排序，不合并总分 | AS在“希望被理解”“帮助解决理解困难”等项目上优于对照，部分项目AS与EA没有明确差异 |

#### 6．具体工作流与对应需求

| 步骤 | 作者具体做了什么 | 做这类研究，需要工具能做什么 |
| --- | --- | --- |
| 1．做出代理 | 把三个已有模型接到日程虚拟人上：解释用户反馈、调整说法、主动索取反馈 | 能接入一个虚拟人，让它说话，并根据反馈决定下一步 |
| 2．设置三个版本 | 给代理配置AS、EA、NA三种策略 | 同一个代理能切换三种说话规则：看反馈再决定、每次都问、直接继续 |
| 3．准备讲解内容 | 将日程和变更拆成信息单元，每阶段2—3个 | 能录入讲解内容、划分单元；重复时知道正在重复哪一条 |
| 4．分配参与者 | 每组12人，每人只接触一种策略 | 给参与者安排一个版本，并保存其条件编号 |
| 5．人工观察反馈 | 研究者看用户，实时向系统输入反馈属性 | 实验员能及时输入“点头”“负向反馈”等，注明这是人工输入 |
| 6．让代理回应 | AS根据模型判断继续、重复或询问 | 人工输入后，代理能执行对应行为；留下判断和实际回应记录 |
| 7．录下用户 | 同时取得声音和头部视频 | 保存同一段互动的声音和视频，能一起回放 |
| 8．分别标注 | Praat标声音，ELAN标头动；排除明确问答中的反馈 | 能标出反馈起止和类型，并注明“自然反馈”还是“回答问题” |
| 9．找组合反馈 | 发声与头动在时间上重叠，记为双模态反馈 | 能找到“嗯＋点头”这种同时发生的组合，并查看原片段 |
| 10．对应代理提示 | 检查提示后4秒内是否有用户反馈 | 能以代理提示为起点，查找指定时间内的反应 |
| 11．计算反馈率 | 反馈数除以实际呈现次数，包含重复 | 能分别数清反馈、首次讲解和重复讲解 |
| 12．收集问卷 | 互动后收20项评分，选6项分析 | 问卷答案能关联到参与者及其代理版本 |
| 13．比较条件 | 比较三组反馈率与各题评分 | 能导出按参与者整理的数据，供R等软件分析 |

### 2 Multi-Modal Repairs of Conversational Breakdowns in Task-Oriented Dialogs

UIST 2020

https://toby.li/files/Li_Sovite_Error_Handling_UIST2020.pdf

语音助手理解错任务后，用户不知道错在哪里，反复换说法也可能无效

作者开发SOVITE：用应用截图展示系统理解的任务，让用户直接指出、修改错误
<img width="1470" height="536" alt="image" src="https://github.com/user-attachments/assets/d50358a9-eeb8-4f20-9d1d-2c013d5b8ed0" />


<img width="1280" height="776" alt="image" src="https://github.com/user-attachments/assets/a846150a-554d-4b33-80ad-22f66185e478" />

#### 2．RQ

RQ1

Can users understand and use SOVITE’s new features for identifying and repairing conversational breakdowns?

RQ2

Is SOVITE effective for fixing conversational breakdowns caused by natural language understanding errors in task-oriented agents?

#### 3．实验设置

用Java开发Android应用SOVITE，接在SUGILITE任务代理上，运行于Pixel 2 XL手机

系统把理解结果显示为应用截图＋高亮参数，例如，叫Uber时，高亮起点和终点，用户可以说出正确应用、展示正确界面、拖动高亮或修改文字

使用语义解析器处理命令、Sentence-BERT查找相关任务

10人分别检查7种预设情境，顺序随机

| 情境 | 原本要做什么 | 系统理解成什么 |
| --- | --- | --- |
| 1 | 致电Amazon | 正确，无需修复 |
| 2 | 用DoorDash点外卖 | 没理解命令 |
| 3 | 订今晚的酒店 | 打开OpenTable订餐厅 |
| 4 | 用Expedia订机票 | 进入酒店预订界面 |
| 5 | 点Iced Espresso | 选成Espresso |
| 6 | 查The Lego Movie场次 | 只提取The Lego |
| 7 | 从家叫Uber去机场 | 起终点反了 |

1. 同意参与，填写人口信息。
2. 看SOVITE功能教程。
3. 阅读某个预设请求及系统回应。
4. 判断系统理解是否符合请求；不符合则尝试修复。
5. 完成全部7种情境。
6. 填写问卷，接受简短访谈。

#### 4．收集什么数据

| 数据 | 具体记录什么 | 怎么收、何时收 |
| --- | --- | --- |
| 用户是否发现理解错误 | 是否指出Uber起终点反了等 | 每种情境观察用户判断 |
| 修复方式及结果 | 是否拖动高亮；最后是否改对 | 修复过程中观察 |
| 操作困难 | 是否误点截图中不可操作的按钮 | 使用过程中观察 |
| 主观评价 | 易用性、有用性、满意度、功能评价 | 全部情境后，七点问卷 |
| 用户解释 | 为什么没发现错误、哪里困惑 | 结束访谈 |

#### 5．数据怎样分析，得到什么

| 对应问题 | 数据怎样对应 | 怎么分析 | 结果 |
| --- | --- | --- | --- |
| RQ1、RQ2：能否发现错误 | 预设正确任务＋系统回应＋用户判断，按参与者和情境对应 | 统计正确发现次数 | 60次错误中发现57次，95%；10次无错误全部判断正确 |
| RQ2：能否修复 | 每次已发现错误＋修复操作＋最后结果 | 统计修复成功次数 | 发现的57次错误全部修好 |
| RQ1：功能是否好用 | 每人对应问卷题评分 | 计算均值、SD | 易用性6.4、有用性6.1、满意度6.3，满分7 |
| 为什么漏检 | 3次漏检＋事后解释 | 描述案例；未报告正式编码方法 | 用户预期系统不会犯这类错误，没有仔细检查 |
| 哪里不直观 | 操作中的困惑＋后续表现 | 描述观察案例 | 部分用户最初以为截图上的所有按钮都能操作 |

**只能说明这7种情境下用户能够发现并修复多数错误；没有比较其他修复工具，也没有证明效率更高。**

#### 6．具体工作流与对应需求

| 步骤 | 作者具体做了什么 | 工具需要能做什么 |
| --- | --- | --- |
| 接入系统 | 在手机上运行SOVITE和任务应用 | 接入真实任务代理，显示实际回应 |
| 准备情境 | 准备7组请求与回应，标明哪里故意理解错 | 分开保存用户请求、系统结果和预设错误 |
| 展示理解 | 截图显示所选应用，高亮起点、终点等参数 | 让参与者看见系统具体理解成什么 |
| 安排任务 | 每人经历全部情境，顺序随机 | 随机排任务，保存每人的顺序 |
| 远程操作 | 用户指挥，研究者代点击、复述 | 区分用户要求和研究者实际执行的动作 |
| 接收修复 | 支持说应用名、展示界面、拖动高亮、改文字 | 同一任务能接收不同方式的纠正 |
| 检查结果 | 分别检查有没有发现、有没有修好 | 两项分别记录，不能只写“任务成功” |
| 收集解释 | 问卷评价整体，访谈解释具体失败 | 整体评价关联参与者，失败解释关联具体情境 |

## B 能否从用户信号判断某种情况？

### Do You (Dis)agree With Me? Modelling Implicit User Disagreement in Human–AI Interaction Using Gaze Data

利用视线数据建模人–AI互动中的用户隐性不同意

CHI 2026

https://www.dfki.de/web/forschung/projekte-publikationen/publikation/1700


<img width="1280" height="457" alt="image" src="https://github.com/user-attachments/assets/05e11d67-d1ed-48b1-aad4-153a269dc767" />
<img width="788" height="668" alt="image" src="https://github.com/user-attachments/assets/5181b6de-b228-407d-8c6f-382b582001e5" />


系统怎样在不要求用户明确输入的情况下，感知用户不同意？

#### 1．背景

用户不同意AI结果时，未必主动反馈,频繁询问又会打断互动。

作者采集眼动和表情，检验它们能否预测用户的同意／不同意判断，并公开数据集

#### 2．RQ／假设

RQ1

Can perceived disagreement with image–caption outputs be reliably detected from passive gaze and facial signals collected during a simulated human–AI interaction task?

能否利用被动采集的眼动和面部信号，识别用户是否不同意图片描述？

RQ2

How do personalised and generalised disagreement-detection models compare in terms of accuracy, reliability, and robustness to inter-participant variability?

个体化与通用模型，在准确性、可靠性及应对个体差异方面表现如何？

RQ3-A

Which gaze-based features are most predictive of perceived disagreement, and how consistent are these predictive features across participants?

哪些眼动特征最能预测不同意？不同人是否一致？

RQ3-B

Which time window prior to a participant’s decision best discriminates perceived disagreement using passive gaze signals, and how does the duration of this window impact classification performance?

判断前哪个时间窗口最有预测价值？窗口长度怎样影响分类？

#### 3．实验设置

系统：模拟图片描述AI.使用预先准备的图片和描述

实验一句话：30人逐项查看154组图片与描述，选择同意／不同意，同时记录眼动和面部视频。

- FOIL-COCO图片描述：77条正确、77条替换一个词
- A、B组看相同图片，但正确／错误描述分配相反
- 每人呈现顺序随机
- 一次数据采集，之后开展多轮离线模型分析

#### 流程

同意参与及人口问卷 → 九点眼动校准 → 练习 → 倒计时 → 图片描述 → 用户提交判断 → 下一项 → 结束说明。

用户负责判断,设备自动记录,模型在采集后训练测试

#### 4．收集什么数据

| 数据 | 具体记录什么 | 怎么收、何时收 |
| --- | --- | --- |
| 眼动与瞳孔 | 看哪里、何时看、瞳孔大小 | Tobii Pro Fusion，250 Hz，全程 |
| 面部视频 | 用户看描述时的面部变化 | OAK-D摄像头，30 Hz，全程 |
| 用户判断 | 每项选择同意还是不同意 | 每次查看后提交 |
| 刺激与时间 | 对应哪张图、哪条描述、出现与提交时间 | 按试次保存；设备同步到电脑时钟 |
| 材料正确答案 | 描述原本正确还是错误 | 来自预设材料，独立于用户判断 |

预处理后得到4,092个有效试次,训练标签用用户选择

#### 5．数据—分析—结果Mapping

| 对应问题 | 数据怎样对应 | 怎么分析 | 结果 |
| --- | --- | --- | --- |
| RQ1：信号能否预测判断 | 每次图片出现至提交之间的眼动、面部数据，对应该次选择 | 提取眼动数值及面部AU统计特征，测试分类模型及模态融合 | 加入面部没有改善表现 |
| RQ2：能否用于新用户 | 按参与者划分数据 | 部分人训练、其他人测试，五折交叉验证 | 通用模型最佳约57%平衡准确率 |
| RQ2：针对个人是否更好 | 每人的试次单独整理 | 同一个人的部分试次训练、其余测试，分层五折交叉验证 | 结合个人特征、窗口选择，平均68.4% |
| RQ3-A：哪些特征有用 | 同意／不同意标签对应各眼动特征 | 分布检验后用t检验或Wilcoxon，BH多重比较校正 | 有差异的特征因人而异 |
| RQ3-B：哪段时间有用 | 每次判断对应完整记录、最后3秒或11秒 | 比较不同窗口下分类表现 | 最佳窗口因人而异，无统一最优窗口 |

#### 6．具体工作流与对应需求

| 步骤 | 作者具体做了什么 | 工具需要能做什么 |
| --- | --- | --- |
| 准备材料 | 为同一图片准备正确和错误描述 | 保存图片、描述及材料答案 |
| 平衡与随机 | 两组分配不同描述，每人顺序随机 | 控制材料分配，保存实际呈现顺序 |
| 校准与同步 | 眼动校准；摄像头、眼动仪同步电脑时间 | 检查校准，让不同设备时间对应 |
| 呈现并收判断 | 显示图片描述，等待用户选择 | 保存刺激出现时间、选择及提交时间 |
| 切分行为 | 截取图片出现至提交之间的数据 | 按试次找回对应眼动和视频 |
| 提取特征 | 识别注视、扫视、兴趣区；提取面部AU | 保留原始数据，关联处理后的特征 |
| 分开两类答案 | 材料正确性与用户判断分别保存 | 不把“描述错误”直接等同“用户不同意” |
| 重选窗口 | 比较完整记录、最后3秒、最后11秒 | 能以提交时刻倒推截取不同长度 |
| 训练测试 | 分别按新用户和同一用户划分 | 保留参与者编号，明确训练／测试归属 |

核心工作流：呈现材料 → 记录行为 → 用户判断 → 按试次对应 → 建立数据集 → 测试识别模型。

## C．用户理解AI内容的过程，怎样被记录和判断？

### From Gaze to Guidance: Interpreting and Adapting to Users’ Cognitive Needs with Multimodal Gaze-Aware AI Assistants

从视线到指导：利用多模态视线感知AI助手，解释并适应用户认知需求

UIST 2026

https://arxiv.org/html/2604.08062v1
<img width="1280" height="509" alt="image" src="https://github.com/user-attachments/assets/12d54c76-c74a-4b9b-ba74-6c70401f3870" />
<img width="1280" height="638" alt="image" src="https://github.com/user-attachments/assets/27ef53e1-6320-4516-bcf2-dbd0fc0c4fc6" />
<img width="1280" height="482" alt="image" src="https://github.com/user-attachments/assets/4bc287fa-791a-44f1-ae1a-f3a195e16ecb" />


#### 1．背景

用户读不懂时，未必能说清卡在哪里。作者让LLM结合阅读视线推测困难，阅读结束后再提供语音帮助

offer more relevant, personalized, and cognitive-oriented support

加入视线后，助手是否更贴合用户、是否改善理解表现

#### 3．实验设置

Aria眼镜采集第一人称画面和视线,GPT-4.1读取带视线标记的图像，形成带时间的观察，再推测困难位置。

参与者：41人招募，36人进入分析。组内设计，每人都用：

视线条件：助手获得文章＋基于视线的困难分析

文字条件：助手获得文章＋仅根据文章推测的困难分析

流程：阅读 → 理解自评 → 与助手语音交流 → 再次自评及测验 → 评价助手的分析

两个主要任务分别读“通货膨胀”“板块构造”，条件顺序平衡；另设并排比较两类分析，最后访谈

#### 4．收集什么数据

| 数据 | 怎么收、何时收 |
| --- | --- |
| 视线＋第一人称画面 | 阅读时由眼镜采集 |
| AI观察和困难分析 | 保存所看内容、时间及推断 |
| 对话记录 | 阅读后语音交流 |
| 主观理解 | 交流前后评分 |
| 客观表现 | 交流后：事实回忆、术语定义、概念应用 |
| 分析评价、体验及访谈 | 评价准确性、个性化、负担和使用体验 |

#### 5．数据—分析—结果Mapping

| 问题 | 数据怎样对应、分析 | 结果 |
| --- | --- | --- |
| 是否改善表现 | 同一人两条件测验配对比较；t检验／Wilcoxon | 回忆96.3%对88.9%；定义、概念应用无显著差异 |
| 是否更贴合用户 | 分析对应本人评分，配对比较 | 感知准确性、个性化更高 |
| 是否减少表达负担 | 对话对应条件，比较字数、轮次 | 用户字数减少；轮次差异不显著 |
| 哪里有用、哪里误判 | 访谈转写，归纳编码 | 帮助更有针对性，但视线也会被误解 |

#### 6．具体工作流与对应需求

| 作者具体做了什么 | 工具需要能做什么 |
| --- | --- |
| 将视线点画在第一人称画面上 | 把“看哪里”对应到实际内容 |
| 每0.5秒发送画面及局部裁剪，生成带时间观察 | 保存图像、时间及AI识别结果 |
| 根据观察序列推测阅读困难 | 把原始观察与AI解释分开存 |
| 阅读结束后，用分析指导语音帮助 | 将阅读记录传给后续对话，不打断阅读 |
| 用两种分析控制同一类助手 | 切换是否提供视线信息，保留条件 |
| 测验、自评、分析评价分别收集 | 分开保存实际表现、自觉理解及对AI判断的认可 |
