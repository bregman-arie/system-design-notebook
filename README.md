# System Design Exercises

## Exercises

For each of the system designs and architectures, answer the following:

* What are the limitations of the system design or architecture?
* How to improve it?
* Are there any limitations, after applying the improvements? If yes, are there any further improvements to apply?

Note: improvement is an improvement. It doesn't has to be the optimal solution. Some exercises don't have an optimal solution.

#### Remote Database


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
  <img src="images/design/remote_database_2.png"/>
  * Replicate each database to the local app server. This has several advantages. First, we are not bound to latency anymore. Secondly, a fai

* Further limitations:
  * We are bound now to bandwidth
  * If the remote database isn't accessible for a long period of time, we'll have an outdated database and each app has the potential to work against a different DB
</details>

#### Remote Database v2

<details>
<summary>The following is the improvement of the previous system design
<img src="images/design/remote_database_2.png"/>
</summary><br><b>
</details>

## Contributions

If you would like to contribute to the project, please read the contribution guidelines.
