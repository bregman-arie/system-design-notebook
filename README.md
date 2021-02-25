<p align="center">
<img src="images/system_design_notebook.png"/>
</p>

> A curated collection of resources and exercises to help you learn about system design

* [Topics](#Topics)
* [Topics Explained](#Topics-explained)
* [Exercises](#Exercises)
* [Questions](#Questions)
* [Resources](#Resources)
* [System Design Process](#system-design-process)
* [Interview Tips](#system-design-interview-tips)
* [Q&A](common-qa.md)

## Topics

* Requirements
  * Functional
  * Non-Functional
* [Basic architecture](#basic-architecture)
  * [Client](#Client)
  * [Server](#Server)
  * Dispatcher
* Scalability 
  * Vertical Scaling
  * Horizontal Scaling
* Availability
* Performance
* Resiliency
* Microservices Architecture
* Monolith Architecture
* Cache
  * Distributed Cache
  * Cache Policy (aka Replacement Policy)
    * LRU (least recently used)
* Load Balancing
  * Consistent Hashing
* Fault Tolerance
* Distributed System
* Extensibility
* Loose Coupling
* Proxy
* CDN
* Networking
  * Latency
  * Throughput
* Design Level
  * Low level design
  * High level design

## Topics Explained

### Basic Architecture

#### Client

A client refers to a software or hardware accessing a resource or a service that is served by a server.
While in some cases the server and the client might be on the same system/host, in most cases they will be on separate systems.

Examples for clients:

* A Web browser that is used by a user to access a certain web page
* A mobile phone that is used by the user to read emails

<p align="center">
<img src="images/design/one_request_too_many_1.png"/>
</p>

#### Server

A server, similarly to a client, can be a software or hardware, but as opposed to a client, its role is to serve the client. It can be by providing a certain resource to the client or let it use a service that is running on the server.
Few examples:

* A system that stores files and allow the user to access or download them
* A system that runs a service which allows users to listen to music

### Scalability

[Wikipedia](): "Scalability is the property of a system to handle a growing amount of work by adding resources to the system"

Simply said, how well a system can handle bigger demand or work? If a system runs a database, does it able to handle more queries? If a system is streaming videos, does it able to provide service to twice the amount of users it supports today? the scalability of system is defined by the answer for such questions.

There are different ways to scale.

#### Vertical Scaling

Adding additional resources to *the existing system/component/unit*. If we have a server, a vertical scaling might be done in one or more of the following ways:

  * Adding more RAM to the server
  * Adding more storage/disks
  * Adding CPUs

#### Horizontal Scaling

Adding more systems/units/components but at the same time, make them work together so it would seems to the client as if there is one system it interacts with.<br>
Few examples:

 * Instead of one web server, having two web servers with one load balancer balancing the traffic between them
 * Instead of one database server, having two databases

#### Scalability Factor

### Networking

#### Latency

The time it takes to perform a certain task/action

#### Throughput

The number of tasks/actions per unit of time

## Exercises

Note: The names of the exercises are quotes from movies (sometimes little bit modified). If you can guess from which movie, please submit it to movies.md file in this way: [QUOTE] [MOVIE] [YOUR NAME]<br>
Another note: Exercises may repeat themselves in different variations to practice and emphasize different concepts.

### Elementary, my dear Watson

<details>
<summary>You have a website running on a single server. It's mostly running fine because only two users access it on weekly basis :'(. It suddenly becomes super popular and many users try to access it, but they are experiencing issues due to high load of the server. Two questions:
  * What term/pattern in system design is referring to the issue you are experiencing?
  * How can you deal with it (even if partially) WITHOUT adding more servers or changing the architecture?
<p align="center">
<img src="images/design/one_request_too_many_1.png"/>
</p>
</summary><br><b>

  * Scalability. Your web server doesn't scale based on demand (= the additional users accessing your website) hence they are experiencing issues.
  * Apply `vertical scaling` which means, adding more resources to your server - more CPU, more RAM. This way, your architecture doesn't change, but your website is able to serve more users.
</b></details>

<details>
<summary>Will 'vertical scaling' solve your scale issues permanently? Is it the optimal solution?</summary><br><b>

It might solve your issue for limited time, but you can't solely rely on it.
Vertical scaling has limitations. You can't keep adding RAM, storage and CPU endlessly. Eventually you'll hit some physical limit where for example, you simply don't have anymore space in your server box and you bought the best components you could.
</b></details>

<details>
<summary>Assuming you now can extend the architecture, what would you change?</summary><br><b>
</b></details>

### Perfectly balanced, as all things should be

<details>
<summary>You have the following simple architecture of a server handling requests from a client. What are the drawbacks of this design and how to improve it?
<p align="center">
<img src="images/design/one_request_too_many_1.png"/>
</p>
</summary><br><b>

* Limitations:
  * Load - at some point it's possible the server will not be able to handle more requests and it will fail or cause delays
  * Single point of failure - if the server goes down, nothing will be able to handle the requests

* How to improve:<br>
  <p align="center">
  <img src="images/design/one_request_too_many_2.png"/>
  </p>

* Further limitations:
    * Load was handled as well as the server being a single point of failure, but now the load balancer is a single point of failure.
</b></details>

<details>
<summary>Is there a way to improve the above design without adding an actual load balancer instance?</summary><br><b>

Yes, one could use DNS load balancing
</b></details>

### Keep calm, all I want is your cash

<details>
<summary>The following is a simple architecture of a client making requests to web server which in turn, retrieves the data from a datastore. What are the drawbacks of this design and how to improve it?
<p align="center">
<img src="images/design/cache_basics_1.png"/>
</p>
</summary><br><b>

* Limitations:
  * Time - retrieving the data from the datastore every time a request is made from the client, might take a while
  * Single point of failure - if the datastore is down (or even slow) it wouldn't be possible to handle the requests
  * Load - the datastore getting all the requests can result in high load on the datastore which might result in a downtime

* How to improve:<br>
  <p align="center">
  <img src="images/design/cache_basics_2.png"/>
  </p>
</b></details>

<details>
<summary>Are you able to explain what is Cache and in what cases you would use it?</summary><br><b>

Why to use cache?

  * Save time - Accessing a remote datastore, and in general making network calls, takes time
  * Reduce load - Instead of the datastore handling all the requests, we can take some of its load and reduce by accessing the cache
  * Avoid repetitive tasks - Instead of querying the data and processing it every time, do it once and store the result in the cache
</b></details>

<details>
<summary>Why not storing everything in the cache?</summary><br><b>

For multiple reasons:

1. The hardware on which we store the cache is in some cases much more expensive
2. More data in the cache, the bigger it gets and longer the put/get actions will take
</b></details>

### In a galaxy far, far away...

<details>
<summary>The following is a system design of a remote database and three applications servers
<p align="center">
<img src="images/design/remote_database_1.png"/>
</p>
</summary><br><b>

* Limitations:
  * Latency. Every query made to the remote database will hit latency, even if small.
  * In case the remote database crashes, the app will stop working

* How to improve:<br>
  <p align="center">
  <img src="images/design/remote_database_2.png"/>
  </p>
  * Replicate each database to the local app server. This has several advantages. First, we are not bound to latency anymore. Secondly, a fai

* Further limitations:
  * We are bound now to bandwidth
  * If the remote database isn't accessible for a long period of time, we'll have an outdated database and each app has the potential to work against a different DB
</b></details>

### A bit on the slow side

<details>
<summary>The following is an improvement of the previous system design
<p align="center">
<img src="images/design/remote_database_2.png"/>
</p>
</summary><br><b>

* Limitations:
  * Queries to database might be slow, even on the server itself where the app is running
  * Once the remote database isn't available, the local databases will not by in sync

* How to improve:<br>
  <img src="images/design/remote_database_v2_1.png"/>
</b></details>

## Questions

This is a more "simplified" version of exercises section. No drawings, no evolving exercises, no strange exercises names, just straightforward questions, each in its own category.

<details>
<summary>Your website usually serves on average a dozen of users and has good CPU and RAM utilization. It suddenly becomes very popular and many users try to access your web server but they are experiencing issues, and CPU, RAM utilization seems to be on 100%. How would you describe the issue?</summary><br><b>

Scalability issue. The web server doesn't scales :'(<br>
In order to avoid such issues, the web server has to scale based on the usage. More users -> More CPU, RAM utilization -> Add more resources (= scale up). An
When there are less users accessing the website, scale down.
</b></details>

### Scalability

<details>
<summary>Explain Scalability</summary><br><b>
</b></details>

<details>
<summary>Explain "Vertical Scaling" and give an example where it can help to solve an issue</summary><br><b>

Vertical scaling is the act of adding

For example, you have a website which serve a class of 20 students. Suddenly, you are teaching multiple classes and your website has to service 40 students. In order to be able to do that, you might have to apply "vertical scaling" and add resources like RAM and CPU to the server running your website.
</b></details>

<details>
<summary>Why we can't usually rely solely on "vertical scaling" to solve scaling issues?</summary><br><b>

Because you can't keep upgrading forever a certain server. At some point, you'll hit limitations of buying the best components you could and not having additional space for more components. Maybe the best RAM you could buy is 10TB, but you actually need 19TB RAM to serve all the users.
</b></details>

<details>
<summary></summary><br><b>
</b></details>

### Cache

<details>
<summary>Tell me everything you know about Cache</summary><br><b>
</b></details>

<details>
<summary>True or False? While caching can reduce load time, it's increasing the load on the server</summary><br><b>

False. If your server doesn't have to execute the request since the result is already in the cache, then it's actually the opposite - there is less load on the server in addition to reduced load times.
</b></details>

### Load Balancer

<details>
<summary>Tell me everything you know about Load Balancers</summary><br><b>
</b></details>

<details>
<summary>What algorithms a load balancer can be using?</summary><br><b>
</b></details>

<details>
<summary>What is an application load balancer?</summary><br><b>
</b></details>

<details>
<summary>At what layers a load balancer can operate?</summary><br><b>
</b></details>

<details>
<summary>What is DNS load balancing?</summary><br><b>
</b></details>

<details>
<summary>What are sticky sessions? What are their pros and cons?</summary><br><b>
</b></details>

### Networking

<details>
<summary>What is latency?</summary><br><b>
</b></details>

<details>
<summary>What is latency of L1 cache reference vs. L2 cache reference?</summary><br><b>

L1 cache reference latency is 0.5 nanosecond
L2 cache reference latency is 7 nanosecond

So basically the latency of L2 cache reference is 14x L1 cache reference.
</b></details>

### Misc

<details>
<summary>How operating systems able to run tasks simultaneously? for example, open a web browser while starting a game</summary><br><b>

The CPU have multiple cores. Each task is executed by a different core.<br>
Also, it might only appear to run simultaneously. If every process is getting CPU allocation every nanosecond, the user might think that both processes are running simultaneously.
</b></details>

<details>
<summary>What is a VPS?</summary><br><b>

[From wikipedia](https://en.wikipedia.org/wiki/Virtual_private_server): "A virtual private server (VPS) is a virtual machine sold as a service by an Internet hosting service."
</b></details>

<details>
<summary>True or False? VPS is basically a shared server where each user is allocated with a portion of the server OS</summary><br><b>

False. You get a private VM that no one else can or should use.
</b></details>

## Resources

There many great resources out there to learn about system design in different ways - videos, blogs, etc. I've gathered some of them here for you

### By Topic

<details>
  <summary>Scalability</summary>

#### Videos
* [Harvard Scalability Lecture - 2012](https://www.youtube.com/watch?v=-W9F__D3oY4&ab_channel=JorgeScott)
#### Repositories
* [awesome-scalability](https://github.com/binhnguyennus/awesome-scalability) - "An updated and organized reading list for illustrating the patterns of scalable, reliable, and performant large-scale systems"
</details>

### By Resources Type

<details>
  <summary>Videos</summary>

#### System Design
* [Gaurav Sen](https://www.youtube.com/watch?v=xpDnVSmNFX0&list=PLMCXHnjXnTnvo6alSjVkgxV-VH6EPyvoX) - Excellent series of videos on system design topics
* [System Design Interview](https://www.youtube.com/channel/UC9vLsnF6QPYuH51njmIooCQ) - How to get through system design interviews. Covering both architecture and code
#### Scalability
* [Harvard Scalability Lecture - 2012](https://www.youtube.com/watch?v=-W9F__D3oY4&ab_channel=JorgeScott)
</details>

<details>
  <summary>Repositories</summary>

#### Scalability
* [awesome-scalability](https://github.com/binhnguyennus/awesome-scalability) - "An updated and organized reading list for illustrating the patterns of scalable, reliable, and performant large-scale systems"
#### System Design
* [system-design-primer](https://github.com/donnemartin/system-design-primer) - "Learn how to design large-scale systems. Prep for the system design interview."
</details>

<details>
  <summary>Books</summary>
</details>

## System Design Process

How to perform system design???

## System Design Interview Tips

If you are here because you have an system design interview, here a couple of suggestions

### What to ask yourself when you see a design and asked to give an opinion on it

Note: You might want to ask yourself these questions also after you've done performing a system design

* Does it scale if I add more users?
* Is there a single point of failure in the design?

### What you might want to ask when you need to perform a system design

* What are the requirements?
  * How the system is used?
  * How much users are expected to access the system?
  * How often the users access the system?
  * Where the users access the system from?

* Are there any constraints?

## Credits

<div>The icon in the banner made by <a href="https://www.flaticon.com/authors/freepik" title="Freepik">Freepik</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div>

## Contributions

If you would like to contribute to the project, please read the [contribution guidelines](CONTRIBUTING.md)

## License

[![License: CC BY-NC-ND 3.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%203.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-nd/3.0/)
