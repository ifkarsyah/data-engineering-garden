---
title: Infrastructure Garden
---

Welcome! I’m excited to share this space with you—a place where ideas bloom, knowledge grows, and curiosity thrives. This Knowledge Garden is more than just a collection of information; it’s a living, breathing ecosystem where I cultivate and nurture my thoughts, experiences, and learnings.


Step by step guide for DevOps, SRE or any other Operations Role: https://roadmap.sh/devops

Learn these [[Programming Languages for SRE]] such as **Go**, **Java**, **C++**. Focus on its concurrency features, how it implement/interact with operating system.

## Fundamental Computer Science
### Operating System

#### Concepts
* Learn OSTEP
* Learn How those concept implemented in Linux
#### Practical
- [[Learn to Live in Terminal]]
- [[Learn how to troubleshoot in Linux]]
#### Reference
- https://linuxupskillchallenge.org/#table-of-contents
- https://linuxjourney.com/
- https://linuxcommand.org/tlcl.php

### Computer Networking

#### Concepts
As a DevOps engineer you will need to understand the basics of [[Network Protocols]], how they work, and how they are used in the real world.
#### Practical
- [[Linux Networking Command]]

## Cloud 1: Introduction

Cloud providers provide a layer of APIs to abstract infrastructure and provision it based on security and billing boundaries. The cloud runs on servers in data centers, but the abstractions cleverly give the appearance of interacting with a single “platform” or large application.
#### AWS
Amazon Web Services has been the market leading cloud computing platform since 2011, ahead of Azure and Google Cloud. 
#### GCP
Google Cloud is Google’s cloud computing service offering, providing over 150 products/services to choose from.
## Common [[System Design Components]]

### Concepts
- **Web Server**: Serves web content, handling requests from clients (like browsers).
- **Load Balancer**: Distributing traffic among multiple servers.
- **Forward Proxy**: A server that acts as an intermediary between client machines and the internet, forwarding client requests to the desired destination.
- **Reverse Proxy**: A server that sits behind a firewall, routing client requests to the appropriate backend server in a private network, often used for load balancing and security.
- **CDN**: A network of servers distributed globally to deliver content to users from the closest geographical location, improving load times and reducing latency.
- **Firewall**: A network security device that monitors and controls incoming and outgoing network traffic based on predefined security policies
### Implementation in Cloud

| **Component**     | **OSS**                            | **AWS**                         | **GCP**                       | **Other Cloud**             |
| ----------------- | ---------------------------------- | ------------------------------- | ----------------------------- | --------------------------- |
| **Web Server**    | - Apache HTTP Server<br>- NGINX    | - AWS Elastic Beanstalk         | - Google App Engine           | - Azure App Service         |
| **Load Balancer** | - HAProxy<br>- NGINX               | - AWS Elastic Load Balancer     | - Google Cloud Load Balancing | - Azure Load Balancer       |
| **Firewall**      | - pfSense                          | - AWS WAF                       | - Google Cloud Armor          | - Azure Firewall            |
| **Forward Proxy** | - Squid Proxy                      | - AWS PrivateLink               | - Google Cloud NAT            | - Azure Front Door          |
| **Reverse Proxy** | - NGINX<br>- Apache Traffic Server | - AWS Application Load Balancer | - Google Cloud Load Balancing | - Azure Application Gateway |
| **CDN**           | - N/A                              | - AWS CloudFront                | - Google Cloud CDN            | - Cloudflare<br>- Fastly    |
## IaaC
- Provisioning Tools with [[Terraform]]
- Configuration Management with [[Ansible]]
- CICD with [[GitHub Action]] or [[Gitlab CI]] or [[Jenkins]]

## [[Kubernetes World]]
Kubernetes is an [open source](https://github.com/kubernetes/kubernetes) container management platform, and the dominant product in this space. Using Kubernetes, teams can deploy images across multiple underlying hosts, defining their desired availability, deployment logic, and scaling logic in YAML.
## Cloud 3: Kubernetes in Cloud
