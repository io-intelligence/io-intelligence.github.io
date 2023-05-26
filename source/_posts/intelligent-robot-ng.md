---
title: Next Generation Intelligent Robots
date: 2023-05-26 18:00:00
tags:
---

______________________________________________

## Major issues in robotics

### Robot locomotion problem

<iframe src="//player.bilibili.com/player.html?aid=229074474&bvid=BV1Lh411c7U6&cid=1142206842&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"
width="100%" height="600" > </iframe> 

![image_0](intelligent-robot-ng/image_0.png)

**BD：Representation of Locomotion Ability for Legged Robots**


![image_1](intelligent-robot-ng/image_1.png)

**Legged Robot SOTA**

<iframe src="//player.bilibili.com/player.html?aid=529099665&bvid=BV1gu411s7Kd&cid=1142207713&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"
width="100%" height="600" > </iframe> 

## Robot manipulation problem

The production line based on traditional industrial robotic arms has become mature. In recent years, some startup companies have introduced vision recognition technology to achieve partially intelligent tasks. However, overall, it is still just letting robots do what they are good at, with a little bit of task-oriented AI added as a seasoning.

![image_2](intelligent-robot-ng/image_2.png)

When it comes to the mid-to-low-end market, we have to mention a company in Japan called Mujin.

![image_3](intelligent-robot-ng/image_3.png)

A Controversy

![image_5](intelligent-robot-ng/image_5.png)

For robotic arms, it's easier to build a car than to open a door. To borrow a phrase from the Clinton campaign, 'It's the AI, stupid. 😀

### Intelligent Understanding and Semantic Task Planning

The problem actually lies in the fact that current robots cannot cope with complex, dynamic and semantically rich real-world environments. The methods currently being used are mostly heuristic or hard-coded.

![image_31](intelligent-robot-ng/image_31.png)

### PDDL

![image_6](intelligent-robot-ng/image_6.png)

In the past, researchers have developed a complete logical method and even programming languages to solve the problem of task planning. However, this requires a lot of manual work from professionals to program and design the scenes (domain), logical semantics (logistics), and robot capabilities. Moreover, this method does not have the generality of scenes, meaning that what works in one room may not work in another.

## Peeking into the current development and related technologies of the robotics industry through the latest research report

![image_7](intelligent-robot-ng/image_7.png)

At the beginning of 2023, the Ministry of Industry and Information Technology's "Robot+" has identified key policy areas in the robotics industry:

1. Economic development (production end): manufacturing, agriculture, construction, energy, commercial logistics.
2. Social livelihood (consumer end): medical health, elderly care services, education, commercial community services, safety and emergency, as well as extreme and special environments.

### Representatives of productivity robots include: industrial robotic arms (collaborative robotic arms), warehousing robots, and commercial cleaning robots.

![image_8](intelligent-robot-ng/image_8.png)

<table>
  <tr>
    <td><img src="/intelligent-robot-ng/image_9.png"></td>
    <td><img src="/intelligent-robot-ng/image_10.png"></td>
  </tr>
</table>

<table>
  <tr>
    <td><img src="/intelligent-robot-ng/image_11.png"></td>
    <td><img src="/intelligent-robot-ng/image_12.png"></td>
  </tr>
</table>

### Representatives of consumer-end robots include: floor-sweeping robots, lawn-mowing robots, and pool-cleaning robots

![image_13](intelligent-robot-ng/image_13.png)

![image_14](intelligent-robot-ng/image_14.png)

### Humanoid Robot

![image_15](intelligent-robot-ng/image_15.png)

## The revolution sparked by large-scale language models.

### Transfomer(Google research 2017)

- Vaswani, Ashish, et al. "Attention is all you need." *Advances in neural information processing systems* 30 (2017).

![image_16](intelligent-robot-ng/image_16.png)

As the title suggests, since the concept of attention was introduced, CNN and RNN network structures have been demonstrated to be subsets of attention in various methods.

### GPT1-3 to ChatGPT(InstructGPT)

![image_17](intelligent-robot-ng/image_17.png)

GPT-1: It consists of two steps. First, an unsupervised language model is trained using unlabeled data, and then fine-tuning is carried out on a downstream specific task's labeled dataset

**From then on, models and data sizes increased exponentially, leading to a significant increase in computing power requirements.**

GPT-2: The GPT-2 model still uses the Transformer model's decoder, but compared to GPT-1, the amount of data and model parameters (1.5B) have become larger, approximately 10 times larger than before. It focuses on zero-shot tasks, where a single model can perform multiple tasks without separate fine-tuning. The learning objective is to use unsupervised pre-training models for supervised tasks.

GPT-3: The structure of GPT-3 is the same as GPT-2, but the data (45TB, equivalent to only 0.6% of all Wikipedia data) is about 1000 times larger than GPT-2, and uses the Common Crawl data from the Internet Archive. The model parameters are about 100 times larger than GPT-2 (175B)

**InstructGPT:**

