---
title: "Cognitive Robotics - Navigation"
subtitle: "Go to the destination!"
description: "Introduction to Robots' motion"
date: 2024-02-19
author: "UNKNOWN SPACE"
image: ""
tags: ["Cognitive Robotics"]
URL: "/2024/02/19/cognitive-robotics-sensors-navigation/"
categories:  ["notes"]
math: True
---

> In this blog, we will discuss about the navigation - how will the robots go the destination we want them to go?

## Navigation
`Navigation`, which in definition it means moving the entire robot from one location to another, this question could also refers to some destination planning. The difference between navigation and manipulation is that, `manipulation` refers to the problems moving body part to
manipulate the environment.

## Locomotion
`Locomotion` are the methods to achieve `navigation`, there are three types of locomotion:
- `Mechanical locomotion`  
Wheels (synchro-drive, omnidirectional wheels)
- `Biomimetic locomotion`  
Crawling, sliding, running
- `Legged locomotion`  
This is a special type of locomotion because we could have multiple states based on how many legs we have(Maybe I got 6). The way to calculate the overall states is by using this equation: $N = (2k-1)!$

## Separate Problems: 4 Key Questions
In robot `navigation`, there are four questions we need to consider:  
1. Where am I going? (and why?) (Mission planning)  
2. What is the best way there? (Path planning)  
3. Where have I been? (Map making (Simultaneous Localization and Mapping))
4. Where am I? (Localization)

We won't go through the first question in this blog, but we will cover some details for the rest of them.

## Path Planning
There are two methods of path planning, `qualitative` path planning and `quantitative` path planning.
1. `Qualitative` path planning (Topological/Route navigation)
- Agent’s perspective
- Topological route with distinctive landmarks
- Topological route with associations (reactive)
- AI search and planning
2. `Quantitative` path planning (Metric navigation)
- Metrics or layout map (bird’s eye view map)
- Orientation- and position-independent

Let's have a look at the following graph:
![alt text](/img/robots/navigation/image.png)
where `distinctive places`(placing landmarks) and `associative methods` are two methods to achieve `qualitative` path planning.

### Distinctive Places (Landmark Methods)
Distinctive places (Landmark methods)

In this method, we choose distinctive features as landmarks which are easy ato recognize, let the robots go to somewhere when or after they 'see' the landmarks. We could choose many different landmarks, some types of landmarks are:
- `Natural` landmark: object or scene
- `Artificial` landmark: sign or visual pattern (e.g. QR-like)
- `Gateway`: landmark to change behavior (e.g. junction)

### Associative Methods
The associative methods refers to some associations between perceptual state and movement. One possible method is `visual homing`, where visual patterns associated with locations/routes. An example could be `bee navigation`, where the bees determines direction and position through the sun, visual landmarks and geomagnetic sensing to achieve effective movement and positioning.

Another possible method is `QualNav`, in this method we infers location from relative positions of landmarks change, such as **constellations**.

## Map Making: Topological Navigation (Relational Graph Methods)
All the other methods mentioned above, we don't have a map for robots to let them know where exactly they are on the map. But now, we are going to take the map into consideration. We represent the world as a relational graph of nodes and edges. `Nodes` represent **gateways, landmarks, or goals**, and edges represent a **navigable path between two nodes**. 

Here we have an example:
![alt text](/img/robots/navigation/image1.png)

And here we have the code to allows it go from R7 to R2:
![alt text](/img/robots/navigation/image2.png)

However, nowadays, we have different expectations for robots - we want them to recognize the environment they located in, without the need of a given map(they still need one!), so they could move in any environment because they are learning through their intelligence. `SLAM`(Simultaneous Localisation and Mapping) algorithm is the method to do this, we will explain it later.

Now, before we look into `SLAM`, let's think about the possible challenges in achieving the effects we described above:
- How can you build the map of a (new) world?
- How do you recognise where you are?
- How can you simultaneously map the world and be sure where you are?
- How do you explore new areas efficiently and consistently?
- How do you label the map with objects and features or terrain?

We will answer them one by one.

