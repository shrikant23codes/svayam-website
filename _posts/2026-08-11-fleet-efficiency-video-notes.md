---
layout: post
title:  "Talk Notes: How Netflix shapes fleet for Efficency and Reliability, Argha C from netflix"
date:   2026-08-11 00:00:00 +0530
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/K-2u50e0VzA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

---
<br>

These notes come from a video on Netflix's infrastructure practices. This post organizes the key ideas into short sections.
 
## Control Plane and Data Plane
 
Netflix runs its control plane in active-active mode. Both regions handle live traffic at the same time. This design improves availability. But it is hard to build correctly.
 
Netflix's data plane is different. It uses Open Connect, Netflix's own CDN. Open Connect moves content closer to users. Search for talks about Open Connect for more detail.
 
## Efficiency, Reliability, and Fleet Tiers
 
Queuing delay grows as system load grows. This growth is not linear. Delay rises fast as load nears full capacity.
 
Utilization alone does not show efficiency. Two systems can run at the same utilization. One can still serve requests faster than the other. The Kingman formula estimates wait time from utilization and variability. Engineers use this formula to model system efficiency.
 
Not all services need the same utilization target. The target depends on the service tier.
- Tier 0 services run at about 30% utilization. This tier carries critical, latency-sensitive traffic and needs spare capacity for sudden load.
- Batch processing services run at about 80% utilization. This work is not latency-sensitive, so it can tolerate delay.
 
A well-designed system also isolates failures. One failing part should not bring down the whole system.
 
## Scaling and Capacity Planning
 
Databases scale slowly. They need reserved capacity ahead of demand. Stateless microservices scale fast and can add or remove instances in minutes.
 
Always benchmark a new AWS instance type before you add it to a fleet. *Side note:* AWS Graviton is an ARM-based EC2 instance. Annapurna Labs designed it, and AWS owns Annapurna Labs. Graviton uses the Neoverse core IP from ARM.
 
Keep buffer capacity for both normal load and failure conditions. Example: Cassandra clusters went down during background compaction jobs, because the clusters did not have enough buffer capacity to absorb this extra load.
 
To plan capacity well, check three signals: CPU use, memory use (live memory and garbage collection), and network use. Stateful services can show sudden bursts in network traffic, so plan buffer capacity for these bursts.
 
## Traffic Routing and Autoscaling
 
Netflix uses Zuul as its API gateway. Zuul is open source. Netflix also built its own DNS system to help route traffic. Search for Sergey's talk on Netflix DNS for more detail.
 
Netflix automates fleet scale-up, but autoscaling can react slowly to sudden load spikes. See the "Live at Netflix" blog series for more detail. Reactive scaling adds capacity after load increases and cannot always keep pace with sudden spikes. Load shedding drops some requests during overload to protect the rest of the system.
 
Netflix has an open-source repository for service capacity modeling. Check this repository for tools and methods.