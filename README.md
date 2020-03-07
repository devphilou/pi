Playground with Raspberry Pi & Docker

## Specs
* Raspberry Pi
```
pi@pi:~$ cat /proc/cpuinfo

processor       : 0
model name      : ARMv6-compatible processor rev 7 (v6l)
BogoMIPS        : 697.95
Features        : half thumb fastmult vfp edsp java tls
CPU implementer : 0x41
CPU architecture: 7
CPU variant     : 0x0
CPU part        : 0xb76
CPU revision    : 7

Hardware        : BCM2835
Revision        : 000e
Serial          : 000000009ea35163
Model           : Raspberry Pi Model B Rev 2
```
* SD-Card 16 GB
* Power supply 5V@1A

## Setup & Configuring OS
1. Install Raspbian Desktop with [NOOBS](https://www.raspberrypi.org/downloads/noobs/)
2. Enable [SSH server](https://www.raspberrypi.org/documentation/remote-access/ssh/)
3. Improve [SSH security](https://www.raspberrypi.org/documentation/configuration/security.md) adding new user and remove pi user ()
