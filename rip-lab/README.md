# RIP Routing Lab (GNS3)

## 📌 Objective
Configure two routers (R1 and R2) using **RIP v2** for dynamic routing, enabling communication between two LANs.

---

## 🖧 Topology
- **PC1** → 192.168.0.10/24  
- **R1 LAN** → 192.168.0.1/24  
- **R1 WAN** → 10.0.0.1/30  
- **R2 WAN** → 10.0.0.2/30  
- **R2 LAN** → 192.168.1.1/24  
- **PC2** → 192.168.1.10/24  

---

## ⚙️ Configuration

### R1
interface FastEthernet0/0
 ip address 192.168.0.1 255.255.255.0
 no shutdown

interface FastEthernet5/0
 ip address 10.0.0.1 255.255.255.252
 no shutdown

router rip
 version 2
 network 192.168.0.0
 network 10.0.0.0

 ### R2 
 interface FastEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown

interface FastEthernet5/0
 ip address 10.0.0.2 255.255.255.252
 no shutdown

router rip
 version 2
 network 192.168.1.0
 network 10.0.0.0


### PC1
ip 192.168.0.10 255.255.255.0 192.168.0.1


### PC2
ip 192.168.1.10 255.255.255.0 192.168.1.1




Verification
sh ip route 
ping <ip>


