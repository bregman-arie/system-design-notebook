# Distributed Systems

- [Distributed Systems](#distributed-systems)
  - [What is a distributed system?](#what-is-a-distributed-system)
  - [Fallacies of distributed systems](#fallacies-of-distributed-systems)
  - [Clock Drift](#clock-drift)
  - [CDN](#cdn)

## What is a distributed system?

* A group of computers/servers working together
* The complexity of distributed system often hidden from the user

<p align="center">
<img src="images/distributed_systems/hidden_complexity.png"/>
</p>

## Fallacies of distributed systems

There are some challenges that we have to deal with when designing and managing distributed/high-scale systems, but not so much with non-distributed systems:

* Network Reliability: when you run a system on a single host, networking isn't as problem as when you need to to manage dozen or hundreds (and more) nodes
* Zero Latency: running on a single host, latency is not an issue, but when managing multiple hosts, how to keep latency as close as possible to zero?
* Bandwidth: same a latency, when running on a single host, bandwidth is infinite, but when the system is distributed you have to move data between the server so bandwidth becomes a challenge 
* Constantly changing Topology: In distributed system, hosts and different components may go down or up meaning, the topology is constantly changing while a single host is a constant
* Security: keeping one host secured is much more simple than securing a distributed system where not only all components should be secured but also the communication between the different hosts and components
* Size of the team: managing one host requires less administrators than managing a distributed system with hundreds, thousands or even more hosts and components

## Clock Drift

[Wikipedia](https://en.wikipedia.org/wiki/Clock_drift): "Clock drift refers to several related phenomena where a clock does not run at exactly the same rate as a reference clock. That is, after some time the clock "drifts apart" or gradually desynchronizes from the other clock"

Synchronizing clock is a challenge in distributed systems because each system has its own clock and once the system's clock drifts, this might affect the system as a whole and lead to unintended behaviours.

## CDN

[Cloudflare](https://www.cloudflare.com/en-gb/learning/cdn/what-is-a-cdn): "A content delivery network (CDN) refers to a geographically distributed group of servers which work together to provide fast delivery of Internet content."

In other words, a content delivery network allows you to quickly transfer content by having servers with the content around the world or certain area. The client then, access these servers instead of the main server where the data originates from.

<p align="center">
<img src="../images/cdn/cdn.png"/>
</p>
