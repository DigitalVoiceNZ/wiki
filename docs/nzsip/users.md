# NZSIP User Information

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

