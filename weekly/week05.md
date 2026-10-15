# Week5

| State | Verbal | Prosody | Head | Gaze | Face/Eye |
| --- | --- | --- | --- | --- | --- |
| UND | backchannel | pitch | nod | gaze variation | blink |
| PART_UND | ... | ... | ... | ... | ... |
| NON_UND | ... | ... | ... | ... | ... |
| MISUND | ... | ... | ... | ... | ... |

## IDEA1

RQ1： 在实时 Human–AI conversation 中，哪些 multimodal cues 能有效反映用户当前state of understanding(Understanding，Partial Understanding，Non-Understanding，Misunderstanding）？【已找到，需要进一步整理】

> RQ1： 在实时 Human–AI conversation …
> 高星宇 8月27日 22:17
> 看看数据：提炼出 codebook(不需要真实数据）但是 rq2,需要真实数据，使用真实数据集，验证一下！

RQ2：AI 如何利用这些 multimodal cues，比仅使用 transcript 更准确地识别用户的 state of understanding？

RQ3：当 AI 根据识别到的 state of understanding 进行 adaptive repair 时，是否能够改善后续 grounding 和 common-ground outcome？

🎁 1 从已有数据和论文确定 human signals:整理哪些 signal 对判断哪些 state 有证据 从别人的数据集里扒

> 1 从已有数据和论文确定 human signals:…
> 高星宇 8月27日 22:11
> 提炼出有因果效应的 labels
>
> 高星宇 8月27日 22:16
> 再看看 data,完整的 data,再标注。
>
> 高星宇 8月27日 22:20
> gap
>
> 高星宇 8月27日 22:21
> 确认：哪些数据集可以用，mapping 到底如何建立（不用到标数据这步）

2 AI 可以采取什么 repair strategies ：AI有什么repair行为或者cues(别人做了什么，我们如何设计）

3 建立 人signal组合 - 人state - AI repair mapping

> 建立 人signal组合 - 人state - AI repair m…
> 高星宇 8月27日 22:23
> 是否有现有文献在做这样的 merge，如果有，就可以这样造数据，
>
> 高星宇 8月27日 22:24
> 可能构建好数据集已经是一个贡献
>
> 高星宇 8月27日 22:43
> 9.18.晚上 10 点

4 做能执行这套 mapping 的 Human–AI demo

5 实验验证是否真的优于普通 AI

(1)主要用 MUNDEX，先确定我们要哪些 signal：有理解状态的答案，也有非常多signal

(2)再看其他 dataset 能不能“补 MUNDEX 缺的 signal”

|  |  |
| --- | --- |
| WEEK5 | MUNDEX（最符合我们的，有数据集，但是没有raw video之类的，官网写的用户隐私不公布）、MM-F2F（只是列出了cues没有说明这些cue和理解状态的关系）、NoXi（需要申请权限） |
| WEEK6 | （1）先把每个 dataset 到底有什么搞清楚，再统一成同一套 signal taxonomy，把不同叫法对齐，看哪些 signals 可以真正使用，（2）梳理AI repair行为有哪些，别人怎么设计的，想想我们怎么设计 |
| WEEK7（9.10投递CHI） |  |
| WEEK8（9.14-9.20） | 构建我们自己的table:哪些 human grounding signals，或者哪些 signal combinations，对判断人的 understanding state 有用？ |
|  |  |
|  |  |

## 怎么开发demo

1 收集人的 signals —确定用哪些工具提取用户的xxx信号？

2 判断 tentative understanding state - 判断understanding state怎么实现？

3 根据 mapping 选择 repair strategy

4 LLM 按这个 strategy 生成回答

## IDEA2-CSCW

📍 1 formative study ：

发现问题。真实 interaction evidence：发现 older / younger adults 的真实 breakdown repair patterns

把问题变成design goals, 让用户参与决定 AI 应该如何承担 repair

> IDEA2-CSCW
> 高星宇 8月27日 22:29
> （1）有没有其他为 group 设计的适应性 interface (2) 为什么要选择 aging,为什么要考虑老年人
>
> 高星宇 8月27日 22:35
> 语音界面设计
>
> 高星宇 8月27日 22:37
> 使用语音试试，写个 script，模拟自己是老人，研究健康问题，一个说话，一个打字，看看会不会不一样。以往文献从人的角度，这篇从技术角度（或许是设计本身带来了 bias）
>
> 高星宇 8月27日 22:42
> 是否只定在语音模态？故事一开始得搭起来。如果语音模态：那就得说明，语音被验证可以给 xx 群体比较好，但,,,。或者:老年人对 AIxxx 与年轻人不一样的。

2 设计并开发Adaptive AI system：验证 adaptive AI 是否减少 breakdown 和 repair burden

older adults 遇到 breakdown 后，会自己做很多 repair：重复、换说法、补充信息、自我纠正，甚至借助家人、日程、环境线索来把对话拉回来；但很多 repair 还是失败，因为系统的 dialogue flow 太 rigid

(1)问题

找到一篇HRI，不同年龄人群如何看breakdwon的paper,但是没发表？

https://doi.org/10.3389/frobt.2022.956709

（2）老年人的对话特点

https://doi.org/10.1145/3498366.3505830

（2）参考范式

https://pi.cs.tsinghua.edu.cn/wp-content/uploads/2024/10/3678516.pdf
