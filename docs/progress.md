installed opnsense 26.7 ufs in VB

WAN-NAT adapter, gets DHCP from VB (10.0.2.x)

LAN - host-only adapter, static 192.168.56.10

Disabled "Block private networks" on WAN — required because VirtualBox NAT uses RFC1918 range, would otherwise block WAN traffic



\## VLAN 10 (Management) — done



\- Created VLAN interface on OPNsense: parent em1 (LAN), tag 10, description MGMT

\- Assigned as interface OPT1, static IPv4 10.0.10.1/24

\- Added firewall rule: Pass, source MGMT net, destination any (temporary — will restrict later)

\- Configured 802.1Q sub-interface on Debian host: enp0s8.10, static 10.0.10.2/24

\- Verified: see \[tests/connectivity-tests.md](../tests/connectivity-tests.md)



!\[firewall rule](images/vlan10\_MGMT\_de\_bian802.1Q/2.png)

