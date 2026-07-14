# Chapter 01 — Commands

# Basic System Information

نمایش اطلاعات کرنل

```bash
uname
```

---

نمایش اطلاعات کامل Kernel

```bash
uname -a
```

---

نمایش نام Host

```bash
hostname
```

---

نمایش نسخه سیستم‌عامل

```bash
cat /etc/os-release
```

---

نمایش نسخه Ubuntu

```bash
lsb_release -a
```

---

نمایش معماری سیستم

```bash
uname -m
```

---

نمایش نسخه Kernel

```bash
uname -r
```

---

# Current User

نمایش نام کاربر فعلی

```bash
whoami
```

---

نمایش شناسه کاربر

```bash
id
```

---

نمایش کاربران لاگین کرده

```bash
who
```

---

نمایش اطلاعات کاربران

```bash
w
```

---

# Date & Time

نمایش تاریخ و ساعت

```bash
date
```

---

نمایش زمان روشن بودن سیستم

```bash
uptime
```

---

# System Information

نمایش اطلاعات CPU

```bash
lscpu
```

---

نمایش اطلاعات RAM

```bash
free -h
```

---

نمایش اطلاعات Block Deviceها

```bash
lsblk
```

---

نمایش فضای دیسک

```bash
df -h
```

---

نمایش اطلاعات فایل سیستم

```bash
mount
```

---

# Help System

نمایش Help یک دستور

```bash
command --help
```

مثال:

```bash
ls --help
```

---

نمایش Manual

```bash
man command
```

مثال:

```bash
man ls
```

---

جستجو در Manualها

```bash
apropos keyword
```

مثال:

```bash
apropos network
```

---

# Command Location

پیدا کردن محل اجرای برنامه

```bash
which command
```

مثال:

```bash
which bash
```

---

نمایش تمام مسیرهای اجرای برنامه

```bash
type -a command
```

مثال:

```bash
type -a ls
```

---

# Shell

نمایش Shell فعلی

```bash
echo $SHELL
```

---

نمایش نام Shell

```bash
echo $0
```

---

# Environment

نمایش متغیرهای محیطی

```bash
env
```

---

نمایش مقدار یک متغیر

```bash
echo $HOME
```

---

نمایش مسیر PATH

```bash
echo $PATH
```

---

# Clear Terminal

پاک کردن صفحه Terminal

```bash
clear
```

یا

```bash
Ctrl + L
```

---

# Exit

خروج از Shell

```bash
exit
```

یا

```bash
Ctrl + D
```

---

# Shutdown & Reboot

خاموش کردن سیستم

```bash
sudo shutdown now
```

---

راه‌اندازی مجدد

```bash
sudo reboot
```

---

خاموش کردن فوری

```bash
sudo poweroff
```

---

# Best Practice

برای هر دستور جدید این سه مرحله را انجام بده:

```bash
command --help
```

↓

```bash
man command
```

↓

اجرا روی محیط آزمایش

---

این عادت باعث می‌شود وابستگی شما به اینترنت به مرور بسیار کمتر شود.