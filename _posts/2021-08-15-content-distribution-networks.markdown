---
layout: default
title:  "Content Distribution Networks"
date:   2021-08-15 23:34:09 +0300
categories: jekyll update
---

# What is a Content Distribution Network(CDN)?
It is also called a Content Delivery Network.
![CDN-1](/assets/images/CDN-1.png) 
*from https://www.hostucan.com/cdn*

## Terms
- **Origin Server** - An origin server is a computer that runs programs designed to listen to and respond to incoming requests or traffic.
- **CDN Node** - A regional server that sends requests and gets responses from the origin server

## Definitions
1. A Content Delivery Network (CDN) is a geographically distributed network of servers and their data centers that help in content distribution to users with minimal delay.
2. A content delivery network (CDN) refers to a geographically distributed group of servers which work together to provide fast delivery of Internet content.
3. It is a group of distributed servers, networked together, so that they can easily deliver webpages and web content to users whenever they require it.

## How does a CDN work?
The goal of a CDN is to reduce **latency** – the delay between submitting a request for a web page and the web page fully loading on your device – by reducing the physical distance that the request has to travel.

For example, a visitor to Uganda wishing to view content which originates at a US-based server will experience poor loading times if this request has to travel across the Atlantic.

CDNs store a cached version of your website content in multiple geographical locations around the world, which are known as “points of presence” (PoPs). These PoPs will contain their own caching servers and will be responsible for delivering that content in the user’s location.

For most CDNs, when a user makes requests for web pages, each request for content will cause the browser to be mapped to a nearby CDN node(server) and the server will reply with the cached (pre-saved) version of the requested files. If it fails to locate the files, it will look for the content on the other servers in the CDN platform and send the response back to the browser. However, when content is unavailable or stale, the CDN will act as a request proxy to the origin server and store the fetched content to serve future requests.

# Why use CDNs?
* Fast content delivery by minimizing latency. Due to the geographically distributed nature of the CDN, it reduces distance between users and the website resources, meaning faster speed. 
* Reliability. Load balancing distributes network traffic evenly across several servers, making it easier to scale rapid boosts in traffic. In the event that an entire data center is having technical issues, Anycast routing transfers the traffic to another available data center, ensuring that no users lose access to the website.
* Improved security. A CDN can keep a site secured with fresh TLS/SSL certificates which will ensure a high standard of authentication, encryption, and integrity.
* Reduced bandwidth costs. - Every time an origin server responds to a request, bandwidth is consumed. The costs of bandwidth consumption is a major expense for businesses. Through caching and other optimizations, CDNs are able to reduce the amount of data an origin server must provide, thus reducing hosting costs for website owners.

## Examples of CDNs
- Akamai
- CloudFlare
- Cloudinary
- Fastly IO
and others.

There you go! You can now consider using a CDN for your website. Remember, fast content delivery keeps customers while slow content delivery loses customers. 