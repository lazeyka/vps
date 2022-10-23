# vps

## VPS hosting without personal data
https://www.kamatera.com/express/compute/?tcampaign=35345_379441_VT131003&bta=35345&nci=5344&afp=VT131003&data1=VT131003

# Link on video tutorial
https://disk.yandex.com/d/9fl35rpQX8ofjw

## Обновляем VPS сервер
- apt update && apt upgrade -y

## Устанавливаем необходимые пакеты, если сервер не распознает
- apt install curl

## openvpn-install
- curl -O https://raw.githubusercontent.com/lazeyka/openvpn-install/master/openvpn-install.sh
- chmod +x openvpn-install.sh
- ./openvpn-install.sh

## WireGuard-install
- curl -O https://raw.githubusercontent.com/lazeyka/wireguard-install/master/wireguard-install.sh
- chmod +x wireguard-install.sh
- ./wireguard-install.sh

## Повторняя генирация QR-кода для созданого клиента
- ls
- qrencode -t ansiutf8 < wg-client.conf

# Обход определения туннеля/Двусторонний пиннг (косвенный фактор)
## Решение: отключить пинг на внешнем интерфейсе

- a) на сервере смотрим 'имя интерфейса' с белым/реальным/ внешним IP, командой ifconfig (apt install net-tools)
- b) iptables -A INPUT -i'имя интерфейса' -p icmp -j DROP
- c) apt update && apt install iptables-persistent
- d) iptables-save > /etc/iptables/rules.v4
- e) reboot

## Усанавливем пакет WireGuard на роутере с OpenWRT
- opkg update
- opkg install wireguard-tools luci-app-wireguard qrencode

## Усанавливем пакет для просмотра загрузка процесора на роутере с OpenWRT
- opkg update
- opkg install htop
### Запускаем просмотр агрузка процесора на роутере с OpenWRT
- htop
