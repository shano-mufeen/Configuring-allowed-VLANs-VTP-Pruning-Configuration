# 🔐 Configuring Allowed VLANs & VTP Pruning

### 🖥️ Cisco Packet Tracer | Switching Technologies | Layer 2 Networking

---

## 📌 Project Overview

This project demonstrates the configuration and verification of **VLANs, Access Ports, Trunk Links, Allowed VLANs, and VTP Pruning** using **Cisco Packet Tracer**.

The primary objective of this project is to understand how VLAN traffic can be controlled across trunk links by allowing only the required VLANs and restricting unnecessary or unauthorized VLAN traffic.

It also demonstrates how **VTP Pruning** can help reduce unnecessary Layer 2 traffic across trunk links.

---

## 🎯 Project Objectives

The main objectives of this project were to:

* 🔹 Create and name multiple VLANs
* 🔹 Configure IP addresses on end devices
* 🔹 Assign switch ports to appropriate VLANs
* 🔹 Configure trunk links between switches
* 🔹 Verify VLANs allowed on trunk interfaces
* 🔹 Restrict unnecessary VLANs from trunk links
* 🔹 Configure VTP Pruning
* 🔹 Test network connectivity using `ping`
* 🔹 Verify configurations using Cisco IOS commands
* 🔹 Understand basic Layer 2 traffic control and security

---

## 🗺️ Network Topology

The topology consists of:

* 🖧 2 Cisco switches
* 💻 Multiple end devices
* 🔗 Trunk links between the switches
* 🏷️ Multiple VLANs for network segmentation

### VLAN Structure

| VLAN ID | VLAN Name | Purpose             |
| ------: | --------- | ------------------- |
|      10 | IT        | IT Network          |
|      20 | HR        | HR Network          |
|      30 | Finance   | Finance Network     |
|      40 | Hacker-1  | Untrusted/Test VLAN |
|      50 | Hacker-2  | Untrusted/Test VLAN |

---

## ⚙️ Configuration Workflow

### 1️⃣ Build the Network Topology

Created the required network topology in Cisco Packet Tracer with two switches, end devices, and inter-switch connections.

---

### 2️⃣ Configure IP Addresses

Assigned IP addresses to the end devices according to their respective VLAN networks.

Example:

```text
VLAN 10 → 10.10.x.x
VLAN 20 → 20.20.x.x
VLAN 30 → 30.30.x.x
```

---

### 3️⃣ Create and Name VLANs

Created and named the required VLANs on the switches.

```text
VLAN 10 → IT
VLAN 20 → HR
VLAN 30 → Finance
VLAN 40 → Hacker-1
VLAN 50 → Hacker-2
```

Example configuration:

```bash
enable
configure terminal

vlan 10
name IT

vlan 20
name HR

vlan 30
name Finance

vlan 40
name Hacker-1

vlan 50
name Hacker-2

exit
```

---

### 4️⃣ Assign Access Ports

Configured end-device interfaces as access ports and assigned them to the appropriate VLANs.

Example:

```bash
interface fa0/3
switchport mode access
switchport access vlan 10
```

Similar configurations were applied to the required ports for VLAN 20 and VLAN 30.

---

### 5️⃣ Configure Trunk Links

Configured the inter-switch interfaces as trunk ports.

Example:

```bash
interface range fa0/23-24
switchport mode trunk
```

🔗 The trunk links allow multiple VLANs to travel between the switches.

---

### 6️⃣ Verify Allowed VLANs

Verified the VLANs currently allowed across the trunk interfaces.

```bash
show interfaces trunk
```

Initially, the trunk interfaces allowed multiple VLANs, including the unnecessary/test VLANs.

⚠️ This demonstrates why controlling the VLANs allowed on trunk links is important.

---

### 7️⃣ Restrict Allowed VLANs

Configured the trunk interfaces to allow only the required VLANs.

```bash
interface range fa0/23-24
switchport trunk allowed vlan 10,20,30
```

✅ Allowed VLANs:

```text
VLAN 10
VLAN 20
VLAN 30
```

🚫 Restricted VLANs:

```text
VLAN 40
VLAN 50
```

This prevents the restricted VLANs from traversing the configured trunk links.

---

### 8️⃣ Test & Verify Connectivity

Connectivity was tested before and after restricting the allowed VLANs.

Example:

```bash
ping <destination-ip>
```

