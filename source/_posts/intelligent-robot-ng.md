# 下一代智能机器人

# 机器人领域的几大主要问题

## **移动问题**

<iframe src="//player.bilibili.com/player.html?aid=229074474&bvid=BV1Lh411c7U6&cid=1142206842&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"
width="100%" height="600" > </iframe> 


![Untitled](intelligent-robot-ng/Untitled.png)

**BD：足式机器人运动能力代表**


![Untitled](intelligent-robot-ng/Untitled%201.png)

Legged Robot SOTA

<iframe src="//player.bilibili.com/player.html?aid=529099665&bvid=BV1gu411s7Kd&cid=1142207713&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"
width="100%" height="600" > </iframe> 


## 操作问题

基于传统工业机械臂的产线，生产制造已趋于成熟。近年技术上部分创业公司加入了视觉识别实现部分智能化任务。但总体来讲，只是让以前机器人继续做机器人“擅长”的事，同时加了一点task oriented “AI调料”。

![Untitled](intelligent-robot-ng/Untitled%202.png)

说到中下游，不得不提日本还有家叫Mujin的公司

![Untitled](intelligent-robot-ng/Untitled%203.png)

A Controversy

![Untitled](intelligent-robot-ng/Untitled%204.png)

![Untitled](intelligent-robot-ng/Untitled%205.png)

对于机械臂而言，造车容易开门难，借用克里顿选举的话：It's the AI, stupid 😀

## **智能理解与语义任务规划**

其实问题都集中在目前机器人的智能无法应对复杂多变且颇具语义的现实环境，而目前用的基本都是heuristic的方法或者hard coding。

