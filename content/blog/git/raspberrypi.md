


## Headless

A device without a monitor or keyboard. to enable headless operations make the following changes t o your SD card.

## Enabling SSH for your Headless Raspberry Pi.

Method 1

creatw an empty file named ssh in the /boot folder of your SD Card.(The file must have no extension i.e does not end .txt oe similar )

## Headless wifi
Ethernet works out of the box, but wireless connection will always need to be configured manually.

1. create a file called "wpa_supplicant.conf" in boot directory
2. Find [iso31166-1 code](https://en.wikipedia.org/wiki/ISO_3166-1) (i.e GB) your SSID  and password for your network
3. Add the following to the conf file.

```conf
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=[WIFI COUNTRY CODE]

network={
 ssid="[NETWORK SSID]"
 psk="[NETWORK PASSWORD]"
}
```

4. On PC set up Team viewer or VNC.

5. Work out address of PI to connect to with PI ....