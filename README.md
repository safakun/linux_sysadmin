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

- Менеджер systemd осуществляет все функции init, ранее реализованные с помо­щью хитроумных уловок и приемов, и формализует их в единое целое, позволяя настра­ивать, получать доступ и управлять службами.

- Системный менеджер systemd это не отдельный демон, а набор программ, де­монов, библиотек, технологий и компонентов ядра. 

- Модульные файлы могут находиться в нескольких местах. Основное место, где паке­ты сохраняют свои модульные файлы во время инсталляции - /usr/liЬ/systemd/system; в некоторых системах для этого испол ьзуется каталог /lib/systemd/system. 

- Менеджер systemd поддерживает телескопическое представление всех этих катало­гов, поэтому они в значительной степени эквивалентны. Если возникает конфликт, то файлы в каталоге /etc имеют наивысший приоритет. 

- По соглашению, модульные файлы именуются суффиксом, который зависит от типа
настраиваемого устройства. Например, служебные модули имеют суффикс .service,
а таймеры используют суффикс .timer. Внутри модульного файла не которые разде­лы (например, [Unit]) относятся в общем случае ко всем типам модулей, но другие (например, [Service]) могут отображаться только в контексте определенного типа устройства. 

- Команда systemctl - это универсальная команда для изучения состояния менед­жера systemd и внесения изменений в его конфигурацию. Как и в случае с системой Git и нескольким и другим и сложными пакетами программного обеспечения, первый аргумент команды systemctl обычно представляет собой подкоманду, которая задает общую последовательность действий, а последующие аргументы являются специфиче­ским и для этой кон кретной подкоманды. Подкоманды могут быть отдельными командам и верхнего уровня, но для согласованности и ясности они объединены в команду **systemctl**.

```bash
$ systemctl list-units --type=service

$ systemctl list-unit-files --type=service 

$ sudo systemctl status -1 cups
$ sudo systemctl еnаblе cups
$ sudo systemctl start cups
```
- Опция -l для запроса полных записей

**Состояния модульных файлов**

- **Ьаd** - У менеджера systemd возникла какая-то проблема; обычно это связано со сбоем
модульного файла
- **disabled** -  Присутствует, но не настроен для автономного запуска
- **enabled** - Инсталлирован и запущен; стартует автономно
- **indirect** - Отключен, но имеет одинаковые значения в разделах Also, которые могут быть включены
- **linked** - Модульный файл, доступный через символическую ссылку
- **masked** - Нежелательный статус с логической точки зрения
- **stаtiс** - Зависит от другого устройства; не требует установки

- У многих устройств нет процедуры инсталляции, поэтому нельзя сказать, что они
включены или отключены; они просто доступны. Статус таких элементов указан как
static. Они активируются только вручную (systemctl start) или указываются в ка­честве зависимостей от других активных модулей.

- Файлы, имеющие состояние linked, были созданы с помощью команды systemctl
link. Эта команда создает символическую ссылку из одного из каталогов system ме­неджера sys temd на модульный файл, который находится в другом месте в файловой
системе. Такие модульные файлы могут обрабатываться командами или указывать­ся в качестве зависимостей, но они не являются полноправными элементами системы и имеют некоторые заметные отклонения. Например, применение команды systemctl disaЬle к модульному файлу в состоянии linked приводит к удалению связи и всех ссылок на него.

- Состояние masked означает "заблокирован администратором". Менеджер systemd знает о модуле, но ему запрещено активировать его или действовать по любой из ero
конфигурационных директив с помощью команды systemctl mask. В этом случае сле­дует отключить модули, находящиеся в состоянии enaЫed или linked, с помощью ко­манды systemctl disable и зарезервировать команду systemctl mask для модулей в состоянии static.

- Традиционный демон init определяет как минимум семь уровней выполнения, но многие из них на самом деле не используются. Стремясь к ложно понятой исторической преемственности, менеджер systemd определяет цели как прямые аналоги уровней за­пуска демона init (runlevel O. target и т.д.). Он также определяет мнемонические цели для повседневного использования, такие как poweroff. target и graphical.target. В табл . 2.6 показано сопоставление между уровнями выполнения init и целя­ми systemd.
- Единственными целями, которые действительно необходимо знать, являются multiuser.target и graphical.target для повседневного использования и rescue.target для доступа к однопользовательскому режиму. Для того чтобы изменить теку­щий режим работы системы, используйте команду systemctl isolate:
```bash
$ sudo systemctl isolate multi-user.tarqet
```

