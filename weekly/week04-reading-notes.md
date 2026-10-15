# Week4-读书笔记

## 根据人的多模态输入，教AI判断，现在应该继续说，嗯一声，还是轮到AI说话了

Lin et al., ACL 2025 — Predicting Turn-Taking and Backchannel in Human-Machine Conversations Using Linguistic, Acoustic, and Visual Signals。

不是在研究 common ground  <https://aclanthology.org/2025.acl-long.743/>

### 1 研究空白

there is a gap in the research on using linguistic, acoustic, and visual signals to predict turn-taking and backchannel actions accurately.

人说话的时候，AI 要实时做三个选择：

KEEP：人继续说，AI继续听。

BACKCHANNEL：人说，但AI可以“嗯嗯 / I see”一下。

TURN：人说完了，轮到AI正式说

这篇关注：如果同时看用户说了什么 + 怎么说 + 脸上怎么表现，能不能更准地判断这三个时机？

### 2 研究问题及场景

语言、声音和视觉信号结合起来，能不能更准确地预测 AI 什么时候应该继续听、什么时候给 backchannel、什么时候正式接话？

### 3 数据收集

收集网上真实的两人面对面对话视频，最后筛出 773 个视频，然后把每一段对话同时拆成：文字 transcript + 原始声音 + speaker 的脸部视频

然后给每个位置标一个答案：这里应该 KEEP？BACKCHANNEL？还是 TURN？

一句话最后一个词标 TURN；典型 backchannel words 对应 BACKCHANNEL；其他位置标 KEEP，之后又人工检查，自动标注 precision 超过 95%。

作者分别用 GPT-2 提取文字特征、HuBERT 提取声音特征、VideoMAE 提取面部视频特征，再把三种特征输入 multimodal fusion module + classifier，由这个分类模型综合判断当前应该是 KEEP、BACKCHANNEL 还是 TURN

### 4. 实验ablation study

拿已经有正确答案的测试集，给模型 text/audio/video ，模型猜 KEEP / BC / TURN ，看猜得准不准

主要做四组比较：第一组：单独看一种模态的输入，第二组：两两组合，第三组：全部一起

### 5. 怎么分析？

核心看 Accuracy

分别看三个类别猜得准不准？

然后看：只给 text 什么结果？再加 audio？再加 video 有没有进一步提高？

### 6. 结果

1 video 单独不厉害。 只看脸其实远不如 text/audio

2 三种加一起整体最好

3 visual information 确实提供了 text/audio 没有的信息。 作者具体观察到 gaze movement、head motion、expression change 能帮助判断 turn-taking/backchannel

## 人表现出来的 multimodal cues，能不能用来判断 listener 当前到底理解了没有

Türk et al., 2024 — Predictability of Understanding in Explanatory Interactions Based on Multimodal Cues  ACM：<https://dl.acm.org/doi/10.1145/3678957.3685741>

### 1 研究问题

人在听别人解释时，会自然产生 声音、表情、头部、手部和身体动作

研究的是 human-human explanation 能不能根据 listener 的这些 multimodal cues，预测他当前是 Understanding 还是 Non-Understanding？

### 2 实验

使用 MUNDEX 中的 21 段 human-human explanation：一个真人 explainer 负责解释，另一个真人 explainee/listener 负责听。

对话结束后，listener 自己回看刚才的录像，指出：这里我当时 understood或did not understand，给研究者提供“正确答案”。 然后：listener 当时的 multimodal behavior+listener 自己标的 Understanding / Non-Understandin用来训练和测试 Random Forest

### 3 结果

（1）可以一定程度区分 Understanding 和 Non-Understanding，说明人的自然 multimodal behavior 里面确实包含 understanding information

（2）不是某一个 signal 单独决定， vocalization、facial expression、head、hand、torso 等不同 modality 都对 prediction 有贡献

（3）但效果还不稳定，作者明确说 data sparsity + individual variation 很严重，所以结果目前不能很好 generalize 到所有人

## 用人的自然面部反应，帮助机器人判断自己是不是出错了，并更早进入 error management

Stiber et al., HRI 2023 — On Using Social Signals to Enable Flexible Error-Aware HRI

ACM：<https://dl.acm.org/doi/10.1145/3568162.3576990>

### 1 研究问题

现有 robot error detection 通常依赖两种方式：用户明确说“你错了”，系统根据规则判断机器人有没有偏离任务，但这两种方法要么慢，要么很依赖具体任务。

人看到机器人出错后会自然出现 facial reactions，这些 social signals 能不能帮助机器人更早、更灵活地发现自己出错？

### 2 原型

作者用摄像头拍用户的脸，再用 OpenFace 提取 17 个 Facial Action Units，例如眉毛、眼睛、嘴角、下巴等脸部动作强度。然后：Human facial AUs - Neural Network - ERROR / NO ERROR

最后实现了一个实时 error-aware robot system：人的面部反应- 检测可能出错- 机器人询问用户确认 -verbal acknowledgement - 执行预先写好的 recovery

### 3 实验

三个HRI 场景，包括协作搭 PVC 管、cooking 和 Programming by Demonstration，故意让机器人出错，机器人犯错时摄像头持续记录用户的脸。两个独立 coder 之后看录像，标出：robot error 什么时候开始，用户什么时候开始出现 visible reaction，用户什么时候恢复正常

然后作者拿：用户当时的标签，训练 neural network，让模型学习：什么样的面部反应通常出现在机器人犯错以后cross-task test：用一种场景训练，再去其他场景测试，看这种方法能不能跨任务使用

### 4 结果

（1）机器人出错后，人确实经常自然露出反应

（2）这些 facial AUs 可以被模型用于 error detection，说明人的自然 social reaction 确实能成为机器人判断错误的额外信息来源；但跨不同任务后性能会下降，仍存在漏检

（3）人的脸通常比人明确开口报告错误更早暴露问题。 在 HRC-A 场景中，social signals 可以比用户明确报告错误提前发现问题

（4）但 facial signal 不能单独可靠使用，因为人可能不反应，也可能只是因为其他原因有表情。因此作者的系统把它和 explicit user report + domain-specific information 一起使用

## 用用户的 speech 和 facial expression 判断用户情绪状态，并生成具有共情能力的 AI grounding response

Arjmand et al., CHI 2024 — Empathic Grounding: Explorations using Multimodal Interaction and Large Language Models with Conversational Agents

ACM：

<https://doi.org/10.1145/3652988.3673949>
