# Week4

## IDEA 1：表情反馈在-实时对话系统

### 前提

Common Ground 不是一次建立完成的，而是在对话过程中持续通过 grounding signals 、evidence of understanding 更新

### 人和人

（1）人在实时对话中会自然产生很多 verbal + nonverbal signals，例如“嗯嗯”“啊？”、停顿、犹豫、点头、皱眉、打断、重复、rephrase。

（2）这些 signals 往往和当前一句话、当前时间点直接对应。例如 speaker 刚讲到某一点，listener 马上皱眉或者“嗯？”，这个反应本身就在提供“这里可能没有理解”的信息

（3）另一方会利用这些 signals 调整后续表达，例如继续、补充、clarification、re-explanation 或 repair

### 人和 AI

现在的 realtime multimodal AI 已经可以接收部分 text、audio、video、face、gaze、gesture

但现有工作更多把这些 signals 用来：

（1）判断 什么时候说话：KEEP / BACKCHANNEL / TURN

（2）判断 emotion / empathy：例如 Empathic Grounding。

（3）判断 interaction rupture / error

### 存在什么问题

用户可能已经通过自然行为表达问题，但 AI 不一定把这些信号作为当前 conversation 的有效信息继续使用。因此可能出现： misunderstanding 或 misalignment 延续

### 为什么发生问题

（1）Signal 很弱：皱眉、“嗯？”犹豫， 不像一句“你说错了”那么明确

（2）Signal 是 multimodal 的：同一个状态可能同时体现在 face、voice、gesture、speech 中

（3）Timing 很重要：只知道“用户皱眉了”不够，还要知道用户是在 AI刚说到哪一部分时皱眉

（4）Signal 和 dialogue context 没有充分 mapping：AI 即使识别了情绪、动作或停顿，也不一定知道这个 signal 对当前 conversation meaning 有什么影响

### 现在大家做到哪里

（1）Human multimodal signal - interaction timing：AI 根据 text / audio / face 判断继续听、backchannel 还是接话

（2）Human signal - affective response：AI 根据 speech + facial expression 判断 emotion，再生成 empathic response

（3）Human signal - understanding / rupture detection：已经有人根据 face、voice、turn-taking 等预测 Understanding / Non-Understanding 或 Interaction Rupture

（4）Human signal - error management：在 physical HRI 中，人的自然 facial reaction 可以让机器人更早发现自身 task error，并进入 acknowledgement / recovery

### 这些工作还没有解决什么

（1）现有 detection 工作还没有充分回答这些 signals 怎么进入后续 conversational AI repair

（2）现有 signal 往往被单独识别，但我们还不清楚：signal + timing + 当前说了什么

结合起来以后，能不能更准确地告诉 AI：“用户是在对我刚才这一部分产生 confusion / disagreement / repair need

（3）即使 AI 根据这些 signals 做了 clarification等repair，我们还不知道是否真的改善后续 interaction / Common Ground

🔴Human natural grounding signals 能否被实时纳入 AI 对当前 conversation 的判断，并用于指导 AI repair，以及这种 repair 是否改善后续 common ground？

### Research Questions

