# Name : Aashika Parveen M R
# Reg.no: 212223060002
# Cycle-1-2-Implementation-of-distance-vector-routing-protocol-RIP-Cisco-packet-tracer
# 🧪 EXPT.NO: 2  
📅 DATE: *(14-11-2026)*

## 📌 TITLE  
**Implementation of Distance Vector Routing Protocol (RIP)**

---

## 🎯 AIM  
To connect computers in multiple networks using Distance Vector Routing Protocol and to verify the connectivity between computers.

---

## 🛠️ EQUIPMENTS REQUIRED

| S.No | Name                   | Quantity |
|------|------------------------|----------|
| 1    | Desktop Computer       | 4        |
| 2    | Cisco 1800 Router      | 2        |
| 3    | USB to Serial Converter| 2        |
| 4    | Cisco 2900 Switch      | 2        |
| 5    | CAT 6 Patch Cable      | 10       |
| 6    | Console Cable          | 2        |

---

## 🌐 IP ASSIGNMENT

| Name       | IP Address     | Subnet Mask     | Network      | Class | Gateway        |
|------------|----------------|-----------------|--------------|-------|----------------|
| PC0        | 192.168.0.1    | 255.255.255.0   | 192.168.0.0  | C     | 192.168.0.200  |
| PC1        | 192.168.0.2    | 255.255.255.0   | 192.168.0.0  | C     | 192.168.0.200  |
| PC2        | 192.168.1.1    | 255.255.255.0   | 192.168.1.0  | C     | 192.168.1.200  |
| PC3        | 192.168.1.2    | 255.255.255.0   | 192.168.1.0  | C     | 192.168.1.200  |
| PC4        | 192.168.2.1    | 255.255.255.0   | 192.168.2.0  | C     | 192.168.2.200  |
| PC5        | 192.168.2.2    | 255.255.255.0   | 192.168.2.0  | C     | 192.168.2.200  |
| Router0 F0/0 | 192.168.0.200 | 255.255.255.0   | 192.168.0.0  | C     | —              |
| Router0 S2/0| 192.168.1.200 | 255.255.255.0   | 192.168.1.0  | C     | —              |
| Router1 F0/0| 192.168.1.201 | 255.255.255.0   | 192.168.1.0  | C     | —              |
| Router1 S2/0| 192.168.2.200 | 255.255.255.0   | 192.168.2.0  | C     | —              |

---

## 🗺️ NETWORK DIAGRAM  
*(Insert diagram or screenshot from Packet Tracer)*

---
<img width="840" height="542" alt="image" src="https://github.com/user-attachments/assets/ffcdce2d-d32b-4c73-82d8-59ae5408b095" />

## 🧭 PROCEDURE

1. Open Cisco Packet Tracer software.  
2. Drag two 2900 switches, two Cisco 1800 routers, and four PC terminals into the workspace.  
3. Connect all devices using CAT 6 patch cables as per the network diagram.  
4. Configure IP addresses and gateways for all PCs.  
5. Configure and restart Router0.  
6. Configure and restart Router1.  
7. Verify connectivity between PCs using the `ping` command.

### Additional IP Configuration for PCs

| PC   | IP Address     | Subnet Mask     | Gateway        |
|------|----------------|-----------------|----------------|
| PC0  | 192.168.1.2    | 255.255.255.0   | 192.168.1.1    |
| PC1  | 192.168.1.3    | 255.255.255.0   | 192.168.1.1    |
| PC2  | 192.168.2.2    | 255.255.255.0   | 192.168.2.1    |
| PC3  | 192.168.3.2    | 255.255.255.0   | 192.168.3.1    |
| PC4  | 192.168.4.2    | 255.255.255.0   | 192.168.4.1    |
| PC5  | 192.168.4.3    | 255.255.255.0   | 192.168.4.1    |

---

## 💻 PROGRAM

### 🔧 Router0 Configuration

```bash
Router> enable
Router# configure terminal
Router(config)# interface FastEthernet0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit
Router(config)# interface FastEthernet0/1
Router(config-if)# ip address 192.168.2.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit
Router(config)# router rip
Router(config-router)# version 2
Router(config-router)# network 192.168.1.0
Router(config-router)# network 192.168.2.0
Router(config-router)# exit
```
### 🔧 Router1 Configuration
```bash
Router> enable
Router# configure terminal
Router(config)# interface FastEthernet0/0
Router(config-if)# ip address 192.168.3.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit
Router(config)# interface FastEthernet0/1
Router(config-if)# ip address 192.168.4.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit
Router(config)# router rip
Router(config-router)# version 2
Router(config-router)# network 192.168.3.0
Router(config-router)# network 192.168.4.0
Router(config-router)# exit
```


## ✅ OUTPUT VERIFICATION

## 🔍 Show RIP Routing Table
### Router# show ip route
<img width="702" height="246" alt="image" src="https://github.com/user-attachments/assets/033250ff-08ac-4d88-90c8-4c3f539f129f" />

### Expected output on Router0:
```
R 192.168.3.0 [120/1] via 192.168.2.2, FastEthernet0/1
R 192.168.4.0 [120/1] via 192.168.2.2, FastEthernet0/1
```
---


### Expected output on Router1:
```
R 192.168.1.0 [120/1] via 192.168.2.1, FastEthernet0/0
R 192.168.2.0 [120/1] via 192.168.2.1, FastEthernet0/0
```
---
<img width="791" height="325" alt="image" src="https://github.com/user-attachments/assets/1944e47d-4432-42db-8f4f-b27194460c14" />


## 📶 Ping Test Between PCs
Example: Ping from PC0 to PC3
C:\> ping 192.168.3.2
### Expected result: Successful replies from PC3.

### Repeat similar tests between other PCs (e.g., PC2 to PC5).

## 📤 OUTPUT
---
<img width="557" height="392" alt="image" src="https://github.com/user-attachments/assets/f77ef637-2105-44d6-85b2-b7b80a2a2673" />


## 📝 RESULT
Thus, the computers in multiple networks using Distance Vector Routing Protocol are successfully connected and the connectivity between them is verified.
