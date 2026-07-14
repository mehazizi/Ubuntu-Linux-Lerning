# Chapter 10 - Commands

## مشاهده فایل DNS

cat /etc/resolv.conf

---

## مشاهده وضعیت Resolver

resolvectl status

---

## مشاهده DNS Server فعلی

resolvectl status

---

## مشاهده ترتیب Name Resolution

grep '^hosts:' /etc/nsswitch.conf

---

## مشاهده Hosts File

cat /etc/hosts

---

## تست DNS

ping google.com

---

## تست شبکه بدون DNS

ping 8.8.8.8

---

## مشاهده Socket مربوط به DNS

sudo ss -tulpn

---

## مشاهده سرویس Resolver

systemctl status systemd-resolved

---

## مشاهده لاگ Resolver

journalctl -u systemd-resolved