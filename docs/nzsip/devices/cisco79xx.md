
# Connecting a Cisco 7940/60 to NZSIP

"The 79 series was a workhorse of the early 2000s office, a fantastic phone, my all time favourite, but setting it up is not for the feint of heart" - VK2WAY.

Originally these phones were tightly locked down to the proprietary Cisco telephony platform, however when they were reaching end of life Cisco made a SIP firmware available for them, giving them a second life in small offices.  

There are two main ways of configuring the phone; the [Cisco 7940/7960 Administrator Manual](https://www.cisco.com/c/en/us/td/docs/voice_ip_comm/cuipph/7960g_7940g/sip/3_0/english/administration/guide/ver3_0/maintain.html) for the phone details much of the technical information and parameters for these phones.

The Cisco 7940 requires changes to your DHCP server, running a tftp server and manually managing configuration files in order for the phone to event boot.  There are plenty of guides on how to install the SIP firmware and set up all the supporting software online.  I highly recommend this one from [James Batchelor](https://james-batchelor.com/index.php/2021/01/23/provisioning-a-cisco-7940-7960/)


The settings in either your SIPxxxxxxxx.cnf or SIPDefault.cnf should include the following:

```
proxy1_address: "EXCHANGE HOSTNAME";
proxy1_port: 5060

line1_authname: "EXTENSION";
line1_password: "SECRET";

directory_url: "http://mmd.dvdmr.org/directory"; 
```

This is not an extensive list of settings needed by the phone, but other settings should be left with somewhat sensible defaults.

Be sure to change the EXCHANGE HOSTNAME, EXTENSION and SECRET to those provided to you in your onboarding email.



