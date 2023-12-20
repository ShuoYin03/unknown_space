---
title:      "GreatUniHack2023 - Postscript to the competition"
subtitle:   "Thoughts and reflections after the 24-hour hackathon"
description: "Just conducted a 24-hour hackathon. This chapter is about my feelings about participating in the hackathon, as well as the shortcomings discovered and the skills that need to be improved in the future."
date:       2023-10-31T12:00:00
author: UNKNOWN SPACE
URL:        "/2023/11/03/greatunihack2023/"
tags:       ["Hackathon"]
categories: ["post"]
---

<!-- >刚刚进行了一场时长24小时的hackathon，本章作为此次参加hackathon的感受，以及发现的不足和以后需要提高的技能。 -->
>Just conducted a 24-hour hackathon. This chapter is about my feelings about participating in the hackathon, as well as the shortcomings discovered and the skills that need to be improved in the future.

<!--more-->
## GreatUniHack 2023

This event provided a variety of challenges, with education, climate, and sustainable development as the main three themes, and gave a variety of technology-related challenges (using LLM technology, streamlit framework, mongoDB, etc.). The contestants were developed in units of 4 people. We chose education as the theme to develop an online battle game. The battle method is to use your own miscellaneous knowledge to answer questions to gain points and win. In order to take into account the team's technical level and familiar language, we used python's flask framework and React framework as the front-end and back-end, mongoDB as the database, and WebSocket as the way for players to connect. The logic of the project is that after confirming that the player is successfully connected, the front end initiates a request to read the problem to the back end. The back end initiates a read to the database and returns the result. After the front end calculates the result and obtains the winning player, it initiates a request to the back end to improve the win. The player's ladder score and the request to reduce the failed player's score, from which the round of the game ends.

<!-- 此次活动提供了多种挑战，以教育，气候，以及可持续发展作为主要三大主题，并且给予了多种技术相关的挑战（运用LLM技术，streamlit框架，mongoDB等等）。参赛选手以4人为单位进行开发，我们选取了教育作为主题，开发一个在线对战游戏，对战方式是运用自己的杂学知识来进行答题从而获得分数，赢取胜利。为了照顾到团队的技术水平以及熟悉的语言，我们使用了python的flask框架和React框架作为前后端，使用mongoDB作为数据库，以及使用WebSocket作为玩家连接的方式。项目的逻辑是在确认玩家成功连接之后，由前端对后端发起读取问题的请求，后端向数据库发起读取并返回结果，在前端计算结果得到获胜的玩家之后，向后端发起提高获胜玩家的天梯分数并减少失败玩家的分数的请求，自此一轮游戏结束。 -->

Due to time, the overall level of the team, and my unfamiliarity with WebSocket technology, we met lots of troubles during adding the function of matching games. We also encountered many problems in other aspects such as front-end and back-end data transmission, front-end interface structure and the use of flask. After summarizing, the following points need to be improved:

<!-- 由于时间，团队的整体水平以及本人对WebSocket的技术并不熟悉，我们并未成功加入匹配游戏的功能。我们在其他的例如前后端的数据传输，前端的界面结构以及flask的使用上也遇到了诸多问题。总结过后需要提升的为以下几点： -->

1. Need to have a better understanding of the basic project structure of a website, and must be familiar with front-end and back-end data transmission, the use of routing, and issues such as database creation, connection, and table creation.
2. Try to unify the team's coding style. If time does not allow, try to write comments (I am surprised that none of the four members of our team have the habit of writing comments, which causes a lot of trouble for development)
3. Clarify the division of labor and the specific functions of the project before starting the project. Do not have a step-by-step mentality, which can easily lead to the project progress getting out of control and the final result being chaos.

<!-- 1. 需要对一个网站基本的项目结构更加了解，要熟悉前后端的数据传输，路由的使用以及数据库从创建，连接到建表等问题
2. 尽量对团队的代码风格进行统一，如果时间不允许，尽量编写注释（很惊讶我们团队四个人都没有写注释的习惯，这对开发造成了不小的困扰）
3. 明确分工，在进行项目之前明确项目的具体功能，不要抱着走一步看一步的心态，容易导致项目进度失去控制，最后一片混乱的结果 -->

postscript:

<!-- 附言： -->

This article commemorates the site’s first blog

<!-- 以此文章纪念站点的第一篇博客 -->


