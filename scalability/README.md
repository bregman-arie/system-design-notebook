# Scalability

- [Scalability](#scalability)
  - [Vertical Scaling](#vertical-scaling)
    - [Use Cases](#use-cases)
    - [Limits](#limits)
  - [Horizontal Scaling](#horizontal-scaling)
  - [Scalability Factor](#scalability-factor)
    - [Linear Scalability](#linear-scalability)
    - [Sub-Linear Scalability](#sub-linear-scalability)
    - [Supra-Linear Scalability](#supra-linear-scalability)
    - [Negative Scalability](#negative-scalability)
  - [Questions](#questions)

[Wikipedia](https://en.wikipedia.org/wiki/Scalability): "Scalability is the property of a system to handle a growing amount of work by adding resources to the system"

In simpler words, scalability is about answering the question whether a system or an architecture are able to scale in a way that meets the new workloads and demand.<br>
More practically, answer questions like:
  * if a system runs a database, does it able to handle more queries?
  * if a system runs a service that streams videos to million of users. Will it able to stream them the same way if the amount of users would triple itself?

Also, scaling can be performed on different components. For example, in most cloud environments scaling is supported in case of:

  * Virtual Machines
  * Virtual network functions
  * Containers

There are different ways to scale.

## Vertical Scaling

Vertical Scaling is about adding additional resources to *the existing system/component/unit*. If for example, we have a server, a vertical scaling might be done in one or more of the following ways:

  * Adding more RAM to the server
  * Adding more storage/disks
  * Adding CPUs

<p align="center">
<img src="../images/scalability/vertical_scaling.png"/>
</p>

### Use Cases

If you are looking for simple change, one that doesn't involves adding new components to your architecture and if your app/system has low traffic, then vertical scaling can be a great option

### Limits

The limit of vertical scaling is clear - you are able to scale until your are no longer able to physically or virtually increase the resources of your machine.

## Horizontal Scaling

Adding more systems/units/components but at the same time, make them work together so it would seems to the client as if there is one system it interacts with.<br>
Few examples:

 * Instead of one web server, having two web servers with one load balancer balancing the traffic between them
 * Instead of one database server, having two databases

<p align="center">
<img src="../images/scalability/horizontal_scaling.png"/>
</p>

Point to think about: now that you know about vertical scaling and horizontal scaling, which one would you perform if you can choose only one of them?

## Scalability Factor

When you double the resources of your system (or design) you might expect your system to be able to handle double the workload as well, right? But this is not necessarily what will happen. Scalability factor is the term used to describe the workload your system is able to handle as a result of scaling your resources.

### Linear Scalability

Linear Scalability happens when the workloads your system is able to handle scale accordingly to the scale in resources. The scalability factor remains constant as you scale.<br>
For example, you triple the resources of your system -> the system is able to handle triple the workloads. In reality, it's actually not the case most of the time.

### Sub-Linear Scalability

A more realistic outcome of scaling systems would be that some resources or component may not scale as expected (or as other resources and components). So doubling the resources will actually lead to an improvement of only x1.5 in workloads handling. In this case the scalability factor will be lower than 1.0

### Supra-Linear Scalability

This is the optimal outcome. You triple the workloads handling by "only" doubling your resources for example. In other words, the ratio in performance change is bigger than the ratio in scaling changes (e.g. adding more CPUs). A scalability factor in this case, is bigger than 1.0

### Negative Scalability

It may sound crazy, but in some cases, scaling your system might actually lead to worse results and that's exactly what negative scalability is all about. Scalability factor is below 0.

## Questions

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
<summary>What is "Horizontal Scaling"?</summary><br><b>
</b></details>

<details>
<summary>If you can only choose to perform horizontal scaling or vertical scaling, but not both, which one would you perform?</summary><br><b>
</b></details>

<details>
<summary>Once we perform "Horizonal Scaling", by for example adding multiple web servers instead of having one server, how do we handle client access to these servers? </summary><br><b>

Using a load balancer
</b></details>

<details>
<summary>Name one disadvantage and one advantage of vertical scaling over horizontal scaling</summary><br><b>

Advantage: Simplicity. You increase the resources (maybe also restart something) but that's it, there is no architectural change. In horizontal scaling, you usually need to add a load balancer to distribute the traffic or access to the different nodes, which is considered an architectural change.

Disadvantage: Redundancy. When performed solely on a single server, your architecture will still suffer from redundancy - when your single server is down, your entire application is down.
</b></details>
