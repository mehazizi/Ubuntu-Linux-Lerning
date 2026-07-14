# Chapter 08 - Lab Exercises

## Lab 1

وضعیت سرویس SSH را بررسی کن.

systemctl status ssh

موارد زیر را شناسایی کن:

- Active
    
- Loaded
    
- Main PID
    
- Memory
    

---

## Lab 2

سرویس Cron را Restart کن.

قبل و بعد از Restart:

systemctl status cron

PID را مقایسه کن.

---

## Lab 3

بررسی کن SSH در بوت اجرا می‌شود یا خیر.

systemctl is-enabled ssh

---

## Lab 4

آخرین 20 لاگ Cron را مشاهده کن.

journalctl -u cron -n 20

---

## Lab 5

لاگ زنده سیستم را مشاهده کن.

journalctl -f

و در یک ترمینال دیگر:

sudo systemctl restart cron

تغییرات را مشاهده کن.

---

## Lab 6

Target پیش‌فرض سیستم را بررسی کن.

systemctl get-default

---

## Lab 7

وابستگی‌های multi-user.target را مشاهده کن.

systemctl list-dependencies multi-user.target

---

## Lab 8

وابستگی‌های graphical.target را مشاهده کن.

systemctl list-dependencies graphical.target

وابستگی graphical.target به multi-user.target را پیدا کن.

---

## Lab 9

یک سرویس دلخواه را انتخاب کن و Workflow زیر را اجرا کن:

1. status
    
2. journalctl -u
    
3. is-active
    
4. is-enabled
    

و نتیجه را تحلیل کن.