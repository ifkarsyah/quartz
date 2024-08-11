---
title: "Book Resume: Stream Processing with Apache Flink"
tags:
  - tool/flink
---
file:///Users/ifkarsyah/Documents/7_book/Data%20Streaming/Stream%20Processing%20with%20Apache%20Flink.pdf

Early Apache Flink committers Fabian Hueske and Vasia Kalavri show you how to implement scalable streaming applications with Flink’s DataStream API and continuously run and maintain these applications in operational environments. 
- Learn concepts and challenges of distributed stateful stream processing
- Explore Flink’s system architecture, including its event-time processing mode and fault-tolerance model
- Understand the fundamentals and building blocks of the DataStream API, including its time-based and statefuloperators
- Read data from and write data to external systems with exactly-once consistency
- Deploy and configure Flink clusters
- Operate continuously running streaming applications

This book will teach you everything you need to know about stream processing with Apache Flink. It consists of 11 chapters that hopefully tell a coherent story. While some chapters are descriptive and aim to introduce high-level design concepts, others are more hands-on and contain many code examples.

While we intended for the book to be read in chapter order when we were writing it, readers familiar with a chapter’s content might want to skip it. Others more interested in writing Flink code right away might want to read the practical chapters first. In the following, we briefly describe the contents of each chapter, so you can directly jump to those chapters that interest you most.
- **Chapter 1** gives an overview of stateful stream processing, data processing application architectures, application designs, and the benefits of stream processing over traditional approaches.
- **Chapter 2** discusses the fundamental concepts and challenges of stream processing, independent of Flink.
- **Chapter 3** describes **Flink’s system architecture and internals**. It discusses distributed architecture, time and state handling in streaming applications, and Flink’s fault-tolerance mechanisms
- **Chapter 4** explains how to **set up an environment** to develop and debug Flink applications.
- **Chapter 5** introduces you to the basics of the **Flink’s DataStream API**. You will learn how to implement a DataStream application and which stream transformations, functions, and data types are supported.
- **Chapter 6** discusses the **time-based operators** of the DataStream API. This includes **window** operators and **time-based joins** as well as process functions that provide the most flexibility when dealing with time in streaming applications.
- **Chapter 7** explains how to implement **stateful functions** and discusses everything around this topic, such as the performance, robustness, and evolution of stateful functions. It also shows how to use Flink’s queryable state
- **Chapter 8** presents Flink’s most commonly used source and sink connectors. It discusses Flink’s approach to end-to-end application consistency and how to implement custom connectors to ingest data from and emit data to external systems.
- **Chapter 9** discusses how to **set up Flink clusters** in various environments.
- **Chapter 10** covers operation, monitoring, and maintenance of streaming app that run 24/7.
- Finally, **Chapter 11** contains resources you can use to ask questions, attend Flink-related events, and learn how Flink is currently being used.
## Chapter 1: Introduction to Stateful Stream Processing

In this chapter, we discuss why stateful stream processing is becoming so popular and assess its potential. We start by reviewing conventional data application architectures and point out their limitations.  Next, we introduce application designs based on stateful stream processing that exhibit many interesting characteristics and benefits over traditional approaches. Finally, we briefly discuss the evolution of open source stream processors and help you run a streaming application on a local Flink instance.
### Traditional Data Infrastructures

The traditional architecture that most businesses implement distinguishes two types of data processing: transactional processing(OLTP) and analytical processing(OLAP)

SKIP

### The Evolution of Open Source Stream Processing

Data stream processing is not a novel technology. Some of the first research prototypes and commercial products date back to the late 1990s. However, the growing adoption of stream processing technology in the recent past has been driven to a large extent by the availability of mature open source stream processors.

Open source software is a major driver of this trend, mainly due to two reasons:
1. Open source stream processing software is a commodity that everybody can evaluate and use.
2. Scalable stream processing technology is rapidly maturing and evolving due to the efforts of many open source communities.

We will take a brief look into the past to see where open source stream processing came from and where it is today.

The first generation of distributed open-source stream processors, such as **Apache Storm** (2011), focused on event processing with millisecond latencies and provided guarantees against the loss of events in the case of failures. These systems had rather low-level APIs and did not offer built-in support for accurate and consistent results of streaming applications, as the results were dependent on the timing and order of arriving events.

Improving on the first generation, the next generation of distributed open source stream processors (2013) provided better failure guarantees and ensured that in case of a failure each input record affects the result exactly once. In addition, programming APIs evolved from rather low-level operator interfaces to high-level APIs with more built-in primitives. However, some improvements such as higher throughput and better failure guarantees came at the cost of increasing processing latencies from milliseconds to seconds. Moreover, results were still dependent on timing and order of arriving events.

