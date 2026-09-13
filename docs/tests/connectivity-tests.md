\\```bash

sudo apt install vlan -y

sudo modprobe 8021q

sudo ip link set enp0s8 up

sudo ip link add link enp0s8 name enp0s8.10 type vlan id 10

sudo ip addr add 10.0.10.2/24 dev enp0s8.10

sudo ip link set enp0s8.10 up

\\```

