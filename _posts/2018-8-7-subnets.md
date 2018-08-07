---
layout: post
title: AWS VPC Networking
---

### public subnets
- Contains resourses which have a private IP address and can have a public IP address.  The public IP address can be accessed by a user outside the VPC and the private IP can be used to access private resourses in the VPC.

### private subnets

- only contains a private IP address and can only be accessed by the internal network.(In the VPC)

### IP Ranges reserved for private networks

Start|End     |Number of addresses
:---:|:---:|:---:
10.0.0.0	|10.255.255.255	|16777216
| |
172.16.0.0|	172.31.255.255|	1048576
| |
192.168.0.0   |	192.168.255.255|	65536
cccccccccccccc|cccccccccccccc|cccccccccccccc

### route tables

These are for determining which physical address to send data to.  It contains the IP address of the gateway the packet is going to and will determine the physical address.

![_config.yml]({{ site.baseurl }}/images/Screen Shot 2018-08-07 at 12.02.53 PM.png)
