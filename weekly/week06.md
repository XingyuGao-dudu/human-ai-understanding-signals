# Week 6

## 人与人 人与AI 人与机器人 表现出的signals有差异

🏝️ 人和人对话signal understanding state的数据集，能不能直接用于AI

1. 信号会不一样
2. 信号语义很可能会变
3. 跨域迁移（人与人和人与chatbot)

（1）On Multimodal Emotion Recognition for Human-Chatbot Interaction in the Wild

https://dl.acm.org/doi/epdf/10.1145/3678957.3685759

|  | Model | Modalities: Text | Audio | Video | Macro F₁ (User Labels): VAD | Valence | Arousal | Dominance | Macro F₁ (Chatbot Labels): VAD | Valence | Arousal | Dominance |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | Baseline | — | — | — | 24.00 | 20.40 | 23.64 | 27.96 | 22.18 | 21.44 | 17.34 | 27.76 |
| Unimodal | MultiGRU | ✓ | — | — | 36.68 | 46.54 | 31.29 | 32.21 | 41.86 | 52.36 | 36.41 | 36.79 |
| Unimodal | SingleGRU | — | ✓ | — | 29.62 | 28.67 | 27.95 | 32.25 | — | — | — | — |
| Unimodal | SingleGRU | — | — | ✓ | 28.41 | 29.38 | 26.25 | 29.60 | — | — | — | — |
| Multimodal | Multimodal-Concat | ✓ | ✓ | — | 41.72 | 49.13 | 38.26 | 37.79 | 41.86 | 52.42 | 36.91 | 36.26 |
| Multimodal | Multimodal-IMA | ✓ | ✓ | — | 40.91 | 48.66 | 39.10 | 34.98 | 40.87 | 51.35 | 36.26 | 35.01 |
| Multimodal | Multimodal-Concat | ✓ | — | ✓ | 39.80 | 47.90 | 35.03 | 36.47 | 40.66 | 51.60 | 35.14 | 35.23 |
| Multimodal | Multimodal-IMA | ✓ | — | ✓ | 37.00 | 46.36 | 32.24 | 32.39 | 40.25 | 49.74 | 36.54 | 34.47 |
| Multimodal | Multimodal-Concat | ✓ | ✓ | ✓ | 39.85 | 47.05 | 36.21 | 36.29 | 40.28 | 51.01 | 35.90 | 33.94 |
| Multimodal | Multimodal-IMA | ✓ | ✓ | ✓ | 38.76 | 45.91 | 33.82 | 36.55 | 39.53 | 49.52 | 35.52 | 33.55 |

Valence：积极还是消极；

Arousal：平静还是兴奋、激动；

Dominance：感觉自己掌控局面，还是被局面控制；

VAD：前三项 Macro F1 的平均值。
<img width="458" height="322" alt="image" src="https://github.com/user-attachments/assets/2e3f72d9-3119-43a7-8d61-e87f39ca2108" />

现有的人人对话情绪识别（ERC）模型，能不能直接用在真实场景的人聊天机器人对话上？

收集了 99 人、三周、与 GPT-3 聊天机器人的文本+音频+视频多模态数据，提取了文本、音频、视频

预测用户情绪和预测感知 chatbot 情绪

结论：（1）面部变化的多样性明显更低，差距集中在脸颊、鼻子、抿嘴区域（2）AI 说什么会改变人的状态（这里主要指情绪状态），chatbot 显得开心，用户自己也倾向于报开心，ai显得低沉，用户也往下走。

（可以学表情分析编码？）

（2） Differentiating depression using facial expressions in a virtual avatar communication system

<img width="1280" height="749" alt="image" src="https://github.com/user-attachments/assets/14c84186-6072-4b13-a36f-d1c4089f2420" />


| Interviewer's behavioural mode | Participant's behavioural mode |
| --- | --- |
| Speaking | Listening |
| Asking a question |  |
| Listening | Reacting |
| Speaking | Listening |
| Asking a question |  |
| Listening | Reacting |
| . | . |
| . | . |

<img width="1136" height="920" alt="image" src="https://github.com/user-attachments/assets/13b29d34-f988-44e8-9714-b6bf2e3a0eda" />


| Upper Face Action Units |  |
| --- | --- |
| AU1 | Inner Brow Raiser |
| AU2 | Outer Brow Raiser |
| AU4 | Brow Lowerer |
| AU5 | Upper Lid Raiser |
| AU6 | Cheek Raiser |
| AU7 | Lid Tightener |
| \*AU41 | Lip Droop |
| \*AU42 | Slit |
| \*AU43 | Eyes Closed |
| AU44 | Squint |
| AU45 | Blink |
| AU46 | Wink |