RQ1： 在实时 Human–AI conversation 中，哪些 multimodal cues 能有效反映用户当前state of understanding(Understanding，Partial Understanding，Non-Understanding，Misunderstanding）？

RQ2：AI 能否利用这些 multimodal cues，比仅使用 transcript 更准确地识别用户的 state of understanding？

RQ3：当 AI 根据识别到的 state of understanding 进行 adaptive repair 时，是否能够改善后续 grounding 和 common-ground outcome？

> 评论（3）
>
> RQ1： 在实时 Human–AI conversation …
>
> 高星宇8月20日 22:21
>
> 从已有文献数据集得到
>
> 高星宇8月20日 22:22
>
> 如果已经知道哪些信号有用和ai 潜在repair 行为，我们想要的是用户来判断
>
> 高星宇8月20日 22:23
>
> 用户实验两种思路：1 还没做出system 之前拿一些信号去让用户打分给反应，2 提出了，我们可以做出对比实验
>
> 高星宇8月20日 22:24
>
> 很难找到关于grounding state的数据集，例如，比较有代表性的：用对方的

### 实验设计

#### 解决两个设计问题：

1. AI 需要表达哪些 grounding states？

2. 这些 states 应该通过什么 cues 表达？

#### Step 1：确定 AI grounding states

State 1：Understanding“我理解你的意思，可以继续。”

对应 human listener：nodding，attentive gaze，positive backchannel

State 2：Partial Understanding

AI：“我理解了一部分，但有信息不确定。”

对应 human listener：eyebrow raisegaze shifthesitation

State 3：Non-understanding

AI：“我没有理解，需要你进一步解释。”

对应：head tilt puzzled expression confused facial movement

#### Step 2：选择 facial cues

根据已有研究：人在 conversation 中最重要的 visible listener feedback：

#### Step 3： prototype

人多模态信号如何被分析然后传输给AI的

AI 如何从这些 cues 推断 user understanding state

Understanding state 如何影响 AI response

| 人的understanding state | cue（模糊不确定性） | AI reponse |
| --- | --- | --- |
| Understanding |  |  |
| Partial Understanding |  |  |
| Non-understanding |  |  |

> Step 3： prototype
>
> 高星宇8月20日 22:21
>
> 已经有相关文献有标注好的数据集，抽取别人标注好的数据集（比如共同的cues）
>
> 高星宇8月20日 22:27
>
> 不能只做可视化cues，背后问题：如何准确理解人的状态
>
> 高星宇8月20日 22:27
>
> or 我们提出一些机制，使信号本身加强和修复
>
> 高星宇8月20日 22:30
>
> 从HCI 视角切入，HCI 可以提供什么：比如：交互的cues，设计一些例如：按钮或button,
>
> 高星宇8月20日 22:33
>
> 如何把模糊的变成精确的信号
>
> 如何把模糊的变成精确的信号
>
> 高星宇8月20日 22:38
>
> （1）先看数据，看看我们如何使用是否使用这些数据，我们是否拿到这些多模态信号，信号可以来自不同维度，比如看看raw数据别的paper 的
>
> 高星宇8月20日 22:43
>
> 如果有数据已经提供：某一刻是否理解，那么我可以标注标注其他grounding 的信号，是在acknowl 还是repa，是否某些信号预测了理解或不理解，或者分析哪个是主因。

用户正在表达需求，AI实时观察cues，判断用户理解状态，AI决定下一步怎么回应

### Study

Jigsaw spoken instruction task

#### Condition 1：

AI 只根据语言内容回应。

#### Condition 2：

AI 根据：用户 speech + multimodal cues判断 understanding state然后回应

## IDEA2

### Older vs younger adults 跟 AI 对话时具体有哪些差异？

(1)对话更长，内容更多，更复杂：older adults 与 spoken conversational agent 的互动轮次更多，老年人的搜索对话持续时间更长，包含的请求也更多。更容易在一次表达中包含 多个 information needs / 更丰富 context ，Sentence structure 更复杂，short pauses 更多，更常出现 rephrasing / reformulation，以及在系统 clarification 后继续 add information   <https://dl.acm.org/doi/10.1145/3498366.3505830>

(2)他们遇到 breakdown 后会主动 repeat、rephrase、add information、clarify、self-correct，只是这些 repair 往往需要用户承担较多额外 effort <https://arxiv.org/pdf/2510.06690>

### Study 1 数据收集

年轻人和老年人在使用AI 时，是否以不同方式经历、识别和修复 conversational breakdown？

#### Participants

例如：Older adults (60+)；Younger adults

#### Data source

收集真实 Human–GenAI conversation。

让参与者提供：最近真实使用记录，或过去一段时间的 conversation history。不要要求他们专门找失败案例。（这里需要设计纳入criteria)

#### Analysis

以 breakdown episode 为分析单位。每个 episode 分析：breakdown recognition, breakdown interpretation, repair strategy, repair outcome

#### 可能发现

- Older adults 更倾向补充背景信息

- Younger adults 更倾向修改 prompt

- 两组对 AI failure 的归因不同

- 某些 repair strategy 对某类用户更有效

### Study 2：Participatory Design

那 AI 应该承担什么 repair 工作？

邀请：older adults,可以加入 younger adults 或设计专家

#### Workshop 流程

（1）给参与者看 Study 1 中匿名化的真实案例

例如：User:“帮我规划如何去xxx医院”，AI:输出的不是路径，问：“这里哪里出了问题？”然后问参与者会如何解决

（2）我们可以设计一些不完美的AI repair方法，激发参与者讨论批判，然后问问他们AI应该怎么做

> Study 2：Participatory Design
>
> 高星宇8月20日 22:55
>
> CHI/DIS,针对的用户是个体所以cscw 投不了，
>
> 高星宇8月20日 22:58
>
> 如果投cscw：（1）拉老年人做参与式，比如老年人自己互相对话，然后老年人互相和AI 对话，然后老年人说和人对话和AI 区别，然后再做design （2）老人老人，老人年轻人，把AI想象成年轻人，年轻人如何理解老年人说话
