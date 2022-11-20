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

## openvpn-install and add new users
```
curl -O https://raw.githubusercontent.com/lazeyka/openvpn-install/master/openvpn-install.sh
chmod +x openvpn-install.sh
./openvpn-install.sh
```

## WireGuard-install and add new users
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

## Setup packets OpenVPN on router with OpenWRT, if you want to use OpenVPN
```
opkg update
opkg install openvpn-openssl luci-app-openvpn
```

## Setup packets WireGuard on router with OpenWRT, if you want to use WireGuard
```
opkg update
opkg install wireguard-tools luci-app-wireguard qrencode
```

## Setup packets on router with OpenWRT for see CPU load
```
opkg update
opkg install htop
```

### Starting htop for see CPU load on router with OpenWRT
```
htop
```

## OpenWRT - Change TTL (Time to Live)
```
If you are using USB tethering, there is a specific TTL value that need to be configured. The common TTL value used by the mobile network operator is 65 while the default value on the computer is 128. We need to change this to have a working internet connection or to be able to use the hotspot. Changing TTL does not 100% give you unlimited hotspot with high speed but it depends on your network operator.  https://disk.yandex.com/i/xTkBpkB49Vvu8g
- Custom Firewall rule:
iptables -t mangle -I POSTROUTING -o wan-interface -j TTL --ttl-set 65
- Edit /etc/sysctl.conf file and add in (in this example TTL 65 is used)
net.ipv4.ip_default_ttl=65
net.ipv6.ip_default_ttl=65
```
