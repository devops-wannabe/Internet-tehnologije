# ❗Readme
Ovaj repozitorijum sadrži prikupljene rokove iz predmeta _Internet tehnologije_.
Za rok koji ima rješenje stoji oznaka __R__.
Usmeni ispit ima oznaku __U__.
Cilj je da na jednom mjestu postoje materijali koji mogu pomoći svim studentima.
Ukoliko uočite neku grešku ili imate pitanje slobodno ukažite na to.
✅ Ukoliko želite da dodate svoj doprinos i dodati svoje materijale, možete otvoriti `Pull Request`.

<p>
Na usmenom ispitu su se pojavljivala i sljedeća pitanja:
1. Integracija WLAN mreže u VLAN
2. NAT
3. ICMP
4. VLAN-ovi
</p>

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
- SSID
- WEP
- WPA
- WI-FI
- NAT na wifi ruteru u privatnoj mreži
- RIP 
