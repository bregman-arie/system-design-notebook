# Basic Architecture

- [Basic Architecture](#basic-architecture)
  - [Client](#client)
  - [Server](#server)
    - [What is a server?](#what-is-a-server)
    - [Server Types](#server-types)
  - [Clients and Servers](#clients-and-servers)

## Client

A client refers to a software or hardware accessing a resource or a service that is served by a server.
While in some cases the server and the client might be on the same system/host, in most cases they will be on separate systems.

Examples for clients:

* A Web browser that is used by a user to access a certain web page
* A mobile phone that is used by the user to read emails

## Server

### What is a server?
A server, similarly to a client, can be a software or hardware, but as opposed to a client, its role is to serve the client. It can be by providing a certain resource to the client or let it use a service that is running on the server.
Few examples:

* A system that stores files and allow the user to access or download them
* A system that runs a service which allows users to listen to music

### Server Types

* Bare Metal: Physical Servers. An actual hardware. Often allocated per one customer, project, ... and not shared as in case of servers used for virtualization and cloud
 
* Virtual: Servers which provisioned on top of virtualization platform or a cloud (clouds like GCP, AWS and Azure for example)

## Clients and Servers

So now that you know what is a server and what is a client, you probably understand the relationship between them where a client sends requests (or replies) to a server, while a server responds to a client based on its request.

<br>
<p align="center">
<img src="../images/architecture/client_server_architecture.png"/>
</p>