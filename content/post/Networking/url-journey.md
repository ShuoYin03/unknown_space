---
title: "Networking - URL Journey From Browser"
subtitle:    "What happen when I search an URL in the browser?"
description: "Describe the process of how a page is display in the browser"
date: 2024-11-07
author: "UNKNOWN SPACE"
image: ""
tags: ["Networking"]
categories: ["notes"]
URL: "/2024/11/07/Networking/url-journey"
draft: False
---

This article will explain the series of processes that occur after a URL is entered 
into a browser and a query is initiated. The content is based on the book How the 
Internet Connects with some additional clarifications and expansions for better 
understanding.

## DNS - From Domain Name to IP Address
When the browser receives a user's URL request, the first step is to resolve the domain 
name into an IP address. This is because domain names are easier for humans to remember 
and are more readable, but computers need IP addresses to identify the location of 
other machines on the network. When we enter a website in the browser and press the 
Enter key, the browser will first call a method named `gethostbyname` from the system's 
`Socket API` (Socket is an interface provided by the operating system for network 
communication. It offers a series of methods for interacting with the network protocol 
stack within the OS). The `gethostbyname` method takes a domain name as a parameter, 
sends a query to the DNS server, and returns the corresponding IP address. (In modern 
systems, this method is gradually being replaced by `getaddrinfo`, which supports a 
wider range of protocols.) The DNS server stores the mappings between domain names 
and IP addresses, and its task is to handle query requests from clients. The query 
parameters typically include three elements:
- Domain
- Class
- Record Type

First, the `Domain` is the parameter we input in the `gethostbyname` method. It is 
important to note that this domain name is not limited to the one we input in the 
browser. It can also include domain names used by services like mail servers (the part 
after the @ symbol). Second, the `Class` parameter is used to identify the type of 
network. Since the Internet is the most commonly used network today, the most typical 
input for this parameter is `IN`, representing the Internet. The third parameter 
indicates the type of data the client wants to retrieve. Here, we will introduce two 
common types: the first is the `A` type, which represents an IP address, the DNS server 
will return the IPv4 address for this type. The second type is the `MX` type used by 
mail servers. In response to this type of query, the DNS server will return the domain 
name of the mail server, its priority, and the corresponding IP address.

However, there are so many IP addresses and domain names globally that no single DNS 
server can handle all the requests worldwide. Therefore, DNS servers are distributed 
across the world.