[https://io-intelligence.feishu.cn/space/api/box/stream/download/asynccode/?code=MzQzYWQwZjU3ZmIzNTM1NTdiM2Y2YWUyYjc1MzFlODZfRUFGY0V6S29Sa21TOW5SdGZLa2VWd0xndm1BajN2bGVfVG9rZW46Ym94Y240TnZQVXhMUWRJS3BJVTBGdk9rWXllXzE2ODUwNjUwMzE6MTY4NTA2ODYzMV9WNA](https://io-intelligence.feishu.cn/space/api/box/stream/download/asynccode/?code=MzQzYWQwZjU3ZmIzNTM1NTdiM2Y2YWUyYjc1MzFlODZfRUFGY0V6S29Sa21TOW5SdGZLa2VWd0xndm1BajN2bGVfVG9rZW46Ym94Y240TnZQVXhMUWRJS3BJVTBGdk9rWXllXzE2ODUwNjUwMzE6MTY4NTA2ODYzMV9WNA)

## **PDDL**

![Untitled](intelligent-robot-ng/Untitled%206.png)

过去研究人员建立了一套完整的逻辑方法，甚至编程语言来解决任务规划的问题，但这里面需要大量的专业人员的人工工作，需要对场景（domain），逻辑语义（logistics）以及机器人的能力进行编程设计。并且，该方法并不具备场景的泛化性，也就是这间屋子可以用，那间可能就不能用了。

# **从最新研报窥视当下机器人行业发展及相关技术**

![Untitled](intelligent-robot-ng/Untitled%207.png)

2023年初，工信部《机器人+》明确行业政策重点领域：

1）**经济发展（生产力端）**：制造业、农业、建筑、能源、商贸物流

2）**社会民生（消费端）**：医疗健康、养老服务、教育、商业社区服务、安全应急以及极限特种环境

## ****生产力机器人代表：工业机械臂（协作机械臂）、仓储机器人、商用清洁机器人****

![Untitled](intelligent-robot-ng/Untitled%208.png)

![Untitled](intelligent-robot-ng/Untitled%209.png)

![Untitled](intelligent-robot-ng/Untitled%2010.png)

![Untitled](intelligent-robot-ng/Untitled%2011.png)

![Untitled](intelligent-robot-ng/Untitled%2012.png)

## ****消费端机器人代表：扫地、割草、泳池****

![Untitled](intelligent-robot-ng/Untitled%2013.png)

![Untitled](intelligent-robot-ng/Untitled%2014.png)

## **人形机器人**

![Untitled](intelligent-robot-ng/Untitled%2015.png)

# **大规模语言模型掀起的变革**

## Transfomer(Google research 2017)

- Vaswani, Ashish, et al. "Attention is all you need." *Advances in neural information processing systems* 30 (2017).

![Untitled](intelligent-robot-ng/Untitled%2016.png)

正如其题目所言，自从attension这个概念提出以后，CNN、RNN这些网络结构已经从各个方法证明都是attention的一个子集。

## **Openai的GPT1-3 再到chatgpt(instructgpt)**

![Untitled](intelligent-robot-ng/Untitled%2017.png)

GPT1 ： 分为两步，首先使用无标注数据训练一个语言模型，而后在下游具体任务的有标签数据集上进行fine-tune

**从此以后力大砖飞（模型大小和数据大小指数上升）**

GPT2：  GPT-2模型依旧使用Transformer模型的decoder，但相比于GPT-1，数据和模型参数（1.5B）变得更大，大约是之前的10倍，主打zero-shot任务，一个模型对应多个任务（不再分别fine-tune）。其学习目标是使用无监督的预训练模型做有监督的任务。

GPT3 ： GPT-3结构和GPT-2一样，但是数据（45TB，维基百科的全部数据只相当于其中的 0.6%）约为GPT-2的1000倍，用了网络公益的[common crawl data](https://commoncrawl.org/)，模型参数约为GPT-2的100倍(175B)。

**Instructgpt:**

![Untitled](intelligent-robot-ng/Untitled%2018.png)

![Untitled](intelligent-robot-ng/Untitled%2019.png)

对于分别两个模型的优化函数：

![Untitled](intelligent-robot-ng/Untitled%2020.png)

![Untitled](intelligent-robot-ng/Untitled%2021.png)

Chartgpt能解决啥我就不再过多赘述了，相信大家已经听的天花乱坠了

# **机器人认知、逻辑解决的可能性**

**更关注的是这一轮LLM AI的突破在机器人能带来什么Insights**

Suppose之前机器人在家里要做一些实际的事情需要有什么预先工作呢
首先需要人为定义domain，即场景：

```c++
(define (domain blocksworld)
  (:requirements :strips :equality)
  (:predicates (clear ?x)
               (on-table ?x)
               (arm-empty)
               (holding ?x)
               (on ?x ?y))

  (:action pickup
    :parameters (?ob)
    :precondition (and (clear ?ob) (on-table ?ob) (arm-empty))
    :effect (and (holding ?ob) (not (clear ?ob)) (not (on-table ?ob))
                 (not (arm-empty))))

  (:action putdown
    :parameters  (?ob)
    :precondition (and (holding ?ob))
    :effect (and (clear ?ob) (arm-empty) (on-table ?ob)
                 (not (holding ?ob))))

  (:action stack
    :parameters  (?ob ?underob)
    :precondition (and  (clear ?underob) (holding ?ob))
    :effect (and (arm-empty) (clear ?ob) (on ?ob ?underob)
                 (not (clear ?underob)) (not (holding ?ob))))

  (:action unstack
    :parameters  (?ob ?underob)
    :precondition (and (on ?ob ?underob) (clear ?ob) (arm-empty))
    :effect (and (holding ?ob) (clear ?underob)
                 (not (on ?ob ?underob)) (not (clear ?ob)) (not (arm-empty))))) 
```

接下来人为定义problem，即状态和任务：

```c
`(define (problem pb2)
   (:domain blocksworld)
   (:objects a b)
   (:init
     (on-table a)
     (on b a)
     (clear b)
     (arm-empty))
   (:goal (on a b)))`
```

接下来便是放入pddl解析器进行求解，这是最简单的场景，就是把物块b放到a上

**目前我们判断chartgpt基本具备解决这个问题的能力，且颇具泛化性**

![Untitled](intelligent-robot-ng/Untitled%2022.png)

![Untitled](intelligent-robot-ng/Untitled%2023.png)

# **关注科技大厂们最新动态**

最“早”是google的工作saycan（2022.8）、rt1（2022.12）以及最新的rossie（2023.2），最近的是微软上个月刚发表的robot chatgpt（2023.2），nvidia的VIMA(2022.10)。

## **Microsoft(2023.02)**

最为简单的方法，直接利用Chatgpt进行原子动作api的映射。
微软的方案是使用LLM规划出一条完整的原子动作序列后，就直接按顺序去执行。
那该如何处理需要重新规划时的情况呢？他们利用了ChatGPT强大的多轮对话能力，能够在用户的帮助下纠正不理想的行为。
此外，基于ChatGPT的coding能力，模型给出的输出，不再是原子动作的名字序列，而可以是一段完整的可运行的代码，代码中甚至可以调用一些感知和运动规划接口（如opencv，ompl），使机器人更加自动化地完成整个任务。

![Untitled](intelligent-robot-ng/Untitled%2024.png)

![Untitled](intelligent-robot-ng/Untitled%2025.png)

![Untitled](intelligent-robot-ng/Untitled%2026.png)

## **Nvidia(2022.10)**

Nividia的方案VIMA (Visuomotor Attention Model)：通过使用多模态的方式定义任务，扩充了机器人可以完成任务的范围，模型的通用性更强，与用户的交互也更加多样有趣。

通过图像+文本 (+视频) 的多模态prompts，在定义任务时，可以用图像替代掉某些文本信息。机器人可以完成这样的任务：

- 使环境改变为 ***{某种图示状态}***
- 使 ***{某个物品}*** 模仿 ***{视频输入的（若干帧图像）运动}***（one-shot learning）
- 学会一些新的 ***{图像}*** 和名称标签之间的关系，并完成新任务
- 在一些 ***{位置约束}*** 下完成某些任务

![Untitled](intelligent-robot-ng/Untitled%2027.png)

## **Google(2022.08、2022.12、2023.2）**

Sayca

![Untitled](intelligent-robot-ng/Untitled%2028.png)

![Untitled](intelligent-robot-ng/Untitled%2029.png)

<iframe src="//player.bilibili.com/player.html?aid=996615483&bvid=BV1ps4y1B7EG&cid=1142205886&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"
width="100%" height="600" > </iframe>


![Untitled](intelligent-robot-ng/Untitled%2030.png)

# **接下来最重要的是**

Under shi's command:

1. Data(first for game, then for robotics cognition) the fuel of future Ai

ref： https://www.thepaper.cn/newsDetail_forward_22641064

a. For game, motion, fight, 定制化较强，数量不多，经常雇人自己采集（2w/天）

b. For academic， 大量，科研数据，精确准确

c. For Robotics，  大量示教数据，最好不需要mapping， for motion：精确控制， for manipulation：逻辑理解

Advantage: 机器人data需要人力采集，网络无法爬取。

Threat： 人力活儿，印度、越南？

1. Software(simulator+cad)

a. AI生成第一版产品构型，urdf等等

b. 替代供应链，推动产业上下游化，集成各种各样上游关节模组、减速机、电机、控制器、传感器等到软件中，创建一个给工程师的零部件平台（仿真环境），保证仿真即所得

1. Affordable robot arm

a. 家用机械臂价格得在1w以内，可以牺牲一部分的精度，但需要力传感，安全保障

b. Peak材料以塑带钢（铝）可能是一个promising的解决方案，打工成本直线下降

1. Humanoid

a. 政策好，但不看好短期商业化的可行性

b. To humanoid的关键上游(关节，灵巧手，数据以及相应的软硬件)倒是布局的好时候

c. RL based, real motion data based humanoid control；believed rrto be the key to locomotion problem