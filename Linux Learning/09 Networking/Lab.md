# Chapter 09 - Lab Exercises

## Lab 1

IP Address و Prefix سیستم را پیدا کن.

ip a

موارد زیر را شناسایی کن:

- Interface Name
    
- IPv4 Address
    
- Prefix
    
- Loopback Interface
    

---

## Lab 2

جدول Route سیستم را مشاهده کن.

ip route

موارد زیر را پیدا کن:

- Default Route
    
- Gateway
    
- Network Route
    

---

## Lab 3

ارتباط با اینترنت را بررسی کن.

ping -c 4 8.8.8.8

میانگین RTT را یادداشت کن.

---

## Lab 4

بررسی DNS Resolution

ابتدا:

ping -c 4 8.8.8.8

سپس:

ping -c 4 google.com

تفاوت نتایج را تحلیل کن.

---

## Lab 5

Loopback Interface را تست کن.

ping -c 4 127.0.0.1

موارد زیر را بررسی کن:

- RTT Average
    
- Packet Loss
    

---

## Lab 6

مسیر رسیدن به Google DNS را بررسی کن.

traceroute 8.8.8.8

موارد زیر را شناسایی کن:

- First Hop
    
- Gateway Address
    
- تعداد Hop های قابل مشاهده
    

---

## Lab 7

Socket ها و Port های باز را مشاهده کن.

ss -tuln

موارد زیر را پیدا کن:

- Port 22
    
- Port 53
    
- Port 68
    

---

## Lab 8

Process مربوط به Port ها را پیدا کن.

sudo ss -tulpn

موارد زیر را شناسایی کن:

- SSH Process
    
- DNS Process
    
- DHCP Process
    

---

## Lab 9

مفهوم Listen Address را بررسی کن.

در خروجی ss موارد زیر را پیدا کن:

- 0.0.0.0
    
- 127.0.0.1
    
- [::]
    

معنی هرکدام را توضیح بده.

---

## Lab 10

کاربرد Port های زیر را بنویس:

- 22
    
- 53
    
- 68
    
- 80
    
- 443
    

و سرویس مربوط به هر Port را مشخص کن.