### ✅ Before VLAN Restriction

Devices in the relevant VLANs were able to communicate across the trunk.

### 🚫 After VLAN Restriction

Traffic belonging to restricted VLANs was prevented from crossing the configured trunk link.

The result was verified using:

```bash
show interfaces trunk
```

---

### 9️⃣ VTP Pruning

Configured **VTP Pruning** as an additional Layer 2 traffic optimization technique.

VTP Pruning helps prevent unnecessary VLAN traffic from being forwarded across trunk links when that traffic is not required on the neighboring switch.

### 💡 Benefit

VTP Pruning can help:

* 📉 Reduce unnecessary Layer 2 traffic
* 🚀 Improve network efficiency
* 🔗 Optimize trunk link utilization
* 🛡️ Improve control over VLAN traffic propagation

---

## 🔑 Important Cisco IOS Commands

### 🔍 View VLANs

```bash
show vlan brief
```

### 🔗 View Trunk Configuration

```bash
show interfaces trunk
```

### 🏷️ Create VLAN

```bash
vlan 10
name IT
```

### 🔌 Configure Access Port

```bash
interface fa0/3
switchport mode access
switchport access vlan 10
```

### 🔗 Configure Trunk

```bash
interface range fa0/23-24
switchport mode trunk
```

### 🚦 Allow Specific VLANs on Trunk

```bash
switchport trunk allowed vlan 10,20,30
```

### 🧪 Test Connectivity

```bash
ping <destination-ip>
```

---

## 🧪 Verification

The following commands were used to verify the configuration:

```bash
show vlan brief
show interfaces trunk
```

The verification confirmed that:

* ✅ Required VLANs were created
* ✅ Access ports were assigned correctly
* ✅ Trunk links were operational
* ✅ Only the required VLANs were permitted on the configured trunk
* ✅ Restricted VLAN traffic was prevented from crossing the trunk
* ✅ Connectivity behavior changed according to the VLAN restrictions

---

## 🧠 Key Concepts Learned

Through this hands-on project, I gained practical experience with:

* 🏷️ VLAN Configuration
* 🔌 Access Port Configuration
* 🔗 Trunk Port Configuration
* 🚦 Allowed VLAN Filtering
* 🛡️ Basic Layer 2 Security
* 🌐 VLAN Segmentation
* ✂️ Restricting Unnecessary VLAN Traffic
* 🌳 VTP Pruning
* 🧪 Network Connectivity Testing
* 🔍 Cisco IOS Verification Commands
* 🛠️ Basic Layer 2 Troubleshooting

---

## 💡 Key Takeaway

> **Do not allow unnecessary VLANs across trunk links.**

By configuring only the required VLANs on a trunk interface, network administrators can gain better control over VLAN traffic and reduce unnecessary traffic propagation.

Combining **VLAN segmentation, allowed VLAN filtering, and VTP Pruning** provides a practical approach to improving Layer 2 network efficiency and control.

---

## 🛠️ Technologies & Tools

| Category              | Technology           |
| --------------------- | -------------------- |
| 🖥️ Network Simulator | Cisco Packet Tracer  |
| 🌐 Networking         | Cisco Switching      |
| 🏷️ VLAN              | IEEE 802.1Q VLAN     |
| 🔗 Trunking           | Switch Trunk Links   |
| 🌳 VLAN Management    | VTP Pruning          |
| 💻 CLI                | Cisco IOS            |
| 🧪 Testing            | Ping / Show Commands |

---


## 👨‍💻 Project Type

**Hands-on Networking Lab**

📚 **Learning Area:** Switching Technologies
🎯 **Focus:** VLAN & Trunk Configuration
🖥️ **Platform:** Cisco Packet Tracer
🔰 **Level:** Beginner / Entry-Level Network Engineering

---

## 🚀 Future Improvements

The lab can be extended by adding:

* 🔹 VTP Server / Client configuration
* 🔹 Inter-VLAN Routing
* 🔹 Router-on-a-Stick
* 🔹 Layer 3 Switch Configuration
* 🔹 EtherChannel
* 🔹 STP Configuration
* 🔹 Port Security
* 🔹 DHCP Configuration
* 🔹 Extended VLAN Security Testing

---

⭐ **This project is part of my hands-on networking practice focused on developing practical Cisco switching and Layer 2 networking skills.**
