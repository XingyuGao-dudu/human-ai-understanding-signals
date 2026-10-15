# IDEA

## IDEA1 AI辅助记笔记-多模态输入

### Background & Related Work

#### 1. 我们聚焦于什么场景：实时AI辅助记笔记

在上课、会议和听报告等，用户需要同时听取内容、理解信息、判断重点并形成自己的笔记。

现在的AI辅助记笔记系统通常由AI实时记录正在发生的内容，例如生成逐字转录、阶段性摘要或结构化笔记；用户则负责判断哪些内容重要，通过不同输入方式选择或修改AI生成的内容，并在需要时主动要求AI补充、解释、查找或重新组织笔记。用户的输入可能是：生成后审阅，或用户先输入，AI再扩展，或实时共同生成

那么我们暂时将研究场景定义在：在人机共同记笔记过程中，用户正在听课、会议或报告时，会产生哪些想要指导AI的即时需求；设计一种多模态交互，使用户在实时听讲和AI辅助记笔记过程中，快速标记相关内容，并表达希望AI执行的操作。

#### 2. 存在什么问题：输入速度，注意力和用户意图的冲突

已有文献支持：在实时信息活动中，用户确实需要主动影响AI笔记，传统文字输入，可能过慢，或转移注意力并增加认知负担，而完全由AI自动生成的内容又可能不符合用户意图。实时记笔记存在输入速度、注意力和用户意图之间的冲突，但目前还不能直接断言用户具体在哪些时刻想让AI做什么、哪些需求因为输入成本而被放弃

#### 3. 现有文献分别做了什么

| 文章 | 场景 | 用户任务 | 输入方式 | 主要发现 |
| --- | --- | --- | --- | --- |
| GazeNoter | 坐着听speech；边走边参加meeting和discussion | 在内容持续发生时，记录重点、稍后要问的问题和自己的观点 | AI生成context、customized和derivative keywords及candidate sentences；用户用gaze选择、ring确认 | User-in-the-loop笔记比全自动笔记更符合用户意图；AR版本比手机打字和手机选择更少打断、负荷更低，并支持更多、更完整的笔记 |
| NoTeeline | 个人在电脑前观看信息密集的预录视频 | 听到重点时快速留下短笔记，之后获得完整、个性化笔记 | 用户键盘输入micronote；AI结合时间点transcript和个人写作样本扩写 | 相比手动笔记，减少47%输入文字和43.9%书写时间，暂停和回看更少，mental demand、effort和frustration更低 |
| MaRginalia | 模拟现场单讲者lecture，学生同时看讲师、幻灯片并听讲 | 捕捉和标注幻灯片或讲话内容，自己书写笔记，并在遗漏后回看历史内容 | MR＋tablet；gaze负责切换和定位空间面板，pen负责捕捉、标注和书写 | 用户多数时间保持heads-up，认为系统能帮助快速捕捉、保持参与并补回遗漏内容；但研究属于可行性和可用性探索 |

现有实时笔记系统主要用多模态输入来捕捉内容、标注内容，或者从AI生成的内容中选择一条笔记；但在AI持续生成转录和笔记的过程中，还不知道用户需要在什么时候、以什么意图，如何用轻量多模态输入，快速表明这些意图：指的是哪段内容， 希望AI对它做什么

<img width="2784" height="1097" alt="image" src="https://github.com/user-attachments/assets/0cfc4d75-0194-4ec1-884c-5411f7692868" />

### References

[1] Hsin-Ruey Tsai, Shih-Kang Chiu, and Bryan Wang. 2025. GazeNoter: Co-Piloted AR Note-Taking via Gaze Selection of LLM Suggestions to Match Users’ Intentions. In Proceedings of the 2025 CHI Conference on Human Factors in Computing Systems (CHI ’25). Association for Computing Machinery, New York, NY, USA, 22 pages. DOI: 10.1145/3706598.3714294.

[2] Faria Huq, Abdus Samee, David Chuan-en Lin, Xiaodi Alice Tang, and Jeffrey P. Bigham. 2025. NoTeeline: Supporting Real-Time, Personalized Notetaking with LLM-Enhanced Micronotes. In Proceedings of the 30th International Conference on Intelligent User Interfaces (IUI ’25). Association for Computing Machinery, New York, NY, USA, 18 pages. DOI: 10.1145/3708359.3712086.