The third generation of distributed open source stream processors (2015) addressed the dependency of results on the timing and order of arriving events. In combination with exactly-once failure semantics, systems of this generation are the first open source stream processors capable of computing consistent and accurate results. By only computing results based on actual data, these systems are also able to process historical data in the same way as “live” data. Another improvement was the dissolution of the latency/throughput tradeoff. While previous stream processors only provide either high throughput or low latency, systems of the third generation are able to serve both ends of the spectrum. Stream processors of this generation made the lambda architecture obsolete.

### A Quick Look at Flink

Apache Flink is a third-generation distributed stream processor with a competitive feature set. It provides accurate stream processing with high throughput and low latency at scale. In particular, the following features make Flink stand out:
- **Event-time** and **processing-time** semantics. Event-time semantics provide consistent and accurate results despite out-of-order events. Processing-time semantics can be used for applications with very low latency requirements. 
- **Exactly-once** state consistency guarantees. Millisecond latencies while processing millions of events per second. Flink applications can be scaled to run on thousands of cores.
- **Layered APIs** with varying tradeoffs for expressiveness and ease of use. This book covers the DataStream API and process functions, which provide primitives for common stream processing operations, such as windowing and asynchronous operations, and interfaces to precisely control state and time. Flink’s relational APIs, SQL and the LINQ-style Table API, are not discussed in this book.
- **Connectors** to the most commonly used storage systems such as Apache Kafka, Apache Cassandra, Elasticsearch, JDBC, Kinesis, and (distributed) filesystems such as HDFS and S3.
- Ability to **update the application code** and migrate jobs to different Flink clusters **without losing the state** of the application.

In addition to these features, Flink is a very developer-friendly framework due to its easy-to-use APIs. The embedded execution mode starts an application and the whole Flink system in a single JVM process, which can be used to run and debug Flink jobs within an IDE. This feature comes in handy when developing and testing Flink applications.
## Chapter 2: Stream Processing Fundamental

The goal of this chapter is to introduce the fundamental concepts of stream processing and the requirements of its frameworks.

### Introduction to Dataflow Programming

Before we delve into the fundamentals of stream processing, let’s look at the background on dataflow programming and the terminology we will use throughout this book.

### Processing Streams in Parallel

Now that you are familiar with the basics of dataflow programming, it’s time to see how these concepts apply to processing data streams in parallel. But first, let’s define the term data stream: a data stream is a potentially unbounded sequence of events.

Events in a data stream can represent monitoring data, sensor measurements, credit card transactions, weather station observations, online user interactions, web searches, etc. In this section, you are going to learn how to process infinite streams in parallel, using the dataflow programming paradigm.

### Time Semantic

In this section, we introduce time semantics and describe the different notions of time in streaming.
See: [[event-time-vs-processing-time|Event vs. Processing Time]]

### State and Consistency Model

See: [[at-most-once-vs-at-leat-once-vs-exactly-once|At-Most Once vs. At-Least Once vs. Exactly Once]]

## Chapter 3: The Architecture of Apache Flink

Chapter 2 discussed important concepts of distributed stream processing, such as parallelization, time, and state. In this chapter, we give a high-level introduction to Flink’s architecture and describe how Flink addresses the aspects of stream processing we discussed earlier. 

In particular, we explain Flink’s distributed architecture, show how it handles time and state in streaming applications, and discuss its faulttolerance mechanisms. This chapter provides relevant background information to successfully implement and operate advanced streaming applications with Apache Flink. 

It will help you to understand Flink’s internals and to reason about the performance and behavior of streaming applications.

### System Architecture

Flink is a distributed system for stream processing. A Flink setup consists of multiple processes that typically run distributed across multiple machines. Common challenges that distributed systems need to address are allocation and management of compute resources in a cluster, process coordination, durable and highly available data storage, and failure recovery.

Flink does not implement all this functionality by itself. Instead, it focuses on its core function—distributed data stream processing—and leverages existing cluster infrastructure and services. 

Flink is well integrated with cluster resource managers, such as Apache Mesos, YARN, and Kubernetes, but can also be configured to run as a standalone cluster. 

Flink does not provide durable, distributed storage. Instead, it takes advantage of distributed filesystems like HDFS or object stores such as S3. For leader election in highly available setups, Flink depends on Apache ZooKeeper.

In this section, we describe the different components of a Flink setup and how they interact with each other to execute an application. We discuss two different styles of deploying Flink applications and the way each distributes and executes tasks.

#### Components of a Flink Setup

A Flink setup consists of four different components that work together to execute streaming applications. These components are a JobManager, a ResourceManager, a TaskManager, and a Dispatcher. Since Flink is implemented in Java and Scala, all components run on Java Virtual Machines (JVMs). Each component has the following responsibilities:

see: [[flink-architecture]]

### Data Transfer in Flink

### Event-Time Processing

### State Management

### Checkpoints, Savepoints, and State Recovery

### Summary