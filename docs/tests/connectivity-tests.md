## VLAN 10 on the Debian test host

### Temporary setup (lost after reboot)

```bash
sudo apt install vlan -y
sudo modprobe 8021q
sudo ip link set enp0s8 up
sudo ip link add link enp0s8 name enp0s8.10 type vlan id 10
sudo ip addr add 10.0.10.2/24 dev enp0s8.10
sudo ip link set enp0s8.10 up
```

These commands live only in memory, so the configuration is reset after a reboot.

### Persistent setup

Load the 8021q module at boot:

```bash
echo 8021q | sudo tee -a /etc/modules
```

`/etc/network/interfaces`:

```
auto enp0s8
iface enp0s8 inet manual

auto enp0s8.10
iface enp0s8.10 inet static
    address 10.0.10.2/24
    gateway 10.0.10.1
    vlan-raw-device enp0s8
```

### Verification (before firewall hardening)

```bash
ip route
ping -c 4 192.168.56.10
ping -c 4 8.8.8.8
```
![ip route](docs/images/tests_vlan10/1.png)
![ping №1](docs/images/tests_vlan10/2.png)
![ping №2](docs/images/tests_vlan10/3.png)