[3] Leping Qiu, Erin Seongyoon Kim, Sangho Suh, Ludwig Sidenmark, and Tovi Grossman. 2025. MaRginalia: Enabling In-person Lecture Capturing and Note-taking Through Mixed Reality. In Proceedings of the 2025 CHI Conference on Human Factors in Computing Systems (CHI ’25). Association for Computing Machinery, New York, NY, USA, 15 pages. DOI: 10.1145/3706598.3714065.

## Idea 2

（1）大模型可能有人在做类似的，包括视频生成，找gap：可能没有关注grounding，关注数据对话过程中可能有grounding （2）backchannel里有没有cues影响人的行为...，做表情—很大的领域，make sure此问题没有类似的paper

研究发现，LLM生成的回复比人类对话包含更少的grounding acts,在真实人机对话日志中，LLM主动发起澄清的可能性约为人类的三分之一，提出follow-up request的可能性约为人类的十六分之一。人类不仅通过澄清、确认和复述，也会利用表情、凝视、停顿和backchannels，在对话进行中判断彼此是否理解，建立common ground。[1,2]

AI点头和面部行为能够提升engagement与perceived understanding，但主要用于情感表达或倾听反馈，而不是呈现AI是否理解、是否不确定或是否需要澄清。[3,4,6]

因此，我们研究AI能否在回应前通过轻量面部线索外显其即时对话状态，帮助用户更早发现并修复误解

| 文章 | 研究问题 | 实验／分析做了什么 | 主要结果 |
| --- | --- | --- | --- |
| Navigating Rifts in Human–LLM Grounding | 人与LLM的grounding行为有什么不同？早期grounding failure是否会导致后续对话崩溃？ | 这不是受控用户实验。作者分析WildChat、MultiWOZ和Bing Chat三类对话日志，建立grounding acts分类并标注对话；随后构建Rifts benchmark，测试当前模型能否在需要时主动澄清或追问。 | 与人类相比，LLM主动澄清的可能性低约3倍，提出follow-up<!-- 原图右侧截断 --><br>性低约16倍；早期未修复的grounding failure能够预测后续互<!-- 原图右侧截断 --><br>沿模型在相关benchmark上的表现仍较差。（ACL Anthology） |
| Empathic Grounding | 与中性backchannel相比，结合面部表情、头部动作和语言的empathic grounding，是否能让用户觉得机器人更理解自己、更有同理心和更值得信任？ | 18人完成实验，1人因技术问题被排除，最终分析17人。参与者被随机分到两组，与人形机器人谈论过去的疼痛经历：一组机器人只做中性点头和“OK”等回应；另一组根据用户语言和面部表情，生成相应的表情、点头和简短共情回应。实验后填写同理心、理解感、情绪智能、信任等量表，并接受访谈。 | Empathic Grounding组认为机器人更有同理心、情绪智能，w<!-- 原图右侧截断 --><br>／trust更高，也更常觉得机器人真正听懂了自己。但实验样本<br>受限，而且它表达的是对**用户情绪的理解**，没有研究AI如何用<!-- 原图右侧截断 --><br>**不确定或需要澄清**。（arXiv） |
<img width="3205" height="442" alt="image" src="https://github.com/user-attachments/assets/cff05c6a-0620-4890-8ec7-d75e4cfd4479" />


[1] Omar Shaikh, Kristina Gligorić, Ashna Khetan, Matthias Gerstgrasser, Diyi Yang, and Dan Jurafsky. 2024. Grounding Gaps in Language Model Generations. In Proceedings of the 2024 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, 6279–6296.

[2] Omar Shaikh, Hussein Mozannar, Gagan Bansal, Adam Fourney, and Eric Horvitz. 2025. Navigating Rifts in Human–LLM Grounding: Study and Benchmark. In Proceedings of the 63rd Annual Meeting of the Association for Computational Linguistics, Article 1016.

[3] Jin Yea Jang, Saim Shin, and Gahgene Gweon. 2024. Minimal Yet Big Impact: How AI Agent Back-channeling Enhances Conversational Engagement through Conversation Persistence and Context Richness. In Findings of the Association for Computational Linguistics: EMNLP 2024, 14509–14521.

[4] Mehdi Arjmand, Farnaz Nouraei, Ian Steenstra, and Timothy Bickmore. 2024. Empathic Grounding: Explorations using Multimodal Interaction and Large Language Models with Conversational Agents. In Proceedings of the 24th ACM International Conference on Intelligent Virtual Agents (IVA ’24), Article 6, 1–10.

