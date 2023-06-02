
### Load Balancing
1. Distributes client requests or network load efficiently across multiple servers
2. Ensures high availability and reliability by sending requests only to servers that are online
3. Provides the flexibility to add or subtract servers as demand dictates
Because of the downsides of client-side load-balancing, most systems built using microservices architecture use Proxy load balancing.
### When Envoy Proxy?
1. But as our system started scaling, as we started having more customers and in turn higher throughput, we started observing performance degradation on a few servers.

2. Consider a single connection from a client to the HAProxy Server, as shown in the figure below, with 5 requests multiplexed on the same connection.

-> Envoy solves this problem with its support for HTTP2 based load balancing.
Consider a similar example as above, where you have a single connection from a client to the Envoy Server, as shown in the figure below. Envoy recognizes the 5 multiplexed requests and load-balances each request by creating 5 individual HTTP2 connections to 5 different backend servers.

### What is the Envoy Proxy
Envoy Proxy is an L7 proxy and communication bus designed for large modern service-oriented architectures.

Layer 7 load balancers operate at the highest level in the OSI model, the Application layer (on the Internet, HTTP is the dominant protocol at this layer). 

The Envoy Proxy configuration primarily consists of listeners, filters and clusters
- Listener
![[Microservice-6.png]]
- Filters
![[Microservice-7.png]]
![[Microservice-8.png]]
- Clusters
![[Microservice-9.png]]



### How we leveraged Envoy to solve yet another scalability challenge


REFERENCES:
[1] What Is Load Balancing? https://www.nginx.com/resources/glossary/load-balancing/

[2] Envoy: Supported Load Balancers https://www.envoyproxy.io/docs/envoy/latest/intro/arch_overview/upstream/load_balancing/load_balancers#:~:text=When%20a%20filter%20needs%20to,cluster%20basis%20in%20the%20configuration.