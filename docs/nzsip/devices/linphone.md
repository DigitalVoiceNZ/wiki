
# Connecting Linphone to NZSIP

Linphone is an open source unified communication application that works across platforms.

It is available for Android, iOS, Linux, macOS and Windows and can be downloaded from [linphone](https://www.linphone.org/en/linphone-softphone/).


Go to Preferences.  On the main page add a new SIP account.

* SIP Address: sip:***EXTENSION***@nzsip.nz
* SIP Server: &lt;sip:nzsip.nz,transport=udp&gt;

Be sure the exchange server (nzsip.nz) matches the server you were provided in your onboarding email; this will either be nzsip.nz or world.nzsip.nz depending on which region you are connecting from.

Scroll down to the "Register" option, ensure that this is set to ON.

Linphone will prompt you for your username (same as your extension) and secret.  These were provided to you in your onboarding email.


## Adding Directory Search

In ***Preferences*** go to Advanced.  Click the + icon next to LDAP.

Click the name of the first LDAP server (ldap:///)

* Display Name: NZSIP Directory
* Server URL:  ldap://nzsip.nz
* Bind DN: [leave blank]
* Password: [leave blank]
* Use TLS: No
* Search Base: dc=nzsip,dc=nz
* Filter: (cn=*%s*)

* Name Attributes: cn
* SIP Attributes: telephoneNumber
* Domain: nzsip.nz

