# Databases

- [Databases](#databases)
  - [What is a Database?](#what-is-a-database)
  - [Types](#types)
    - [SQL](#sql)
    - [NoSQL](#nosql)
      - [MongoDB](#mongodb)
      - [Cassandra](#cassandra)
  - [Replication](#replication)
  - [Partitioning](#partitioning)
    - [Horizontal Partitioning](#horizontal-partitioning)
    - [Vertical Partitioning](#vertical-partitioning)
  - [Questions](#questions)

## What is a Database?

[Wikipedia](https://en.wikipedia.org/wiki/Database): "a database is an organized collection of data stored and accessed electronically from a computer system."

Perhaps the most basic example for a database would be a file on filesystem. This file can store information on people and their addresses, it can contain information on types of wine, or any other organized data.

Even though a file can be considered a database, you'll not find it used in system designs. Databases today are full and rich services that supports much more than just storing your data.

## Types

### SQL

### NoSQL

NoSQL don't use the traditional tabular relationship as in SQL databases. They are also known as "Sharded Databases" as information is [horizontally partitioned](#horizontal-partitioning).

Some of the challenges with such databases is the operation of resharding - how to add or remove shards based on the scaling that has to take place?
Another challenge is what is known as "hotspots" - how to deal with shards/partitions that are more popular than other shards? In other words, how to take into account traffic/popularity when performing partitioning?

Let's look at some examples of such databases

#### MongoDB

<p align="center">
<img src="../images/databases/MongoDB.png"/>
</p>

#### Cassandra

NoSQL database. Its architecture can be can seen in the drawing below. Each node can act as a primary interface so availability is high in Cassandra architecture

<p align="center">
<img src="../images/databases/cassandra_architecture.png"/>
</p>

While availability might be better in Cassandra compared to other databases, as each node can be the primary interface, it requires constantly synching them so consistency isn't at its top.

## Replication

[Wikipedia](https://en.wikipedia.org/wiki/Replication_(computing)): "Replication in computing involves sharing information so as to ensure consistency between redundant resources, such as software or hardware components, to improve reliability, fault-tolerance, or accessibility."

You'll see in many system designs that it's quite common to have separate instance for writes and another instance for reads. Thing is, when you split it into read and write instances, you have to make sure the data is consistent. This is where replication becomes relevant.

## Partitioning

The ways you divide DB tables into additional tables

<p align="center">
<img src="../images/databases/partitioning.png"/>
</p>

### Horizontal Partitioning

Dividing a table into multiple tables. While it's physically split, logically it's treated as one table.

As an example, let's take a database for video games. We might have a separate database for each video game genre or each video game developer company, but eventually all treated as "video games" database so each table has the same columns.

To summarize:
* Divide table into multiple tables with different rows
* Each table has the same columns but different rows
* Horizontal partition is also known as Shard.

<p align="center">
<img src="../images/databases/horizontal_partitioning.png"/>
</p>

### Vertical Partitioning

Similarly to Horizontal Partitioning, we divide the table into tables. The difference is that in Vertical Partitioning each table has less columns (while in Horizontal Partitioning it's the same number of columns in each separate table)

To summarize:
* Divide table into multiple tables with different columns
* Each table doesn't have the same columns

<p align="center">
<img src="../images/databases/vertical_partitioning.png"/>
</p>

## Questions

<details>
<summary>What are the advantages of replicating a database?</summary><br><b>

* Introducing high-availability: when creating a replication, you actually create another source of data you can use, even when your original instance is down
* Performances are better spread: you can decide that one of the instances is for reads while the other one is for reads
* Your app becomes more reliable: even if your database is down, the replication can still be used
</b></details>

<details>
<summary>Explain Horizontal Partitioning</summary><br><b>

Read [here](#horizontal-partitioning)
</b></details>

<details>
<summary>Explain Vertical Partitioning</summary><br><b>

Read [here](#vertical-partitioning)
</b></details>

<details>
<summary>What's a Shard?</summary><br><b>

Another name for [horizontal partitioning](#horizontal-partitioning) where a single table becomes multiple smaller tables.
</b></details>

<details>
<summary>Describe the architecture of one common database</summary><br><b>

There are a couple mentioned in this page:

* [MongoDB](#mongodb)
* [Cassandra](#cassandra)
</b></details>

<details>
<summary>What is Resharding?</summary><br><b>
</b></details>