| Lower Face Action Units |  |
| --- | --- |
| AU9 | Nose Wrinkler |
| AU10 | Upper Lip Raiser |
| AU11 | Nasolabial Deepener |
| AU12 | Lip Corner Puller |
| AU13 | Cheek Puffer |
| AU14 | Dimpler |
| AU15 | Lip Corner Depressor |
| AU16 | Lower Lip Depressor |
| AU17 | Chin Raiser |
| AU18 | Lip Puckerer |
| AU20 | Lip Stretcher |
| AU22 | Lip Funneler |
| AU23 | Lip Tightener |
| AU24 | Lip Pressor |
| \*AU25 | Lips Parts |
| \*AU26 | Jaw Drop |
| \*AU27 | Mouth Stretch |
| AU28 | Lip Suck |

https://www.frontiersin.org/journals/digital-health/articles/10.3389/fdgth.2023.1080023/full

1. 面试官是真人还是屏幕里的虚拟人，对人的情绪、表情、眼神有影响吗？
2. 聊的话题是中性（园艺、旅行）还是负面（战争、孤独），对人有什么影响？
3. 有抑郁症状的人和正常人，说话用词、表情、眼神有什么差别？

结论：虚拟人和真人，对情绪、表情、眼神几乎没有影响。负面话题（战争、孤独）让情绪量表的负面分上升、正面分下降，人向下看的次数变多。

(3) AutoTutor and Affective AutoTutor: Learning by Talking with Cognitively and Emotionally Intelligent Computers that Talk Back
<img width="1078" height="880" alt="image" src="https://github.com/user-attachments/assets/d4217dab-8c85-4582-b0d0-03a98179680b" />

<img width="950" height="712" alt="image" src="https://github.com/user-attachments/assets/faae19b9-5d4c-4dc2-912c-531eb93e689c" />

https://www.ida.liu.se/divisions/hcs/seminars/cogsciseminars/Papers/dmello-TiiS12.pdf

A：一个用文字对话的电脑导师。它问学生问题，分析学生的文字回答，判断学生懂没懂

B：在上面基础上加了情绪检测，从面部表情、身体姿态、对话线索里识别学生的无聊、困惑、挫败，然后调整教学策略去化解负面情绪

Expectations：理想答案应包含的关键知识点

Misconceptions：学生可能出现的典型错误认识

学生的认知输入：答案说了什么、说得对不对

学生的情绪输入：是否表现出困惑、无聊或挫败

## 人与AI的数据集

🥇 到底有没有人和AI的signals-understanding state的文献

error / rupture / awkwardness / affect

Look at Me When I Talk to You

https://arxiv.org/abs/2104.07153

Detecting Interlocutor Confusion in Situated Human–Avatar Dialogue: A Pilot Study

## 未来方向

人外显 → AI 观察 → AI 调整 → 再继续对话

RQ1： 在实时 Human–AI conversation 中，哪些 multimodal cues 能有效反映用户当前state of understanding(Understanding，Partial Understanding，Non-Understanding，Misunderstanding）？

在实时人-AI 对话中，哪些 cue（及组合）与 understanding state 相关？它们与人人对话中的已知映射（AU4/AU7、皱眉、点头、gaze 等）相比，发生了怎样的偏移？

RQ2：AI 如何利用这些 multimodal cues识别用户的 state of understanding？

RQ3：当 AI 根据识别到的 state of understanding 进行 adaptive repair 时，是否能够改善后续 grounding 和 common-ground outcome？

## 步骤

1 准备工作

有哪些理解状态

四级：Understanding,Partial ,Non-Understanding, Misunderstanding

学习状态：投入/无聊/困惑/挫败/顿悟

有哪些可能的信号

表情、gaze、头部、声音（音高、停顿或沉默时长、响度、语速）、坐姿压力变化、语言（回答长度、回应延迟、元认知话语：懂了，我没懂，哦明白）

大家都是怎么收集的

2 数据集

人数

任务及场景

AI 形态：纯语音 vs 带脸虚拟形象

需要采集哪些模态 如何采集不同模态信息

标注方法

3 系统：

OpenFace/openSMILE/ASR 提取不同signal

根据训练好的模型判断state

再mapping选择不同repair策略

LLM执行

4评估实验

任务是？（与步骤 2 的任务领域绑定）

understanding 测什么（转述准确性？预测性问题？）

被试量（按效应量反推，参照 AutoTutor d≈0.7）

评估指标

评估周期：单次会话 or多会话

## 贡献点

1. 第一个人—AI signal—understanding 数据集（主贡献）
2. 人人 vs 人-AI 信号偏移的实证测量（对比贡献）
3. 带时机的 adaptive repair 系统的验证（系统贡献）
