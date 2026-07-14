# Chapter 09 - Commands

## مشاهده IP Address ها

ip a

---

## مشاهده Routing Table

ip route

---

## تست ارتباط با IP

ping 8.8.8.8

---

## تست DNS Resolution

ping google.com

---

## تست Loopback

ping -c 4 127.0.0.1

---

## مشاهده مسیر عبور بسته ها

traceroute 8.8.8.8

---

## مشاهده Socket ها و Port های باز

ss -tuln

---

## مشاهده Process مربوط به Port ها

sudo ss -tulpn

---

## مشاهده لاگ SSH

journalctl -u ssh

---

## مشاهده لاگ زنده سیستم

journalctl -f