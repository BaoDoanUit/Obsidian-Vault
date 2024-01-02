### Integrates well with legacy systems
**Monolithic systems are hard to maintain**. Many legacy systems are poorly structured, poorly tested, or depend upon outdated technologies. Luckily, microservices can work alongside legacy systems to improve the code and replace old parts of the system. Integration is easy and can solve many of the problems that make monolithic systems something of the past.
**Microservice architectures** create systems that remain maintainable in the long run since the various parts are replaceable. This means that a microservice can easily be rewritten without compromising the whole system. As long as the dependencies between microservices are managed appropriately, changes can easily be made to optimize team needs and performance.

### Drawbacks
Deployment requires more effort
Testing must be independent
Difficult to change multiple microservices

### Microservices and Docker
Microservices must be separately deployable, scalable independent units.
Docker is a lightweight solution for deploying microservices
A microservice can be packed into a Docker image and isolated as a Docker container.

>### Micro and Macro architecture decisions
It is possible to extend the concept of micro and macro architecture to **technical decisions**
<img src=https://miro.medium.com/v2/resize:fit:1400/format:webp/0*_oHhaYGdlUaUNBea.png />

### Self-contained systems
**A self-contained system** (SCS) is a type of microservice architecture that specifies the elements of a macro architecture. This means they do not represent the whole system. Since an SCS is self-contained, it provides everything you need to implement one part of the domain logic, such as log data and a UI. SCSs also have an optional API.
**Think of these as a collection of best practices**; SCSs provide precise rules based on established patterns, offering a point of reference for how to build a microservice architecture. All of these rules ensure that an SCS implements a domain, so an addded feature only changes one SCS.
<img src=https://miro.medium.com/v2/resize:fit:1400/format:webp/0*akfvO6nu9xQqov8K.png />

### Asynchronous Microservices
Synchronous microservices make a request to other microservices while it processes requests and waits for results. Asynchronous communication protocols send messages that the recipients react to, but there is no direct response. A microservice could be defined as asynchronous if it does not make requests to other microserices while processing, or it makes requests but does not wait for results.
<img src=https://miro.medium.com/v2/resize:fit:1400/format:webp/0*SqT9uthxJwptgG47.png />

### Microservices Platforms
**Microservice platforms**, such as PaaS and Docker scheduler, support the operation and communication of your microservices. These technologies enable communication between microservices for deplopment, log analysis and monitoring.
**These platforms support HTTP and REST** with load balancing and service discovery. Limited operations support is needed for the implementation of microservices, so they can be quickly deployed and support multiple microservices.
<img src=https://miro.medium.com/v2/resize:fit:1400/format:webp/0*yuugfIaXfROEAuFE.png />
