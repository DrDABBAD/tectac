

##  Materials

    Raspberry PI 3
    USB-to-Ethernet Adapter (I used an Ultralink UL-USB02-EN)
    RPi Power Supply
    16Gb MicroSD Card
    Peripherals to do setup (display, mouse, keyboard)

## Build tasks

1. Create imaging  https://www.raspberrypi.org/documentation/installation/installing-images/
   (Be sure to download the Raspbian Jessie Lite image (Not NOOBS)).  ??? Check current versions for this

    REset DEfault loign How?

2. Basic configuration
	* Update image
	```
	  Sudo Su
	  apt-get update; apt-get -y upgrade

	```
	* configure host name

	```
	echo "gateway.butterworth" > /etc/hostname; bash;
    root@gateway:/home/pi#
    ```
	* Create yourself a user other than pi, although using an ssh key and disabling all password authentication may be better.

3. Configure interface for gate way router
	* Check current config
   ```
   ifconfig | grep eth
   ```
   Expect
   eth0  Link encap:Ethernet  HWaddr b8:27:eb:9a:a1:62
   eth1      Link encap:Ethernet  HWaddr 00:e0:4c:53:44:58


   * configure these in /etc/dhcpcd.conf  (This is specfic to PI)

   ```
   nano /etc/dhcpcd.conf#Add the following lines
		interface eth1
		static ip_address=10.0.0.1
		static routers=10.0.0.1
		static domain_name_servers=10.0.0.1,8.8.8.8
   ```

    /etc/init.d/networking restart  may not reconfig interface correctly
	Hence use
	sudo reboot

    Check Ifconfig again

	Expect: etho has assighed address for external router exth has internal route


4. DHCP server setup

   ```
   apt-get install -y isc-dhcp-server
   ```


   let’s configure it —
```
nano /etc/dhcp/dhcpd.conf#add the following to the endsubnet 10.0.0.0 netmask 255.255.255.0 {    range 10.0.0.10 10.0.0.50;
    option domain-name-servers 10.0.0.1, 8.8.8.8;
    option domain-name "butterworth";
    option routers 10.0.0.1;
    option broadcast-address 10.0.0.255;
    default-lease-time 600;
    max-lease-time 7200;}

```

  Restart service
  /etc/init.d/isc-dhcp-server restart

5. Iptable routing

   NEED  NOTES ON IPTABLESHERE

    we use iptables :

iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth1 -j ACCEPT
mkdir /etc/iptables; iptables-save > /etc/iptables/rules.v4



But this will not persist across reboots. So we add a line to rc.local to restore like so :

nano /etc/rc.local
#add the following (BEFORE THE exit 0)iptables-restore /etc/iptables/rules.v4exit 0


TESt buy ping to google


6. Add Traffic GUI

A network traffic GUI — ntoppng — ( http://www.ntop.org ) :

apt-get install -y ntopng
