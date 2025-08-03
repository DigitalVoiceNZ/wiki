
# Connecting Asterisk to NZSIP

If you intend to connect Asterisk to NZSIP it is recommended that you request an IAX2 extension.

IAX2 is a more efficient protocol than SIP and allows better firewall traversal and plays more nicely with NAT.

```
[nzsip]
host=<YOUREXCHANGE>
username=<YOUREXTENSION>
secret=<YOURPASSWORD>
type=friend
trunk=yes
insecure=port,invite
requirecalltoken=yes
qualifyfreqok=25000
qualify=yes
transfer=no
dyanmic=yes
context=from-nzsip
forceencryption=no
encryption=yes
auth=md5
```

Ensure you update YOUREXCHANGE, YOUREXTENSION, YOURPASSWORD with the values provided to you when your extension was provisioned.


You will require a dialplan context named [from-nzsip] to handle inbound calls on your NZSIP extension.