## Robot Localization
As the robots still need a map to understand the environment they are in, a wonderful sensor(laser !) which we introduced in the last blog could be used, you could click [here](https://shuoyin03.github.io/2024/02/14/cognitive-robotics-sensors-and-actuators/) to go back. 

After we have the map, we need robots to know where they are, and this need a representation of their current location. The pose $x$ of a robot contains its position $(x, y)$ and a orientation. The math equation is like this:
$$x = (x, y, \theta)^T$$
We use `Bayesian` algorithms to estimate probable location, there are two methods, the first one is `feature-based localization`(Marcov, Extended Kalman Filters) and the other one is `iconic localization`(Monte Carlo localisation / Particles)

### Feature-Based Localization
For this method, we extract features like corners, walls, and doors from raw data and match them to the map efficiently using `Markov localization` and `extended Kalman Filters`.

#### Marcov Localization
Let's have a look at an example first:
![alt text](/img/robots/navigation/image3.png)

In this graph, consider picture a on the top-left corner, the robot is between a door and a wall. The robot extract the features and understand this fact, and now it knows some possible locations it might be in (shown in picture b). After it uses all the information it could use, it moves to find if there are any other features. In this example, the robot moves to a point between door 4 and a wall (shown in picture c). Now, after it extract the information, it clearly knows that it is not possible to be in the location of $X_3$ and $X_4$, because the features and environment doesn't match, therefore now it only has two choices. And then it moves again (picture e), and $X_2$ is filtered and it clearly know its location.

### Extended Kalman Filters
The extended kalman filter's idea is that, after the robot has known all the features of its current location, it predicts what it will see if it moves forward, and it takes difference between the prediction and what it actually senses, to correct/finetune the estimations.

#### Iconic Localization
For this kind of localization method, there is no abstract features but a real image about the environment. It is a grid-based method that the world partitioned into tesselation of convex polygons, we will calculate the likelihood(belief) of all possible poses within each polygon, and for each poses we will add a particle, some particles will “die” if they have a low probability, and the rest of them are the poses that the robot is likely to be in.

Here is an example in youtube. [Iconic localization](https://www.youtube.com/watch?v=qsNGoHi7o2U)

### SLAM (Simultaneous Localization and Mapping)
`SLAM` is a technology that simultaneously localizes and constructs locations at the same time, and is a new environment for exploration. Among them, Rao-Blackwellized Particle Filter is a commonly used calculation method, where each particle has one path diameter and one local area. Every time I look at it, I only update the area that I can sense, and each time I calculate the accuracy of each particle. At the same time, the history of the history of the past use is preserved, and it is convenient to go back and forth. In addition, the Loop closure technology is used to ensure correctness of the layout of the area, and the accuracy of the route information system and the improvement of the area.

Here is a youtube video of an example of `SLAM`, this is the link: [3D Lidar-SLAM With Loop Closure](https://www.youtube.com/watch?v=OV6wNr62nqQ). In this video, when the robot made a circle and rotates back to its original point, the map get updates that it closes the loop.

## Cognitive Navigation
As this series of blog is about cognitive robotics, we will discover some method for robots to "think" using their brain. An obvious disadvantage of the previous methods is, even we have the whole map generated of its current environment, it would be difficult for robots to handle changes in the environment (a car drives away), because a single change will causes the result of "my current location is not the same as what the map says". But cognitive systems are used for handling this situations.

### RatSLAM 
`RatSLAM` simulates the mouse hippocampal system's overall navigation ability, which can also be used in a large-scale military environment. Compared to `SLAM`, the accuracy is low, but the suitability is more flexible, and it can handle complex, noisy input and circumstances. In `ratSLAM`, we will use some cells discovered from rats' brain, they are `place cells`, `head direction cells` and `grid cells`.

#### Place Cell
The `place cells` are used to help rat recognize specific familiar place that it has been to before, this type of cell will fires when rats arrives at the familiar places. The "fire" behaviors are influenced by input from the external environment or events as well as input from the internal path integration system (self-motion). Cognitive maps in the hippocampus are composed of thousands of place cells that cover the surface of space and act as a mapping system to help animals build and maintain cognitive maps of their environment.

#### Head Direction Cell
`Head direction cells` activate when the mouse's head is pointed in a specific direction, and its activity is independent of the animal's body position. All directions are represented by populations of head-direction cells, whose activity forms a map of all possible directions. Tuning curves for head direction cells are shown in polar coordinates, showing that their activity is not related to the path taken by the mouse, but only to the direction of the head.

#### Grid Cell
`Grid cells` are continuously active in a regular pattern across the entire surface of a given environment, similar to place cells but with multiple firing fields. Grid cells activated when the mouse was located at any vertex of a hexagonal pattern in the environment. These cells vary in spacing, phase, and orientation. The activity of grid cells provides signals for measuring displacement distance and direction, thereby forming a metric space.

So, by connecting the SLAM and the different cells we have learned so far, we could know that ratSLAM is the robot navigation and SLAM based on computational models of the hippocampus. It is made up of `pose cells`(analogous to rat’s grid cells), local view cells(interface to the robot’s sensors) and experience map(replaces place cells). Here are some of its characteristics:
- appearance based visual scene matching
- competitive attractor networks
- semi-metric topological map representation

![alt text](/img/robots/navigation/image4.png)

As you can see from the above image, the initial map is similar with the normal SLAM algorithm output, but with the more training process, the map is gradually being concise and accurate.

![alt text](/img/robots/navigation/image5.png)