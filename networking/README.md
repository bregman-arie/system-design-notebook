# Networking

- [Networking](#networking)
  - [What is Networking?](#what-is-networking)
    - [Public IP](#public-ip)
    - [Private IP](#private-ip)
    - [Latency](#latency)
    - [Throughput](#throughput)
  - [Questions](#questions)

## What is Networking?

TODO

### Public IP

[Wikipedia](): "A public IP address, in common parlance, is a globally routable unicast IP address, meaning that the address is not an address reserved for use in private networks"

From system design perspective, when you have a resources or a component, you would like everyone to be able to access to, whether for direct communication (like a web server) or as a gateway for other components (like a load balancer), you should use a public IP

### Private IP

Whenever you DON'T want users to be able to globally interact with a certain component or resource, you should use a private IP address. Few examples:

  * Web servers that only the load balancer should communicate with them directly and not the users/clients themselves
  * Internal servers that users outside the organization shouldn't access

Private IPs, as opposed to public IPs, don't have to be unique and each separate network, can use the same addresses (because it's private :) )

### Latency

The time it takes to perform a certain task/action

### Throughput

The number of tasks/actions per unit of time

## Questions

<details>
<summary>What is a public IP? In which scenarios, one should use a public IP?</summary><br><b>
</b></details>

<details>
<summary>What is a private IP? In which scenarios, one should use a private IP?</summary><br><b>
</b></details>

<details>
<summary>What is latency?</summary><br><b>
</b></details>

<details>
<summary>What is latency of L1 cache reference vs. L2 cache reference?</summary><br><b>

L1 cache reference latency is 0.5 nanosecond
L2 cache reference latency is 7 nanosecond

So basically the latency of L2 cache reference is 14x L1 cache reference.
</b></details>
