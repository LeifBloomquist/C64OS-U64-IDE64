# C64OS-U64-IDE64
Configuration and tips for running C64OS on an Ultimate64+IDE64

## Background
I adore my Commodore 64! 

But, it's not your everyday Commodore 64.   I've souped up my C64 setup to the extreme, with what I consider the perfect trifecta of modern accessories and tools:

* [Ultimate 64](https://ultimate64.com/) from Gideon's Logic [(GitHub)](https://github.com/GideonZ)
* [IDE64](https://www.ide64.org/) from the IDE64 Team
* [C64OS](https://c64os.com/) from Opcoders Inc (Greg Nacu)  [(GitHub)](https://github.com/OpCoders-Inc)

My setup.  64KB RAM, 16MB REU, 48MHz acceleration, 64GB internal USB, 64GB Compact Flash card.

![Ultimate 64](https://github.com/LeifBloomquist/C64OS-U64-IDE64/blob/main/Photos/u64-2024-sm.jpg)

### Configuration

As you might imagine, this is pushing the limits of the good old C64 pretty hard, so it took me a bit of juggling to find a configuration that works, especially with regards to memory addresses.

### Addressing

The following settings worked, including REU and network access via the U64's Swiftlink emulation:

* IDE64 on $DE00 (hardcoded)
* REU in the U64 on $DF00 (hardcoded)
* ACIA / SwiftLink Emulation from the U64 on $DF80/NMI (configurable with Ultimate 64)

### Port Configuration

Additionally, the U64 cartridge port settings have to be made manually, to force it to recognize the IDE64 (external) and emulated REU (internal) at the same time:

* Bus Sharing - I/O1 = External
* Bus Sharing - I/O2 = Internal

Bus Operation Mode also has to be set to Dynamic for the IDE64 to function properly.

![Settings](https://github.com/LeifBloomquist/C64OS-U64-IDE64/blob/main/Screenshots/u64-cart-settings.png)

### C64OS Configuration

#### For v1.08
In v1.08, the $DF80 driver can now be chosen directly from the Network Utility.  Drivers get pulled into Network Utility automatically by pattern: 

//os/drivers/:nhd.????.??

* slde.u6 is for $DE00
* sldf.u6 is for $DF00
* sld+.u6 is for $DF80  (new)

See https://www.c64os.com/c64os/networkingguide/  for details.

#### For v1.07

In v1.07, to trick C64OS into using the SwiftLink Emulation at $DF80:

In File Manager, under //os//drivers/ :

* Find the file nhd.sldf.u6 and **rename** it to a new file nhd.sldf**0**.u6 using File Info
* Find the file nhd.sldf8.u6 and **copy** it to nhd.sldf.u6 using File Info


### Configuration File

My configuration file can be found [here](https://github.com/LeifBloomquist/C64OS-U64-IDE64/blob/main/Configuration/C64OS-IDE64.cfg) for reference.   You will need to adjust some entries for your network and SID configuration, etc.
