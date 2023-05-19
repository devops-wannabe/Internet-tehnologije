# ❗READ ME
Ovaj repozitorijum sadrži prikupljene rokove iz predmeta _Internet tehnologije_.
Za rok koji ima rješenje stoji oznaka __R__.
Usmeni ispit ima oznaku __U__.
Cilj je da na jednom mjestu postoje materijali koji mogu pomoći svim studentima.
Ukoliko uočite neku grešku ili imate pitanje slobodno ukažite na <vanja.github@gmail.com>.
<p>✅ Ukoliko želite da dodate svoj doprinos i dodate svoje materijale, možete otvoriti Pull Request.</p>


Na usmenom ispitu su se pojavljivala i sljedeća pitanja:
1. Integracija WLAN mreže u VLAN
2. NAT
3. ICMP
4. VLAN-ovi


## Packet tracer commands

- `Switch# show spanning-tree`
- `Switch(config)# spanning-tree vlan 1 priority X` - increments od 4096 <0-61 440>   default = 32769 za VLAN=1
- `Switch(config)# spanning-tree vlan 1 root primary/secondary`
- `Switch(config-if)# spanning-tree portfast`
- `Switch(config-if)# spanning-tree bduguard enable`
- `Switch(config-if)# spanning-tree vlan 1 port-priority X` - increments of 16 <0 - 240>  default = 128

---

- `Switch# show vlan brief`
- `Switch(config)# vlan 10`
- `Switch(config-vlan)# name Studenti`
- `Switch(config-if)# switchport mode access`
- `Switch(config-if)# switchport access vlan 10 `
- `Switch(config-if)# switchport mode trunk`
- `Router(config-int)# interface G0/0.brojVLAN` - brojVLAN dobra praksa
- `Router(config-subif)# encapsulation dot1Q BROJ_VLAN` - BROJ_VLAN MORA!  **Bitan redoslijed**
- `Router(config-subif)# ip address 192.168.10.254 255.255.255.0` - default gateway

---

- `Switch(config-if-range)# channel-group <1-6> mode on` - do 8 linkova u 1 etherchannel (fizičke linkove posmatra kao 1 logički) **uraditi na oba switcha**
- **PREDUSLOV** U Etherchannel stavljamo linkove istih karakteristika, npr. istih brzina.
- `R1(config-if)# encapsulation ppp`
- `R1(config)# username R2 password lozinka` - potrebno da šifra bude ista na obe strane  
- `R2(config)# username R1 password lozinka`
- `R1(config-if)# ppp authentication chap` - **Challenge-Handshake Authentication Protocol**

---

- `R1(config)# router rip`
- `R1(config-router)# network 192.168.1.0`
- `R1(config-router)# network 192.168.12.0`
- `R1(config-router)# network 192.168.13.0`
- `R1(config)# router rip`
- `R1(config)# version 2`
- `R1(config)# no auto-summary`

---

- `R3(config)# router ospf 1`
- `R3(config-router)# area 1 range 172.16.0.0 255.255.252.0`
- `R3(config)# network 192.168.1.0 0.0.0.255 area 0`
- `R3# show ospf neighbor`
- `R3(config)# ip ospf priority <0-255>`

---

- `R2(config)# ip dhcp excluded-addresss 192.168.10.1 192.168.10.10`
- `R2(config)# dhcp pool R1-LAN`
- `R2(config)# network 192.168.10.0 255.255.255.0`
- `R2(config)# default-router 192.168.10.1`
- `R2(config)# dns-server 192.168.20.254`
- `R2(config)# interface g0/0` - interfejs koji prima DHCP broadcast poruku
- `R2(config-if)# ip helper-address 10.1.1.2` - IP adresa DHCP servera ili interfejsa rutera koji ima ulogu DHCP servera
- `R2(config-if)# ip address dhcp` - ruter dobija adresu preko DHCP-a

---

- `R1(config)# ip nat inside source static 172.16.16.1 64.100.50.1`
- `R1(config-if)# ip nat inside`
- `R1(config-if)# ip nat outside`
- `R1# show ip nat translations`
- `R2(config)# access-list 1 permit 172.16.0.0 0.0.255.255`
- `R2(config)# ip nat pool POOL 209.165.200.229 209.165.200.230 netmask 255.255.255.224`
- `R2(config)# ip nat inside source list 1 pool POOL`
- `R2(config-if)# ip nat inside`
- `R2(config-if)# ip nat outside`
- PAT isto kao kod dinamičkog samo se dodaje __overload__ na kraju komande ili
- `R2(config)# access-list 2 permit 172.17.0.0 0.0.255.255`
- `R2(config)# ip nat inside source list 2 interface S0/1/1 overload`
- `R2(config-if)# ip nat inside`
- `R2(config-if)# ip nat outside`

---

- `R1(config)# ipv6 unicast-routing`
- `R1(config-if)# ipv6 address 2001:db8:1:1::1/64`
- `R1(config-if)# ipv6 address fe80::1 link-local`
