
# Reflectors

A reflector is a software running on a computer with no radios attached to it, typically a server in a datacenter, to which repeaters and hotspots connect to. A reflector can be thought of an audio conference server.

Each reflector has different modules, identified with letters. The modules can be seen as conference rooms within the conference server. Repeaters/hotspots connect to a module of the reflector. Whenever someone transmits via radio onto a repeater/hotspot connected to this reflector module the transmission will be rebroadcasted toward all other repeaters/hotspots connected to that same reflector. The transmission gets reflected to all connected repeaters/hotspots, hence the name reflector module.

Ok now, what is the difference between all those flavors of reflectors? Virtually there is no difference or, at least, not for the people who are just using them.

## The different reflectors

### REF

The first reflectors where the REF reflectors. A list of those reflectors can be found [here](http://www.dstarinfo.com/reflectors.aspx). To convey the DStar information the software used to run a REF reflector uses a network protocol called DPlus to communicate with the repeaters. The DPlus protocol requires you to be registered into the US-Trust system, but I will cover this in a later article. To connect your repeater to a REF reflector you’ll issue a command REFxxxaL on your radio, replacing xxx with the wanted number and a with the wanted module.

### XRF

The second type of reflectors that came up were the XRF reflectors. A list of those reflectors can be found [here](http://xrefl.net/). The software used to run the XRF reflector uses another network protocol called DExtra. To connect your repeater to a XRF reflector you’ll issue a command XRFxxxaL on your radio, replacing xxx with the wanted number and a with the wanted module.

### DCS

The [DCS reflectors](http://xreflector.net/) arrived later and originated in Germany. It is/was a centralized system ran by German hams. If you wanted to run a reflector you had to give admin rights to some German OMs who would installed the software for you on your server. Quite awkward. Ok focus back. The DCS reflectors also come with their own network protocol. The protocol here is simply called DCS. Recently the OMs in charge of the DCS decided to drop the system, but some fellow hams decided to take it over. To connect your repeater to a DCS reflector you’ll issue a command DCSxxxaL on your radio, replacing xxx with the wanted number and a with the wanted module.

### XLX

Now we went through all three historical reflector and you are probably thinking “Ok no need to continue reading, he’ll tell us XLX is a reflector that speaks XLX protocol”… Nope! You are wrong! Continue reading!

The software used to run the [XLX reflectors](https://github.com/LX3JL/xlxd) actually speaks all three previous protocols REF, XRF, DCS and additionally its own protocol which is only used to interconnect reflectors together. As a side note, XLX reflectors are very versatile and can also be accessed through DMR and Fusion with full audio transcoding. For the sake of clarity this aspect will not be covered here.

Back to DStar. The 3 protocols (DCS,XRF,DCS) capability brought lots of confusion and still confuses DStar newbies : some reflector sysops did not do their homework and just hijacked reflector numbers that were used in the legacy XRF and DCS systems. This caused names collision and sometime you did not know if you were really connected to where you wanted to connect.

Let’s assume you want to connect to XLX299B. According to the previous examples with REF, XRF and DCS you would expect to have to issue the command XLX299BL from your radio. Unfortunately, this will lead you nowhere. You’ll need to issue either XRF299BL or DCS299BL. Both commands will connect your repeater to XLX299 module B the first one using the DExtra protocol, the other using the DCS protocol. If two repeaters connect to the same reflector module using different protocols the reflector software will convert protocols back and forth i.e. a repeater connected using DExtra will be get the transmissions from the one connected through DCS and vice versa.



All credit to Geoffrey Merck (F4FXL)