**Сопоставление между уровня ми запуска ini t и системными целями**
Уровень выполнения - цель - описание
О - poweroff.target - Остановка системы
emergency - emergency.target - Простейшая оболочка для восстановления системы
1, s, single - rescue.target - Однопользовательский режим
2 - multi-user.target - Многопользовательский режим (командная строка)
3 - multi-user.target - Многопользовательский сетевой режим
4 - multi-user.target - Обычно не используется init
5 - graphical.target - Многопользовательский сетевой режим с графическим
интерфейсом
6 - reboot.target - Перезагрузка системы

- Для того чтобы увидеть цель, к которой система загружается по умолчанию, запусти­те подкоманду get-default:
```bash
$ systemctl get-default
```

- Большинство дистрибути вов Linux загружаются п о умолчанию в модуль graphical .
targe t , что не подходит для серверов, которы м не н ужен графический и нтерфейс. Но
это легко изменить:
```bash
$ sudo systemctl set-default multi-user.target
```

- Чтобы увидеть все доступные цели с истемы , запустите с исте м н ые списки:
```bash
$ systemctl list-units --type=target
```

### зависимости между модулями

- Явные зависимости в разделе [Unit] модульного файла

- Wants - Модули, которые должны быть активированы одновременно, если это возможно, но не
обязательно
- Requires - Строгие зависимости; отказ от каких-либо предварительных условий прекращает работу
этой службы
- Requisite - Аналогично Requires, но модуль должен быть активным
- BindsTo - Аналогично Requires, но модуль должен быть связан еще более тесно
- PartOf - Аналогично Requires, но вли яет только на запуск и остановку
- Сonf1iсts - Отрицательные зависимости; не может взаимодействовать с этими единицами

- Теперь внимательно рассмотрим несколько директив, используемых в модульных файлах. Вот модульный файл для веб-сервера NGINX, nginx.service:
```bash
[Unit]
Description=The nginx НТTР and reverse proxy server
After=network.target remote-fs.target nss-lookup.target

[Service]
Type=forking
PIDFile=/run/nginx.pid
ExecStartPre=/usr/bin/rm -f /run/nginx.pid
ExecStartPre=/usr/sbin/nginx -t
ExecStart=/usr/sbin/nginx
ExecReload=/bin/kill -s HUP $МAINPID
KillMode=process
KillSignal=SIGQUIT
TimeoutStopSec=5
PrivateTmp=true

[Install]
WantedBy=multi-user.target
```

- Эта служба имеет тип forking, что означает, что команда запуска должна завершить­ся, даже если демон продолжает работать в фоновом режиме

- Просмотрите примеры в каталоге /usr/lib/system.d/system

Поместите свой новый файл в каталог /etc/system.d/system. Затем можно запу­стить команду
```bash
$ sudo systemctl еnаblе custom.service
```

```bash
$ sudo systemctl edit nginx.service
<отредактируйте замещающий файл в редакторе>
$ sudo systemctl restart nginx.service
```

Как правило, не следует редактировать модульный файл, написанный не вами.
Вместо этого создайте каталог конфигурации в каталоге /etc/system.d/system/unit­file.d и добавьте один или несколько файлов конфигурации, которые называются ххх.conf. Часть ххх не имеет значения; просто убедитесь, что файл имеет суффикс conf
и находится в нужном месте. Имя override.conf я вляется стандартным.
Файлы с расширением .conf имеют тот же формат, что и модульные файлы, и на
самом деле менеджер systemd сглаживает их все вместе с исходным файлом. Однако,
если оба источника попытаются установить значение одного и того же параметра, переопределенные файлы имеют приоритет над исходным и модульными файлами.

**Журнал systemd**
```bash
$ journalctl
$ journalctl --list-boots
$ journalctl -Ь -1
$ journalctl -Ь a73415fade0e4e7f4bea6091383d180dc
$ journalctl -u ntp

```
Выключение и перезагрузка системы
```bash
$ halt -p
$ reboot
$ shutdown
```

### В случае, если система не грузится

- Не отлаживать; просто верните систему в хорошо известное состояние.
- Довести систему до уровня, достаточного для запуска оболочки и отладки в интерактивном режиме.
- Загрузить отдельный системный образ, смонтировать файловые системы неис­правной системы и исследовать его.

