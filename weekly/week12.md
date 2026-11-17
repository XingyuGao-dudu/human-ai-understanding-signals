## Week 12｜会议总结

- **目前卡住的地方**：已初步梳理 45 篇人–AI 互动文献。心理状态和用户信号的一级分类可以保留，但二级目前更像例子清单。接下来要明确每类状态需要记录哪些字段，以及哪些信号能为这些字段提供证据。

- **先搭建编码框架（coding schema）**：用「状态 → 字段 → 信号 → 采集时机与方法 → 判断依据」逐篇标注。例如，把「用户想达成什么」和「目标完成到哪一步」分开记录；意图和情绪可能随对话变化，需要注明证据对应哪一轮或哪个时点。再跨论文统计哪些信号被反复使用、各自支持什么判断、哪些字段仍缺证据（属性）。

- **补找参考论文**：再找会上提到的、先对记忆相关内容分类再据此设计系统的论文。两类方法参考：一是如何从文献归纳出可逐篇使用的编码框架，二是如何用对话信号逐轮更新用户状态。

- **后续有两个方向，暂未选定**：
  1. **评估框架／benchmark**：用框架评估一批对话和信号数据，看每一轮能判断哪些状态、还缺什么，也可以测试新增一种信号是否有帮助。
  2. **可复用的研究工具**：把反复使用的信号采集方法做成可配置模块，让研究者按自己的问题选择要记录的字段、信号和采集时机。

下一步先把编码框架搭出来，用几篇不同类型的论文试标，再决定后续方向。


## 1 schema搭建方法论
<img width="1626" height="482" alt="image" src="https://github.com/user-attachments/assets/5d4a6ffa-8caa-467e-a88a-ab65332f0e8f" />


用 Noy 与 McGuinness 的七步法搭建概念 schema

1. domain and scope：明确覆盖什么领域、用来做什么、由谁使用和维护。用 competency    questions 写清 schema 应能回答哪些问题，并据此检查是否包含必要的信息

2. 考察现有模型（reuse）：查找已有本体，判断能否直接复用，或经修改、扩展后使用。先看已有定义是否满足需要；如果要与使用同一定义的应用交互，优先考虑复用

3. important terms: 列出需要描述的概念，以及需要说明它们的哪些信息,先尽量列全，暂时保留重叠，也不急于决定哪些术语是类、哪些是属性

4. 定义类和类层级（classes and class hierarchy）可以自顶向下、自底向上，或结合两种方式。    用 is-a 检查层级：如果 A 是 B 的子类，A 的每个实例也必须是 B 的实例

5. 定义属性和关系properties / slots, 明确各类有哪些特征，以及它们与其他类有什么关系。把属性定义在它适用的最上层类，由子类继承.只适用于某个子类的属性，就放在该子类。关系本身也可以有属性；描述的是这次关联的信息，就归到关系上

6. 定义约束（constraints）。 规定属性值的类型（value type）、数量（cardinality），以及属性适用于哪些类（domain）、可指向哪些类（range）。把允许的情况写清楚,还要明确关系两端的对应数量，例如一对一、一对多或多对多

7. 创建并检查实例（instances）。 选定类，创建具体实例，再按约束填写属性。原则：用实例检查结构能否表达实际材料，再用第一步的问题检查信息是否够用。发现缺项或定义不合适，就回到相应步骤修改

### 整体原则

- 同一领域可以有多种合理的建模方式, 用途决定哪些区分值得保留、需要细到什么程度。

- 建模是迭代的。 初版写出来后，用实际实例和预定问题检验，再修订。

- 概念和关系应对应领域中的对象及其联系。 结构要表达清楚这些对象是什么、彼此如何关联

### 参考文献

[1] Natalya F. Noy and Deborah L. McGuinness. 2001. Ontology Development 101: A Guide to Creating Your First Ontology. Technical Report KSL-01-05. Stanford Knowledge Systems Laboratory, Stanford University.<https://protege.stanford.edu/publications/ontology_development/ontology101.pdf>

[2] Peter Pin-Shan Chen. 1976. The entity-relationship model—toward a unified view of data. ACM Trans. Database Syst. 1, 1 (March 1976), 9–36. DOI: 10.1145/320434.320440

## 定义classes and class hierarchy

<img width="1280" height="1273" alt="image" src="https://github.com/user-attachments/assets/d9c44074-b226-420a-ad38-895d893d879f" />


## 定义属性和关系properties / slots+定义约束（constraints）

<img width="1280" height="707" alt="image" src="https://github.com/user-attachments/assets/75219f16-9cf5-4f08-914a-ad590b533855" />


<img width="1280" height="748" alt="image" src="https://github.com/user-attachments/assets/f6454cb0-8237-46fd-9953-733e8a448e4c" />


<img width="1280" height="905" alt="image" src="https://github.com/user-attachments/assets/87a5d420-953c-4e5b-9c3e-5fd23e010d8d" />




## 绘图
<img width="804" height="310" alt="image" src="https://github.com/user-attachments/assets/f20c5069-9eac-4262-bc5e-508f4133b342" />



## 下一步

两种：

1. 做benchmark， schema 分析一批真实人–AI 对话，逐轮看哪些状态能依据现有信号判断、哪些仍缺证据，以及增加一种信号后能多判断什么

2. 做研究工具， 把 mapping 做成开放、可配置的工具，让研究者从想测的心理状态出发，查到该收哪些信号、何时收、用什么作参照
