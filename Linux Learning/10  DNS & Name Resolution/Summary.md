# Chapter 10 — DNS & Name Resolution

## DNS چیست؟

DNS مخفف Domain Name System است.

وظیفه DNS تبدیل نام‌ها به IP Address است.

مثال:

google.com

↓

142.x.x.x

---

## چرا DNS وجود دارد؟

انسان‌ها نام‌ها را بهتر از IPها به خاطر می‌سپارند.

مثال:

google.com

به جای:

142.250.x.x

---

## DNS Resolution

هنگام اجرای:

ping google.com

سیستم ابتدا باید نام را به IP تبدیل کند.

---

## resolv.conf

فایل سنتی تنظیم DNS در لینوکس:

/etc/resolv.conf

در سیستم‌های مدرن معمولاً توسط systemd-resolved ساخته می‌شود.

نباید مستقیماً ویرایش شود.

---

## systemd-resolved

Resolver داخلی لینوکس‌های مدرن.

روی:

127.0.0.53

گوش می‌دهد.

برنامه‌ها درخواست DNS را به آن ارسال می‌کنند.

---

## DNS Server واقعی

در سیستم آزمایشگاهی:

192.168.67.2

DNS Server واقعی است که توسط DHCP دریافت شده است.

---

## resolvectl

برای مشاهده وضعیت Resolver استفاده می‌شود.

نمایش می‌دهد:

- DNS Server فعلی
    
- Domain ها
    
- وضعیت Resolver
    

---

## Search Domain

مثال:

search localdomain

اگر نام ناقص وارد شود:

ping server1

سیستم تلاش می‌کند:

server1.localdomain

را Resolve کند.

---

## Hosts File

فایل:

/etc/hosts

قبل از DNS بررسی می‌شود.

مثال:

192.168.67.50 mail.lab.local

---

## NSS

NSS مخفف:

Name Service Switch

فایل تنظیمات:

/etc/nsswitch.conf

---

## Name Resolution Order

در سیستم فعلی:

hosts: files dns

یعنی:

1. /etc/hosts
    
2. DNS
    

---

## زنجیره کامل Name Resolution

Application

↓

nsswitch.conf

↓

files

(/etc/hosts)

↓

اگر پیدا نشد

↓

127.0.0.53

↓

systemd-resolved

↓

Configured DNS Server

↓

DNS Response

↓

Application

---

## DNS Troubleshooting

اگر:

ping 8.8.8.8

موفق باشد

و:

ping google.com

ناموفق باشد

احتمال زیاد مشکل در DNS است نه شبکه.