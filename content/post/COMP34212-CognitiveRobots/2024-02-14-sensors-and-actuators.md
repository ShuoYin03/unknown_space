---
title: "Cognitive Robotics - Sensors and Actuators"
subtitle: "How do they feel?"
description: "Introduction to different sensors and actuators"
date: 2024-02-14
author: "UNKNOWN SPACE"
image: ""
tags: ["Cognitive Robotics"]
URL: "/2024/02/05/cognitive-robotics-sensors-and-actuators/"
categories:  ["notes"]
---

A robot is mainly consist of 4 components, which is:
1. Physical Body
2. Sensors
3. Effectors and actuators 
4. Controller

Here we will mainly talk about `effectors`, `actuators` and `sensors`. 

## Actuators, Effectors and Actions
`Effectors` are any device that can make an effect on the environment, for example, the arms on human body or robot body. And `Actuators` are devices which **enables effectors to execute movements**. For example, muscles and electric motors. Note that one `effector` must have one `actuator` to support it.

A `joint` is an actuator **connecting two effectors**, it can move it more than one direction or method, for example, moving forward, backward, and rotates. We give the above situation a name called `DOF`, stands for **degrees of freedoms**. The formal definition of DOF is that, the dimension in which a movement can be produced in 3D. For a freely attached body in 3D spaces, it could have 6 DOFs, which could be separated into `translational DOF` and `Rotational DOF`.

`Translational DOF` contains movements on x, y and z axis, which is, moving **forward/backward, up/down and left/right**. `Rotational DOF` includes the **rotation from side to side, pitching up and down and turning left or right**. 

It is obvious that not every objects could perform all DOFs due to it constraints. Therefore, there is a definition of `total DOF` and `controllable DOF`, where `total DOF` represents all 6 DOFs and `controllable DOF` only represents those DOF the object could perform. As an example, the `controllable DOF` of a car is only moving forward/backward, and turning left and right.

Based of this theory, we have `total DOF to controllable DOF ratio`. If the `controllable DOF` is exactly `total DOF`, we name it `holonomic`. If the number of controllable DOF is less than total DOF, then we name it `non-holonomic`. And at last, if the number of controllable DOF is greater than total DOF, we call it `redundant`. `Holonomic` and `non-holonomic` are easy to understand, an example of `redundant` is the human arm, it can perform seven DOF, three shoulders and three wrists can both do up/down, side to side, and rotate on their axis, and plus a DOF on the elbow, that’s a total of seven.

There is also definition for active and passive actuation. `Active actuation` is achieved by active actuators, it means to use energies to provide power moving the effectors to a desired location. The safety of robots is a good example, we use software & hardware to control its motor, stop the running when necessary. `Passive actuation` is achieved by effectors, where effectors use no or minimum energy to move, with exploiting body-environment physics interactions. Walking is an example, where we passively use the gravity to move.

## Embodied Intelligence 

The `embodied intelligence` emphasizes the importance of body-environment interactions in the goal of efficient actuation. In robotics, it is reflected in ecological balance of the relation between morphology, materials and control, based on different environments the robots will run on, use different design of the three variables above.

After introducing the basic definitions of actuators, let’s have a look at the different types of actuators. There are four main types of actuators: `electric motors`, `hydraulics`, `pneumatics` and `reactive materials`.

## Electric motors

This is the type of actuator generating power by using electric to rotate motor, there are four main types of electric motors, `DC motors`, `geared motors`, `servo motors` and `stepper motors`. Before introduces each of them, it is necessary to explain some characteristics of electric motors. There are two parameters influence electric motors the most - `torque` and `speed`. 

`Torque` is the rotational force produced in a given distance, and `speed` is the rotational velocity (revolutions per minutes/seconds, rpm/rps). The electric motors can provide two kinds of control to robots’ joint. The first one is `positional control`, the robot drives the motor to provide the power it needs to reach the target position, and if there is an external force, motor will try increase or decrease the power to maintain the position. The second one is `torque control`, which means the motor will maintain the target torque in order to execute unstoppable tasks (holding something).

### DC Motors

The `DC motors` are the most commonly used type of actuator in robotics, it convert electric energy into rotating movements. `Voltage modulation` could produce rotations different speeds and torques. Typically, the speed is between **3000 - 9000 rpm**, which is definitely a high speed, and DC motors produces low torque. 
![alt text](/img/robots/sensors/image.png)

### Geared Motors

`Gear Motors` are usually appear as a system which consist of small and large gears working together to converts the speed and torque of the rotating shaft into slower/stronger movements. If a small gear drives a large one, torque will increase and speed will decrease.

![alt text](/img/robots/sensors/image-1.png)
### Servo Motors

`Servo Motors`, aka Servos, responsible for rotating the shaft to a specific angular position. It contains three components, a DC motor, electronics component to turn the shaft to target position, and potentiometer to sense the current position of the shaft. This kind of motors has high precision because of it will calculate error and adjust position by processing the returned feedback. It is now large used in robots because of its high precision.

### Stepper Motors
The `stepper motors` rotates in specified “steps”, or degrees of rotation, to move the actuator to a desired angular position.

Overall, this type of actuators are simple, cheap and common, however, they produce heat (might influence the system) and they are not that energy efficient.

## Hydraulic and Pneumatic Actuators

