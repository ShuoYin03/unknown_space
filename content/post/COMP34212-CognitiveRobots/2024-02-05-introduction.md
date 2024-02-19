---
title: "Cognitive Robotics - Introduction"
subtitle: "Can they understand?"
description: "Introduction to some basics definitions"
date: 2024-02-05
author: "UNKNOWN SPACE"
image: ""
tags: ["Cognitive Robotics"]
URL: "/2024/02/05/cognitive-robotics-introduction/"
categories:  ["notes"]
---

## What are Robots?

A `robot`, is a machine capable of carrying out a complex series of actions automatically, especially one programmable by a computer. Also, it could be described as an autonomous system which exists in the physical world, can sense its environment, and can act on it to achieve some goals. There are many types of robots that we define today. For example, they are:
- Humanoid
- Android
- Biomimetic
- Industrial (manipulation, navigation)
- Medical
- Assistive

### Humanoid Robots
A `humanoid robot` has an `anthropomorphic` body plan and actuators with `human-like senses` for human-robot interaction. For example, a `humanoid robot` could contains **a head, two legs, two arms and a torso**, and it contains **cameras, microphones, and touch sensors** to simulate humans' five senses. 

### Android Robots
An `android robot` is intentionally designed with the goal of being human-like and **indistinguishable from humans** in its external appearance and behavior, the difference between `android robots` and `humanoid robots` is that humanoid robots keeps the external appearance of a robot, which is distinguishable from human beings.

Note that there is a theory related to `android robots`, which is `uncanny valley`. It describes that humans affinity significantly reduced for robots that are similar but slightly different from real people. This is also the reason why we feeling scary to some human-like products. The following graph represents the `uncanny valley` in a data perspective.
![alt text](/img/robots/introduction/image.png)

### Biomimetic Robots
A `biomimetic robot` has an `animal-like` (humans, animals, plants) body plan and actuators, used to **exploit biological structures and mechanisms**.

### Industrial Robots (Manipulation & Navigation)
As the name describes, `industrial robots` are used in factories for manufacturing tasks, or, used for logistics centres, (semi)autonomous flying, and autonomous vehicles.

## What is Cognition?

`Cognition` is the process by which an `autonomous system` perceives its environment, learns from experience, anticipates the outcome of events, acts to pursue goals, and adapts to changing circumstances. The `cognition` could be defined as many stages, the following image could describe cognition by a cycle of `anticipation`:
![alt text](/img/robots/introduction/image-2.png)

If we want to develop some cognitive robotics robots, we have to make some sense of abstraction, for example, an abstraction of movement, because we can not abstract everything. Here we have `Marr's Levels of Abstraction`, proposed by `David Marr`, is a framework for understanding how information processing systems, particularly in the context of vision and perception, operate at different levels of abstraction. There are three levels of abstraction, which are:
1. Computational / theory  
This is the highest level of Marr's framework, where we focuses on define the problem, arise questions like what should the system does and why does it does it.
2. Representation / algorithmic
This level mainly focuses on the specific methods and strategies for solving the problem, it also defines how the information processes in the system.
3. Implementation
This is the most concrete level in Marr's framework, it deals with physical realization of the system, including hardware, neural mechanisms, or any other physical substrate.
![alt text](/img/robots/introduction/image-1.png)

## What is cognitive robotics?

In definition, `cognitive robotics` combines insights and methods from AI, as well as `cognitive` and `biological` sciences, to perform the design of `sensorimotor` and `cognitive capabilities` in `intelligent robots`(Engineering approach to the design of intelligent capabilities
in robots using any Artificial Intelligence methods). For all the normal robots, it is easy if we `pre-programmed` the robots so they can memorize dictionaries and achieve some goal in communicating with human beings, however, they are **not able to understand the language** they use.

Here we also have a definition for `artificial cognitive systems`, as it is use to design a cognitive robotics robot, by using the modelling of simulated and embodied/robotic agents taking inspiration from natural and cognitive systems.

There are four approaches to implement cognitive robotics, which is `developmental robotics` (Cangelosi & Schlesinger 2015), `evolutionary robotics` (Nolfi & Floreano 2002), `swarm Robotics` (Dorigo et al. 2014; Hamann 2018), and `soft Robotics` (Laschi et al. 2016; Veri et al. 2015).

