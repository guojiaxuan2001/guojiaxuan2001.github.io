---
author: ["Kelly"]
title: "网络技术基础"
date: "2019-03-10"
description: "Sample article showcasing basic code syntax and formatting for HTML elements."
summary: "Sample article showcasing basic code syntax and formatting for HTML elements."
tags: ["TCP, IP, HTTP"]
categories: ["themes", "syntax"]
series: ["Themes Guide"]
ShowToc: true
TocOpen: true
---

3网络层、4传输层、7应用层，在系统设计面试中最重要

理解隔层运作原理很关键

最重要的是3（网络层），是IP和InfiniBand等协议所在的层级

4: TCP，UDP

7: HTTP，WebSocket

## Layer 3: Network Layer

### **Internet Protocol (IP)**

为网络节点提供可用的命名方案并实现路由功能

IPv4（对外保证兼容性）

IPv6（对内更现代）

Private Address：其他所有

Public Addresses：通常用于API Gateway, Load Balancers, 以及设计中对外的组件

## Layer 4: Transports Layer

### Protocols

TCP(Default, Reliable): Connection-Oriented, Reliable Delivery, Guaranteed Ordering, Higher Latency, Flow Control/Congestion Control

UDP(Machinegun): Connectionless, No Delivery Guarantee, No Ordering, Lower Latency

有了IP地址，可以向主机发送大数据包/数据块，但缺少：

1.上下文，需要知道数据来自哪个应用，发往哪个应用，一般用端口号解决

2.关心发送顺序和发送成功与否

IP地址没这些功能，所以需要传输协议，如TCP，UDP，QUIC（TCP的现代版本）

### TCP

本质上是在建立序列机制，即给数据包分配序列号

因此如果出现乱序或丢失，发送方和接收方都能知道哪出了问题

（虽然如此，但也只能处理网络上的丢失，比如说你不知道写入磁盘没）

缺点：

吞吐量和延迟

比如丢数据了，TCP必须重传才能继续，如果两台主机距离远，会耗费大量时间

有些应用不需要这种保障，所以UDP游泳

### UDP

只管发，传不传得到无所谓

比如视频会议，丢帧了，无所谓，直接扔了，稳定下音频就继续传输

不必过分纠结每个数据

因此适合实时性应用，或高容错场景（多人游戏，视频会议）

**TCP vs UDP**

当延迟是主要考量，同时可以处理丢包和乱序问题时，才考虑UDP

浏览器原生不支持UDP

## Layer 7: Application Layer

### HTTP

通过纯文本格式的请求响应工作
