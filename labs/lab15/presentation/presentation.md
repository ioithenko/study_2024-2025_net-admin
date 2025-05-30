---
## Front matter
lang: ru-RU
title: Лабораторная работа №15
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

Настроить динамическую маршрутизацию между территориями организации.

# Выполнение лабораторной работы

##

![Настройка маршрутизатора msk-donskaya-gw-1](image/1.png){#fig:001 width=70%}

##

![Настройка маршрутизатора msk-q42-gw-1](image/2.png){#fig:002 width=70%}

##

![Настройка маршрутизирующего коммутатора msk-hostel-gw-1](image/3.png){#fig:003 width=70%}

##

![Настройка маршрутизатора sch-sochi-gw-1](image/4.png){#fig:004 width=70%}

##

![Проверка состояния протокола OSPF на маршрутизаторе msk-q42-gw-1](image/5.png){#fig:005 width=70%}

##

![Проверка состояния протокола OSPF на маршрутизаторе msk-hostel-gw-1](image/6.png){#fig:006 width=70%}

##

![Проверка состояния протокола OSPF на маршрутизаторе sch-sochi-gw-1](image/7.png){#fig:007 width=70%}

##

![Настройка интерфейсов коммутатора provider-sw-1](image/8.png){#fig:08 width=70%}

##

![Настройка маршрутизатора msk-q42-gw-1](image/9.png){#fig:09 width=70%}

##

![Настройка коммутатора sch-sochi-sw-1](image/10.png){#fig:010 width=70%}

##

![Настройка маршрутизатора sch-sochi-gw-1](image/11.png){#fig:011 width=70%}

##

![Движение пакета ICMP при пересылке с администратора на ПК в Сочи в режиме симуляции](image/12.png){#fig:012 width=70%}

##

![Движение пакета ICMP при пересылке с администратора на ПК в Сочи в режиме симуляции после отключения vlan 6](image/14.png){#fig:013 width=70%}

##

![Движение пакета ICMP при пересылке с администратора на ПК в Сочи в режиме симуляции после подключения vlan 6](image/15.png){#fig:014 width=70%}

## Выводы

В ходе выполнения лабораторной работы я настроила динамическую маршрутизацию между территориями организации.
