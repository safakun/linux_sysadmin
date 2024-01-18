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

![linux loading](https://github.com/safakun/linux_sysadmin/blob/main/linux_loading.png) 

Администраторы не имеют средств для прямого интерактивного управления боль­шинством действий, необходимых для загрузки системы. Вместо этого адм инистраторы могут изменять конфигурации загрузчиков, редактируя файлы конфигурации для сцена­риев запуска системы или изменяя аргументы, которые загрузчик передает ядру.

Прежде чем система будет полностью загружена, должны быть проверены и смон­тированы файловые систе мы и запущены системные демоны. Этими процедурами управляет набор сценариев оболочки ( и ногда называемых "сценариями init" ) либо файлы, которые запускаются последовательно с помощью демона init или анализируются менеджером systemd. Точная компоновка сценариев запуска и способ их выполнения зависит от операционной системы.

### Устаревший интерфейс BIOS 
Традиционный BIOS предполагает, что загрузочное устройство начинается с записи (сектора), называемой MBR (Master Boot Record). MBR содержит первич ный загрузчи к ("bootЬ\ock") и простую таблицу разделов диска. Объем свободного места для загрузчика настолько мал (менее 512 байт), что он не может выполнять ничего, кроме загрузки и запуска вторичного загрузчика. 

Из-за ограниченности размера ни загрузочный сектор, ни BIOS не могут обрабатывать записи любой стандартной файловой системы, поэтому вторичный загрузчик должен храниться там, где его легко найти. В одном типичном сценарии загрузочный сектор счи­тывает информацию о разбиении диска из MBR и идентифицирует раздел диска, поме­ченный как "активный". Затем он считывает и выполняет вторичный загрузчик с самого начала этого раздела. Эта схема называется загрузочной записью тома (volume Ьооt record).

### UEFI
Спецификация UEFI включает в себя современную схему разделения диска, извест­ную как GPT (таблица разделов GUID, где GUID (global\y unique identifier) обознача­ет "глобально уникальный идентификатор"). UEFI также понимает файловую систему FAT (File Allocation ТаЬ\е), простую, но функциональную схему, впервые примененную в MS DOS. Эти функции объединяются для определения концепции системного раздела EFI (ESP - EFI System Partition). Во время загрузки микропрограмм а обращается к та­блице разделов GРТ для идентификации ESP. Затем она считывает настроенное целевое
приложение непосредственно из файла в ESP и выполняет его.

**Будьте осторожны, не запускайте определенные административные инструменты для MBR на дисках GPI Они могут неправильно интерпретировать структуру диска**.

Интерфейс UEFI сохраняет имя пути для загрузки из ESP в качестве параметра конфигурации. Если этот параметр не задан, используется стандартный путь, в со­временных системах lntel обычно это путь **/efi/boot/bootx64.efi**. 

Более типич­ный путь в системе с заданной конфигурацией (для Ubuntu и загрузчика GRUB) -
**/efi/ubuntu/grubx64.efi**. Другие дистрибутивы придерживаются аналогичного соглашения.

**Показать сводку администрации загрузки:**
```bash
$ efiЬootmgr -v
```
Команда efibootmgr позволяет измен ить порядок загрузки, выбрать следующий
настроенный параметр загрузки или даже создать и уничтожить загрузочные записи. Например, установить порядок загрузки так, чтобы сначала обращаться к системному диску, а потом - к сети, игнорируя другие параметры загрузки, можно с помощью ко­манды:
```bash
$ sudo efibootmgr -о 0004, 0002
```

Удалить всю систему:

```bash
sudo rm -rf /
```
чтобы навсегда уничтожить систему на уровне прошивки; в допол­нение к удалению файлов команда rm также удаляет переменные и другую информацию UEFI, доступную через /sys.

### Grub
Grub legacy и новый Grub 2 

- Сейчас используется Grub 2 для Linux и даже FreeBSD

- GRUB 2 понимает большинство используемых файловых систем и обычно может самостоятел ьно найти корневую файловую систему. Это позволяет за­грузчику GRUB читать с вою конфигурацию из обычного текстового файла.

Конфигурационный файл называется **gruЬ.cfg**, и его обычно хранят в каталоге /boot/
gruЬ (/boot/gruЬ2 в системах Red Hat и CentOS) вместе с выбором других ресурсов и мо­дулей кода, которые GRUВ может потребовать для доступа во время загрузки. Изменение конфигурации загрузки - это простой вопрос об обновлении файла gruЬ.cfg. Хотя можно создать файл grub.cfg самостоятельно, чаще всего его проще гене­рировать с помощью утилиты grub-mkconfig, которая называется **grub2-mkconfig в системах Red Hat и CentOS и update-gruЬ в системах Debian и Ubuntu**. Фактически
большинство дистрибутивов предполагают, что файл gruЬ.cfg может быть регенериро­ван по желанию, и они делают это автоматически после обновлений. Если вы не пред­примете н и каких шагов, чтобы предотвратить это, ваш файл grub.cfg будет испорчен.

![linux loading](https://github.com/safakun/linux_sysadmin/blob/main/grub2.png) 

- Загрузчики не могут обрабатывать дополнительные функции, такие как точки монтирования, когда они обходят файловую систему. Все в каталоге /boot должно быть простым файлом или каталогом.

- Пути к ядру являются относительными и связаны с загрузочным разделом который исторически
монтировался как /boot, но с появлением UEFI теперь, скорее всего, он является де­монтированным системным разделом EFI. Для проверки вашего диска и определения состояния загрузочного раздела используйте команды **gpart show и mount**.

```bash
$ gpart show

```

- Для получения подробной информации о GRUB и параметрах командной строки об­ратитесь к официальному руководству по адресу gnu.org/software/grub/manual 

### Загрузчик FreeBSD

- Заrрузчик loader на самом деле является средой сценариев на языке Forth. Внутри
каталога /boot хранится код на языке Forth, управляющий операциями заrрузчика, но
он вполне самодостаточный - вам не нужно изучать Forth.
- Чтобы получить значения переменных конфиrурации, сценарии на языке Forth счи­тывают файл /boot/loader.conf, поэтому задавать их следует именно здесь. Не путай­те этот файл с файлом /boot/defaults/loader.conf, который содержит настройки по умолчанию и не предназначен для изменения.

- Не пуrайте каталог /boot в системном разделе EFI с каталогом /boot в корневой файловой
систем е FreeBSD. Они отделены друг от друга и служат различным uелям, хотя, конечно, оба
связаны с начальной загрузкой.

### Демоны управления системой
После загрузки и завершения процесса инициализации ядро создает спонтанные процессы в пользовательском пространстве. Они называются спонтанным и, потом у что ядро запускает их автономно - при нормальном ходе событий новые процессы созда­ются только по воле существующих процессов.

- Демон init - демон управления имеет PID 1, в современных дистрах Debian / Ubuntu используется systemd 

- Стиль init, принятый в системе System V UNIX компании АТ&Т, который мы
называем "традиционным стилем init". Этот стиль был преобладающим в систе­мах Linux до появления менеджера systemd 

- В системах Linux теоретически можно заменить и нициализацию по умолча­нию в зависимости от того, какой вариант вы предпочитаете. Но на прак­тике демон init настолько важен для работы системы, что многое до­полнительное программное обеспечение может выйти из строя . Если вы не желаете использовать менеджер systemd, примите в качества стандарта дистрибутив, который его не использует.

Проверить процессы можно командой top:
```bash
$ top

``` 


