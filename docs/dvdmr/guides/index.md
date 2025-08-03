# Configuration Guides

## Pi-Star & WPSD Custom Hosts

Digital Voice DMR is not yet listed in the Pi-Star hosts file; to be able to select it from the Pi-star menu you will need to add some custom local hosts.

Modifying Pi-Star & WPSD `DMR_Hosts.txt` file for the DVDU servers.

1) SSH into you Pi-Star
2) Make the filesystem read/write for Pi-Star. (This step not needed for WPSD)
```
rpi-rw
```
3) Edit the `DMR_Hosts.txt` file:
```
sudo nano /root/DMR_Hosts.txt
```

Scroll to the end the file and added the following server info between the two lines of hashes like below

```
##############################################################################################
#
#                               Custom DMR Hosts
#
##############################################################################################
# Name                          DMR-ID  IP/Hostname                     Password        Port #
##############################################################################################
FD_DVDU_DV-AU                   5053    dmr.dvau.au                     passw0rd        62031
FD_DVDU_DV-NZ                   5300    dmr.dvnz.nz                     passw0rd        62031
FD_DVDU_VKRadio-AU              5052    dmr.vkradio.com                 passw0rd        62031
##############################################################################################
```

Use `ctrl-o` to save and `ctrl-x` to exit.

4) Update the Pi Star hosts

```
sudo bash /usr/local/sbin/HostFilesUpdate.sh
```

Now you should be able to select one the DVDU servers from the drop down menu on the Configuration page for single host mode aka MMDVMHost.

TNX to Dale ([VK5TUX](https://www.qrz.com/db/VK5TUX)) for the instructions for Pi-Star, and Dan ([ZL4ER](https://www.qrz.com/db/ZL4ER)) for comfirming this Howto also works on WPSD.


## Pi-Star / DMR Gateway

DMR Gateway allows you to run multiple simultanious DMR networks and have custom talkgroup rewriting rules.

If you are using DMR Gateway on your Pi-Star you can run multiple simultanious DMR networks.   Log into the web gui of you Pi-Star in you web browser and go to [Configuration] => [Expert] => Full Edit: [DMR GW].

If you are running DMR Gateway outside of Pi-Star or with DMR Only Hotspot update your DMRGateway.ini configuration file with a block for Digital Voice DMR.

Please don’t just copy and paste what below, it just sample. Scroll down the file to the following and change what is mentioned to change.

```
[DMR Network 2]
Enabled=1
Address=dmr.dvnz.nz
Port=62031 # CHANGE TO THIS
TGRewrite0=2,1,2,1,999998
SrcRewrite0=2,1,2,1,999998
PCRewrite0=2,1,2,1,999998
Password="passw0rd"
Debug=0
Id=1234567 # CHANGE THIS TO YOUR DMRID
Name=DVNZ_DMR-NZ
Location=0
Options="TS2=90,91,92,530,5301,5302,5303,5304,5304,5305,50500;VOICE=0;LANG=en_GB;TIMER=15" # CHANGE OPTIONS TO YOUR NEEDS
```

press [Apply] and should be ready to go

Notes: The sample above has DVAU DMR routing all it’s traffic over TS2 with the way the Rewrite rules are configured on a duplex HS. Read more about [rewrite rules](https://github.com/g4klx/DMRGateway/wiki/Rewrite-Rules).

TNX to Dale ([VK5TUX](https://www.qrz.com/db/VK5TUX)) for the instructions for Pi-Star & DMR Gateway and VK2WAY for additional information around DMR Only Hotspot.

