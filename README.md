# vps

- curl -O https://raw.githubusercontent.com/lazeyka/openvpn-install/master/openvpn-install.sh
- chmod +x openvpn-install.sh
- ./openvpn-install.sh

- curl -O https://raw.githubusercontent.com/lazeyka/wireguard-install/master/wireguard-install.sh
- chmod +x wireguard-install.sh
- ./wireguard-install.sh

# Обход определения туннеля/Двусторонний пиннг (косвенный фактор)
## Решение: отключить пинг на внешнем интерфейсе

- a) на сервере смотрим 'имя интерфейса' с белым/реальным/ внешним IP, командой ifconfig (apt install net-tools)
- b) iptables -A INPUT -i'имя интерфейса' -p icmp -j DROP
- c) apt update && apt install iptables-persistent
- d) iptables-save > /etc/iptables/rules.v4
- e) reboot
