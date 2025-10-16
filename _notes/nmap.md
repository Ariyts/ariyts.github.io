---
layout: default
title: Nmap
---

# Nmap Заметки

## Навигация

[← Назад на главную](/)
- [Список хостов (-sL)](#список-хостов--sl)
- [ARP-сканирование (-PR)](#arp-сканирование--pr)
- [ICMP Echo (-PE)](#icmp-echo--pe)
- [ICMP Timestamp и Address Mask (-PP, -PM)](#icmp-timestamp-и-address-mask--pp--pm)
- [TCP SYN Ping (-PS)](#tcp-syn-ping--ps)
- [TCP ACK Ping (-PA)](#tcp-ack-ping--pa)
- [UDP Ping (-PU)](#udp-ping--pu)
- [DNS-запросы (-R, -n, --dns-servers)](#dns-запросы--r--n---dns-servers)

---

## Список хостов (-sL)
Если вы хотите проверить список хостов, которые Nmap будет сканировать, используйте:

```bash
nmap -sL -n 10.10.12.13/29
```
Опция -sL предоставит подробный список хостов, которые Nmap будет сканировать, не сканируя их. Однако Nmap попытается выполнить обратное разрешение DNS для всех целей, чтобы получить их имена. Если вы не хотите, чтобы Nmap отправлял DNS-запросы, добавьте -n.


ARP-сканирование (-PR)

Чтобы выполнить только ARP-сканирование без сканирования портов:

```bash
nmap -PR -sn TARGETS
```
Опция -PR указывает, что нужно только ARP-сканирование.

ICMP Echo (-PE)

Чтобы использовать эхо-запрос ICMP для обнаружения активных хостов:.

```bash
nmap -PE -sn TARGETS
```

ICMP Timestamp и Address Mask (-PP, -PM)
Пример использования:
```bash
nmap -PP -sn MACHINE_IP/24
nmap -PM -sn MACHINE_IP/24
```

    -PP — ICMP Timestamp (Type 13/14).

    -PM — ICMP Address Mask (Type 17/18).

Если один тип пакета блокируется, можно использовать другой.

TCP SYN Ping (-PS)

Использование TCP SYN ping:
```bash
nmap -PS21 -sn MACHINE_IP/24
nmap -PS21-25 -sn MACHINE_IP/24
nmap -PS80,443,8080 -sn MACHINE_IP/24
```

Привилегированные пользователи могут отправлять SYN без завершения рукопожатия.

Непривилегированные обязаны завершать TCP‑handshake.

TCP ACK Ping (-PA)

Обнаружение онлайн-хостов в подсети:

```bash
nmap -PA -sn MACHINE_IP/24
```
-PA сопровождается портом или диапазоном (например, -PA21, -PA21-25, -PA80,443,8080).

Если порт не указан, используется 80.

UDP Ping (-PU)

Чтобы проверить хосты через UDP:

```bash
nmap -PU -sn 10.10.68.220/24
```

DNS-запросы (-R, -n, --dns-servers)

    По умолчанию Nmap делает обратные DNS-запросы.

    Чтобы отключить — используйте -n.

    Чтобы принудительно запросить DNS даже для офлайн-хостов — -R.

    Чтобы указать конкретный DNS-сервер:

    ```bash
nmap --dns-servers DNS_SERVER TARGETS
```

---