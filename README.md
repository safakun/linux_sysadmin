### Linux system administrator course 
https://youtu.be/UCr04qIB7uc?si=UiAJ605C8VqpU3st 

### WHat is Linux?

- Linux is a kernel that powers Linux operating system
- Kernels are programs that talk directly to the hardware amd manage resources and processes 
- Kernels need a whole operating system to be useful 
- When a Linux kernel is bundled woth operating system software and shipped together, that is called a Linux distribution 

### Linux distributions 
- Red Hat Family 
- Debiam Family
- Source code distros
- System V init and SystemD 

### Minimalistic distros
- CoreOS
- Alpine linux 

Works inside Docker containers

package management system 

### Hardeare considerations
- Can your machine boot the installation media?
- How much hard drive space do you have?
- How much RAM do you need?
- Will your video card work?
- Will your wireless card work?
- What other hardware needs to work? 

### Ins5allation methods 
- DVD installation / ISO installation 
- USB installation 
- Hard drive installation 
- Network installation 

### Time and date
- How does a computer clock work?
- Why do time zones matter?
- Stored as localtime or UTC? What is the difference? 
- How does network time works?


### MAke hands dirty 

- info about package - man

```bash
$ man sudo
$ man -k sudo
$ man mandb
$ man nroff
```
- to exit press q button

- To see a path to man:
```bash
$ manpath

$ export МANPATH=/home/ share/ localman : /usr/share/man
```

How to detect if a software is installed - which in ubuntu and debian based, locate - in FreeBSD
```bash
ubuntu$ which gcc
freebsd$ ;pcate gcc
```
- command whereis searchs everywhere
```bash
ubuntu$ whereis gcc
freebsd$ locate signal.h
redhat$ rpm -q python

redhat$ rpm -qf /etc/httpd
freebsd$ pkg which /usr/ local / sbin/httpd
ubuntu$ dpkg-query -S /etc/apache2
```

- tcpdump - Tcpdump  prints  out a description of the contents of packets on a network interface that match the Boolean expression
```bash
ubuntu# sudo apt-qet install tcpdump
redhat# sudo yum install tcpdump
freebsd# sudo pkq install -у tcpdump
``` 

### Compile software from source code 

```bash
redhat$ cd / tmp

redhat$ git clone https://githuЬ.com/the-tcpdump-group/tcpdump.git

<status messages as repository is cloned>

redhat$ cd tcpdump

redhat$ git checkout taqs/tcpdump-4.7.4 -Ь tcpdump-4.7.4

Switched to а new branch 'tcpdump-4.7.4'

redhat$ . /confiqure

checking build system type... x86_64 - unknown - linux - gnu
checking for gcc... gcc
checking whether the С compiler works... yes

redhat$ make

<several pages of compilation output>

redhat$ sudo make install

<filesare moved into place>
```
- Look at README and INSTALL files of source code of packet to see what kind of steps need to install it from source cdoe


### install packets from web via curl
- curl  is  a tool for transferring data from or to a server. It supports
       these protocols: DICT, FILE, FTP, FTPS, GOPHER, GOPHERS,  HTTP,  HTTPS,
       IMAP,  IMAPS,  LDAP,  LDAPS, MQTT, POP3, POP3S, RTMP, RTMPS, RTSP, SCP,
       SFTP, SMB, SMBS, SMTP, SMTPS, TELNET or TFTP. The command  is  designed
       to work without user interaction.

```bash
$ curl о / tmp/ s al tboot -sL https : / /bootstrap . saltstack . com
$ sudo sh / tmp/ saltboot

$ curl -L https : / /badvendor . com 1 sudo sh
```

Публичные облачные провайдеры лучше, чем ЦОД 

### Loading 

Процесс загрузки состоит из нескольких задач, определенных в широком смысле.
• Поиск, ввод в память и запуск кода начальной загрузки.
• Поиск, ввод в память и запус к ядра операционной системы.
• Активирование сценариев запуска и системных демонов.
• Поддержание порядка управление переходам и системы из одного состояния в другое.

- Действия , указанные в последнем пункте, продолжаются до тех пор, пока система
остается в рабочем состоянии, поэтому граница между загрузкой и нормальной работой
по своей сути немного размыта.