[5] Sunnie S. Y. Kim, Q. Vera Liao, Mihaela Vorvoreanu, Stephanie Ballard, and Jennifer Wortman Vaughan. 2024. “I’m Not Sure, But…”: Examining the Impact of Large Language Models’ Uncertainty Expression on User Reliance and Trust. In Proceedings of the 2024 ACM Conference on Fairness, Accountability, and Transparency (FAccT ’24), 822–835.

[6] Silke ter Stal, Gerbrich Jongbloed, and Monique Tabak. 2021. Embodied Conversational Agents in eHealth: How Facial and Textual Expressions of Positive and Neutral Emotions Influence Perceptions of Mutual Understanding. Interacting with Computers 33, 2, 167–176.

[7] Peter Zeng, Weiling Li, Amie J. Paige, Zhengxiang Wang, Panagiotis Kaliosis, Dimitris Samaras, Gregory J. Zelinsky, Susan Brennan, and Owen Rambow. 2026. LVLMs and Humans Ground Differently in Referential Communication. In Proceedings of the 64th Annual Meeting of the Association for Computational Linguistics, 9061–9087.

## idea3

算法研究主要提高AI对输入的识别和处理能力，例如：识别老年人口语，补全缺失信息，改写冗长或不清楚的请求，根据上下文推断用户意图。它解决的是：AI能否从技术上推测用户想表达什么。但算法准确，并不等于双方已经形成common ground，两组人对AI具有什么能力、记得什么、是否真正理解语言，有不同的假设和习惯，因此采用不同的grounding strategies

因此，我们需要知道老年人与年轻人如何与AI建立和修复common ground，他们在哪些环节出现不同困难？

AI如何面对不同群体的需求，

搜文献，在ai：可能直接通过改模型就可以直接解决问题了，
| 文章 | 算法解决什么 | 怎么做 | 结果 |
| --- | --- | --- | --- |
| Empowering Older Adults in Digital Technology Use with Foundation Models（Sharifi et al., 2026） | 老年人在求助数字技术问题时，可能出现描述冗长、信息不完整、过度具体或不够具体，导致AI和搜索系统难以理解 | 使用GPT-4o的prompt-chaining：先追问缺失的背景信息，再改写老年人的原始问题，最后生成解决方案；同时构建老年人技术求助数据集OATS | AI改写后，解决方案准确率从46%提高到69%，搜索结果准确率从35%提高到69%。说明算法通过补全和重写输入，提高了机器对老年人意图的理解。（arX<!-- 原图右侧截断 -->） |
| COAS2W: A Chinese Older-Adults Spoken-to-Written Transformation Corpus with Context Awareness（Kang et al., EMNLP 2025） | 老年人口语中可能包含省略、语序混乱、成分错误和重复，直接转录后不适合后续AI任务 | 建立包含10,004条中国老年人口语的spoken-to-written数据集，并用上下文微调轻量开源模型，将口语转换成规范书面表达 | 微调后的轻量模型优于更大的闭源模型；加入多句上下文能提高转换表现，规范化后的文本也改善了下游翻译任务。（ACL Anthology） |

<img width="1886" height="886" alt="image" src="https://github.com/user-attachments/assets/468c7cd3-feee-4041-99b2-3d3b21360217" />


### Xing, Yuan, & Mostafa (2022)

Age-related Difference in Conversational Search Behavior: Preliminary Findings

ACM CHIIR 2022

DOI：10.1145/3498366.3505830

## idea4 Making Group Alignment Visible

多人共同使用AI时，通常是大家输入意见，AI最后总结或生成方案。但AI可能会：主要吸收说话最多的人的意见,忽略没有被重复强调的个人限制，把沉默当成同意，为了生成统一答案，过早消除真实分歧。

因此，AI给出的结果可能看起来代表整个群体，实际上只和部分成员对齐。

这里有三种alignment：1 成员是否理解彼此 2 AI是否理解每个成员 3 AI结果是否真正代表群体。

设计并评估一个alignment-aware AI system，帮助成员检查AI是否准确代表每个人，并在形成最终方案前修复错误对齐。

<img width="2180" height="668" alt="image" src="https://github.com/user-attachments/assets/0c08bf54-d08b-4ba7-8f76-8b1b99bc89b9" />


“AI as an Agent and Collaborative Space: Exploring the Role of Generative AI in Small Group Synchronous and Asynchronous Collaborative Dynamics.”

CHI 2026