Первый вариант наиболее часто используется в облаке  но он может быть полезен и на
физических серверах, если у вас есть доступ к последнему образу всего загрузочного дис­ка. Если ваша организация делает резервные копи и файловой системы, восстановление всей системы может создать больше проблем, чем хотелось бы. Мы обсуждаем вариант восстановления всей системы в режиме восстановления облачных систем немного ниже.

- Часто можно найти указатели на доступные файловые системы, просмотрев ка­талог /etc/fstab. В системе Linux можно выполнить команду fdisk -l (буква L в нижнем регистре), чтобы просмотреть список разделов диска локальной системы. Аналогичная процедура для системы FreeBSD заключается в том, чтобы выполнить ко­манду camcontrol devlist для идентификации дисковых устройств, а затем - коман­ду fdisk -s устройство для каждого диска.

- Если каталог /etc является ча­стью корневой файловой системы (обычный случай), то будет невозможно редактиро­вать многие важные файлы конфигурации. Чтобы устранить эту проблему, необходимо начать сеанс в одн опользовательс ком режиме, перемонтировав каталог в режиме чтения и записи. В системе Linux этот трюк обычно выполняет команда
```bash
linux# mount -о rw , remount /
```
В системах FreeBSD возможность повторного подключения является неявной, когда вы
повторяете монтирование, но необходимо явно указать исходное устройство. Например,
```bash
freebsd# mount - о rw /dev/qpt/rootfs /
```

### Файловая система и контроль доступа 

- Оперделить владельца файла
```bash
$ ls -l README.md
```

- И ядро, и файловая система отслеживают владельцев и группы как числа, а не как
текстовые имена. В подавляющем большинстве случаев идентификационные номера
пользователей (короткие идентификаторы UID) сопоставляются с именами пользовате­
лей в файле **/etc/passwd**, а идентификационные номера групп (GID) сопоставляются
с именами групп в файле **/etc/ group**

- Определяющей характеристикой учетной записи root является ее идентификатор
UID, равный О. Ничто не м шает вам изменять имя пользователя в этой учетной записи
ии создавать дополнительные учетные записи, идентификаторы UID которых равны О; однако это плохие идеи. Такие изменения обычно создают непреднамеренные нарушения безопасности системы. Они также создают путаницу, когда другим людям приходит­ся иметь дело со странным способом настройки вашей системы.

- пароли (традиционно) хранятся в защищенном файле **/etc/master.passwd** или **/etc/shadow**, пользователя м нужна команда passwd, чтобы обеспечить доступ. Пользователи могут изменять только собственные пароли, но пользователь root может изменять любой пароль. 

- Команда **su** не фиксирует действия, производимые привилегированным пользо­вателем, но добавляет запись в журнальный файл с указанием, кто и когда вошел в си­стему под именем root.

- Команду su в значительной степени может заменить программа sudo (см. следую­щий раздел), саму же команду su лучше всего оставить для аварийных ситуаций.

```bash
ubuntu$ sudo -u operator /usr/sbin/ dump Ou /dev/sda1
```

**Отключение входа с root**
- В системе Linux, команда **passwd -l** блокирует учетную запись, добавляя
знак ! к зашифрованному паролю с эквивалентными результатами.

разблокировать учетную за­пись
```bash
ubuntu$ sudo passwd -u root
```

- Обычно принято заменять звездочкой зашифрованное поле пароля этих специальных пользователей в файле shadow или master.passwd, чтобы под их учетными за­писями нельзя было войти в систему. В качестве их системных оболочек должны быть установлены программы /Ьin/false или /Ьin/nologin, чтобы защитить от удаленных попыток входа в систему, которые используют альтернативы паролей, такие как файлы ключей SSH.

- Система Linux может распределять процессы по иерархическим разделам (пространствам имен), из которых видна только часть системных файлов, се­тевых портов и процессов. Ломимо прочего, эта схема действует как форма превентивного контроля доступа. Вместо того, чтобы основывать решения
управления доступом на потенциально тонких критериях, ядро просто отри­цает существование объектов, которые не видны изнутри данной области.

- Внутри раздела применяются обычные правила контроля доступа, и в большинстве
случаев процессы, которые бъmи ограничены, даже не знают об этом. Лоскольку огра­ничение является необратимым, внутри раздела процессы могут выполняться с правами root, не опасаясь, что они могут поставить под угрозу другие части системы. Этот умный трюк является одним из оснований для программной контейнеризации и его наиболее известной реализации **Docker**.

