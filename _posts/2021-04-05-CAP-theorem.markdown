---
layout: post
title:  "The CAP theorem"
description: "cap theorem"
date:   2021-04-05 11:03:42 +0300
categories: jekyll update
---

## What is the CAP theorem all about?
The CAP theorem talks about mainly three properties:
* Consistency
* Availability
* Partition tolerence

The CAP theorem, also known as Brewer's theorem states that for any distributed data store, it is impossible to provide more than two out of the three properties above. For a more detailed description of the CAP theorem, please refer to [Gilbert and Lynch's paper](http://groups.csail.mit.edu/tds/papers/Gilbert/Brewer2.pdf).

### A distributed system
A distributed system may be composed of two or more servers, that keep track of the same variables. These servers can communicate with each other, and with external clients. A server may perform computations upon receiving requests from the client and gives the appropriate response.

Let's now take a look at the three properties:

### Consistency
According to Gilbert and Lynch, Consistency can be best describes as 
> any read operation that begins after a write operation completes must return that value, or the result of a later write operation

If a client writes to one server and the server approves, it will expect the same value from another server in the system upon a read request. However, should a different value other than the most recent be gotten from another server, this is a proof of inconsistency in the system. A consistent system on the other hand will only approve to the client that the value has been changed after updating all the servers in the system with the new value.

### Availability
Here's how Gilbert and Lynch describe Availability
> every request received by a non-failing node in the system must result in a response

For a system to be considered available, if a client sends a request to a server and the server has not crashed, then the server must eventually respond to the client. The server is not allowed to ignore the client's requests.

### Partition Tolerance
Gilbert and Lynch describe Partition tolerance as
> the network will be allowed to lose arbitrarily many messages sent from one node to another

This means that any messages being sent between the servers can be dropped. If all the messages were being dropped, then our system would not show any communications between the servers. For the system to be confirmed as partition tolerant, it needs to work correctly despite the network partitions.

<hr>

A system can not provide all the three properties simultaneously.