# Chapter 09 — Networking Basics

## IP Address

- هر دستگاه در شبکه یک IP Address دارد.
    
- IP مانند آدرس پستی برای ارسال و دریافت بسته‌ها عمل می‌کند.
    

## Prefix / CIDR

- مشخص می‌کند چه بخشی از IP مربوط به شبکه و چه بخشی مربوط به Host است.
    
- مثال:
    

192.168.67.139/24

- معادل Subnet Mask زیر است:
    

255.255.255.0

## Gateway

- مسیر خروج از شبکه محلی است.
    
- اگر مقصد در شبکه محلی نباشد، بسته به Gateway ارسال می‌شود.
    

## Routing Table

- جدول تصمیم‌گیری مسیرها است.
    
- با دستور ip route نمایش داده می‌شود.
    
- قانون اصلی:
    

Longest Prefix Match Wins

## ARP

- وظیفه تبدیل IP به MAC را بر عهده دارد.
    
- اگر مقصد داخل شبکه محلی باشد، ARP روی مقصد انجام می‌شود.
    
- اگر مقصد خارج از شبکه باشد، ARP روی Gateway انجام می‌شود.
    

## Loopback

- آدرس 127.0.0.1 به خود سیستم اشاره می‌کند.
    
- Interface مربوطه lo نام دارد.
    
- Loopback یک DNS Server نیست؛ فقط یک Interface داخلی است.
    

## ICMP

- مخفف Internet Control Message Protocol
    
- برای پیام‌های کنترلی و عیب‌یابی شبکه استفاده می‌شود.
    

## Ping

- از ICMP Echo Request و Echo Reply استفاده می‌کند.
    
- برای تست ارتباط شبکه کاربرد دارد.
    

## RTT

- Round Trip Time
    
- زمان رفت و برگشت بسته بین مبدأ و مقصد.
    

## TTL

- مخفف Time To Live
    
- در هر Router یک واحد کم می‌شود.
    
- برای جلوگیری از Routing Loop استفاده می‌شود.
    

## Traceroute

- مسیر عبور بسته‌ها تا مقصد را نمایش می‌دهد.
    
- با تغییر TTL مسیر Routerها را کشف می‌کند.
    

## Listening Ports

- سرویس‌های شبکه روی Portهای مشخص Listen می‌کنند.
    

## ss

- ابزار مدرن مشاهده Socketها و Portهای باز در لینوکس.
    

## Well-Known Ports

- 22 = SSH
    
- 53 = DNS
    
- 68 = DHCP Client
    
- 80 = HTTP
    
- 443 = HTTPS
    

## Listen Addresses

### 0.0.0.0

تمام Interface های IPv4

### [::]

تمام Interface های IPv6

### 127.0.0.1

فقط خود سیستم