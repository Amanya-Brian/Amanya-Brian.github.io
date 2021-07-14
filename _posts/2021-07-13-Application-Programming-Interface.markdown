---
layout: default
title:  "Application Programming Interface"
date:   2021-07-13 19:51:18 +0300
categories: jekyll update
---

# What is an API?
An API in full form is an Application Programming Interface, and it allows two applications to talk to each other. It is a set of functions and procedures that allow for the creation of applications that access data and features of other applications, services, or operating systems.

![API demo](/assets/images/API.png)                                           
*adopted from apifriends.com*

# Understanding an API
Think about the applications that you use every day. We have web and mobile applications that are designed for humans to use, while APIs are designed for other digital systems and applications to use. Websites and APIs both do the same things, like return data, content, images, video, and other information. But APIs don’t return all the details that are needed to make things look pretty for the human eye—you only get the raw data and other machine-readable information needed behind the scenes to put the resources being delivered to work, with very little assistance from a human.

# How an API works
Practically, imagine you’re sitting at a table in a restaurant with a menu. The kitchen is the part of the “system” that will prepare your order. What is missing is that link to communicate your order to the kitchen and return your food back to your table. That’s where the waiter or API comes in. The waiter is the messenger – or API – that takes your order and tells the kitchen – the system – what to do. Then the waiter delivers the response back to you; in this case, it is the food.

# Let's look at the common uses of APIs
* They are behind most web applications
* They are used in most mobile applications
* They connect devices to the internet
* They power desktop applications
* APIs define the networks—or the information passed between applications, systems, and devices

# Why should you use an API?
* Integration with internal and external systems  by allowing two systems to communicate with each other
* Adding or enhancing functionality fo existing systems, both internal and external
* Speeding up software and systems development by allowing front end and backend teams to work in parallel
* Reducing software development costs by allowing sectors accross an organization to use the same API to access data
* Enhancing organizational security by requiring authorization before accessing services
* Enabling mobile applications by allowing users to obtain data from a database onto their screens

# API Architecture
There are different styles of API architecture, some currently used while some are obsolete.
- REST APIs, REST in full is REpresentational State Transfer. These rely on clients-server structure, stateless operations and more.
- Webhooks, which are also called 'reverse APIs' as a concept for checking changes in data. The are event based and automatically send messages from one application to another once an event occurs.
- SOAP APIs, SOAP stands for Simple Object Access Protocol. These are more structured and formalized than other APIs. They are very reliable but tend to be slower than other APIs.
- GraphQL APIs, GraphQL is an acronym for Graph Query Language. The Graph Query Language defines how one API asks another API for information rather than relying on how the server defines the endpoint.
- WebSocket API, these depend on the WebSocket computer communications protocol, a full-duplex communication channel over a single TCP connection. Compare WebSocket protocol to HTTP (HyperText Transfer Protocol), which is a half-duplex communication. WebSocket APIs provide a standard way for servers to send information and data to clients, even when the client is not requesting data. WebSocket APIs allow data to be communicated between clients and servers, while keeping connections open.
- Server-sent event API, Server-Sent Events, also known as SSE, is a technology that relies on data being sent from the server. This allows a client to receive updates automatically via a HTTP connection.
And many others.

# Disadvantages of using APIs
- It sometimes takes time to understand and integrate an API into an existing system. Developing APIs is also a time consuming process.
- There is lack of documentation especially for the consummers of the APIs who don't understand to the core how an API works.
- Implementation of APIs can be very complicated though the concept seems to be quite simple.
- Many consumers of APIs have very little knowledge on how the APIs work and their various features.

And that is it! I hope you now have a general understanding of APIs and how they work. 