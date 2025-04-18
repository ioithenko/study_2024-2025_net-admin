---
## Front matter
title: "Отчёт по лабораторной работе №10"
subtitle: "Администрирование локальных сетей"
author: "Ищенко Ирина НПИбд-02-22"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Освоить настройку прав доступа пользователей к ресурсам сети [@netadmin].

# Задание

1. Требуется настроить следующие правила доступа:
1) web-сервер: разрешить доступ всем пользователям по протоколу HTTP
через порт 80 протокола TCP, а для администратора открыть доступ
по протоколам Telnet и FTP;
2) файловый сервер: с внутренних адресов сети доступ открыт по портам
для общедоступных каталогов, с внешних — доступ по протоколу FTP;
3) почтовый сервер: разрешить пользователям работать по протоколам
SMTP и POP3 (соответственно через порты 25 и 110 протокола TCP),
а для администратора — открыть доступ по протоколам Telnet и FTP;
4) DNS-сервер: открыть порт 53 протокола UDP для доступа из внутренней сети;
5) разрешить icmp-сообщения, направленные в сеть серверов;
6) запретить для сети Other любые запросы за пределы сети, за исключением администратора;
7) разрешить доступ в сеть управления сетевым оборудованием только
администратору сети.
2. Требуется проверить правильность действия установленных правил доступа.
3. Требуется выполнить задание для самостоятельной работы по настройке
прав доступа администратора сети на Павловской.

# Выполнение лабораторной работы

В рабочей области проекта подключим ноутбук администратора с именем admin к сети к other-donskaya-1 с тем, чтобы разрешить ему потом любые действия, связанные с управлением сетью. Для этого подсоединим ноутбук к порту 24 коммутатора msk-donskaya-sw-4 (рис. [-@fig:001]) и присвоим ему статический адрес 10.128.6.200 (рис. [-@fig:002]), указав в качестве gateway-адреса 10.128.6.1 и адреса
DNS-сервера 10.128.0.5  (рис. [-@fig:003]).

![Добавление ноутбука](image/1.png){#fig:001 width=70%}

![IP](image/2.png){#fig:002 width=70%}

![Шлюз и адрес DNS-сервера](image/3.png){#fig:003 width=70%}

Проверим доступность устройств до настройки маршрутизатора (рис. [-@fig:004]).

![Проверка пинга до настройки](image/4.png){#fig:004 width=70%}

Настроим доступа к web-серверу по порту tcp 80 (рис. [-@fig:005]).

![Доступ к web-серверу по tcp 80](image/5.png){#fig:005 width=70%}

Добавим список управления доступом к интерфейсу (рис. [-@fig:006]).

![Список управления доступом к интерфейсу](image/6.png){#fig:006 width=70%}

Проверим, что доступ к web-серверу есть через протокол HTTP (введя в строке браузера хоста ip-адрес web-сервера) (рис. [-@fig:003]).

![Проверка доступа по HTTP](image/7.png){#fig:007 width=70%}

При этом команда  ping будет демонстрировать недоступность web-сервера как по имени, так и по ip-адресу web-сервера (рис. [-@fig:008]).

![Проверка пингом](image/8.png){#fig:008 width=70%}

Настроим дополнительный доступ для администратора по протоколам Telnet и FTP (рис. [-@fig:009]).

![Доступ для admin по Telnet и FTP](image/9.png){#fig:009 width=70%}

Убедимся, что с узла с ip-адресом 10.128.6.200 есть доступ по протоколу FTP. Для этого в командной строке устройства администратора введем ftp 10.128.0.2, а затем по запросу имя пользователя cisco и пароль cisco (рис. [-@fig:0010]).

![Проверка FTP](image/10.png){#fig:0010 width=70%}

Попробуем провести аналогичную процедуру с другого устройства сети. Убедимся, что доступ будет запрещён (рис. [-@fig:0011]).

![Проверка FTP](image/11.png){#fig:0011 width=70%}

Настроим доступ к файловому серверу. Настроим доступ к почтовому серверу, доступ к DNS-серверу. Разрешим icmp-запросы (рис. [-@fig:0012]).

![Файловый, почтовый и DNS сервер](image/12.png){#fig:0012 width=70%}

Настроим доступ для сети Other (требуется наложить ограничение на исходящий из сети Other трафик, который по отношению к маршрутизатору msk-donskaya-gw-1 является входящим трафиком) (рис. [-@fig:0013]).

![Доступ для сети Other](image/14.png){#fig:0013 width=70%}

Настроим доступ администратора к сети сетевого оборудования (рис. [-@fig:0014]).

![Доступ к сети сетевого оборудования](image/15.png){#fig:0014 width=70%}

Проверим корректность установленных правил доступа, попытавшись получить доступ по различным протоколам с разных устройств сети к подсети серверов и подсети сетевого оборудования. Откроем терминал dep-donskaya-1 и пропингуем разные устройства. Увидим, что серверы и другие оконечные устройства пингуются, однако к сетевому оборудованию доступа нет, как и должно быть. (рис. [-@fig:0015]). 

![Проверка доступа](image/17.png){#fig:0015 width=70%}

Откроем терминал dk-donskaya-dmbelicheva-1 и пропингуем разные устройства. Увидим, что серверы и другие оконечные устройства пингуются, однако к сетевому оборудованию доступа нет, как и должно быть. Также попробуем подключится к web-серверу по ftp, доступ закрыт (рис. [-@fig:0016]).

![Проверка доступа](image/18.png){#fig:0016 width=70%}

Теперь проверим корректность настроенного доступа с admin. Есть доступ к серверу по ftp, а также успешно пингуется сетевое оборудование (рис. [-@fig:0017]).

![Проверка доступа](image/19.png){#fig:0017 width=70%}

Разместим еще один ноутбук admin на Павловской (рис. [-@fig:0018]).

![Размещение устройства](image/20.png){#fig:0018 width=70%}

Разрешим администратору из сети Other на Павловской действия, аналогичные действиям администратора сети Other на Донской (рис. [-@fig:0019]).

![Правила](image/21.png){#fig:0019 width=70%}

Просмотрим список правил в нашей сети. После выполнения была изменена обратная маска в правилах для их корректной работы (рис. [-@fig:0020]).

![Список правил](image/22.png){#fig:0020 width=70%}

Проверим работу устройства администратора (рис. [-@fig:0021]).

![Проверка](image/23.jpg){#fig:0021 width=70%}

# Выводы

В ходе выполнения лабораторной работы я освоила настройку прав доступа пользователей к ресурсам сети.

# Контрольные вопросы

1. Как задать действие правила для конкретного протокола?

Например, `permit tcp any host 10.128.0.4 eq pop3`.

2. Как задать действие правила сразу для нескольких портов?

Для этого нужна команда `interface range`.

3. Как узнать номер правила в списке прав доступа?

С помощью команды `show access-lists`.

4. Каким образом можно изменить порядок применения правил в списке контроля доступа?

Команда `access-list <номер в списке> permit`.

# Список литературы{.unnumbered}

::: {#refs}
:::
