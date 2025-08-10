
# Yealink SIP-T2 Series IP Phone

This phone setup guide should be read in conjunction with our [NZSIP User Guide](../index.md).

!!! note
    Yealink SIP T20P IP Phone - Firmware version 9.60.0.140 on hardware 7.0.0.60 was used for this guide

1.  Connect to your Yealink IP Phone's web interface and authenticate as administrator.  The default username and password is `admin`.

2.  Click on the ***Account*** tab and select ***Line 1*** or ***Line 2*** from the dropdown box depending on which line you wish to configure for NZSIP.

3.  Set the following settings:

    * Account active: True
    * Label: NZSIP
    * Display Name: ***YOUR CALLSIGN***
    * Register Name: ***YOUR EXTENSION***
    * User Name: ***YOUR EXTENSION***
    * Password: ***YOUR SECRET***
    * SIP Server: ***YOUR EXCHANGE***
    * SIP Server Port: 5060
    * Enable Outbound Proxy Server: Disabled
    * Voice Mail: \*97

    Settings under CODECS and ADVANCED can be left at defaults.

!!! warning
    Be sure to update YOUR CALLSIGN, YOUR EXTENSION, YOUR SECRET and YOUR EXCHANGE settings to the values sent to you in your onboarding email.


!!! note
    There is no way to integrate an online directory with this phone.


