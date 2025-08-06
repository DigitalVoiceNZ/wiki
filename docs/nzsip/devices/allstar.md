# NZSIP AllStarLink Bridges

AllStarLink provides a network of internet connected RF Nodes, Conferences and Bridges.  You can find out more on their [website](https://allstarlink.org).

This guide is designed for those who would like to connect an AllStar node to the NZSIP network via a telephone bridge (with push to talk).

Request a new trunk from the [NZSIP Helpdesk](https://helpdesk.nzsip.nz).  Only one trunk is required per AllStar server; extensions will be routed to the trunk for each individual service or IVR menu you wish to provide.

Setting up nodes on your AllStarLink server is beyond the scope of this document.

!!! success
    It is strongly advised that you create a private node to connect to NZSIP and have that node connect to your public allstar node; this not only helps remove telemetry from being broadcast but allows you to easily drop the connection should problems arise.


Throughout these examples you'll see some numbers:

* 69333 and 69292 are NZSIP extensions routed across the example trunk.
* 1923 and 1922 are Private Allstar Node numbers on the allstar node with assumed 'on-startup' connections to public allstar nodes.


## Create a ASL Private Node

Follow the ASL menu configuration tool prompts to add a new private node to your server.   You must give private nodes numbers in the range 1900-1999.  


## NZSIP IAX Friend Configuration

Configure your NZSIP IAX friend, this block goes in your `/etc/asterisk/custom/iax.conf` configuration file; if you do not have a custom directory you may have to create it first.

```
[nzsip]
type = friend
context = from-nzsip
username = ***TRUNK USERNAME***
auth = md5
secret = ***TRUNK SECRET***
host = ***TRUNK EXCHANGE***
disallow = all                    
allow = ulaw
allow = g726aal2
allow = adpcm
allow = gsm                       
transfer = no
codecpriority=host
insecure=port,invite
requirecalltoken=yes
```

!!! warning
    Be sure to replace ***TRUNK USERNAME***, ***TRUNK SECRET*** and ***TRUNK EXCHANGE*** with the details provided to you in your provisioning email.  Do not create your friend block until you have been provided your onboarding details as you may block yourself on our firewall.

When handing calls off to your trunk NZSIP will use the extension number dialled; you will need a `from-nzsip` dialplan context to handle these calls and route them to your repeater nodes.


## Dialplan Context

In your `/etc/asterisk/custom/extensions.conf` create a `from-nzsip` dialplan context, this contains the extension mapping from NZSIP to your particualar nodes or services, this is essentially your mapping of numbers to allstar node, repeat the block line for each number.


```
[from-nzsip]
exten => 69292,1,Playback(rpt/node)
same => n,SayAlpha(560022)
same => n,rpt(1922,P)

exten => 69333,1,Playback(rpt/node)
same => n,SayAlpha(560023)
same => n,rpt(1923,P)
```

!!! warning
    We require AllStarLink numbers to identify themselves when they answer rather than droppig a user into a bridge with no instructions.  Update the *SayAlpha* lines in the above block to reflect the public node number that your private node connects to (560022 and 560023 in this example).


## Custom Announcements  (optional)

If you'd like to welcome callers to your gateway with a custom greeting and additional instructions; you can add a common block to use for all your extensions and play your announcements based on that node.    This also simplifies your inbound context by routing the calls through a common block.


Add another context named `[asl-direct-dial]` to your `/etc/asterisk/custom/extensions.conf` file.

```
[asl-direct-dial]
exten => _X.,1,Answer()
same => n,Set(RPT_NODE=${EXTEN})
same => n,Playback(custom/welcome)
same => n,Playback(custom/dialled${EXTEN})
same => n,Playback(custom/ptt)
same => n,Playback(beep)
same => n,rpt(${EXTEN},P)
```

This example assumes you have uploaded audio files `welcome`, `dialledXXXXX` and `ptt` to the `custom` sound files in your allstar node.  Each node should have it's own dialledXXXXXX file where the XXXXX is the node number dialled (e.g. 1923).

Update your `[from-nzsip]` block to call the asl-direct-dial context instead of the repeater function:

```
exten => 69292,1,Goto(asl-direct-dial,1922,1)
exten => 69333,1,Goto(asl-direct-dial,1923,1)
```

## IVR Menu (Optional)

If you'd like to create an IVR menu for multiple allstar nodes; here is an example:


```
[asl-menu]
; menu entry point
exten => 200,1,Answer()

; uninerruptable greeting
same => n,Playback(custom/welcome-gateway)

; interruptable menu; multiple items must be concatenated with
; & so that they play as one task to be interrupted correcctly
same => n(ivrloop),Background(custom/menu-dial-1&custom/menu-dial-2)
same => n(ivrwait),WaitExten()

; The numbers to dial in the menu mapped to private node
; via the block we created in the above example;  the parameters
; are the private node; the first number before the comma 
; is the menu option dialled.
exten => 1,1,Goto(asl-direct-dial,1922,1)
exten => 2,1,Goto(asl-direct-dial,1923,1)

; press * to repeat the menu
exten => *,1,Goto(asl-menu,200,ivrloop)

; invalid extension handler
exten => i,1,Playback(custom/whatwasthat)
same => n,Goto(asl-menu,200,ivrwait)

; timeout handler
exten => t,1,Playback(custom/whatwasthat)
```
!!! note
    The extension number 200 within the menu context is the entrypoint; if you require a menu option 200 please change it to any number unused by your menu but update it accordingly in the inbound context below.

This example assumes you have audio files `welcome-gateway`, `menu-dial-XX`, and `whatwasthat` in your allstar node's custom asterisk sounds folder. The menu-XX files should be replicated for each menu item read out.  

The menu can be interrupted by dialling the option at any time.

You can then map an extension to your menu in your `from-nzsip` block:

```
exten => 69333,1,Goto(asl-menu,200,1) 
```



