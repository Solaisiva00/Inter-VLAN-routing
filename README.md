# 🧪 Exercise 3: Inter-VLAN Routing (Router-on-a-Stick)

Enable communication between VLANs using a router.

---

## 🛠️ Router Configuration (R1)


### 1. Enter Global Configuration Mode
```bash
Router>en
Router#config t
```

### 2. Remove IP from Physical Interface
```bash
Router(config)#interface GigabitEthernet0/0
Router(config-if)# no ip address
Router(config-if)# no shutdown
Router(config)#exit
```
### 3. Create Subinterface for VLAN 10
```bash
Router(config)#interface GigabitEthernet0/0.10
Router(config-if)#encapsulation dot1Q 10
Router(config-if)# ip address 192.168.10.1 255.255.255.0
Router(config)#exit
```

### 4. Create Subinterface for VLAN 20
```bash
Router(config)#interface GigabitEthernet0/0.20
Router(config-if)#encapsulation dot1Q 10
Router(config-if)# ip address 192.168.30.1 255.255.255.0
Router(config)#exit
```

---
## 💻 PC Configuration

### On PC2 (VLAN 20)
Update the default gateway:
```bash
Default Gateway: 192.168.30.1
```

## ✅ Verification Commands (on R1)

### 1. Check Routing Table
```bash
show ip route
```

Expected connected routes:
- 192.168.10.0/24  
- 192.168.20.0/24  
- 192.168.30.0/24

### 2. Check Interface Status
```bash
show ip interface brief
```
Should show:

- GigabitEthernet0/0.10 — 192.168.10.1 — up/up

- GigabitEthernet0/0.20 — 192.168.30.1 — up/up

---
### 🔄 Testing Connectivity
 - From PC1 to PC2
 - From PC2 to PC1 vice-versa
 - From both PCs, test connectivity to SW2 subnet

---
![Screenshot 2025-04-22 192628](https://github.com/user-attachments/assets/0e0bd904-72c1-4370-9430-fe4b6087493c)

