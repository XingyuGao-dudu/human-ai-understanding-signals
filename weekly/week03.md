# Week3

## IDEA 1：表情反馈在-实时对话系统

前提：Common Ground 需要双方持续获得 evidence of understanding，确认彼此足够一致，才能继续任务

### 人和人：

（1）在面对面实时对话中，listener 会通过可视化feedback 持续外显自己的 understanding state

speaker 会监控这些反馈，并在发现对方没有理解时实时调整表达。

common ground 的更新不是只发生在一句话结束后，而可以是 continuous 的

[www.coli.uni-saarland.de](https://www.coli.uni-saarland.de/~masta/WS13/ClarkKrych_04.pdf)

（2）这种反馈往往是短暂的 backchannel，可以嵌在 speaker 持续讲话的过程中，而不需要 listener 完整取得话轮 [talkbank.org](https://talkbank.org/ca/access/0docs/JOC-PDF/4-bavelas%2C%20coates%20%26%20johnson.pdf)

（3）当 listener 表现出confusion时，speaker增加重复和解释。<https://aclanthology.org/W08-0105.pdf>

### 人和 AI：

LLM 更少主动 clarification 和 追问

### 存在什么问题：

人和AI对话还在顺畅继续，但双方实际上并没有充分对齐

### 为什么发生问题：

（1）用户这边：用户经常无法把真实目标、要求和判断标准完整说出来

（2）AI 这边：AI 经常不会主动确认自己到底理解对没有，而是直接假设双方已经理解一致直接继续

用户没说全+AI没反馈直接进行=双方可能在理解并未真正对齐时继续对话

### 现在大家怎么解决：

（1）用户提交需求前：系统用结构、分块、提示等方式帮助用户把目标和条件表达完整。[PromptFlow, CHI 2026](https://dl.acm.org/doi/10.1145/3772363.3799168)

（2）用户说完后，AI 发现信息不足时：AI 主动问 clarification question，用户再补充信息。 [Resolving Ambiguity Through Interaction with LMs, NAACL 2025](https://aclanthology.org/2025.findings-naacl.306/)，[ACL Anthology](https://aclanthology.org/2025.findings-naacl.306.pdf?utm_source=chatgpt.com)

（3）AI 已经形成理解后：AI 把“我现在是这么理解你的”外显出来

（4）用户正在说话时：AI 用实时 目光/指代手势/head turning / highlighting：我理解成了什么 / verbal clarification：我哪里没懂/       来反馈当前理解 [Prompting an Embodied AI Agent: How Embodiment and Multimodal Signaling Affects Prompting Behaviour](https://dl.acm.org/doi/10.1145/3706598.3713110)

<https://dl.acm.org/doi/10.1145/3706598.3713110>

### 为什么关注表情

（1）人和人对话里，face 本来就是 speaker 用来实时判断 listener 是否跟上的一个 interaction channel，而且 facial trouble signals 会直接改变 speaker 的 repair behavior

🔴证据

A 表情不只是表达 emotion，还本身具有 conversational functions，包括 listener comments、backchannels 等，而且可以传递 listener 对当前内容的 understanding [UVicSpace](https://dspace.library.uvic.ca/items/1fb3cc1a-fbe1-47ef-9592-e435606f74e6)

B speaker 看见“对方好像没懂”的脸以后，会主动多解释。[PubMed](https://pubmed.ncbi.nlm.nih.gov/40078914/?utm_source=chatgpt.com)

(2) 表情可以在 speaker 持续讲话时，通过不打断用户，的视觉实时表达 listener 的，特别适合 continuous spoken interaction

🔴gestural backchannels 更容易直接 overlap 在 speaker 正在讲话的时候，而 vocal backchannels 更倾向出现在 speech gap。“嗯嗯/啊”虽然很短，但还是占用了 auditory channel；face 可以完全静默地持续存在

### 这些方法还没有解决什么：

（1）已有工作已经研究了 实时 feedback 怎么告诉用户“AI 理解成了什么”

（2）已有 facial grounding 工作也研究了能不能被理解为understanding confusion

（3）但是还不清楚：当 AI 作为 listener，在用户正在讲话时通过表情表达不同理解状态时，用户会不会像人人互动一样主动 repair；什么时候 repair、怎么 repair，以及最终 common ground 是否真的改善

### 研究问题

在实时对话场景中

RQ1：AI用表情外显自己的理解状态是否会让用户发现当前 grounding problem？

RQ2：用户看到 facial signal 后，会有什么行为，什么时候做出这些行为？

RQ3：这些行为是否最终改善 common ground（任务结果？）？

### 实验设计   Tangram？Jigsaw task？

Facial signal → 用户是否发现 grounding problem → 什么时候 repair → 怎么 repair→ common ground 是否改善

(1)在此之前需要定义有AI哪些grounding state需要实时展示，对应什么表情

(2) pre-experiment（先研究表情）先定义 AI 要表达的 grounding state, 然后测试哪些 facial signals 能稳定被理解

(3)正式实验(WOZ)（再研究用户行为）一个需要连续 spoken instruction 的任务，在预先设置的问题-表情映射系统中，由研究者判断并触发表情反馈

> 评论（4）
>
> 实验设计 Tangram？Jigsaw task？
>
> 高星宇8月14日 22:19
>
> 文献
>
> (1)在此之前需要定义有AI哪些grounding…
>
> 高星宇8月14日 22:22
>
> 多模态模型得和说话时间配上

### 可能的结果（假设）

（1）表情 让用户更早主动 repair，而不是等 AI 说完再 clarification

（2）不同表情会触发不同 repair，比如，更多的解释

（3）表情不一定总是有效

（4）表情可能适合表达早期、低程度 uncertainty

### 我们如何讨论

1 Facial feedback 和现有 grounding 方法是什么关系：根据实验结果比较 facial signal、verbal clarification、head/gaze/highlighting 分别适合什么情况，哪些可以互补，哪些不能替代

2 表情怎么改变 repair process,和human-human grounding 研究有什么一致或不同

3 什么样的 facial signal 才适合用于 grounding

### 我们的贡献可能是？

（1）Empirical contribution：第一次系统研究 AI facial grounding feedback 如何影响真实 spoken interaction 中用户的 speaker initiated行为 和 common ground outcome

（2）说明用户看到 AI facial feedback 后，什么时候 repair、怎么 repair、哪些情况下不 repair

（3）Design contribution：给出设计原则，包括 什么 grounding state 应该展示、用什么 facial signal

## IDEA2

Romative study

### State of the world

（1）用户群体从技术专家扩展到不同年龄、不同经验水平的人群

（2）interaction breakdown 不可避免

（3）有效使用还赖用户理解 AI capabilities、limitations，并能够评价和调整交互（AI literacy）

### The Big BUT

（1）现有解决方式是提升用户的AI literacy，教育用户

（2）然而，这种路径默认用户能够识别 AI misunderstanding，并主动完成 interaction repair

（3）我们尚不清楚不同年龄用户是否能够以相同方式发现、解释和修复 breakdown

### Therefore

> Therefore
>
> 高星宇8月14日 22:52
>
> 老年人年轻人习惯是什么，然后在实验中看看如何h

RQ1：不同年龄用户如何发现并解释breakdwon？

RQ2：breakdown 发生时，不同年龄用户采取什么repair strategy？

RQ3：这些差异如何帮助设计更适应不同用户的 conversational AI？

> RQ3：这些差异如何帮助设计更适应不同…
>
> 高星宇8月14日 22:53
>
> 给了不同适应情况，绿野仙踪，然后给不同年龄的人做
>
> 高星宇8月14日 22:54
>
> 收集很多对话后，对对话进行聚类，

### Key findings

### Discussion

（1）需要从AI端来思考如何解决：现有 AI 设计隐含要求用户完成大量 alignment work，而这种负担可能并不是所有用户都能同等承担

（2）为什么在识别break dwon or repair strategy会有差异？什么原因导致的，怎么设计？

### Contributions

#### Empirical Contribution

揭示不同年龄用户在 breakdown 中：如何发现问题，如何解释，如何修复

#### Conceptual Contribution

提出：Breakdown and Repair Framework


#### Design Contribution

提出支持不同用户的 adaptive conversational AI design implications。
