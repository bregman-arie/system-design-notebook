# System Design Exercises

<p align="center">
<img src="images/system_design_exercises.png"/>
</p>

This repository was created for educational purposes. Use it to learn system design step by step.
For any improvements suggestions, questions or comment, please feel free to open an issue.

* [Topics](#Topics)
* [Exercises](#Exercises)
* [Resources](#Resources)
* [Q&A](#Q&A)

## Topics

It's recommended that before you try to solve any of the exercises, to first read about the following topics:

* Scalability 
    * Vertical Scaling
    * Horizontal Scaling
* Resiliency
* Microservices Architecture
* Monolith Architecture
* Distributed System
* Load Balancing
* Fault Tolerance
* Extensibility
* Loose Coupling
* Consistent Hashing
* Design Level
    * Low level design
    * High level design

## Exercises

For each of the system designs and architectures, answer the following:

* What are the limitations of the system design or architecture?
* How to improve it?
* Are there any limitations, after applying the improvements? If yes, are there any further improvements to apply?

Note: not every improvement mentioned in the solution is the optimal solution or the only one.

#### One request too many

<details>
<summary>The following is probably the most simple design of a server handling requests
<p align="center">
<img src="images/design/one_request_too_many_1.png"/>
</p>
</summary><br><b>

* Limitiations:
  * Load - at some point it's possible the server will not be able to handle more requests and it will fail or cause delays
  * Single point of failure - if the server goes down, nothing will be able to handle the requests

* How to improve:<br>
  <p align="center">
  <img src="images/design/one_request_too_many_2.png"/>
  </p>

* Further limitations:
    * Load was handled as well as the server being a single point of failure but now the load balancer is a single point of failure

</b></details>

#### In a far far database...

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

#### In a far far database... v2

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

## Resources

There many great resources out there to learn about system design in other ways - videos, blogs, etc. I would like to mention some of them here:

* [Gaurav Sen Youtube Channel](https://www.youtube.com/watch?v=xpDnVSmNFX0&list=PLMCXHnjXnTnvo6alSjVkgxV-VH6EPyvoX) - Excellent series of videos on system design topics

# Q&A

Q: Can I add my own exercises?
A: Yes you can!

Q: Why the exercises have strange names?
A: Well, that's nice of you :'( Anyway, I was just trying to amuse myself while creating this project

## Credits

<div>Icons made by <a href="https://www.flaticon.com/authors/freepik" title="Freepik">Freepik</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div>

## Contributions

If you would like to contribute to the project, please read the contribution guidelines.
