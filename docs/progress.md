## OPNsense installation

- Installed OPNsense 26.7 (UFS) in VirtualBox.
- WAN: NAT adapter, DHCP from VirtualBox (10.0.2.x).
- LAN: Host-only adapter, static 192.168.56.10.
- Disabled "Block private networks" on WAN. It is required because VirtualBox NAT uses an RFC1918 range and OPNsense would otherwise block its own WAN traffic.

## VLAN 10 (Management): done

- Created the VLAN device on OPNsense: parent `em1` (LAN), tag 10, description MGMT.
- Assigned it as interface OPT1 with static IPv4 `10.0.10.1/24`.
- Added a firewall rule: Pass, source MGMT net, destination any (temporary, to be restricted later).
- Configured an 802.1Q sub-interface on the Debian host: `enp0s8.10`, static `10.0.10.2/24`.
- Verified: see [docs/tests/connectivity-tests.md](../docs/tests/connectivity-tests.md)

![Firewall rule](/docs/images/vlan10_MGMT_debian802.1Q/2.png)
