---
title: "Cognitive Robotics - Robot Software"
subtitle: "Programming Robots!"
description: "Introduction to programming of robots"
date: 2024-02-28
author: "UNKNOWN SPACE"
image: ""
tags: ["Cognitive Robotics"]
URL: "/2024/02/28/cognitive-robotics-robot-software/"
categories:  ["notes"]
math: True
---

## Autonomous Robot Workflow
A autonomous robot workflow would be like this: the sensors collect data from the real-world environment, experienced the learning process sensing, reasoning, and acting. Then it give its feedback, doing some movements or actions by sensors.
![alt text](/img/robots/software/image.png)

The code below is a great example, where the first line is getting the information from outside world, and the second line is doing some reasoning, limit the distance, and if the distance is less than 0.3, the actuators stops.
```Python
distance = sensor.get_distance()
if distance < 0.3:
	wheels.stop()
```

## Softbank Pepper Robot
This is a robot developed by a company used for greeting people in scenarios like banking, hotel, etc. It contains many sensors and actuators as you can see from the picture below.
![alt text](/img/robots/software/image-1.png)

## Tools

Now, because we don't want to focus on the basic thing like the code above, we will use middlewares to make the "rules" for our robots. In middleware, both application and hardware elements are considered as "nodes" which are connected by the middleware infrastructure, and each node specifies its inputs and outputs. Nowadays, some middleware that we could use are `ROS`, `YARP`, `NAOqi`, etc. Some of them are following one idea - publisher to subscriber structure. In this structure, publishers publish nodes on topics with some information, and the subscriber receive it from the same topic. Here is a code example:

```Python
## Publisher
import rospy
from std_msgs.msg import String

def talker():
    """
    Publish the message "hello world!"
    """
    pub = rospy.Publisher('chatter-topic'，String, queue_size = 10)
    rospy.init_node('talker')
    rate = rospy.Rate(10) #10hz
    while not rospy.is_shutdown():
        hello_str = "hello world!"
        pub.publish(hello_str)
        rate.sleep()

if __name__ == '__main__':
    talker()
```

```Python
## listener
import rospy
from std_msgs.msg import String

def callback(data):
    """
    Called when receives the message
    """
    rospy.loginfo("I heard: %s", data.data)

def listener():
    """
    Wait until receive the message "hello world!"
    """
    rospy.init_node('listener')
    rospy.Subscriber("chatter-topic", String, callback)
    rospy.spin() # loops until killed

if __name__ == '__main__':
    listener()
```

### (To be continue...)