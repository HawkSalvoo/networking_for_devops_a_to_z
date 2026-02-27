# IP Addressing & Subnetting

*A beginner-friendly guide for DevOps engineers*

---
# 📘 Fundamentals of IP Addressing
---

## 🌐 What is an IP Address?

An **IP (Internet Protocol) Address** is a unique numerical label assigned to every device connected to a network. It allows devices to **identify, locate, and communicate** with each other over a network like the internet.

Think of it as a **home address for your server**. Without it, data wouldn’t know where to go.

---

## 🧠 Why IP Addressing Matters in DevOps

In DevOps, you constantly work with:

* Cloud servers
* Containers
* Load balancers
* Kubernetes clusters
* CI/CD pipelines
* Firewalls and security groups

All of these rely heavily on networking and IP management.

For example:

* Deploying apps on **Amazon Web Services**
* Managing networking in **Google Cloud Platform**
* Configuring virtual machines in **Microsoft Azure**
* Handling cluster networking in **Kubernetes**
* Managing container communication via **Docker**

Without understanding IP addressing, troubleshooting deployments becomes extremely difficult.

---

# 🏗 Types of IP Addresses

## 1️⃣ IPv4 (Internet Protocol Version 4)

* 32-bit address
* Written in dotted decimal format
* Example: `192.168.1.10`
* Around 4.3 billion addresses

### Structure of IPv4

```
192.168.1.10
|   |   |   |
8b  8b  8b  8b  = 32 bits
```

---

## 2️⃣ IPv6 (Internet Protocol Version 6)

* 128-bit address
* Written in hexadecimal
* Example: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`
* Practically unlimited addresses

### Structure of IPv6

```
|<--------------------------- 128 bits ---------------------------->|

2001     0db8     85a3     0000     0000     8a2e     0370     7334
|----|   |----|   |----|   |----|   |----|   |----|   |----|   |----|
 16b      16b      16b      16b      16b      16b      16b      16b

```

---

# 🧩 Public vs Private IP

## 🌍 Public IP

* Accessible over the internet
* Assigned by ISP
* Used for public-facing applications

## 🏠 Private IP

* Used inside private networks
* Not accessible from the internet

---

# 📊 Visual Diagram: How IP Communication Works

```
        Client (Laptop)
        IP: 192.168.1.5
              |
              |  (Router/NAT)
              |
      Public IP: 49.204.10.22
              |
        -------------------
        |                 |
   Web Server        Database Server
   10.0.1.5           10.0.2.8
```
---

# 🚀 Why IP Knowledge is Critical for DevOps

## 1️⃣ Cloud Infrastructure Setup

* Creating VPCs
* Subnet design
* Route tables
* Internet gateways

## 2️⃣ Kubernetes Networking

* Pod IPs
* Service IPs
* Cluster IP
* Node IP
* CNI plugins

## 3️⃣ Load Balancing

* Public IP → Load Balancer → Private IP backend

## 4️⃣ CI/CD Pipelines

* Runners need network access
* Firewall rules based on IP ranges

## 5️⃣ Troubleshooting

Common issues:

* “Connection refused”
* “Host unreachable”
* “Timeout error”

Most are IP/network misconfigurations.

---
# 🛠 Common DevOps Networking Commands

```bash
ip addr
ifconfig
ping 8.8.8.8
netstat -tulnp
ss -tulnp
traceroute google.com
```

---

# 📘 Fundamentals of Subnetting

---

## 🌐 What is an Subnet?

A subnet (subnetwork) is a logical subdivision of an IP network. Subnetting divides a large network into smaller, manageable networks to improve:

Performance

Security

Organization

Scalability

---

# 📊 Visual Diagram: How Subnet Works

```
                     Internet
                         |
                  ┌───────────────┐
                  │    Router     │
                  └───────┬───────┘
                          |
        ---------------------------------------
        |                                     |
  ┌──────────────┐                     ┌──────────────┐
  │  Subnet A    │                     │  Subnet B    │
  │192.168.1.0/25│                     │192.168.1.128/25│
  └──────┬───────┘                     └──────┬────────┘
         |                                       |
   ┌──────────┐                           ┌──────────┐
   │  Server1 │                           │  Server2 │
   └──────────┘                           └──────────┘

