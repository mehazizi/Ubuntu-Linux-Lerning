# Chapter 10 - Lab Exercises

## Lab 1

فایل DNS سیستم را بررسی کن.

cat /etc/resolv.conf

موارد زیر را پیدا کن:

- nameserver
    
- search
    
- options
    

---

## Lab 2

وضعیت Resolver را بررسی کن.

resolvectl status

موارد زیر را شناسایی کن:

- Current DNS Server
    
- DNS Servers
    
- DNS Domain
    

---

## Lab 3

ترتیب Name Resolution را مشاهده کن.

grep '^hosts:' /etc/nsswitch.conf

توضیح بده:

files

و

dns

چه معنایی دارند.

---

## Lab 4

فایل Hosts را مشاهده کن.

cat /etc/hosts

تمام رکوردهای موجود را تحلیل کن.

---

## Lab 5

تست DNS Resolution.

ping google.com

توضیح بده قبل از ارسال Ping چه اتفاقی رخ می‌دهد.

---

## Lab 6

تست ارتباط بدون DNS.

ping 8.8.8.8

توضیح بده چرا DNS در این تست دخالتی ندارد.

---

## Lab 7

زنجیره کامل Name Resolution را روی کاغذ رسم کن.

از:

Application

تا:

DNS Server

---

## Lab 8

فرض کن در /etc/hosts این رکورد وجود دارد:

1.2.3.4 google.com

توضیح بده:

ping google.com

به چه IP ای خواهد رفت و چرا.

---

## Lab 9

سناریوی زیر را تحلیل کن:

ping 8.8.8.8

موفق

ping google.com

ناموفق

مراحل عیب‌یابی را به ترتیب بنویس.

---

## Lab 10

تفاوت وظایف این اجزا را توضیح بده:

- /etc/hosts
    
- /etc/resolv.conf
    
- systemd-resolved
    
- DNS Server
    
- /etc/nsswitch.conf