### Why Load Balancer ?

The aim of load balancing is to optimize the use of your resources, while maximizing throughput and minimizing the time it takes for a response. It helps ensure high Availability

### what is load balancer ?

Distribute the network traffic within your network and the network traffic arriving from outside your network.
across a group of backend computing resources or servers. Load balancing aims to optimize resource use, maximize throughput, minimize response time, and avoid overloading any single resource. It can also improve availability by sharing a workload across redundant computing resources

### types of load balancer

Based on layer where they work 

- `Layer 4` : 

- `Layer 7 ` : 7 load balancers that only accept HTTP(S) traffic. They are intended for web applications or other HTTP(S) endpoints. They include features such as SSL offload, web application firewall, path-based load balancing, and session affinity.

Based on regions 

- `Regional LB` : Regional load-balancing services distribute traffic within virtual networks across virtual machines (VMs) or zonal and zone-redundant service endpoints within a region. You can think of them as systems that load balance between VMs, containers, or clusters within a region in a virtual network.

- `Global LB` : traffic across regional backends, clouds, or hybrid on-premises services. These services route end-user traffic to the closest available backend

### load balancing options

> Go to portal.azure.com --> G / --> load balancing (help me choose)

Azure provides various load balancing services that you can use to distribute your workloads across multiple computing resources, but the following are the main services:

- `Azure Load Balancer` - high-performance, ultra-low-latency Layer 4 load-balancing service (inbound and outbound) for all UDP and TCP protocols. It is built to handle millions of requests per second while ensuring your solution is highly available. Azure Load Balancer is zone-redundant, ensuring high availability across Availability Zones.

- `Traffic Manager` - DNS-based traffic load balancer that enables you to distribute traffic optimally to services across global Azure regions, while providing high availability and responsiveness. Because Traffic Manager is a DNS-based load-balancing service, it load-balances only at the domain level. For that reason, it can't fail over as quickly as Front Door, because of common challenges around DNS caching and systems not honoring DNS time-to-live values (TTLs).

- `Azure Application Gateway` - provides application delivery controller (ADC) as a service, offering various Layer 7 load-balancing capabilities. Use it to optimize web farm productivity by offloading CPU-intensive SSL termination to the gateway.

- `Azure Front Door` - application delivery network that provides global load balancing and site acceleration service for web applications. It offers Layer 7 capabilities for your application like SSL offload, path-based routing, fast failover, caching, etc. to improve performance and high-availability of your applications

Table of summary :

HTTP(S) VERSUS NON-HTTP(S)
|Service|	Global/regional | 	Recommended traffic |
|-------|--------------|-------------|
| Azure Front Door |	Global	| HTTP(S) |
| Traffic Manager |	Global |non-HTTP(S) |
|Application Gateway | Regional |	HTTP(S) |
|Azure Load Balancer|	Regional|	non-HTTP(S)|

![](https://docs.microsoft.com/en-us/learn/wwl-azure/load-balancing-non-https-traffic-azure/media/load-balancing-decision-tree-3f132096.png).
