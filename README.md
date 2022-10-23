# vps

## VPS hosting without personal data
https://www.kamatera.com/express/compute/?tcampaign=35345_379441_VT131003&bta=35345&nci=5344&afp=VT131003&data1=VT131003


## Link to video tutorial
https://disk.yandex.com/d/9fl35rpQX8ofjw

## Update VPS server
```
apt update && apt upgrade -y
```

## Setup necessary packets by need
```
apt install curl
```

## openvpn-install
```
curl -O https://raw.githubusercontent.com/lazeyka/openvpn-install/master/openvpn-install.sh
chmod +x openvpn-install.sh
./openvpn-install.sh
```

## WireGuard-install
```
curl -O https://raw.githubusercontent.com/lazeyka/wireguard-install/master/wireguard-install.sh
chmod +x wireguard-install.sh
./wireguard-install.sh
```

## QR сode regeneration for the WireGuard created client
```
ls
qrencode -t ansiutf8 < wg-client.conf
```

## Обход определения туннеля/Двусторонний пиннг (косвенный фактор) отключаем пинг на внешнем интерфейсе
### на сервере смотрим 'имя интерфейса' с белым/реальным/ внешним IP, командой ifconfig (apt install net-tools)
```
iptables -A INPUT -i'имя интерфейса' -p icmp -j DROP
apt update && apt install iptables-persistent
iptables-save > /etc/iptables/rules.v4
reboot
```

## Setup packets OpenVPN on router with OpenWRT
```
opkg update
opkg install openvpn-openssl luci-app-openvpn
```

## Setup packets WireGuard on router with OpenWRT
```
opkg update
opkg install wireguard-tools luci-app-wireguard qrencode
```

## Setup packets on router with OpenWRT for see CPU load
```
opkg update
opkg install htop
```

### Starting htop for see CPU load
```
htop
```
