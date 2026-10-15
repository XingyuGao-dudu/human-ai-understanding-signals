# Week5-DATASET

## MUNDEX dataset

| Tier |  |  |
| --- | --- | --- |
| EX_SPEECH | 德语原话、&lt;laugh&gt;、&lt;dis&gt;、&lt;back&gt; 等 | EX 什么时候说了什么 |
| EE_SPEECH | 同上 | EE 什么时候说了什么 |
| EX_FORWARD | S, A, RA, AD, SQ, YNQ, FE⋯ | EX 当前这句话想对后面的对话做什么 |
| EE_FORWARD | 同上 | EE 当前这句话想对后面的对话做什么 |
| EX_BACKWARD | AW, AutoFB, AlloFB, R, RR, COR, SU⋯ | EX 当前这句话和前面的话是什么关系 |
| EE_BACKWARD | AW, AutoFB, AlloFB, SU, SNU, SPU, RR, COR⋯ | 非常重要：EE 的反馈、理解、不理解、重复、纠正等 |
| EX_DIALOGUE_CO | TT, TG, TK, TR, TA, ST | EX 怎么管理说话轮次 |
| EE_DIALOGUE_CO | 同上 | EE 怎么拿/抢/保持/释放说话轮次 |
| EE_BACKCHANNELS | okay, ja, mhm, ah, hm, aha⋯ | EE 的短反馈，例如 “嗯” “okay” “aha” |
| EXPL_PHASE | GAME NOT PRESENT / GAME PRESENT / GAME PLAY | 当前处于实验的哪个阶段 |
| EXPL_TOPICS | 1, 2.1, 4.2, 5.2⋯ | 当前在讲哪条桌游规则 |
| EE_ADAPTORS | self-adaptor, object-adaptor⋯ | EE 的摸脸、摸自己、摆弄东西等非语义小动作 |
| EX_GAZE | EE / TABLE / AWAY | EX 在看 EE、桌面，还是看向别处 |
| EE_GAZE | EX / TABLE / AWAY | EE 在看 EX、桌面，还是看向别处 |
| MUTUAL_GAZE | EX EE 等 | 两个人是不是正在互相看 |
| EE_HEAD_GEST | nod_s, nod_r, shake_s⋯ | EE 点头、摇头、歪头等 |
| EX_GESTURE_DEIXIS_LEFT | D, DI, DB, DIB | EX 左手的指向型手势 |
| EX_GESTURE_DEIXIS_RIGHT | D, DI, DB, DIB | EX 右手的指向型手势 |
| EX_VR | 一大段德语评论 | EX 事后回看录像，对 “EE 当时懂没懂” 的评论 |
| EX_UND | UND / PART_UND / NON_UND / MISUND | 根据 EX 的事后评论标出的 EE understanding state |
| EE_VR | 一大段德语评论 | EE 自己事后回看录像，说自己当时懂没懂 |
| EE_UND | UND / PART_UND / NON_UND / MISUND | 最重要的 listener state：根据 EE 自己的回忆得到的理解状态 |
| UND_MATCH | YES / NO | EX 和 EE 的 video-recall comment 是否能够匹配/连接 |
| EX_UND_MATCH | 四种 understanding labels | 对齐后的 EX understanding annotation |
| EE_UND_MATCH | 四种 understanding labels | 对齐后的 EE understanding annotation |
| Daniel_EE_BACKCHANNELS | ja, okay, mhm⋯ | 只在 1 个 EAF 中出现，不在官方标准 tier 列表里，正式分析先别用 |
| qweqwe | 一些奇怪的组合字符串 | 不在官方 README/manual 的标准 tier 中，用途无法确认，直接忽略 |

| 标签 | 全称 |  |
| --- | --- | --- |
| S | Statement | 普通陈述 |
| A | Assert | 陈述一条游戏规则/事实 |
| RA | Re-assert | 把之前说过的事实再说一次 |
| AD | Action Directive | “你现在掷骰子” 这种让对方做事 |
| IR | Information Request | 请求信息的大类 |
| SQ | Set Question | WH-question，例如 “为什么？” “怎么？” |
| YNQ | Yes/No Question | 能回答 yes/no 的问题 |
| FE | Feedback Elicitation | “我这样理解对吗？”，主动索取确认 |
| AW | Answer | 回答问题 |
| FB | Feedback | Feedback 大类 |
| AutoFB | Auto-Feedback | 对对方刚才说的话直接给反馈 |
| AlloFB | Allo-Feedback | 对 “对方的 feedback” 再给 feedback |
| SFB | Self-Feedback | 对自己刚才的理解/动作确认 |
| U | Understanding | 表示与理解有关，但无法细分 |
| R | Resolution | 一个理解问题成功解决了 |
| COM | Compound | 两个人共同补全/共同构建一句信息 |
| H | Hold | 暂时不直接回答，先确认别的信息 |
| RR | Repeat / Rephrase | 重复/换句话说刚才内容来检查理解 |
| COR | Correct | 纠正对方说错的内容 |
| SES | Self-error Signal | “不对，我刚才说错了” |
| SU | Signal Understanding | 明确表现 “我懂了” |
| SNU | Signal Non-Understanding | 明确表现 “我没懂” |
| SPU | Signal Partial Understanding | 明确表现 “我没完全懂” |
| TT | Turn Take | 正常接过话轮 |
| TG | Turn Grab | 抢/打断别人拿到话轮 |
| TK | Turn Keep | 继续保持自己的话轮 |
| TR | Turn Release | 把话轮让给对方 |
| TA | Turn Accept | 接受对方让出的 turn |
| ST | Stalling | “嗯……那个……” 这种为了争取思考时间的停顿/填充 |

## 眼睛看哪

| 眼睛看哪 |  |  |
| --- | --- | --- |
| EE_GAZE | EX | EE 看着 EX |
| EE_GAZE | TABLE | EE 看桌面 / 游戏 / shared space |
| EE_GAZE | AWAY | EE 看向上方或旁边 |
| EX_GAZE | EE | EX 看着 EE |
| EX_GAZE | TABLE | EX 看桌面 |
| EX_GAZE | AWAY | EX 看向别处 |

## adaptor

self-adaptor：摸脸、挠头、搓手、手指 fidget、调整坐姿/衣服。

object-adaptor：无关游戏规则地摸、转、摆弄骰子等物体。

_h：hidden，动作发生在 shared space 外，例如桌子下面，对另一个人不可见。

self-adaptor_h = 在桌子下面做了 self-adaptor

## 方向

|  |  |
| --- | --- |
| D | Deictic：纯指向，“这里、那里” |
| DI | Deictic + Iconic：一边指，一边用手形描绘形状/动作 |
| DB | Deictic + Beat：一边指，一边有节奏地敲/强调 |
| DIB | Deictic + Iconic + Beat：三个一起 |

## 理解状态

| EE_UND |  |
| --- | --- |
| UND | EE 自己事后说：当时理解了 |
| PART_UND | 当时只理解了一部分 |
| NON_UND | 当时没理解 |
| MISUND | 当时形成了一个理解，但这个理解是错的 |