###  SElinix 
Файл /etc/selinux/config - это элемент управления верхнего уровня для систем SELinux. В нем есть и нтересные строки:
```bash
SELINUX=enforcing
SELINUXTYPE=targeted
```
Первая строка имеет три возможных значения: enforcing, permissive или disabled. Параметр enforcing гарантирует, что загруженная политика применяется и запрещает нарушения. Параметр реrmissive допускает нарушения, но регистрирует их в журнале syslog, что полезно для отладки и разработки политики. Параметр disabled полностью отключает систему SELinux.
Имя SELINUXTYPE представляет собой имя используемой базы данных политик. Это, по суrи, имя подкаталога внуrри каталога /etc/selinux. В один и тот же момент вре­мени применяться может только одна политика, а доступные наборы политик зависят от системы.

В Red Hat Чтобы получить полную систему МАС, удалите модули unconfinedus и unconfineduser с помощью команды semodule -d
```bash
redhat$ semodule -d
```

- Система Red Hat также определяет политику mls, которая реализует м ногоуровне­вую зашиту DoD. Она устанавливается отдельно с помощью команды yum install selinux-policy-mls.
- Если вы заинтересованы в разработке собственных политик SELinux, обратите внимание на утилиту audit2allow. Она создает определения политики из журналов нару­шений. Идея заключается в том, чтобы разрешить защиту подсистемы, регистрируя, но не запрещая ее нарушения. Затем можно подключить подсистему и создать политику, которая, по существу, позволяет этой подсистеме все. К сожалению,трудно гарантиро­вать полное покрытие всех путей кода с помощью такого подхода, поэтому автоматиче­ски созданные профили вряд ли будут идеальными.

### AppArmor 
- Apparmot используется в Ubutnu 
- Система AppArmor реализует стратегию МАС и предназначена в качестве дополне­ния к традиционной системе управления доступом UNIX. Несмотря на то что возмож­на любая конфигурация, AppArmor не предназначена для системы, ориентированной на пользователя. Ее основная цель - обеспечение безопасности, т.е. ограничение ущер­ба, который могут нанести отдельные программы, если они будут скомпрометированы или запущены. 

- Профили AppArmor хранятся в файле **/etc/apparmor.d**, и относительно понят­ны даже без подробного знания системы. Например, вот профиль для демона cups ­browsed, входящего в систему печати в операционной системе Ubuntu:
```bash
#include <tunables/global>
/usr/sbin/cups-browsed(
#include <abstractions/base>
#include <abstractions/nameservice>
#include <abstractions/cups-client>
#include <abstractions/dbus>
#include <abstractions/pll-kit>
/etc/cups/cups-browsed.conf r,
/etc/cups/lpoptions r,
/{var/,} run /cups/certs/* r,
/var/cache/cups/* r w,
/tmp/** r w,
#Site-specificadditions and overrides. See local / README .
#include <local/usr.sbin.cups-browsed>
)
```

