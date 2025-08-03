# NZSIP User Information

## Configuring your Device

You can utilise any SIP phone or device as an extension on NZSIP.   On provisioning of your extension you will receive an
email with the following details:

* SIP Server - the hostname you need to connect to for your SIP service;  NZSIP uses the default 5060/udp port for SIP.
* Username - this is your username used for registering and for authenticating calls made to NZSIP.  It is the same as your extension number.
* Secret - this is the secret/password used for authenticating your SIP device.

Your device *should* send registration events;  this is what tells NZSIP where to reach your phone.

The SIP server will be either one of nzsip.nz or world.nzsip.nz depending upon which region you are located in.

## Numbering Plan

NZSIP utilises 5 digit numbers for all our extensions, we use the following numbering plan:

|Pattern|Description|Exchange|
|:--|:--|:--|
|5xxxx|***Exchange 1 Prefix (AU/NZ)***|nzsip.nz|
|50xxx|Australian Extensions|nzsip.nz|
|53xxx|New Zealand Extensions|nzsip.nz|
|59xxx|Services, Conferences &amp; Bridges|nzsip.nz|
|6xxxx|***Exchange 2 Prefix (World)***|world.nzsip.nz|
|610xx|World Extensions|world.nzsip.nz|
|611xx|Americas Extensions|world.nzsip.nz|
|612xx|Oceania Extensions|world.nzsip.nz|
|620xx|Europe Extensions|world.nzsip.nz|
|621xx|Americas Extensions|world.nzsip.nz|
|622xx|Africa Extensions|world.nzsip.nz|
|623xx|Asia Extensions|world.nzsip.nz|
|69xxx|Services, Conferences &amp; Bridges|world.nzsip.nz|
|+577\*|Inter Exchange Trunk - ***Hams Over IP***| |
|+910\*|Inter Exchange Trunk - ***Amatuer Wire***| |


See our [Devices](devices/index.md) page for information on configuring various phones, systems and software with NZSIP.

## Direct Dial

NZSIP is interconnected with both Hams Over IP and Amatuer Wire.

* ***Hams Over IP*** prefix the HoIP number with +577 when dialing from NZSIP.
* ***Amatuer Wire*** prefix the Amatuer Wire number with +910 when dialing from NZSIP.

NZSIP numbers can be dialled from either Hams Over IP or Amatuer Wire by prefixing the NZSIP number with +640.

## LDAP Directory

Our LDAP directory is available at ldap://directory.nzsip.nz.

Anonymous bind is supported and allows searching of the NZSIP or global ham phone directories.

The global directory can be searched using `dc=nzsip, dc=nz`.   The Organisational units `ou=nzsip` or `ou=external` can be prefixed to the base DN to limit your search within the NZSIP or global directories.

Extensions on other services returned by the NZSIP directory are automatically prefixed with the correct dialing code to reach that particular network.

See our Phone Configuration guide for how to configure the directory on your specific phone.

Our directory is also available as a Cisco XML Application for use with older Cisco phones expecting Cisco Call Manager;  this directory application can be used by specifying `http://directory.nzsip.nz/cisco/directory` as the Directory URL in your phone configuration file.

