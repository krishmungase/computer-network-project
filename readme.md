# Trading Operations Support Centre - Network Infrastructure Design

## Overview
This document outlines the network design and implementation plan for the Trading Operations Support Centre’s relocation to a new facility. The objective is to establish a reliable, scalable, and secure network infrastructure that meets current business operations and supports future growth.

---

## 1. Logical Design Summary
- Network simulation and configuration will be implemented using **Cisco Packet Tracer**.  
- The design follows a **three-layer hierarchical model** — Core, Distribution, and Access.  
- **High availability** is achieved with redundant devices, including **two routers** and **two multilayer switches**.

---

## 2. Departmental Floor Layout

### Ground Floor
- **Sales & Marketing Unit** – 120 users  
- **HR & Logistics Division** – 120 users  

### First Floor
- **Finance & Accounting Section** – 120 users  
- **Administration & Public Relations Department** – 120 users  

### Second Floor
- **ICT Operations Department** – 120 users  
- **Server Room** – 12 devices (servers, DHCP, DNS, and core network hardware)

---

## 3. Network Design Requirements

### Redundancy and Internet Connectivity
- Dual connectivity to **two separate ISPs** to ensure uninterrupted access.  
- Each router will have uplinks to both ISPs using the allocated public IP subnets:
  - `195.136.17.0/30`  
  - `195.136.17.4/30`

### Wireless Networks
- Each department will be assigned a **dedicated wireless SSID** for internal user access.  
- Wireless Access Points (WAPs) will be installed on every floor for full coverage.

### VLAN and IP Addressing
- Base private network: **172.16.1.0/16**  
- Each department is assigned its own **VLAN** and **subnet** to segment traffic logically.  
- Subnetting will be based on the required number of users per department.

### DHCP and Static IP Assignment
- A **DHCP server** (located in the server room) will automatically assign IP addresses to end-user devices.  
- **Static IPs** will be used for servers, routers, and switches for stability and consistency.

### Routing and Switching
- **Inter-VLAN routing** will be performed by multilayer switches (Layer 3).  
- **OSPF (Open Shortest Path First)** protocol will handle route advertisement between routers and switches.  

### Security and Access Control
- **SSH** will be configured on all routers and Layer 3 switches for secure administrative access.  
- **Port security** will be applied to the **Finance & Accounting VLAN**, allowing only authorized devices using **sticky MAC addresses**.  
- Violation mode will be set to **shutdown** to disable ports upon unauthorized access.

### NAT and ACLs
- **Port Address Translation (PAT)** will be configured on the outbound router interface to allow internal users to share ISP-assigned public IPs.  
- **Access Control Lists (ACLs)** will manage and restrict traffic as per company policies.

---

## 4. Device Configuration Standards
Each device in the network will follow these baseline configurations:
- Assign a unique **hostname** based on function and floor.  
- Configure **console and enable passwords** for device protection.  
- Set up **login banners** to display security warnings.  
- Disable **IP domain lookup** to prevent command errors.

---

## 5. Future Scalability
- VLAN design allows easy addition of new departments or users.  
- Redundant links and routing ensure minimal downtime.  
- Modular device configuration enables future upgrades without major reconfiguration.

---

## Tools and Technologies
- **Cisco Packet Tracer**
- **Routers:** Cisco 2900 Series  
- **Switches:** Cisco 3560 Multilayer Switches  
- **Routing Protocol:** OSPF  
- **IP Management:** DHCP  
- **Security:** SSH, Port Security, ACLs  
- **Address Translation:** PAT  

---

## Project Members
1. **Krishna Mungase**  
2. **Srushti Kapase**  
3. **Adhven Patil**
