Repository dedicated to Kappa Architecture. I collect and publish articles, tutorials, talks, projects and examples related to Kappa Architecture.

## What is Kappa Architecture?

Kappa Architecture is a software architecture pattern. Rather than using a relational DB like SQL or a key-value store like Cassandra, the canonical data store in a Kappa Architecture system is an append-only immutable log. From the log, data is streamed through a computational system and fed into auxiliary stores for serving.

Kappa Architecture is a simplification of [Lambda Architecture](https://en.wikipedia.org/wiki/Lambda_architecture). A Kappa Architecture system is like a Lambda Architecture system with the batch processing system removed. To replace batch processing, data is simply fed through the streaming system quickly.

## But why?

Kappa Architecture revolutionizes database migrations and reorganizations: just delete your serving layer database and populate a new copy from the canonical store! Since there is no batch processing layer, only one set of code needs to be maintained.

## Says who?

The idea of Kappa Architecture was first described in an [article](https://www.oreilly.com/ideas/questioning-the-lambda-architecture) by [Jay Kreps](https://www.linkedin.com/in/jaykreps) from LinkedIn. Then came the talk ["Turning the database inside out with Apache Samza"](https://www.youtube.com/watch?v=fU9hR3kiOK0) by [Martin Kleppmann](https://martin.kleppmann.com) at 2014 [StrangeLoop](https://thestrangeloop.com) which inspired this web site.

### Turning the database inside out with Apache Samza

<iframe width="560" height="315" src="//www.youtube.com/embed/fU9hR3kiOK0" frameborder="0" allowfullscreen></iframe>

### How do I make my own?

<iframe width="560" height="315" src="//www.youtube.com/embed/kyu8RY5NO3w" frameborder="0" allowfullscreen></iframe>

### Resources

* [Questioning the Lambda Architecture](https://www.oreilly.com/ideas/questioning-the-lambda-architecture)
* [Apache Kafka and the Next 700 Stream Processing Systems](https://www.youtube.com/watch?v=9RMOc0SwRro)
* Article by Jay Kreps: [The Log: What every software engineer should know about real-time data's unifying abstraction](https://engineering.linkedin.com/distributed-systems/log-what-every-software-engineer-should-know-about-real-time-datas-unifying)
* Presentation: [Discovering Kappa Architecture the hard way](https://novoj.github.io/reveal.js/kappa-architecture.html#/)
* Linux Foundation Presentation: [Kappa Architecture: Our Experience](https://events.linuxfoundation.org/sites/events/files/slides/ASPgems%20-%20Kappa%20Architecture.pdf)
* [Liquid: Unifying Nearline and Offline Big Data Integration](https://web.archive.org/web/20160324171136/http://www.cidrdb.org/cidr2015/Papers/CIDR15_Paper25u.pdf) (Summary of Liquid paper can be found [here](https://blog.acolyer.org/2015/02/04/liquid-unifying-nearline-and-offline-big-data-integration/).)
* Article by Joan Goyeau: [Functional Programming with Kafka Streams and Scala](https://itnext.io/a-cqrs-approach-with-kafka-streams-and-scala-49bfa78e4295)
* [Kappa architecture workshop in Node.js](https://kappa-db.github.io/workshop/build/01.html)
* [`kappa-core`: Minimal peer-to-peer database in Node.js, based on kappa architecture](https://github.com/kappa-db/kappa-core)

## Tools

### Log data stores

An append-only immutable log store is the canonical store in a Kappa Architecture (or Lambda Architecture) system. Some log databases:

* [Amazon Quantum Ledger Database (QLDB)](https://aws.amazon.com/qldb/)
* [Apache Kafka](https://kafka.apache.org/)
* [Apache Pulsar](https://pulsar.apache.org/)
* [Amazon Kinesis](https://aws.amazon.com/kinesis/)
* [Amazon DynamoDB Streams](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Streams.html)
* [Azure Cosmos DB Change Feed](https://docs.microsoft.com/en-us/azure/cosmos-db/change-feed)
* [Azure EventHub](https://azure.microsoft.com/en-us/services/event-hubs/)
* [DistributedLog](https://bookkeeper.apache.org/distributedlog/)
* [EventStore](https://eventstore.org)
* [Chronicle Queue](https://github.com/OpenHFT/Chronicle-Queue)
* [Pravega](http://pravega.io/)
* [Hypercore](https://github.com/mafintosh/hypercore)

### Streaming computation systems

In Kappa Architecture, data is fed from the log store into a streaming computation system. Some distributed streaming systems:

* [Amazon Kinesis](https://aws.amazon.com/kinesis/)
* [Apache Flink](https://flink.apache.org/)
* [Apache Samza](https://samza.apache.org/)
* [Apache Spark](https://spark.apache.org/)
* [Apache Storm](https://storm.apache.org/)
* [Apache Beam](https://beam.apache.org/)
* [Azure Stream Analytics](https://azure.microsoft.com/en-us/services/stream-analytics/)
* [Hazelcast Jet](https://jet.hazelcast.org/)
* [Kafka Streams](https://kafka.apache.org/documentation.html#streams)
* [Onyx](https://www.onyxplatform.org/)
* [Siddhi](https://siddhi.io/)
* [Materialize](https://materialize.com/)

### Serving layer stores

The purpose of the serving layer is to provide optimized responses to queries. These databases aren't used as canonical stores: at any point, you can wipe them and regenerate them from the canonical data store. Almost any database, in-memory or persistent, might be used in the serving layer. This also includes special-purpose databases, e.g. for full text search.

## Contributing

This project is still in its initial phase. Please feel free to send your suggestions, comments to [me](mailto:milinda.pathirage@gmail.com). Also feel free to fork the [repo](https://github.com/milinda/kappa-architecture.com) and send pull requests.

<div class="github-fork-ribbon-wrapper right fixed" style="width: 150px;height: 150px;position: fixed;overflow: hidden;top: 0;z-index: 9999;pointer-events: none;right: 0;"><div class="github-fork-ribbon" style="position: absolute;padding: 2px 0;background-color: #333;background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.15));-webkit-box-shadow: 0 2px 3px 0 rgba(0, 0, 0, 0.5);-moz-box-shadow: 0 2px 3px 0 rgba(0, 0, 0, 0.5);box-shadow: 0 2px 3px 0 rgba(0, 0, 0, 0.5);z-index: 9999;pointer-events: auto;top: 42px;right: -43px;-webkit-transform: rotate(45deg);-moz-transform: rotate(45deg);-ms-transform: rotate(45deg);-o-transform: rotate(45deg);transform: rotate(45deg);"><a href="https://github.com/milinda/kappa-architecture.com" style="font: 700 13px &quot;Helvetica Neue&quot;, Helvetica, Arial, sans-serif;color: #fff;text-decoration: none;text-shadow: 0 -1px rgba(0, 0, 0, 0.5);text-align: center;width: 200px;line-height: 20px;display: inline-block;padding: 2px 0;border-width: 1px 0;border-style: dotted;border-color: rgba(255, 255, 255, 0.7);">Fork me on GitHub</a></div></div>
