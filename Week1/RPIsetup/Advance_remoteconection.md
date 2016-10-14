# Remote connection to your Raspberry Pi

### Checking your IP address from the terminal

We can use a command to check the different internet connections available on our system: _ifconfig_ or _ifconfig -a_.
```bash
ifconfig
```
This command allows to know the IP addresses assigned to our RPi. The _wlan0_, indicates the status of the WiFi, and _eth0_ shows the status of the Ethernet (wired) connection). In the next screen shoot shows an example of a RPi connected to the internet using the ethernet port. The red oval shows where to find the IP address assigned to the RPi.

<img src="ifconfig.png" alt="ifconfig" style="width: 400px;"/>

If you do not know what is an **IP address**, please go to the next [link](https://www.youtube.com/watch?v=7_-qWlvQQtY) for a quick explanation. The IPs can be dynamic or static, but what is the difference? When a device is assigned a static IP address, the address does not change. Most devices use dynamic IP addresses, which are assigned by the network when they connect and change over time.

### Why I need to know my IP address?
We already know how to connect through weaved service, but we know the connection last just 30 minutes and lets just to work on a terminal session at the time. Therefore, with the help of weave and another command we can connect to or RPi for longer and using multiple terminals.

* First connect as usual to your weaved account and then connect to your RPi using the terminal of your laptop of desktop as you already did when you [set up weaved](RPI_setup.md).
* Then, you need to know the IP address assigned to your RPi:
```bash
ifconfig
```
Once you know the IP (e.g. your IP is 192.31.123.122), you can access using other terminal to the RPi as:
```bash
$ ssh pi@192.31.123.122
```
Remember that the **root username** is **pi**, the syntax for the ssh command is: ```ssh username@IP``` or ```ssh username@machine_name```.

**Note:** Since at Imperial network the IPs are dynamic, the IP is constantly changing, so could be that the IP changes in a day or hours (could be sometimes longer) and you need to repeat the procedure using weaved.

##### Copying files from my laptop to my RPi
If are programing in your laptop and you want to transfer it to test your code in your RPi, you can use this commands:

| Commands| Description| Example| Syntax|
|:---------|:----------|:---------|:-------|
|```scp``` |Copy files from your machine to your RPi| ``` scp program.py pi@123.232.232.3:/home/pi```| ```scp filename username@IP_of_machine:/path/where/to/Copy/in/RPi```|
| ```scp -r``` |Copy folders from your machine to your RPi| ``` scp -r code pi@123.232.232.3:/home/pi```| ```scp -r folder username@IP_of_machine:/path/where/to/Copy/in/RPi```|

**Note:** The next command is for updating and upgrading the Linux packages in the operative system, but it won't be executed during the workshop since it can take a while. It is always good to keep the system up to date:
``` bash
$ ‰sudo apt-get -y update && sudo apt-get -y upgrade
```