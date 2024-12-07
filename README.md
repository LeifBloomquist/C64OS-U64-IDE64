# C64OS-U64-IDE64
Configuration and tips for running C64OS on an Ultimate64+IDE64

## Background
I adore my Commodore 64! 

But, it's not your everyday Commodore 64.   I've souped up my C64 setup to the extreme, with what I consider the perfect trifecta of modern accessories and tools:

* [Ultimate 64](https://ultimate64.com/) from Gideon's Logic [(GitHub)](https://github.com/GideonZ)
* [IDE64](https://www.ide64.org/) from the IDE64 Team
* [C64OS](https://c64os.com/) from Opcoders Inc (Greg Nacu)  [(GitHub)](https://github.com/OpCoders-Inc)

My setup:
![Ultimate 64](https://github.com/LeifBloomquist/C64OS-U64-IDE64/blob/main/u64-2024-sm.jpg)

### Configuration

As you might imagine, this is pushing the limits of the good old C64 pretty hard, so it took me a bit of juggling to find a configuration that works, especially with regards to memory addresses.

### Addressing

The following settings worked:

* IDE64 on $DE00 (hardcoded)
* REU in the U64 on $DF00 (hardcoded)
* ACIA / SwiftLink Emulation from the U64 on $DF80 (configurable)

### Port Configuration





### Configuration File

My configuration file can be found [here] [GitHub Pages](https://github.com/LeifBloomquist/C64OS-U64-IDE64/blob/main/C64OS-IDE64.cfg) for references.   You will need to adjust some entries for your network and SID configuration, etc.
