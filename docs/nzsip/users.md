# NZSIP User Information

## Configuration Summary

* SIP Server
  * `nzsip.nz` (NZ/AU subscribers) 
  * `world.nzsip.nz` (International subscribers)
  
* LDAP Directory
  * `ldap://nzsip.nz`
  * `ldap://world.nzsip.nz`
  * Base DN: `dc=nzsip,dc=nz`


## Configuring your Device

You can utilise any SIP phone or device as an extension on NZSIP.   On provisioning of your extension you will receive an
email with the following details:

* SIP Server - the hostname you need to connect to for your SIP service;  NZSIP uses the default 5060/udp port for SIP.
* Username - this is your username used for registering and for authenticating calls made to NZSIP.  It is the same as your extension number.
* Secret - this is the secret/password used for authenticating your SIP device.

Your device *should* send registration events;  this is what tells NZSIP where to reach your phone.

The SIP server will be either one of `nzsip.nz` or `world.nzsip.nz` depending upon which region you are located in.

See our [Device Configuration Guide](devices/index.md) for specific information relevant to various devices, contributed by our community.


## Extension Status

You can view the status of the extensions directly connected to our network at our [multi-exchange BLF indicator](https://mmd.dvdmr.org).

## Exchanges

NZSIP currently operates 2 exchanges:

* Oceania (AU/NZ) - `nzsip.nz`
* Worldwide - `world.nzsip.nz`

## Numbering Plan

NZSIP utilises 5 digit numbers for all our extensions, we use the following numbering plan:

|Prefix||Description|Exchange|
|:--|:--|:--|:--|
|5x xxx||***Exchange 1 Prefix (AU/NZ)***|nzsip.nz|
||50 xxx|Australian Extensions||
||53 xxx|New Zealand Extensions||
||59 xxx|Services, Conferences &amp; Bridges||
|6x xxx||***Exchange 2 Prefix (World)***|world.nzsip.nz|
||610 xx|World Extensions||
||611 xx|Americas Extensions||
||612 xx|Oceania Extensions||
||620 xx|Europe Extensions||
||621 xx|Americas Extensions||
||622 xx|Africa Extensions||
||623 xx|Asia Extensions||
||69 xxx|Services, Conferences &amp; Bridges||

### Other Networks

|Prefix|Description|
|:--|:--|
|577 \*|Inter Exchange Trunk - ***Hams Over IP***|
|910 \*|Inter Exchange Trunk - ***Amateur Wire***|


See our [Devices](devices/index.md) page for information on configuring various phones, systems and software with NZSIP.

## Network Services

Test and local service numbers:

* \*43 – Echo Test
* \*60 – Speaking Clock
* \*68 – Wake Up Calls
* \*97 – My Voicemail
* \*65 – Speak Your Exten Number

### Other services to try:

* 69199 - Amateur Radio News Services Playout 
* 69200 - Digital Voice DMR Worldwide Talkgroup Bridge (TG 90,91,92,333,666)
* 59801 - IVR Adventure Game
* 59802 - Your Call is Important to Us (Menu Maze Game)

## Direct Dial

NZSIP is interconnected with both Hams Over IP and Amateur Wire.

NZSIP numbers can be dialled from either Hams Over IP or Amateur Wire by prefixing the NZSIP number with *640*.

When dialling other services your caller ID information will be automatically prefixed with the necessary information for the other party to return the call to the number they missed.  Additionally your name will be prefixed with `NZSIP-`.

### Hams Over IP

You can phone Hams Over IP extensions by prefixing the number with *577*.

You can find the Hams Over IP phone book on their [website](https://hamsoverip.com)


### Amateur Wire

You can phone Hams Over IP extensions by prefixing the number with *910*.

You can find the Amateur Wire phone book on their [website](https://amateurwire.org/)




## LDAP Directory

Our LDAP directory is at the same hostname as your exchange,  you are encouraged to use the same LDAP directory as exchange you were allocated.   These directories are mirroed copies of each other and the content will be the same:

* ldap://nzsip.nz
* ldap://world.nzsip.nz

Anonymous bind is supported and allows searching of the NZSIP or global ham phone directories.

The global directory can be searched using `dc=nzsip, dc=nz`.   The Organisational units `ou=nzsip` or `ou=external` can be prefixed to the base DN to limit your search within the NZSIP or global directories.

Extensions on other services returned by the NZSIP directory are automatically prefixed with the correct dialing code to reach that particular network.

See our Phone Configuration guide for how to configure the directory on your specific phone.

### Cisco XML Directory

Our directory is also available as a Cisco XML Application for use with older Cisco phones expecting Cisco Call Manager;  this directory application can be used by specifying `http://services.nzsip.nz/directory` as the Directory URL in your phone configuration file.


