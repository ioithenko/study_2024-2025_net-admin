---
## Front matter
lang: ru-RU
title: Лабораторная работа №11
subtitle: Администрирование локальных сетей
author:
  - Ищенко Ирина
institute:
  - Российский университет дружбы народов, Москва, Россия


## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
---

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

  * Ищенко Ирина Олеговна
  * 1132226529
  * уч. группа: НПИбд-02-22
  * Факультет физико-математических и естественных наук

:::
::: {.column width="30%"}


:::
::::::::::::::

## Цель работы

Провести подготовительные мероприятия по подключению локальной сети организации к Интернету.

##

![Схема сети с NAT](image/NAT.png){#fig:001 width=70%}

##

![Схема L1 сети с выходом в Интернет](image/L1.png){#fig:002 width=70%}

##

![Схема L2 сети с выходом в Интернет](image/L2.png){#fig:003 width=70%}

##

![Схема L3 сети с выходом в Интернет](image/L3.png){#fig:004 width=70%}

##

![Размещение устройств](image/1.png){#fig:005 width=70%}

##

![Добавление зданий](image/2.png){#fig:006 width=70%}

##

![Замена модулей на медиаконвертерах](image/3.png){#fig:007 width=70%}

##

![Соединение объектов](image/4.png){#fig:008 width=70%}

## Распределение ip-адресов модельного Интернета

: Распределение ip-адресов модельного Интернета

| IP-адреса     | Примечание            |
|---------------|-----------------------|
| 192.0.2.1     | provider-gw-1         |
| 192.0.2.11    | www.yandex.ru         |
| 192.0.2.12    | stud.rudn.university  |
| 192.0.2.13    | esystem.pfur.ru       |
| 192.0.2.14    | www.rudn.ru           |

##

![Указание шлюза](image/5.png){#fig:009 width=70%}

##

![IP-адрес](image/6.png){#fig:0010 width=70%}

##

![Сведения о серверах](image/7.png){#fig:0011 width=70%}

## Выводы

В ходе выполнения лабораторной работы я провела подготовительные мероприятия по подключению локальной сети организации к Интернету.
