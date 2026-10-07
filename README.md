# MICRO-SOFT-VIRTUAL-NETWORK-PEERING # Microsoft Azure Virtual Network & VNet Peering Lab

## Overview

This project demonstrates the design and configuration of Microsoft Azure Virtual Networks (VNets), subnetting, virtual machines, VNet peering, and network connectivity testing using Azure Network Watcher.

The lab was designed to simulate two separate environments:

- **Core IT Network**
- **Manufacturing Network**

The two networks were deployed as separate Azure VNets and connected using **VNet Peering** to allow communication between resources in both environments.

## Technologies and Azure Services Used

- Microsoft Azure
- Azure Virtual Network (VNet)
- Subnets
- Virtual Machines (VMs)
- VNet Peering
- Network Security Groups (NSGs)
- Azure Network Watcher
- IP Addressing and CIDR
- Network Connectivity Testing

## Lab Architecture

The environment consisted of two independent Azure Virtual Networks representing different business environments.

### Core IT Network

The Core IT environment contained a dedicated Azure VNet with its own address space and subnet. A virtual machine was deployed inside the network to represent an IT workload.

### Manufacturing Network

The Manufacturing environment was created as a separate Azure VNet with its own address space and subnet. A virtual machine was deployed inside this network to represent a manufacturing workload.

### VNet Peering

VNet Peering was configured between the Core IT Network and the Manufacturing Network.

This allowed resources in the two VNets to communicate privately over the Azure backbone without requiring public IP communication.

The basic architecture was:

Core IT VNet → VNet Peering → Manufacturing VNet

VM in Core IT → Private Network Communication → VM in Manufacturing

## IP Addressing and CIDR Planning

One of the most important parts of this lab was planning the VNet address spaces correctly.

Each VNet was assigned a CIDR block large enough to accommodate the current resources while also allowing room for future expansion.

A major lesson from this lab was that **CIDR planning should not only consider the resources being deployed today**. The address space should provide enough room for additional subnets, virtual machines, applications, and other network resources that may be required in the future.

### Important CIDR Lessons

- VNet address spaces must be properly planned before deployment.
- Peered VNets should not have overlapping IP address ranges.
- Subnets must fall within the VNet address space.
- Address spaces should provide room for future growth.
- Poor CIDR planning can make future expansion difficult.
- Changing network address spaces later can be more complicated than planning them correctly from the beginning.

## Virtual Machines

Virtual machines were deployed inside the different VNets to represent workloads in the IT and Manufacturing environments.

The VMs were connected to their respective subnets and used to test communication between the two networks.

The lab demonstrated how Azure VMs communicate using private IP addresses within and across appropriately configured VNets.

## VNet Peering Configuration

VNet Peering was configured between the two VNets.

The peering configuration allowed traffic to flow between the Core IT and Manufacturing networks.

The general process was:

1. Create the Core IT VNet.
2. Create the Manufacturing VNet.
3. Create appropriate subnets inside each VNet.
4. Deploy virtual machines into the subnets.
5. Configure VNet Peering between the two VNets.
6. Verify the peering status.
7. Test network connectivity between resources.
8. Troubleshoot connectivity issues where necessary.

## Network Security

Network security was considered when configuring communication between the environments.

Network Security Groups (NSGs) can be used to control inbound and outbound traffic to Azure resources.

When troubleshooting connectivity, it is important to check:

- NSG inbound rules
- NSG outbound rules
- Subnet configuration
- VM network interface configuration
- Private IP addresses
- Route configuration
- VNet peering status
- Firewall settings

## Azure Network Watcher

Azure Network Watcher was used to test and troubleshoot connectivity within the Azure environment.

Network Watcher provides tools that help identify network connectivity problems and understand how traffic moves between Azure resources.

Connectivity testing was useful for verifying whether the virtual machines could communicate across the peered VNets.

The testing process helped demonstrate that successful VNet Peering configuration does not automatically mean every application or port will be reachable. Security rules and service configuration must also allow the required traffic.

## Key Challenges and Lessons Learned

### 1. CIDR Address Planning

One of the biggest lessons from this project was the importance of selecting appropriate CIDR blocks.

The address space needs to be large enough for the current deployment and future growth.

For example, creating a VNet with an address range that is too small may work initially but become a problem when additional subnets or workloads need to be added.

### 2. Avoiding Overlapping Address Spaces

VNet Peering requires careful IP address planning.

Overlapping address spaces between VNets can cause routing and connectivity problems.

Therefore, each VNet should have a clearly defined and non-overlapping address range.

### 3. Network Troubleshooting

Azure Network Watcher provides valuable tools for diagnosing connectivity problems.

Instead of assuming that a failed connection is caused by VNet Peering, network troubleshooting should examine the entire communication path, including:

**VM → NIC → NSG → Subnet → VNet → VNet Peering → Destination VNet → Destination VM**

### 4. Planning for Future Growth

A cloud network should be designed with scalability in mind.

Network architecture should consider future:

- Virtual machines
- Applications
- Subnets
- Workloads
- Security requirements
- Network connections

Good network planning reduces the need for major redesigns later.

## What I Learned

Through this project, I gained practical experience with:

- Creating Azure Virtual Networks.
- Creating and configuring subnets.
- Deploying Azure Virtual Machines.
- Connecting separate VNets using VNet Peering.
- Understanding private IP communication in Azure.
- Working with CIDR address ranges.
- Avoiding overlapping network ranges.
- Using Azure Network Watcher for connectivity testing.
- Troubleshooting Azure network connectivity.
- Understanding the importance of scalable network architecture.
- Designing networks with future growth in mind.

## Real-World Use Case

A company may have separate networks for different departments or business operations.

For example:

**Core IT Network**
- Application servers
- Internal services
- IT management systems

**Manufacturing Network**
- Production systems
- Manufacturing applications
- Industrial workloads

These environments can remain logically separated while still communicating through controlled VNet Peering.

This approach provides network segmentation while allowing required communication between business environments.

## Skills Demonstrated

**Cloud:** Microsoft Azure

**Networking:** VNet, Subnets, CIDR, Private IP, VNet Peering, NSGs

**Compute:** Azure Virtual Machines

**Monitoring & Troubleshooting:** Azure Network Watcher

**Architecture:** Cloud Network Design, Network Segmentation, Connectivity Testing

## Conclusion

This Microsoft Azure Virtual Network project provided practical experience designing and troubleshooting cloud networking infrastructure.

The most important takeaway was that successful cloud networking starts with good IP address planning. CIDR ranges should be carefully selected, networks should avoid overlapping address spaces, and the architecture should provide enough capacity for future growth.

The project also demonstrated how Azure VNet Peering can connect separate network environments while maintaining logical network separation.

This lab strengthened my practical understanding of **Microsoft Azure networking, VNet architecture, subnetting, CIDR planning, VNet Peering, virtual machines, and network troubleshooting**.
