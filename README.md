Configuring Allowed VLANs and VTP Pruning Using Cisco Packet Tracer

Project Overview

This project demonstrates basic Cisco switching and VLAN security configurations using Cisco Packet Tracer.

The main objective was to configure VLANs, assign end devices to appropriate VLANs, establish trunk links between switches, and control which VLANs are allowed to traverse the trunk interfaces.

The project also covers VTP Pruning configuration to reduce unnecessary VLAN traffic across trunk links.

Project Objectives

* Create and name VLANs on multiple switches
* Assign switch ports to the appropriate VLANs
* Configure IP addresses on end devices
* Configure trunk links between switches
* Verify VLANs allowed on trunk interfaces
* Restrict unauthorized/unnecessary VLANs from crossing trunk links
* Configure VTP Pruning
* Test connectivity before and after VLAN restrictions
* Verify the final configuration using Cisco IOS show commands

Network Topology

The topology consists of two Cisco switches connected through trunk links.

End devices are placed into different VLANs:

VLAN	Name	Purpose
VLAN 10	IT	IT network
VLAN 20	HR	HR network
VLAN 30	Finance	Finance network
VLAN 40	Hacker-1	Untrusted/test VLAN
VLAN 50	Hacker-2	Untrusted/test VLAN

Configuration Steps

1. Create the Network Topology

Created the required topology in Cisco Packet Tracer with:

* Two Cisco switches
* Multiple end devices
* Trunk connections between the switches
* Separate VLANs for different network segments

2. Configure IP Addresses

Configured IP addresses for the end devices according to their respective VLAN networks.

Example:

* VLAN 10 → 10.10.x.x
* VLAN 20 → 20.20.x.x
* VLAN 30 → 30.30.x.x

3. Create and Name VLANs

Created and named the required VLANs on the switches:

VLAN 10  → IT
VLAN 20  → HR
VLAN 30  → Finance
VLAN 40  → Hacker-1
VLAN 50  → Hacker-2

4. Assign Access Ports to VLANs

Configured end-device switch ports as access ports and assigned them to their respective VLANs.

Example:

interface fa0/3
switchport mode access
switchport access vlan 10

Similar configurations were applied for VLANs 20 and 30.

5. Configure Trunk Links

Configured the inter-switch interfaces as trunk ports.

Example:

interface range fa0/23-24
switchport mode trunk

These trunk links allow VLAN traffic to travel between the switches.

6. Verify Allowed VLANs on Trunk Interfaces

Verified the VLANs allowed across the trunk using:

show interfaces trunk

Initially, the trunk allowed all VLANs by default.

This means even unnecessary or untrusted VLANs could potentially traverse the trunk.

7. Restrict VLANs on the Trunk

Instead of allowing every VLAN, configured the trunk to carry only the required VLANs.

Example:

interface range fa0/23-24
switchport trunk allowed vlan 10,20,30

This configuration allows only:

VLAN 10
VLAN 20
VLAN 30

VLANs 40 and 50 are prevented from traversing the trunk.

8. Test and Verify Connectivity

Connectivity was tested between devices before and after applying the VLAN restrictions.

For example:

* Communication between devices in allowed VLANs was successful.
* Traffic from a restricted VLAN was prevented from crossing the trunk.

The configuration was verified using:

show interfaces trunk

and connectivity tests using:

ping <destination-ip>

9. VTP Pruning Configuration

VTP Pruning was configured as an additional switching optimization to prevent unnecessary broadcast, multicast, and unknown-unicast traffic from being forwarded through trunk links where it is not required.

This helps reduce unnecessary traffic and improves network efficiency in larger VLAN environments.

Key Commands Used

show vlan brief
show interfaces trunk
interface fa0/3
switchport mode access
switchport access vlan 10
interface range fa0/23-24
switchport mode trunk
switchport trunk allowed vlan 10,20,30

Key Learning Outcomes

Through this project, I practiced:

* VLAN creation and management
* VLAN naming
* Access port configuration
* Trunk port configuration
* Allowed VLAN configuration
* VLAN traffic restriction
* Basic Layer 2 security concepts
* VTP Pruning
* Network connectivity testing
* Cisco IOS verification commands
* Troubleshooting VLAN and trunk connectivity

Project Result

The final configuration successfully restricted trunk traffic to the required VLANs while preventing unnecessary/untrusted VLANs from traversing the trunk.

This demonstrates how VLAN segmentation, trunk VLAN filtering, and VTP Pruning can be used to improve Layer 2 network control, security, and efficiency.