## Developmental Robotics

`Developmental Robotics` is the **interdisciplinary approach** to the autonomous design of behavioral and cognitive capabilities in artificial agents (robots) that takes **direct inspiration from the developmental principles and mechanisms observed in natural cognitive systems**.

There are few principles to consider while designing the developmental robotics. They are:
1. Dynamical System
2. Phylogenetic & Ontogenetic Interaction
3. Embodied & Situated Development
4. Intrinsic Motivation and Social Learning
5. Nonlinear, Stage-Like Development
6. Online Open-Ended Cumulative Learning

### Dynamical System
`Dynamical system` emphasizes the role of dynamic systems in `self-organization` and `emergence`. It describes the `decentralized nature` of a system, that is, the system consists of many interacting parts, and the interaction between these parts produces the behavior and structure of the whole. This self-organizing nature leads to the `multicausality`, and when they develops over time they **nested at different time scales**.

Child development is a great example of dynamical system, the picture blow demonstrate a child who is learning walking.
![alt text](/img/robots/introduction/image-3.png)

### Evolution & Learning
For `evolution` and `learning`, evolution involves the evolution of species, known as `phylogeny`, which affects the basic design and structure of robots. Development then involves the process of growth and development of an individual, known as ontogeny, including aspects such as maturation and critical periods. Finally, learning refers to the robot gradually improving and optimizing its behavior and capabilities through interaction with the environment and accumulation of experience. These processes interact to shape the robot's behavior and intelligence.

### Embodied & Situated
`Embodiment` refers to robots learning and adapting through the interaction of their body, brain, and environment. `Situation` refers to the robot learning and acting in specific environments and situations, including the robot's unique model of the world, morphological computation, and understanding of the basis of language. These concepts emphasize the close connection between the robot and its environment and guide the robot to learn and act in real environments.

### Intrinsic Motivation & Social Learning
In this part, `intrinsic motivation` involves factors that drive a robot from within, such as curiosity, a sense of wonder, seeking novelty, values, and motivations. `Social learning` and imitation involve robots learning by observing and imitating the behavior of others. These concepts emphasize the importance of the intrinsic dynamics of robot learning and social interaction for its development and progress.

### Non Linear, Stage Development
`Stage development` refers to that, the development of a child (or robot) is separated into stages and we could observe milestones within the stage. In Piaget's `genetic epistemology theory`, there are four stages in total, they are: 
1. Sensorimotor stage: Birth to 2 years
2. Preoperational stage: Ages 2 to 7
3. Concrete operational stage: Ages 7 to 11
4. Formal operational stage: Ages 12 and up

Detailed information for Piaget's theory could be find here: [Piaget's 4 Stages of Cognitive Development Explained](https://www.verywellmind.com/piagets-stages-of-cognitive-development-2795457).

Note that the development of children will be show in a data perspective in a U-shape, look at the following graph.
![alt text](/img/robots/introduction/image-4.png)
The chart on the left shows an infant's cumulative vocabulary growth as he ages. We can see from the figure that the growth of vocabulary is not a straight line, but a step-like curve, which shows that the growth rate of infant vocabulary is significantly different in different time periods. The picture on the right represents the U-shaped development phenomenon in language acquisition. This refers to a typical phenomenon when children acquire certain grammatical structures during the language learning process, especially when children learn a second language. At first, children may intuitively use the correct form (for example, using the past tense of the irregular verb "spoke"). Then as time goes by and the rules of grammar are learned, they may overgeneralize the rules, mistakenly creating forms like "spoken" (this is wrong because they are trying to apply the past tense construction of regular verbs to something other than regular verbs). Eventually, with more learning and revision, they will use the correct form again (using "spoke" again). This process presents a U-shaped curve, from correct to incorrect, and then to correct again.

### Online, Open Ended, Cumulative
This part emphasizes the importance of online learning, which means that learning is an ongoing process that can occur at any time. Furthermore, cumulative learning means that knowledge and experience are gradually accumulated, resulting in a deeper and richer understanding. This learning style also spans different modes of perception and cognitive domains, promoting cognitive enlightenment and development.