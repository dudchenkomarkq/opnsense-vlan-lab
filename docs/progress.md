installed opnsense 26.7 ufs in VB

WAN-NAT adapter, gets DHCP from VB (10.0.2.x)

LAN - host-only adapter, static 192.168.56.10

Disabled "Block private networks" on WAN — required because VirtualBox NAT uses RFC1918 range, would otherwise block WAN traffic

