# Chapter 05 — Commands

# Current Processes

نمایش Processهای جاری Shell

```bash
ps
```

---

نمایش تمام Processهای سیستم

```bash
ps -e
```

---

نمایش کامل اطلاعات Processها

```bash
ps -ef
```

---

نمایش به سبک BSD

```bash
ps aux
```

---

نمایش Processهای یک کاربر

```bash
ps -u mehdi
```

---

نمایش Processها به صورت درختی

```bash
ps -ejH
```

---

# Interactive Process Monitoring

نمایش زنده Processها

```bash
top
```

---

نمایش پیشرفته Processها

```bash
htop
```

در صورت نصب نبودن:

```bash
sudo apt install htop
```

---

# Find Processes

پیدا کردن PID یک برنامه

```bash
pidof sshd
```

---

جستجوی Process بر اساس نام

```bash
pgrep ssh
```

---

جستجو همراه نمایش اطلاعات

```bash
pgrep -a ssh
```

---

نمایش Processهای مرتبط

```bash
ps aux | grep ssh
```

---

# Kill Processes

اتمام معمولی Process

```bash
kill PID
```

---

ارسال SIGTERM

```bash
kill -15 PID
```

---

اتمام اجباری

```bash
kill -9 PID
```

---

اتمام همه Processهای یک برنامه

```bash
killall firefox
```

---

اتمام بر اساس نام

```bash
pkill firefox
```

---

# Signals

نمایش لیست Signalها

```bash
kill -l
```

---

ارسال SIGSTOP

```bash
kill -STOP PID
```

---

ادامه اجرای Process

```bash
kill -CONT PID
```

---

# Jobs

اجرای برنامه در Background

```bash
sleep 300 &
```

---

نمایش Jobها

```bash
jobs
```

---

انتقال Job به Foreground

```bash
fg
```

---

انتقال Job مشخص

```bash
fg %1
```

---

ارسال Job به Background

```bash
bg
```

---

ارسال Job مشخص

```bash
bg %1
```

---

توقف Process با صفحه‌کلید

```text
Ctrl + Z
```

---

اتمام Process با صفحه‌کلید

```text
Ctrl + C
```

---

# Nice Priority

اجرای برنامه با Priority کمتر

```bash
nice -n 10 command
```

---

اجرای برنامه با Priority بیشتر (Root)

```bash
sudo nice -n -10 command
```

---

نمایش Nice Value

```bash
ps -o pid,ni,comm
```

---

تغییر Nice Process

```bash
sudo renice 10 PID
```

---

افزایش Priority

```bash
sudo renice -5 PID
```

---

# CPU & Memory Usage

مرتب‌سازی بر اساس CPU

```bash
ps aux --sort=-%cpu
```

---

۱۰ Process پرمصرف CPU

```bash
ps aux --sort=-%cpu | head
```

---

مرتب‌سازی بر اساس RAM

```bash
ps aux --sort=-%mem
```

---

۱۰ Process پرمصرف RAM

```bash
ps aux --sort=-%mem | head
```

---

# Process Tree

نمایش درخت Processها

```bash
pstree
```

---

نمایش همراه PID

```bash
pstree -p
```

---

در صورت نصب نبودن:

```bash
sudo apt install psmisc
```

---

# Background Daemons

نمایش Daemonهای Systemd

```bash
systemctl list-units --type=service
```

---

نمایش سرویس فعال

```bash
systemctl status ssh
```

---

# Process Files

نمایش اطلاعات Process

```bash
cat /proc/PID/status
```

---

نمایش مسیر فایل اجرایی

```bash
readlink /proc/PID/exe
```

---

نمایش Directory کاری Process

```bash
readlink /proc/PID/cwd
```

---

# Uptime & Load

نمایش مدت روشن بودن سیستم

```bash
uptime
```

---

نمایش Load Average

```bash
cat /proc/loadavg
```

---

# System Information

نمایش حافظه

```bash
free -h
```

---

نمایش CPU

```bash
lscpu
```

---

نمایش اطلاعات Kernel

```bash
uname -a
```

---

# Help

راهنمای ps

```bash
man ps
```

---

راهنمای top

```bash
man top
```

---

راهنمای htop

```bash
man htop
```

---

راهنمای kill

```bash
man kill
```

---

راهنمای nice

```bash
man nice
```

---

راهنمای renice

```bash
man renice
```

---

راهنمای jobs

```bash
help jobs
```

---

راهنمای fg

```bash
help fg
```

---

راهنمای bg

```bash
help bg
```

---

# Best Practice

قبل از Kill کردن یک Process ابتدا اطلاعات آن را بررسی کنید:

```bash
ps -fp PID
```

---

ابتدا از خاتمه عادی استفاده کنید:

```bash
kill PID
```

و فقط در صورت پاسخ ندادن:

```bash
kill -9 PID
```

---

برای مانیتورینگ روزانه سیستم:

```bash
htop
```

---

برای پیدا کردن Processهای پرمصرف:

```bash
ps aux --sort=-%cpu | head
```

و

```bash
ps aux --sort=-%mem | head
```

---

هنگام اجرای برنامه‌های طولانی که نمی‌خواهید ترمینال را اشغال کنند، از اجرای Background (`&`) استفاده کنید. در فصل‌های آینده با ابزارهای حرفه‌ای‌تر مانند **screen** و **tmux** نیز آشنا خواهید شد.