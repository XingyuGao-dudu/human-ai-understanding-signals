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

![](assets/week01/figure-01.png)

现有实时笔记系统主要用多模态输入来捕捉内容、标注内容，或者从AI生成的内容中选择一条笔记；但在AI持续生成转录和笔记的过程中，还不知道用户需要在什么时候、以什么意图，如何用轻量多模态输入，快速表明这些意图：指的是哪段内容， 希望AI对它做什么

![](assets/week01/figure-02.jpeg)

### References

[1] Hsin-Ruey Tsai, Shih-Kang Chiu, and Bryan Wang. 2025. GazeNoter: Co-Piloted AR Note-Taking via Gaze Selection of LLM Suggestions to Match Users’ Intentions. In Proceedings of the 2025 CHI Conference on Human Factors in Computing Systems (CHI ’25). Association for Computing Machinery, New York, NY, USA, 22 pages. DOI: 10.1145/3706598.3714294.

[2] Faria Huq, Abdus Samee, David Chuan-en Lin, Xiaodi Alice Tang, and Jeffrey P. Bigham. 2025. NoTeeline: Supporting Real-Time, Personalized Notetaking with LLM-Enhanced Micronotes. In Proceedings of the 30th International Conference on Intelligent User Interfaces (IUI ’25). Association for Computing Machinery, New York, NY, USA, 18 pages. DOI: 10.1145/3708359.3712086.

[3] Leping Qiu, Erin Seongyoon Kim, Sangho Suh, Ludwig Sidenmark, and Tovi Grossman. 2025. MaRginalia: Enabling In-person Lecture Capturing and Note-taking Through Mixed Reality. In Proceedings of the 2025 CHI Conference on Human Factors in Computing Systems (CHI ’25). Association for Computing Machinery, New York, NY, USA, 15 pages. DOI: 10.1145/3706598.3714065.

## Idea 2

（1）大模型可能有人在做类似的，包括视频生成，找gap：可能没有关注grounding，关注数据对话过程中可能有grounding （2）backchannel里有没有cues影响人的行为...，做表情—很大的领域，make sure此问题没有类似的paper

研究发现，LLM生成的回复比人类对话包含更少的grounding acts,在真实人机对话日志中，LLM主动发起澄清的可能性约为人类的三分之一，提出follow-up request的可能性约为人类的十六分之一。人类不仅通过澄清、确认和复述，也会利用表情、凝视、停顿和backchannels，在对话进行中判断彼此是否理解，建立common ground。[1,2]

AI点头和面部行为能够提升engagement与perceived understanding，但主要用于情感表达或倾听反馈，而不是呈现AI是否理解、是否不确定或是否需要澄清。[3,4,6]

因此，我们研究AI能否在回应前通过轻量面部线索外显其即时对话状态，帮助用户更早发现并修复误解

![](assets/week01/figure-03.png)

![](assets/week01/figure-04.jpeg)

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

![](assets/week01/figure-05.png)

![](assets/week01/figure-06.jpeg)

### Xing, Yuan, & Mostafa (2022)

Age-related Difference in Conversational Search Behavior: Preliminary Findings

ACM CHIIR 2022

DOI：10.1145/3498366.3505830

## idea4 Making Group Alignment Visible

多人共同使用AI时，通常是大家输入意见，AI最后总结或生成方案。但AI可能会：主要吸收说话最多的人的意见,忽略没有被重复强调的个人限制，把沉默当成同意，为了生成统一答案，过早消除真实分歧。

因此，AI给出的结果可能看起来代表整个群体，实际上只和部分成员对齐。

这里有三种alignment：1 成员是否理解彼此 2 AI是否理解每个成员 3 AI结果是否真正代表群体。

设计并评估一个alignment-aware AI system，帮助成员检查AI是否准确代表每个人，并在形成最终方案前修复错误对齐。

![](assets/week01/figure-07.jpeg)

“AI as an Agent and Collaborative Space: Exploring the Role of Generative AI in Small Group Synchronous and Asynchronous Collaborative Dynamics.”

CHI 2026
