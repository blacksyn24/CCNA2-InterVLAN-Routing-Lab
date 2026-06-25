# 🌐 CCNA2 — Inter-VLAN Routing Lab
> Router-on-a-Stick | Entreprise LogiCom

![Cisco](https://img.shields.io/badge/Cisco-CCNA2-blue?style=for-the-badge&logo=cisco&logoColor=white)
![PacketTracer](https://img.shields.io/badge/Packet%20Tracer-8.x-orange?style=for-the-badge&logo=cisco)
![Status](https://img.shields.io/badge/Status-✅%20Completed-brightgreen?style=for-the-badge)
![VLANs](https://img.shields.io/badge/VLANs-5-purple?style=for-the-badge)
![Switches](https://img.shields.io/badge/Switches-2-red?style=for-the-badge)
![PCs](https://img.shields.io/badge/PCs-15-yellow?style=for-the-badge)
![Router](https://img.shields.io/badge/Router-1-lightblue?style=for-the-badge)

---

## 📋 Description

Ce TP simule le réseau de l'entreprise **LogiCom** composée de
5 départements répartis sur 2 étages. L'objectif est de :

- ✅ Segmenter le réseau avec des **VLANs**
- ✅ Assurer la communication inter-VLAN via **Router-on-a-Stick**
- ✅ Relier deux switches via un **lien trunk**
- ✅ Tester la connectivité entre tous les départements

---

## 🖥️ Équipements utilisés

| Équipement | Modèle | Nom | Quantité |
|-----------|--------|-----|----------|
| 🔀 Routeur | Cisco 2911 | R1 | 1 |
| 🔌 Switch | Cisco 2960-24TT | SW1 | 1 |
| 🔌 Switch | Cisco 2960-24TT | SW2 | 1 |
| 💻 PC | PC-PT | PC1 à PC15 | 15 |

---

## 🗺️ Topologie

```
              [R1 - 2911]
                   |
                 Gig0/0
                   |
                 Gig0/1
             [SW1 - 2960]
            /      |      \
        Fa0/1-3 Fa0/4-6 Fa0/7-9    Gig0/2
          |       |        |           |
       VLAN10  VLAN20   VLAN30       Gig0/1
       PC1-3   PC4-6    PC7-9    [SW2 - 2960]
                                  /         \
                              Fa0/1-3     Fa0/4-6
                                 |            |
                              VLAN40       VLAN50
                             PC10-12      PC13-15
```

---

## 🔌 Câblage

| De | Port | Vers | Port |
|----|------|------|------|
| R1 | Gig0/0 | SW1 | Gig0/1 |
| SW1 | Gig0/2 | SW2 | Gig0/1 |
| SW1 | Fa0/1 | PC1 | Fa0 |
| SW1 | Fa0/2 | PC2 | Fa0 |
| SW1 | Fa0/3 | PC3 | Fa0 |
| SW1 | Fa0/4 | PC4 | Fa0 |
| SW1 | Fa0/5 | PC5 | Fa0 |
| SW1 | Fa0/6 | PC6 | Fa0 |
| SW1 | Fa0/7 | PC7 | Fa0 |
| SW1 | Fa0/8 | PC8 | Fa0 |
| SW1 | Fa0/9 | PC9 | Fa0 |
| SW2 | Fa0/1 | PC10 | Fa0 |
| SW2 | Fa0/2 | PC11 | Fa0 |
| SW2 | Fa0/3 | PC12 | Fa0 |
| SW2 | Fa0/4 | PC13 | Fa0 |
| SW2 | Fa0/5 | PC14 | Fa0 |
| SW2 | Fa0/6 | PC15 | Fa0 |

---

## 📊 Plan d'adressage

| VLAN | 🏷️ Nom | Réseau | Passerelle | PCs | Switch |
|------|--------|--------|------------|-----|--------|
| 10 | 👔 DIRECTION | 192.168.10.0/24 | 192.168.10.1 | PC1,PC2,PC3 | SW1 |
| 20 | 💰 FINANCE | 192.168.20.0/24 | 192.168.20.1 | PC4,PC5,PC6 | SW1 |
| 30 | 👥 RH | 192.168.30.0/24 | 192.168.30.1 | PC7,PC8,PC9 | SW1 |
| 40 | 🛒 VENTES | 192.168.40.0/24 | 192.168.40.1 | PC10,PC11,PC12 | SW2 |
| 50 | 📦 LOGISTIQUE | 192.168.50.0/24 | 192.168.50.1 | PC13,PC14,PC15 | SW2 |
| 99 | 🔒 NATIF | — | — | aucun | SW1+SW2 |

---

## 🖥️ Adresses IP des PC

### VLAN 10 — 👔 DIRECTION (SW1 Fa0/1-3)
| PC | IP | Masque | Passerelle |
|----|-----|--------|------------|
| PC1 | 192.168.10.10 | 255.255.255.0 | 192.168.10.1 |
| PC2 | 192.168.10.11 | 255.255.255.0 | 192.168.10.1 |
| PC3 | 192.168.10.12 | 255.255.255.0 | 192.168.10.1 |

### VLAN 20 — 💰 FINANCE (SW1 Fa0/4-6)
| PC | IP | Masque | Passerelle |
|----|-----|--------|------------|
| PC4 | 192.168.20.10 | 255.255.255.0 | 192.168.20.1 |
| PC5 | 192.168.20.11 | 255.255.255.0 | 192.168.20.1 |
| PC6 | 192.168.20.12 | 255.255.255.0 | 192.168.20.1 |

### VLAN 30 — 👥 RH (SW1 Fa0/7-9)
| PC | IP | Masque | Passerelle |
|----|-----|--------|------------|
| PC7 | 192.168.30.10 | 255.255.255.0 | 192.168.30.1 |
| PC8 | 192.168.30.11 | 255.255.255.0 | 192.168.30.1 |
| PC9 | 192.168.30.12 | 255.255.255.0 | 192.168.30.1 |

### VLAN 40 — 🛒 VENTES (SW2 Fa0/1-3)
| PC | IP | Masque | Passerelle |
|----|-----|--------|------------|
| PC10 | 192.168.40.10 | 255.255.255.0 | 192.168.40.1 |
| PC11 | 192.168.40.11 | 255.255.255.0 | 192.168.40.1 |
| PC12 | 192.168.40.12 | 255.255.255.0 | 192.168.40.1 |

### VLAN 50 — 📦 LOGISTIQUE (SW2 Fa0/4-6)
| PC | IP | Masque | Passerelle |
|----|-----|--------|------------|
| PC13 | 192.168.50.10 | 255.255.255.0 | 192.168.50.1 |
| PC14 | 192.168.50.11 | 255.255.255.0 | 192.168.50.1 |
| PC15 | 192.168.50.12 | 255.255.255.0 | 192.168.50.1 |

---

## ⚙️ Configuration complète

### 🔧 SW1 — Switch principal

```cisco
enable
configure terminal
hostname SW1

vlan 10
name DIRECTION
exit
vlan 20
name FINANCE
exit
vlan 30
name RH
exit
vlan 40
name VENTES
exit
vlan 50
name LOGISTIQUE
exit
vlan 99
name NATIF
exit

interface range fa0/1-3
switchport mode access
switchport access vlan 10
exit

interface range fa0/4-6
switchport mode access
switchport access vlan 20
exit

interface range fa0/7-9
switchport mode access
switchport access vlan 30
exit

interface gig0/1
switchport mode trunk
switchport trunk native vlan 99
switchport trunk allowed vlan 10,20,30,40,50,99
exit

interface gig0/2
switchport mode trunk
switchport trunk native vlan 99
switchport trunk allowed vlan 10,20,30,40,50,99
exit

end
write
```

---

### 🔧 SW2 — Switch secondaire

```cisco
enable
configure terminal
hostname SW2

vlan 40
name VENTES
exit
vlan 50
name LOGISTIQUE
exit
vlan 99
name NATIF
exit

interface range fa0/1-3
switchport mode access
switchport access vlan 40
exit

interface range fa0/4-6
switchport mode access
switchport access vlan 50
exit

interface gig0/1
switchport mode trunk
switchport trunk native vlan 99
switchport trunk allowed vlan 40,50,99
exit

end
write
```

---

### 🔧 R1 — Routeur 2911

```cisco
enable
configure terminal
hostname R1

interface gig0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
exit

interface gig0/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
exit

interface gig0/0.30
encapsulation dot1Q 30
ip address 192.168.30.1 255.255.255.0
exit

interface gig0/0.40
encapsulation dot1Q 40
ip address 192.168.40.1 255.255.255.0
exit

interface gig0/0.50
encapsulation dot1Q 50
ip address 192.168.50.1 255.255.255.0
exit

interface gig0/0.99
encapsulation dot1Q 99 native
exit

interface gig0/0
no shutdown
exit

end
write
```

---

## 🔍 Vérifications

```cisco
! ✅ Sur SW1 et SW2
show vlan brief
show interfaces trunk

! ✅ Sur R1
show ip interface brief
show ip route
```

### Résultat attendu SW1 — show vlan brief
```
10  DIRECTION    active  Fa0/1, Fa0/2, Fa0/3
20  FINANCE      active  Fa0/4, Fa0/5, Fa0/6
30  RH           active  Fa0/7, Fa0/8, Fa0/9
40  VENTES       active
50  LOGISTIQUE   active
99  NATIF        active
```

### Résultat attendu R1 — show ip interface brief
```
Gig0/0        unassigned    up   up
Gig0/0.10     192.168.10.1  up   up
Gig0/0.20     192.168.20.1  up   up
Gig0/0.30     192.168.30.1  up   up
Gig0/0.40     192.168.40.1  up   up
Gig0/0.50     192.168.50.1  up   up
```

---

## 🧪 Tests de connectivité

```
✅ PC1  → ping 192.168.10.1   (passerelle VLAN10)
✅ PC1  → ping 192.168.20.10  (inter-VLAN 10→20)
✅ PC1  → ping 192.168.30.10  (inter-VLAN 10→30)
✅ PC1  → ping 192.168.40.10  (inter-VLAN 10→40 via SW2)
✅ PC1  → ping 192.168.50.10  (inter-VLAN 10→50 via SW2)
✅ PC10 → ping 192.168.10.10  (inter-VLAN 40→10 SW2→SW1)
✅ PC13 → ping 192.168.30.10  (inter-VLAN 50→30 SW2→SW1)
```

---

## 💡 Points clés

| 🔑 Point | 📖 Explication |
|----------|---------------|
| `encapsulation dot1Q` | Toujours avant l'adresse IP |
| `no shutdown` | Sur Gig0/0 uniquement |
| VLANs SW1 | Créer TOUS les VLANs (10,20,30,40,50,99) |
| VLANs SW2 | Seulement les VLANs locaux (40,50,99) |
| VLAN natif | Identique des deux côtés (99) |
| Passerelle PC | IP de la sous-interface R1 |

---

## 🛠️ Outils

![Cisco Packet Tracer](https://img.shields.io/badge/Cisco%20Packet%20Tracer-8.x-orange?style=flat-square&logo=cisco)
![Cisco IOS](https://img.shields.io/badge/Cisco%20IOS-15.x-blue?style=flat-square)
![GitHub](https://img.shields.io/badge/GitHub-black?style=flat-square&logo=github)
![Linux](https://img.shields.io/badge/Ubuntu-24.04-E95420?style=flat-square&logo=ubuntu)

---

## 👨‍💻 Auteur

**Urbain Sedami**
🎓 Étudiant CCNA 2 — Cisco Networking Academy
📍 Cotonou, Bénin 🇧🇯

---

## 📄 Licence

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Libre d'utilisation pour l'apprentissage et la formation réseau.
