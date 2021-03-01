---
author: jfcorugedo
title: Reactive applications with Spring Webflux
featimg: 3.jpg
tags: [reactive,spring,webflux]
category: [programming]
---
## Reactive programming model
<p>
There have been a long time since the [Reactive Manifesto](https://www.reactivemanifesto.org/) was written in 2013.
</p>
<p>
Since then, we have seen how the topic of Reactive becomes more and more important.
</p>
<p>
Only five years ago it was quite difficult to find someone putting in producction a reactive application. 
</p>
<p>
Spring Boot was the king in the Java microservice landscape and Java 8 was the brand-new version of this language. A version full of new features, some of them was going to produce a hugh change inside our traditional programming model.
</p>
<p>
Nowadays everyone has heard about Reactive, and a lot of people are working with reactive frameworks:
[Micronaut](https://micronaut.io/), [Quarkus](https://quarkus.io/), [Spring Webflux](https://docs.spring.io/spring-framework/docs/current/reference/html/web-reactive.html#webflux), [Akka](https://doc.akka.io/docs/akka/current/index.html), etc...
</p>

### Why does Reactive become so popular?

<p>
Long time ago, it was completely normal to build applications that would only ever run on a single computer, a single CPU. 
</p>
<p>
If an application wasn’t fast enough, the standard response would be to wait for a while for CPUs to get faster; no need to change any code. Problem solved.
</p>
<p>
More and better hardware was the standard way to scale software.
</p>
<p>
Unfortunately, in the last 10 years this situation has changed a lot. 
</p>
<p>
A limit to increasing CPU clock speeds has been reached. The dream was over.
</p>

![complexity vs resources](../img/complexityVsResources.png)

<p>
If applications need to perform faster, or if they need to support more users, they will have to be **concurrent**.
</p>
<p>
We need a new programming model that let us do a better use of our resources.
</p>

### What does Reactive really mean?

<p>
Reactive is a set of design principles for creating cohesive systems. It’s a way of thinking about systems architecture and design in a distributed environment where implementation techniques, tooling, and design patterns are components of a larger whole.
</p>
<p>
In this post we are going to focus on one of the aspects in a Reactive System: *Reactive Programming*.
</p>
<p>
This technique is based on the concept where the availability of new information drives the logic forward rather than having control flow driven by a thread-of-execution.
</p>
<p>
Interesting... but what does it really mean?
</p>
<p>
Let's take a look at these two images:
</p>

![Blocking vs Reactive](../img/blockingVsReactive.png)

<p>
The diagram on the left shows a traditional application, where the thread is blocked all the time. Only when an answerd has been generated then the thread can be released.
</p>
<p>
On the other hand, the diagram on the right shows a non-blocking application, where each thread is released without waiting for an answer.
</p>
<p>
In both cases, the answer takes the same time to be delivered to the caller. However, from the point of view of the resources, the non-blocking approach is much better.
</p>
<p>
We can use the threads and the CPU to do other stuff while we are waiting for someone else to answer us. For example, there is no point in having a thread waiting for the response of an HTTP request. Instead of that, we can release the thread so it can handle other tasks. When the data arrives, we can pickup a thread to process it.
</p>
<p>
That is what `availability of new information drives the logic` means. Only when the data is ready we are going to allocate resources to process it.
</p>
<p>
This is by far, a smarter approach to deal with a lot of technical tasks we need to deal with during the execution of our application.
</p>
