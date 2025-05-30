---
## Front matter
title: "Отчёт по лабораторной работе №5"
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

Получить основные навыки по настройке VLAN на коммутаторах сети [@netadmin].

# Задание

1. На коммутаторах сети настроить Trunk-порты на соответствующих интерфейсах, связывающих коммутаторы между
собой.
2. Коммутатор msk-donskaya-sw-1 настроить как VTP-сервер и прописать на
нём номера и названия VLAN.
3. Коммутаторы msk-donskaya-sw-2 — msk-donskaya-sw-4, mskpavlovskaya-sw-1 настроить как VTP-клиенты, на интерфейсах указать
принадлежность к соответствующему VLAN.
4. На серверах прописать IP-адреса.
5. На оконечных устройствах указать соответствующий адрес шлюза и прописать статические IP-адреса из диапазона соответствующей сети, следуя
регламенту выделения ip-адресов (см. табл. 3.4 из раздела 3.3).
6. Проверить доступность устройств, принадлежащих одному VLAN, и недоступность устройств, принадлежащих разным VLAN.



# Выполнение лабораторной работы

Настроим Trunk-порты на соответствующих интерфейсах всех коммутаторов (рис. [-@fig:001]), (рис. [-@fig:002]), (рис. [-@fig:003]), (рис. [-@fig:004]) и (рис. [-@fig:005]).

![Trunk-порты](image/1.png){#fig:001 width=70%}

![Trunk-порты](image/2.png){#fig:002 width=70%}

![Trunk-порты](image/3.png){#fig:003 width=70%}

![Trunk-порты](image/4.png){#fig:004 width=70%}

![Trunk-порты](image/5.png){#fig:005 width=70%}

Настроим коммутатор msk-donskaya-sw-1 как VTP-сервер и пропишем на нём номера и названия VLAN (рис. [-@fig:006]).

![VTP-сервер](image/6.png){#fig:006 width=70%}

Настроим коммутаторы msk-donskaya-sw-2 — mskdonskaya-sw-4, msk-pavlovskaya-sw-1 как VTP-клиенты и на интерфейсах укажем принадлежность к VLAN (рис. [-@fig:007]), (рис. [-@fig:008]), (рис. [-@fig:009]) и (рис. [-@fig:0010]). Дополнительно используем команду, чтобы получить информацию о VLAN:

`vtp password cisco`

![VTP-клиент](image/7.png){#fig:007 width=70%}

![VTP-клиент](image/8.png){#fig:008 width=70%}

![VTP-клиент](image/9.png){#fig:009 width=70%}

![VTP-клиент](image/10.png){#fig:0010 width=70%}

Проверим корректность VLAN (рис. [-@fig:0011]).

![VLAN](image/11.png){#fig:0011 width=70%}

На серверах пропишем IP-адреса (рис. [-@fig:0012]) и (рис. [-@fig:0013]).

![Шлюз](image/12.png){#fig:0012 width=70%}

![IP-адрес](image/13.png){#fig:0013 width=70%}

Также после указания статических IP-адресов на оконечных устройствах проверим с помощью команды ping доступность устройств, принадлежащих
одному VLAN, и недоступность устройств, принадлежащих разным VLAN (рис. [-@fig:0014]). Внутри одного VLAN пропингуем с `dk-pavlovskaya-1` `dk-donskaya-1`. Пакеты успешно доходят. С того же устройства попробуем пропинговать другой VLAN. Пакеты не доходят.

![Проверка доступности устройств](image/14.png){#fig:0014 width=70%}

Используя режим симуляции в Packet Tracer, изучим процесс передвижения пакета ICMP по сети. Изучим содержимое передаваемого пакета и заголовки задействованных протоколов (рис. [-@fig:0015]) и (рис. [-@fig:0016]).
Можем посмотреть информацию о пакете, его заголовки. Кадр физического уровня Ethernet, где указаны mac-адреса, кадр сетевого уровня IP, где указаны IP-адреса и ICMP кадр.

![ICMP](image/15.png){#fig:0015 width=70%}

При передаче этого пакета произошел сбой, так как устройства относятся к разным VLAN.

![ICMP](image/16.png){#fig:0016 width=70%}

# Выводы

В ходе выполнения лабораторной работы я получила основные навыки по настройке VLAN на коммутаторах сети.


## Контрольные вопросы

1. Какая команда используется для просмотра списка VLAN на сетевом устройстве?

```
show vlan
```

2. Охарактеризуйте VLAN Trunking Protocol (VTP). Приведите перечень команд с пояснениями для настройки и просмотра информации о VLAN.

VLAN Trunking Protocol (VTP) - протокол для обмена информацией о VLAN между коммутаторами. Команды: 
   - vtp mode server/client/transparent - установить режим VTP
   - vtp domain <domain_name> - задать домен VTP
   - show vtp status - просмотр информации о статусе VTP

3. Охарактеризуйте Internet Control Message Protocol (ICMP). Опишите формат пакета ICMP.

ICMP - протокол управляющих сообщений Интернета. Формат: Заголовок ICMP (тип сообщения, код, контрольная сумма) + Данные.

4. Охарактеризуйте Address Resolution Protocol (ARP). Опишите формат пакета ARP.

ARP - протокол разрешения адресов. Формат: ARP-запрос (отправитель MAC, отправитель IP, получатель IP) + ARP-ответ (MAC отправителя, IP отправителя).

5. Что такое MAC-адрес? Какова его структура?

MAC-адрес - адрес устройства в сети. Структура: 6 октетов в шестнадцатеричной системе, разделенные двоеточиями (например, 00:1A:2B:3C:4D:5E).

# Список литературы{.unnumbered}

::: {#refs}
:::
