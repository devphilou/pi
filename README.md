# [Raspberry Pi](https://www.raspberrypi.org/) Playground

## Hardware
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
3. Improve [SSH security](https://www.raspberrypi.org/documentation/configuration/security.md) adding new user and remove pi user
4. Update packages: `pi@pi:~$ sudo apt-get update && sudo apt-get upgrade`

## [PostgreSQL](https://www.postgresql.org/)
1. Install packages: `pi@pi:~$ sudo apt install postgresql libpq-dev postgresql-client postgresql-client-common -y`
2. Switch to postgres user: `pi@pi:~$ sudo su postgres`
3. Create new user: `postgres@raspberrypi:/home/pi$ createuser pi -P --interactive`
    - enter password
    - **n** for superuser
    - **y** for the last two options (create database / new roles)
4. Connect to postgres: `postgres@raspberrypi:/home/pi$ psql`
5. Create test database: `postgres=# create database test;`
    - go back to pi shell `pi@pi` using `exit` -> Enter -> `exit` -> Enter
6. Direct connect to test database: `pi@pi:~$ psql test`

### PostgreSQL remote access
1. Edit `pi@pi:~$ sudo vim /etc/postgresql/11/main/postgresql.conf` and uncomment line `listen_addresses` and change value `'localhost'` to `'*'`
2. Edit `pi@pi:~$ sudo vim /etc/postgresql/11/main/pg_hba.conf` and change settings
    - IPv4 `127.0.0.1/32` to `0.0.0.0/0`
    - IPv6 `::1/128` to `::/0`
3. Restart service: `pi@pi:~$ sudo service postgresql restart`
