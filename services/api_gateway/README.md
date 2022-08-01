# API Gateway

- [API Gateway](#api-gateway)
  - [What is API Gateway?](#what-is-api-gateway)
  - [Questions](#questions)

## What is API Gateway?
With the transition from monolith to microservices architecture, clients suddenly had to contact many different services and each service had to apply the very same methods of monitoring, logging and security.

To handle with this situation, the API Gateway was invented. An API management component that sits between the clients and the different services/APIs.

Advantages:
  * Reducing round trips: client performance is better as the client doesn't have to contact all the different services/APIs. This is done by the API gateway itself so the client has only to contact the API gateway.
  * Protocol Switching: The client can use one type of protocol to communicate with the API gateway, while the API gateway will use another protocol to communicate with the services (e.g. client is using HTTPS while API gateway uses HTTP)
  * Offload Functionality: Many times you'll see that some of the services/APIs functionalities are moving to the API gateway itself like rate limiting, API logging, etc.  this allows the services to focus solely on the functionality they need to provide.
  * Security: Instead of having all the APIs open and available for everyone, it can be available only to the API gateway and security can be applied on the API gateway so everyone contacting the different service go through the same security measurements in one consolidated component

## Questions

<details>
<summary>Explain what is an API Gateway. Why it was invented</summary><br><b>

Read [here](#api-gateway) about API Gateway
</b></details>

<details>
<summary>Name three advantages of using API gateway</summary><br><b>

* Security: everyone access the different services through one component which can be secured
* Better client performances: less round trips to perform for clients to communicate with the different services
* Offload functionalities from services into one place: insead of each service implementing things like rate limiting, logging, ... it can all be implemented in API gateway and applied for multiple services as well as new services added in the future

For more details read [here](#api-gateway) about API Gateway
</b></details>