### Signals
![linux loading](https://github.com/safakun/linux_sysadmin/blob/main/signals.png) 

- Получить список названий сигналов:
```bash
ubuntu$ kill -l
```

- Синтаксис команды kill:
kill [-сигнал] pid

Команда killall уничтожает процессы, заданные именем. Например, следующая команда уничтожает все процессы веб-сервера Apache.
```bash
ubuntu$ sudo killall httpd
```
Команда pkill осуществляет поиск процессов, заданных именами (или другими атрибутами, например EUID), и посылает найденным процессам сигнал. Например, следующая команда посылает сигнал TERM всем процессам, выполняемым от имени пользователя ben.
```bash
$ sudo pkill -u bеn
```
- Команда ps - основной инструмент, которым системный администратор пользует­ся для текущего контроля процессов. 

```
redhat$ ps aux
redhat$ ps lax
$ ps aux | grep sshd
$ ps aux | grep -v grep | grep sshd
$ pidof /usr/bin/bash
$ pgrep bash
```

- интерактивный мониторинг процессов с помощью команды top
```bash
ubuntu$ top
freebsd$ top -P
```

```bash
$ nice -n 5 /bin/lonqtask // Понижаем приоритет (увеличиваем фактор уступчивости) на 
$ sudo renice -5 8829 // Задаем фактор уступчивости равным 5
$ sudo renice 5 -u boggs // Задаем фактор уступчивости процессов пользователя boggs равным 5
```
- Команда vmstat - Report virtual memory statistics
```bash
ubuntu$ vmstat
ubuntu$ man proc
freebsd$ sudo mount -t procfs proc /proc
ubuntu$ man strace 
ubuntu$ strace -р [PID]

```

- Трассировка системных вызовов - мощный инструмент для отладки в руках систем ных администраторов. Переходите к этим инструментам после того, как исчерпаете бо­лее традиционные способы, такие как просмотр файлов журнала и настройка процесса
для подробного вывода. Не пугайтесь плотного вывода; обычно достаточно сосредоточиться на читаемых человеком частях. 

- Вы можете определить процессы, которые используют чрезмерное процессорное
время, просматривая результаты работы команд **ps** или **top**. Также проверьте сред­ние значения загрузки системы, о которых сообщает команда **uptime**. Традиционно эти значения определяют среднее количество процессов, которые были запущены за предыдущие 1-, 5- и 15- минутные интервалы. В системе Linux среднее значение на­грузки также учитывает занятость, вызванную дисковым трафиком и другими форма­ми ввода-вывода.

- Помните о возможности взлома. Вредоносная программа, как правило, не прове­ряется на правильность в различных средах, поэтому более вероятно, что в среднем возникнет какое-то вырожденное состояние. Если вы подозреваете неладное, полу­чите трассировку системного вызова с помощью команд **strace** или **truss**, чтобы понять, что делает данный процесс (например, взламывает пароли) и rде хранятся его данные.

- Команды **df** и **du** описывают использование диска по-разному. Команда **df** сообщает о дисковой памяти, используемой смонтированной файловой с истемой, в соответствии с показателями , записанными в метаданных файловой системы. Команда du суммирует размеры всех файлов в данном каталоге. 

- Если вы не можете определить, какой процесс использует файл, попробуйте за­пустить команды **fuser** и **lsof**, чтобы получить дополнительную информацию. 

### Демон cron 
Мы также рекомендуем использовать полный путь к команде, чтобы задание выполнялось должным образом, даже если параметр РАТН не установлен так, как ожидалось. Например, следующая команда каждую м инуту записывает дату и время безотказной работы в файл в домашнем каталоге пользователя:
* * * * * echo $ ( /bin/date ) - $ (/usr/bin/uptime) >> ~/uptime.log
Кроме того, вы можете явно задать переменные среды в верхней части файла crontab:
РАТH = /bin: /USR/bin
* * * * * echo $(date) - $(uptime) >> ~/uptime.log
- Вот еще несколько примеров корректных записей в файле crontab:
```bash
* / 1 0 * * * 1, 3, 5 echo ruok | /usr/bin/nc localhost 2181
mail -s "TCP-port 2181 status" ben@admin.com
```

- Эта строка отправляет результаты проверки подключения к порту 2181 каждые
10 минут по понедельникам, средам и пятницам. Поскольку демон cron выполняет
команду посредством оболочки sh, специальные символы оболочки, такие как каналы
и перенаправления, функционируют должным образом.

```bash
20 1 * * * find /tmp -mtime +7 - type f -ехес rm -f { } ';'
```
- Эта команда выполняется каждую ночь в 1:20. Она удаляет все файлы в каталоге
/tmp, которые не были изменены за семь дней. Символы ';' в конце строки означают
конец аргументов подкоманды для поиска.

- Демон cron не пытается компенсировать команды, которые не были запущены,
пока система не работала. Тем не менее он хорошо разбирается в настройках времени,
например при переходе на летнее и зимнее время.
- Если ваше задание cron является сценарием, обязательно сделайте его исполняемым
(с помощью команды chmod +х), иначе демон cron не сможет его выполнить. В каче­стве альтернативы настройте команду cron для непосредственного вы полнения вашего
сценария прямо из командной оболочки (например, **bash -с ~/bin/myscript.sh**).

```
$ man crontab
```
- Демон cron регистрирует свою деятельность в журнале syslog, используя функцию
cron, причем большинство сообщений отправляется на уровне info. Конфигурации
журнала syslog, заданные по умолчанию, обычно отправляют данные журнала cron
в отдельный файл.

- Два файла конфигурации указывают, какие пользователи могут отправлять файлы
crontab: в системе Linux - /etc/cron.{ allow , deny }, а в системе FreeBSD - /var/cron/{ allow , deny }. Многие стандарты безопасности требуют, чтобы файлы crontab бьли до­ступны только для обслуживания учетных записей или для пользователей, имеющих на это обоснованное право. Файлы allow и deny способствуют соблюдению этих требований.

- Таймеры systemd:
```bash
$ systemctl enable
$ systemctl start 
```

С помощью команды **systemd-run** можно запланировать выполнение команды в соответствии с любым из стандартных типов таймера systemd, но не создавая файлы
таймера и службы, предназначенные для конкретной задачи. Например, можно извле­кать файлы из репозитория Git каждые десять минут:
```bash
$ systemd-run --on-calendar '*:0/10' /bin/sh -с "cd /арр && git pull"
```

- Чтобы отменить и удалить временный таймер, просто остановите его, выполнив ко­манду stop systemctl:
```bash
$ sudo systemctl stop run-8823.timer
```
- Команда systemd-run создает таймер и модульные файлы в подкаталогах /run/systemd/system Однако временные таймеры после перезагрузки не сохраняются. Чтобы сделать их постоянными, нужно найти их в каталоге /run, настроить их по мере необходимости и инсталлировать в каталоге /etc/systemd/system. Обязательно оста­новите временный таймер перед запуском или включением постоянной версии.

### В этом разделе м ы рассмотри м несколько общих задач, которые часто автоматизиру­ются с помощью демона cron или таймера systemd. 

- Следующая запись crontab реализует простую электронную почту. Вы можете использовать такую запись, чтобы автоматически отправлять результаты ежедневного отчета или результаты выполнения команды. (Строки были обрезаны, чтобы поместиться
на странице. На самом деле это одна длинная строка.)
```bash
30 4 25 * * /usr/bin/mail -s "Time to do the TCP reports" ben@admin.com%TCP reports are due to the end of the month! Get busy!%%Sincerely, %cron% 
```
- Обратите внимание на использование символа % как для выделения команды из
входного текста, так и для отметки окончаний строки внутри ввода. Это сообщение отправляется по электронной почте в 4:30 утра 25 числа каждого месяца. 

- Очистка файловой системы
- Ротация файла журнала
- Выполнение пакетных заданий
- Резервное копирование и зеркалирование
Вы можете использовать запланированную задачу для автоматического резервного
копирования каталога в удаленную систему. Мы рекомендуем запускать полное резерв­ное копирование один раз в неделю, накапливая инкрементные различия каждую ночь. Запускайте резервное копирование поздно ночью, когда нагрузка на систему, вероятно,
будет низкой. Зеркала - это побайтовые копии файловых систем или каталогов, размещенных в другой системе. Они могут использоваться как форма резервного копирования или как способ сделать файлы доступными в нескольких местах. Веб-сайты и репозитории программного обеспечения часто зеркалируются, чтобы повысить отказоустойчивость системы и обеспечить более быстрый доступ для физически удаленных пользователей. Используйте периодическое выполнение команды **rsync** для поддержания зеркал в ак­туальном состоянии. 

# Файловая система 
### В файловую систему UNIX/Linux входят
- процессы
- аудиоустройства 
- структуры данных ядра и параметры настройки
- каналы межзадачного взаимодействия 
- файлы 

Файловую систему можно представить состоящей из четырех основных компонентов:
1. пространство имен - методы именования объектов и организации их в виде еди ­
н о й иерархии;
2. API - набор системных вызовов для перемещения между объектами и управле­ния ими;
3. модель безопасности - схема защиты, сокрытия и совместного использования объектов;
4. реализация - программный код, который связывает логические модели с диско­вой подсистемой.

- В современных ядрах систем определен абстрактный интерфейс, позволяющий рабо­тать с различными файловыми системами. Одни части файлового дерева обрабатывают­ся традиционной дисковой подсистемой, другие управляются специальными драйверами ядра. Например, за работу файловых систем - как сетевых (Network File System - NFS),
так и общих межсетевых (Common Internet File System - CIFS), - отвечает драйвер, кото­рый перенаправляет запросы серверу, расположенному на другом компьютере. 

- файлы устройств позволяют программам взаи­модействовать с драйверами ядра. Они не являются файлами данных, но обрабатывают­ся файловой с истемой, а их характеристики записываются на диск. Еще одним усложняющим фактором является то, что ядро поддерживает несколь­ко типов дисковых файловых систем. Доминирующими стандартами в данный момент являются системы ext4, XFS и UFS, а также ZFS и Btrfs компании Oracle. Однако су­ществует и множество других файловых систем, таких как VxFS компании Veritas и JFS компани и IВМ.


