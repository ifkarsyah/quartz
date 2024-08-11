---
title: Flink History
tags:
  - content-type/history
  - tool/flink
  - component/stream-processing
---
[[tool/overview/flink|Apache Flink]]'s history is rooted in academic research and has evolved into a prominent open-source [[stream-processing | stream processing]] framework widely used in the industry. Here's a timeline of key events in Flink's development:

A decade ago, I stumbled upon an intriguing big data project called [Stratosphere](http://stratosphere.eu/). What immediately captured my interest was a particular section in its introduction: the ability to initiate a cluster on a single machine and execute MapReduce-based `WordCount` computations with just 3 lines of code! During a time dominated by Hadoop, installing and running a `WordCount` program would typically require several hours or even days. 

Therefore, encountering a project that achieved the same functionality in merely three lines of code left an indelible impression on me. Motivated by this concise yet powerful approach, I delved extensively into the project and eventually became a contributor.
### Early Beginnings (2008–2013)
**Flink** began as a research project called **Stratosphere** at the **Technical University of Berlin**.   Stratosphere project motivation was to address several limitations and challenges in existing big data processing systems including:
- **Gap in Unified Processing**: At the time, there was a clear distinction between batch processing systems (like Apache Hadoop) and stream processing systems (like Apache Storm). These systems were often used separately, requiring different architectures, APIs, and infrastructures. The Stratosphere project aimed to create a unified framework that could handle both batch and stream processing seamlessly, allowing developers to work with a single system for different types of data workloads.

### Apache Incubation (2014–2015)

- **2014**: Stratosphere entered the Apache Software Foundation (ASF) as an incubator project, and the name was changed to Apache Flink. The goal was to become a fully-fledged, open-source stream processing framework under the Apache umbrella.
- **December 2014**: Apache Flink graduated from the Apache Incubator, becoming a top-level project. This marked a significant milestone, demonstrating the project's maturity and the community's commitment to its success.

### Growth and Adoption (2015–2017)

- **2015**: Flink gained recognition for its robust stream processing capabilities, offering features like stateful stream processing, exactly-once semantics, and event time processing. It began to compete with other big data processing frameworks like Apache Spark and Apache Storm.
- **2016**: Flink's first major release (Flink 1.0) introduced support for complex event processing (CEP) and enhanced the framework's API for both batch and stream processing. This release solidified Flink's position as a leading stream processing engine.
- **2017**: Companies like Alibaba, Uber, and Netflix began adopting Flink for real-time data processing, contributing to its growing popularity in the industry. The community continued to expand, with more contributors and a wider range of use cases.

### Innovation and Industry Impact (2018–2020)

- **2018**: Flink 1.4 introduced features like distributed state management and improved fault tolerance. The community also focused on enhancing the framework's scalability and performance for large-scale deployments.
- **2019**: Apache Flink continued to evolve with the release of Flink 1.8, which brought improvements in state management, dynamic scaling, and better integration with popular data storage systems like Apache Kafka and Apache Hadoop.
- **2020**: Flink's capabilities in streaming SQL were significantly enhanced, making it easier for users to query streaming data with SQL-like syntax. This was a key factor in Flink's adoption by enterprises looking to leverage real-time analytics.

### Modern Developments (2021–Present)

- **2021**: Flink introduced support for native Kubernetes deployments, reflecting the industry's shift towards containerized environments and cloud-native applications. This release also focused on improving the user experience, making it easier to develop, deploy, and manage Flink applications.
- **2022**: The community continued to innovate with features like Stateful Functions, which enabled stateful processing at scale in serverless environments. Flink's role in real-time data processing pipelines became even more prominent.
- **2023**: Apache Flink remains a leading framework for real-time stream processing, with a vibrant community and widespread adoption across various industries, including e-commerce, finance, telecommunications, and more.

References:
- https://alibabatech.medium.com/a-flink-series-from-the-alibaba-tech-team-b8b5539fdc70
- https://hackernoon.com/a-brief-history-of-flink-tracing-the-big-data-engines-open-source-development-87464fd19e0f
- https://hackernoon.com/in-search-of-data-dominance-spark-versus-flink-45cefb28f377
- https://hackernoon.com/flink-or-flunk-why-ele-me-is-developing-a-taste-for-apache-flink-7d2a74e4d6c0
- https://betterprogramming.pub/start-your-stream-processing-journey-with-just-4-lines-of-code-5863573268b9
- Introduction to Apache Flink Book