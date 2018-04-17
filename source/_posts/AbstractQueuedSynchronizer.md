---
title: AbstractQueuedSynchronizer
date: 2018-04-17 14:30:38
tags:
---
# java concurrent 代码分析之 Condtion

条件变量的出现是为了更精细控制线程等待与唤醒，在Java5之前，线程的等待与唤醒依靠的是Object对象的wait()和notify()/notifyAll()方法，这样的处理不够精细。

通熟易懂的说，就是消费者/生产者的场景中，在原来的基础上，增加了队列满时及时通知消费者，队列空时及时通知生产者的优化，通常是两个条件变量一起出现，一个控制值，但两个条件变量可以毫无关系，终归来说还是在Lock的范围内。所以，从本质上来说，是对Object监视器的场景性优化，而不是全新机制的引入。


使用场景：生成消费者，生产者await当队列满的时候，consumer await当 队列空的时候


可以   Reentrantlock queueLock;  full= queueLock.newCondition ,empty=queueLock.newCondition  自动释放lock



java concurrent 代码分析之 ReentrantLock 本质上和synchronized 方法和语句块 没有区别，只是可扩展性好些