<table>
  <tr>
    <td><img src="/intelligent-robot-ng/image_18.png"></td>
    <td><img src="/intelligent-robot-ng/image_19.png"></td>
  </tr>
</table>

The optimization functions are different for the two models:

![image_20](intelligent-robot-ng/image_20.png)

![image_21](intelligent-robot-ng/image_21.png)

I won't go into too much detail about what ChartGPT can solve, as I believe many of you have already heard about its impressive capabilities.

## The possibilities of robot cognition and logical problem-solving

**What is more important is what insights this breakthrough in LLM AI can bring to robotics**

If a robot needs to perform practical tasks at home, what kind of preparatory work is required beforehand? First, a domain needs to be defined manually, i.e. the scene:

```lisp
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

Next, the problem needs to be defined manually, i.e. the state and task:

```lisp
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

Next, we put it into a PDDL parser for solving. This is the simplest scenario, which is to put object B on top of object A.

**At present, we believe that ChartGPT has the ability to solve this problem and has good generalization ability.**

<table>
  <tr>
    <td><img src="/intelligent-robot-ng/image_22.png"></td>
    <td><img src="/intelligent-robot-ng/image_23.png"></td>
  </tr>
</table>

## Latest developments from major tech companies

The earliest works were Google's SayCAM (August 2022), RT1 (December 2022), and the latest Rossie (February 2023). The most recent one is Microsoft's Robot ChartGPT (February 2023), and Nvidia's VIMA (October 2022).

### Microsoft(2023.02)

The simplest method is to directly map atomic action APIs using ChatGPT. Microsoft's approach is to use LLM to plan a complete sequence of atomic actions, which are then executed in order. How do they handle situations that require re-planning? They leverage ChatGPT's powerful multi-turn dialogue ability to correct undesirable behavior with the help of the user.

In addition, based on ChatGPT's coding ability, the output provided by the model is no longer just a sequence of atomic action names, but can be a complete and executable code block, which can even call some perception and motion planning interfaces (such as OpenCV and OMPL), allowing the robot to complete the entire task more automatically.

![image_24](intelligent-robot-ng/image_24.png)

![image_25](intelligent-robot-ng/image_25.png)

![image_26](intelligent-robot-ng/image_26.png)

### Nvidia(2022.10)

- Nvidia's VIMA (Visuomotor Attention Model) approach: by defining tasks in a multi-modal way, the range of tasks that robots can complete is expanded, making the model more versatile and the interaction with users more diverse and interesting.

  Through multi-modal prompts using images, text, and sometimes videos, certain text information can be replaced by images when defining tasks. The robot can then complete tasks such as:

  - Changing the environment to a ***{certain visual state}***
  - Making ***{a certain object}*** imitate ***{a motion in a video input (several frames of images)}*** (one-shot learning)
  - Learning the relationship between new ***{images}*** and their label names, and completing new tasks
  - Completing certain tasks under some ***{position constraints}***

![image_27](intelligent-robot-ng/image_27.png)

### Google(2022.08、2022.12、2023.2）

Saycan

![image_28](intelligent-robot-ng/image_28.png)

![image_29](intelligent-robot-ng/image_29.png)

<iframe src="//player.bilibili.com/player.html?aid=996615483&bvid=BV1ps4y1B7EG&cid=1142205886&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"
width="100%" height="600" > </iframe>

![image_30](intelligent-robot-ng/image_30.png)

## The most important thing next is...

1.Data (first for gaming, then for robotics cognition) is the fuel for future AI.

Ref: https://www.thepaper.cn/newsDetail_forward_22641064

  a. For gaming, motion, and fighting, the data is highly customized, not very abundant, and often collected by hiring people themselves (20,000 per day).

  b. For academic research, there is a large quantity of precise and accurate data.

  c. For robotics, a large amount of teaching data is needed, preferably without the need for mapping. For motion: precise control; for manipulation: logical understanding.

Advantage: Robot data needs to be collected by humans, and cannot be crawled from the internet.

Threat: Labor-intensive work, India, Vietnam?

2.Software (simulator + CAD)

  a. AI generates the first version of product configuration, such as URDF.

  b. Replaces the supply chain and promotes the upstream and downstream of the industry, integrating various upstream joint modules, reducers, motors, controllers, sensors, etc. into the software, creating a component platform (simulation environment) for engineers, ensuring simulation is the same as reality.

3.Affordable robot arm

  a. The price of a household robot arm must be within 10,000 yuan, and a portion of accuracy can be sacrificed, but force sensing and safety guarantees are needed.

  b. Peak materials such as plastic strips and steel (aluminum) may be a promising solution, with decreasing labor costs.

4.Humanoid

  a. Policies are good, but the feasibility of short-term commercialization is not optimistic.

  b. The key upstream components (joints, dexterous hands, data, and corresponding software and hardware) for humanoid robots are well-positioned.

  c. RL-based and real-motion-data-based humanoid control is believed to be the key to solving the locomotion problem."