The `hydraulic and pneumatic actuators` are the type of actuators that is strong and common in industrial robotics. The principles of it is to use water or air pressure in a tube to produce a linear shrinking or elongation. The Hydraulic actuator could offer a high level of precision for the target position, and pneumatic actuators can model the dynamics of muscles. An example of pneumatic motor is McKibben pneumatic air muscles.

![alt text](/img/robots/sensors/image-2.png)

In the left part of the picture, the pneumatic motor in **relax mode and pressurized mode** is shown, when the muscle is pressurized, it can contract up to about 75% of it's relaxed length.

## Reactive Material Actuators

This type of actuators are made by variety of special materials, e.g. **fabric or polymers and chemical compounds**. The principles of this actuator is to let it react to light, chemical substances, temperature or electric to produce the power or movements the robots need. It is suitable for soft robots.

## Sensors and Perception

`Sensors` are internal or external physical devices use to measure physical quantities, we use `state` (in a `state space`) to describe all possible values or variations of a sensor in both discrete and continuous ways.

![alt text](/img/robots/sensors/image-3.png)

This image shows a robot with **sensors and its state table**. We can see that the robot has two collision sensors, located on the left and right sides of the robot, to detect whether the robot has hit an obstacle. At the same time, the robot also has a battery sensor to monitor the battery power. The battery status can be high or low.

The status table on the right side of the picture lists the possible states of the battery sensor (high or low) and whether the left and right impact sensors are triggered (on or off). Each row in the table represents a specific combination of states that the robot may encounter. **We can use a formula to define the total state of the robot**. For the current robot, it is a combination of the state of the battery sensor and the state of the left and right collision sensors.

In 2007, Mataric describes about "uncertainty" in sensors, which refers to a situation where a robot lacks confidence in its own state and the state of its environment. This uncertainty can be caused by a variety of factors, including but not limited to:

- Sensor noise and errors
- Sensor Limitations
- Sensor calibration issues
- Effector and actuator noise and errors
- Hidden and partially observable states
- Lack of prior knowledge about environment, or dynamic and changing environment

## Levels of Sensory Processing

Based on the easy level to observe different physical parameters, we could separate the levels into low, medium and high, where low levels are usually `electronics` (bump sensor, odometry), medium levels are about `signal processing` (microphone, sonar), and high level are the hardest part, such as `computation` (vision, NLP, map) and `sensors fusion` (multi-modal).

For vision, a parameter classified in high level, could be identified as passive vision and active vision. Passive vision is the bottom-up image-processing approach, and active vision is to use knowledge about task to look for particular stimuli.

## Type of Sensors

`Sensor` could also be classified into passive and active sensors, where passive sensors are just single detectors and active sensors are systems, where emitters produce signals and detector perceives it. Here is a graph showing different `sensors`(devices) and descriptions.
![alt text](/img/robots/sensors/image-4.png)
We will introduce some of them below.

### Switches
A `switch sensor` is a physical device used to detect whether an electrical circuit is open or closed. They function by sensing when electronic circuits are on and off. Switch sensors serve a variety of functions, including contact sensors, limit sensors, and shaft encoders. Among them, collision switches (also called contact switches) are often used to detect whether the body parts of the robot are in contact with external objects, such as triggering corresponding actions when touching an obstacle. They can be mounted on the robot's body or sensory organs, such as whiskers or antennas, to detect contact with the surrounding environment.
![alt text](/img/robots/sensors/image-5.png)
### Light
`Light sensors` can be used to detect the intensity of light in the environment or the reflection of light. Photocell is a common light sensor whose resistance changes with the intensity of light. This kind of sensor is usually used to detect the intensity of light or trigger corresponding actions in dark environments. In addition, there are reflective photoelectric sensors, which detect the reflection of objects by emitting and receiving light signals, and are often used to detect the presence or position of objects.
![alt text](/img/robots/sensors/image-6.png)
### Shaft Encoders
A `shaft encoder` is a sensor used to measure the angle of rotation of a shaft or shaft. They typically use a damaging beam or reflection mechanism to measure the angle or speed of rotation. Shaft encoders are widely used in the field of robotics to measure the angle or position of robot joints to achieve precise control and movement.
![alt text](/img/robots/sensors/image-7.png)
### Sonars
`Sonar` is a sensor that uses sound waves to detect the location of objects. They typically use ultrasonic frequencies and use the time it takes for sound to travel through space to determine the distance to a target. Sonar sensors play an important role in robot navigation and positioning, helping robots to perceive the surrounding environment and navigate and avoid obstacles.
![alt text](/img/robots/sensors/image-8.png)
### Laser/LIDAR
`Lidar` (LIDAR) is a sensor that uses laser beams to scan and measure the surrounding environment. They typically use highly amplified and coherent laser radiation and determine the position and distance of a target by measuring the reflection time or phase change of the beam. LiDAR is widely used in tasks such as navigation, positioning and mapping in the field of robotics.
![alt text](/img/robots/sensors/image-9.png)
### Vision
`Vision sensors` are key components in robots, including 2D cameras and 3D RGB-D cameras. The 3D RGB-D camera uses an infrared light stripe system (random points) and an RGB camera to obtain three-dimensional information of objects. Low-cost products such as Microsoft Kinect and ASUS Xtion have a range of 1.2 meters to 3.5 meters. Now, there are devices such as LeapMotion for gesture control, and DeepPose technology based on RGB images for gesture recognition.