```

---

# Why Subnet Knowledge Is Critical for DevOps

In modern infrastructure, networking is not optional — it is foundational. Whether you're deploying containers, provisioning cloud resources, or building CI/CD pipelines, subnet knowledge directly impacts reliability, security, and scalability.

---

## 1️⃣ Cloud Infrastructure Is Built on Subnets

All major cloud providers require subnet design:

* Amazon Web Services (VPC & Subnets)
* Microsoft Azure (VNets & Subnets)
* Google Cloud (VPC Networks)

When creating a VPC like:

```
10.0.0.0/16
```

You must divide it into subnets:

```
10.0.1.0/24  → Public
10.0.2.0/24  → Private App
10.0.3.0/24  → Database
```

If you don’t understand subnet sizing:

* You may run out of IPs
* You may overlap CIDR ranges
* Peering/VPN connections may fail

---

## 2️⃣ Security Depends on Network Segmentation

Subnetting enables **network isolation**.

Example 3-tier architecture:

```
             Internet
                 |
          [Public Subnet]
              Web Tier
                 |
          [Private Subnet]
              App Tier
                 |
          [DB Subnet]
             Database
```

Benefits:

* Databases not exposed to internet
* Only required ports are allowed
* Reduced attack surface

DevOps engineers design these boundaries using security groups and route tables.

---

## 3️⃣ Kubernetes & Containers Require IP Planning

Container platforms rely heavily on networking:

* Kubernetes
* Docker

Each:

* Node gets IP
* Pod gets IP
* Service gets virtual IP

If subnet planning is poor:

* Pods fail to schedule
* IP exhaustion happens
* Cluster networking breaks

Example:
If your subnet supports only 64 IPs, your cluster cannot scale beyond that limit.

---

## 4️⃣ Infrastructure as Code (IaC) Needs CIDR Planning

Tools like:

* Terraform
* AWS CloudFormation

Require subnet definitions:

```hcl
resource "aws_subnet" "private" {
  cidr_block = "10.0.2.0/24"
}
```

If CIDR blocks overlap:

* Deployment fails
* Peering breaks
* Production downtime may occur

Subnet mistakes in IaC propagate quickly across environments.

---

## 5️⃣ High Availability & Multi-AZ Architecture

In AWS architecture:

* Each Availability Zone must have separate subnets
* Load balancers span multiple subnets
* Databases replicate across zones

Without subnet understanding:

* HA cannot be implemented correctly
* Failover may not work
* Traffic routing may fail

---

## 6️⃣ Troubleshooting Production Issues

Common DevOps problems caused by subnet misunderstanding:

* ❌ "Instance cannot reach internet"
* ❌ "Pod cannot connect to database"
* ❌ "Service not reachable from load balancer"
* ❌ "VPN connected but no traffic flows"

Root causes often involve:

* Wrong subnet association
* Incorrect route table
* Missing NAT Gateway
* CIDR mismatch

Subnet knowledge allows faster debugging.

---

# 📊 Visual Summary

```
        VPC (10.0.0.0/16)
                |
    --------------------------------
    |              |               |
 Public         Private         Database
 Subnet         Subnet          Subnet
 /24             /24              /24
    |              |               |
 Load Balancer   App Servers      DB
```

Each subnet:

* Has its own routing
* Has its own security boundaries
* Controls traffic flow

---

## Key Takeaways

✅ IP addresses identify devices on a network  
✅ Private IPs are for internal networks  
✅ Public IPs are for internet communication  
✅ Subnetting helps organize and secure networks 

---

*Last Updated: 2024*  
*Author: SalvatoreOps*  
*License: Public Domain / Free to share*

---
