# 🌐 Smart Office VLAN Configuration | Cisco Packet Tracer

**One Office. Four Departments. Four VLANs. One Switch.**

A Cisco Packet Tracer networking project demonstrating how to segment a physical office network into four logical networks using Virtual Local Area Networks (VLANs).

The office contains four departments: IT, Sales, Marketing, and Finance. Each department is assigned a separate VLAN to organize network traffic and provide logical separation between departments.

## 📌 Project Overview

- **Project Name:** Smart Office VLAN Configuration
- **Technology:** Cisco Packet Tracer
- **Device:** Cisco Catalyst 2960 Switch
- **Networking Concept:** VLANs and Access Port Configuration
- **Departments:** IT, Sales, Marketing, Finance
- **Number of VLANs:** 4
- **Number of PCs:** 15
- **Router Required:** No, for this VLAN-only demonstration

## 🏢 Network Topology

The office uses one physical switch to connect computers <img width="872" height="337" alt="Screenshot 2026-10-27 112449" src="https://github.com/user-attachments/assets/ecd5ed0f-6946-4a7f-861a-42f6a06b7363" />
from four different departments.


### Department Segmentation

| Department | VLAN ID | Network Address | Color |
|---|---:|---|---|
| IT | 10 | `192.168.10.0/24` | Yellow |
| Sales | 20 | `192.168.10.0/24` | Pink |
| Marketing | 30 | `192.168.10.0/24` | Green |
| Finance | 40 | `192.168.10.0/24` | Purple |

## 🎯 Project Objectives

- Understand VLANs and logical network segmentation.
- Create multiple VLANs on a Cisco switch.
- Assign switch access ports to the appropriate VLANs.
- Configure IP addresses for PCs in different departments.
- Verify VLAN membership using Cisco IOS commands.
- Test communication between devices in the same VLAN.
- Understand why communication between different IP subnets requires Layer 3 routing.

## 🧰 Devices Required

| Device | Quantity |
|---|---:|
| Cisco 2960 Switch | 1 |
| PCs | 15 |
| Copper Straight-Through Cables | 15 |

## 🔌 Port Assignment

| Switch Port | Connected Devices | VLAN |
|---|---|---:|
| `Fa0/1` | PC1 — IT | 10 |
| `Fa0/2` | PC2 — IT | 10 |
| `Fa0/3` | PC3 — Sales | 20 |
| `Fa0/4` | PC4 — Sales | 20 |
| `Fa0/5` | PC5 — Marketing | 30 |
| `Fa0/6` | PC6 — Marketing | 30 |
| `Fa0/7` | PC7 — Finance | 40 |
| `Fa0/8` | PC8 — Finance | 40 | .........

## 💻 Cisco Switch Configuration

### Step 1: Enter Privileged EXEC Mode

```text
enable
configure terminal
```

### Step 2: Create VLANs

```text
vlan 10
name IT
exit

vlan 20
name SALES
exit

vlan 30
name MARKETING
exit

vlan 40
name FINANCE
exit
```

### Step 3: Assign Access Ports

**IT Department — VLAN 10**

```text
interface range fa0/1-4
switchport mode access
switchport access vlan 10
exit
```

**Sales Department — VLAN 20**

```text
interface range fa0/5-7
switchport mode access
switchport access vlan 20
exit
```

**Marketing Department — VLAN 30**

```text
interface range fa0/8-11
switchport mode access
switchport access vlan 30
exit
```

**Finance Department — VLAN 40**

```text
interface range fa0/12-15
switchport mode access
switchport access vlan 40
exit
```

### Step 4: Save the Configuration

```text
end
copy running-config startup-config
```

Press Enter if prompted to confirm the destination filename.

## 🌐 IP Address Configuration

Configure each PC through **Desktop → IP Configuration** in Cisco Packet Tracer.

| PC | IP Address | Subnet Mask |
|---|---|---|
| PC1 | `192.168.10.1` | `255.255.255.0` |
| PC2 | `192.168.10.2` | `255.255.255.0` |
| PC3 | `192.168.10.3` | `255.255.255.0` |
| PC4 | `192.168.10.4` | `255.255.255.0` |
| PC5 | `192.168.10.5` | `255.255.255.0` |
| PC6 | `192.168.10.6` | `255.255.255.0` |
| PC7 | `192.168.10.7` | `255.255.255.0` |
| PC8 | `192.168.10.8` | `255.255.255.0` |   ......

**Note:** Default gateways are not required for this VLAN-only lab because no inter-VLAN routing is configured.

## 🔍 Verification Commands

Use the following commands on the switch to verify the configuration.

### Display VLANs

```text
show vlan brief
```

Expected result: VLANs 10, 20, 30, and 40 appear with the correct names and assigned access ports.

### View the Running Configuration

```text
show running-config
```

### View Switch Port Status

```text
show interfaces status
```

## 🧪 Connectivity Testing

### Test 1: Communication Within the Same VLAN

From PC1, open **Desktop → Command Prompt** and enter:

```text
ping 192.168.10.2
```

Expected result: PC1 can communicate with PC2 because both belong to VLAN 10 and the same IP subnet.

Repeat the test for PCs in the other departments.

### Test 2: Communication Between Different VLANs

From PC1, enter:

```text
ping 192.168.20.11
```

Expected result: The ping fails because PC1 and PC11 belong to different IP subnets and no Layer 3 routing is configured.

**Important:** VLANs provide logical separation, but a VLAN alone is not a complete security policy. Inter-VLAN communication can be enabled later using a router or Layer 3 switch, with ACLs where appropriate.

## 📚 Concepts Learned

- Virtual Local Area Networks (VLANs)
- Cisco IOS command-line interface
- VLAN creation and naming
- Access port configuration
- IP addressing and subnet masks
- Same-VLAN connectivity testing
- Network segmentation
- Basic network troubleshooting

## 🚀 How to Run This Project

1. Install Cisco Packet Tracer.
2. Download or clone this repository.
3. Open the `.pkt` project file.
4. Inspect the switch topology and PC connections.
5. Review the IP address assignments.
6. Verify VLANs using `show vlan brief`.
7. Test connectivity using the PC command prompts.

## 📁 Repository Structure

```text
Smart-Office-VLAN/
├── README.md
├── Smart_Office_VLAN.pkt
├── smart-office-vlan.png
└── commands.txt
```

Replace the example filenames with the actual filenames you upload to GitHub.


## 👩‍💻 Author

Created as a hands-on networking lab to practise Cisco switching and VLAN configuration using Cisco Packet Tracer.

**If you found this project helpful, give the repository a ⭐ star and follow for more CCNA networking projects!**

## 📄 Disclaimer

This is an educational simulation created using Cisco Packet Tracer. Device availability, command support, and interface names may vary depending on the selected device model and Packet Tracer version.
