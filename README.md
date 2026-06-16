# Load Balancing + PCC + Failover (MikroTik)
## Overview
This project demonstrates a multi-WAN implementation on MikroTik RouterOS using Per Connection Classifier (PCC) for load balancing and automatic failover.

The objective was to distribute client traffic across two primary WAN connections while maintaining uninterrupted connectivity by automatically switching to available links whenever a failure occurs.


## Objectives
* Implement load balancing between two Internet connections using PCC.

* Configure automatic failover between primary WAN links.

* Enable backup Internet connectivity when both primary links become unavailable.

* Ensure the backup link remains excluded from load balancing during normal operation.


## Technologies Used
* MikroTik RouterOS
* GNS3
* PCC (Per Connection Classifier)
* Mangle
* Static Routing
* Policy Routing
* NAT
* Failover


## Key Features
* Traffic distribution across two WAN links using PCC.

* Automatic failover based on route distance and gateway monitoring.

* Backup WAN activation only when both primary links fail.

* Policy-based routing using dedicated routing tables.

* Source NAT for each Internet connection.


## Repository Structure
```
README.md
Documentation.md
Topology.png
Sources/
```


## Validation
The implementation was verified by:

* Confirming balanced traffic distribution through PCC counters.

* Verifying simultaneous utilization of both primary WAN links.

* Testing failover by disconnecting each WAN individually.

* Confirming automatic backup link activation when both primary WAN links became unavailable.


## Challenges
The primary challenge was related to the GNS3 environment rather than the RouterOS configuration.

After resolving the lab environment issues, the load balancing and failover mechanisms operated as expected.


## Documentation
Detailed configuration steps, screenshots, verification results, and implementation notes are available in `Documentation.md`.

>**Note**: The detailed documentation is currently written in Persian (Farsi).


## Learning Outcomes
Through this project I gained hands-on experience with:

* Multi-WAN network design
* PCC-based load balancing
* Policy-based routing
* Automatic failover implementation
* Traffic verification and troubleshooting
