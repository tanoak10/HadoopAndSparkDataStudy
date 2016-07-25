# 3.Hadoop与Spark的区别

##概述

&#160; &#160; &#160; &#160;谈到大数据，相信大家对Hadoop和Apache Spark这两个名字并不陌生。但我们往往对它们的理解只是提留在字面上，并没有对它们进行深入的思考，下面不妨跟我一块看下它们究竟有什么异同。

##解决问题的层面不一样

&#160; &#160; &#160; &#160;首先，Hadoop和Apache Spark两者都是大数据框架，但是各自存在的目的不尽相同。Hadoop实质上更多是一个分布式数据基础设施: 它将巨大的数据集分派到一个由普通计算机组成的集群中的多个节点进行存储，意味着您不需要购买和维护昂贵的服务器硬件。

&#160; &#160; &#160; &#160;同时，Hadoop还会索引和跟踪这些数据，让大数据处理和分析效率达到前所未有的高度。Spark，则是那么一个专门用来对那些分布式存储的大数据进行处理的工具，它并不会进行分布式数据的存储。

##两者可合可分

&#160; &#160; &#160; &#160;Hadoop除了提供为大家所共识的HDFS分布式数据存储功能之外，还提供了叫做MapReduce的数据处理功能。所以这里我们完全可以抛开Spark，使用Hadoop自身的MapReduce来完成数据的处理。

&#160; &#160; &#160; &#160;相反，Spark也不是非要依附在Hadoop身上才能生存。但如上所述，毕竟它没有提供文件管理系统，所以，它必须和其他的分布式文件系统进行集 成才能运作。这里我们可以选择Hadoop的HDFS,也可以选择其他的基于云的数据系统平台。但Spark默认来说还是被用在Hadoop上面的，毕 竟，大家都认为它们的结合是最好的。

以下是天地会珠海分舵从网上摘录的对MapReduce的最简洁明了的解析:

我们要数图书馆中的所有书。你数1号书架，我数2号书架。这就是“Map”。我们人越多，数书就更快。

现在我们到一起，把所有人的统计数加在一起。这就是“Reduce”。

##Spark数据处理速度秒杀MapReduce

&#160; &#160; &#160; &#160;Spark因为其处理数据的方式不一样，会比MapReduce快上很多。MapReduce是分步对数据进行处理的: ”从集群中读取数据，进行一次处理，将结果写到集群，从集群中读取更新后的数据，进行下一次的处理，将结果写到集群，等等…“ Booz Allen Hamilton的数据科学家Kirk Borne如此解析。

&#160; &#160; &#160; &#160;反观Spark，它会在内存中以接近“实时”的时间完成所有的数据分析：“从集群中读取数据，完成所有必须的分析处理，将结果写回集群，完成，” Born说道。Spark的批处理速度比MapReduce快近10倍，内存中的数据分析速度则快近100倍。

&#160; &#160; &#160; &#160;如果需要处理的数据和结果需求大部分情况下是静态的，且你也有耐心等待批处理的完成的话，MapReduce的处理方式也是完全可以接受的。

&#160; &#160; &#160; &#160;但如果你需要对流数据进行分析，比如那些来自于工厂的传感器收集回来的数据，又或者说你的应用是需要多重数据处理的，那么你也许更应该使用Spark进行处理。

&#160; &#160; &#160; &#160;大部分机器学习算法都是需要多重数据处理的。此外，通常会用到Spark的应用场景有以下方面：实时的市场活动，在线产品推荐，网络安全分析，机器日记监控等。

##灾难恢复

&#160; &#160; &#160; &#160;两者的灾难恢复方式迥异，但是都很不错。因为Hadoop将每次处理后的数据都写入到磁盘上，所以其天生就能很有弹性的对系统错误进行处理。

&#160; &#160; &#160; &#160;Spark的数据对象存储在分布于数据集群中的叫做弹性分布式数据集(RDD: Resilient Distributed Dataset)中。“这些数据对象既可以放在内存，也可以放在磁盘，所以RDD同样也可以提供完成的灾难恢复功能，”Borne指出。