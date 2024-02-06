---
title: "Cyber Security - Basics"
subtitle: "Security Basics"
description: "Introduced the what threats do we have in the our world, security properties and models"
date: 2024-01-31
author: UNKNOWN SPACE
image: ""
tags: ["Cyber Security"]
categories: ["notes"]
URL: "/2024/01/31/cyber-security-basics/"
---

Currently in our world, there are a huge amount of attacks occurring everyday, bringing unpredictable loss to individuals, organizations or even governments. Such attacks could be: Malware, Ransomware, Adware, Hacking, Spoofing, Phishing, Pharming, DDoS... It is important that we care about security in the development of anything. In definition, there are three aspects in security, which are `confidentiality`, `Integrity` and `Availability`.

## CIA Triad  

1. Confidentiality  
The `confidentiality` contains two definitions, `data confidentiality` and `privacy`. The `data confidentiality` is to ensure data not to be used by unauthorized people, or leaked to other people. The `privacy` is to ensure individuals has the complete control to the data's collection and storage, and they could decide who to leak their data.

2. Integrity  
The `integrity` contains `entity integrity`, `content integrity`, and `origin integrity`. `Entity integrity` ensures that entities in the data indeed possess the claimed identity. The `content integrity` ensures the data is unchanged during transmission, as well as detecting the replayed transmissions. And the `origin integrity` ensures the data source is claimed before.

3. Availability  
As the name saids, the `availability` ensures the data is available to authorized users.

Above are the contents of `CIA`, however, some people think we need more definitions to describe security for a comprehensive description, therefore we have:

4. Freshness  
It ensures data is not a re-transmission from the old ones.

5. Non-repudiation  
It ensures that users can't deny the operations they did in the past. For example, they can not deny they didn't conduct a transaction.

6. Fairness  
It ensures everyone receive nothing or receive the same information that is useful.

Similar to software development, cyber security has its own `life-cycle`, to ensure we are doing the right things on security.

## Security Life-Cycle

The `security Life-Cycle` consist three main parts: 
1. We have to define what kind of protect should we achieve, what kinds of threats should we focus on (`threat analysis`) and what are the specified security policy? .

2. The second step is to design, and implement the method we are going to take to achieve the security goal.

3. By doing some valuation, we access how well does our method achieves the goal to assure the security effects.

Below we will talk about it one by one to go into some details. First of all, let's have a look at what is `threat analysis`.

## Threat Analysis

The `threat analysis` is to identify three things: `assets`, `threats` and `vulnerabilities`. We are going to ask some questions and answer them to get the result. The questions are:

1. What are the assets to protect?
2. What is the value of each asset (to see if it is worth protecting)?
3. What are the threats?
4. Where are they from or how are they mounted?
5. Where are the vulnerabilities? What are the likelihood of their exploitation?
6. Who are the adversaries, and what are their resources?

Remember, not all of the threats worth to be protect, there might be a cost vs benefit trade-off that need to be consider. There is a method to help us doing `threat analysis`, which is `attack tree analysis`.

### Attack Tree Analysis

The `attack tree`, or `threat tree`, is a conceptual tree diagram demonstrating the possible attacking methods. 
![Alt text](/img/cyber-security/basics/image.png)

As we can see from the above example, the `root node` symbolize the attack goal, and it is also the thing we want to prevent. The child nodes are conditions or methods to achieve the attack goal, where we might have a value indicated for each nodes. There are many kinds of values, like likelihood that an attacker will mount the attack, or possibilities of succeeding the attack. All the edges are either 'OR' or 'AND' demonstrating the relationship between nodes, where 'OR' means to use an alternative attack methods, and 'AND' means there are multiple steps required to launch the attack.

Once the `attack tree` is completed, it is better for us to evaluate from any paths on the diagram make decisions on trade-offs.

## Design & Implementation

There are lots of measures we could take to achieve protection goals. 

1. Security Measures  
The `security measures` are used to **mitigate the observed risks**, by using technique measures, procedure measures, recovery measures, etc.

2. Preventive Measures  
`Preventive measures` are methods preventing attacks, for example, we could close vulnerabilities by doing penetration testing and ethical hacking. Or we could make the attacks harder to success by adding access control, firewalls, encryption, digital signatures, etc. And, some tricks might be useful, like adding some Honeypots.

3. Detective Measures
`Detective measures` are methods we take during or after the attacks, like during logging or auditing, or during intrusion detected system.

The above three measures are measures we take to immediately stops the attacks, and below are some other things we care.

1. Response and Recovery  
With `response and recovery`, if the attacks succeeded, we need to take some methods to recover the system, for example, we could use a back-up, or adding more redundancies for the system.

2. Ignore  
In some cases we could just ignore the attacks, do nothing to it.

Notes that, in this stage, as we have the design of specific security measures, we have to consider about the cost-benefit analysis to identify which measures are worth to take and which are not.

## Security Assurance

This is the final stage in a security life-cycle, where we need some standard set up and try to access how well our measures could protect the assets. 

Overall, the deployment of security also has its corresponding cycle. Like software, it is easier and less expensive to consider the security implications into the development process at the beginning than to consider security issues at the end.

## Security Models

In the following blog, we will discuss about different security models, where we will use a model to represent components of security better.

### Distributed System Security Model
![alt text](/img/cyber-security/basics/image-1.png)
This model consist of two roles: clients and servers. These two roles communicate with a network connection. The security issues within this model is that, the channel should be secured. We have to prevent perpetrators on the network to read, copy, alter, or inject messages as they travel across the network and gateways, or to save copies of messages and to replay them at a later time. We should also ask some questions within this model:
1. Could the server be certain about the identity of the principal behind the invocation?
2. Could the client be certain about the invocation response message?
3. Are the messages from the intended server?
4. Has the messages been altered during transit?

### Communication Security Model
![alt text](/img/cyber-security/basics/image-2.png)
This model is aim to protect data over the channel, where we have two communication hosts, sending messages to each other through some encryption & decryption methods. Security questions in this model could be about authenticity (prove the origin of a message + its integrity) and confidentiality.

### Networked System Security Model
![alt text](/img/cyber-security/basics/image-3.png)
Here the focus is on protecting data and services on a network against **external attacks or unauthorized usage**. An complex variable to this model is the **use of mobile devices**, which will make the `boundary`(the boundary of network) hard to define, because mobile devices could connect and disconnect to the network anytime and anywhere, therefore, we need multi-level security measures for protecting both internal and external devices.

### E-commerce Security Model
![alt text](/img/cyber-security/basics/image-4.png)
For this security model we have three roles, `customer`, `merchant` and `TTP`(a trusted third party). Unlike other model which focuses on external attackers, within this model, our 'enemy' is now `misbehaving insider` - it might be **employees, partners, or any other internal participants**. An important concept for this model is that `Non-repudiation service`, which all parties involved in the transaction cannot deny their actions.