# Chapter 05 — Complete Lab Exercises

# هدف آزمایش‌ها

در پایان این آزمایش‌ها باید بتوانید:

- Processهای سیستم را مشاهده و تحلیل کنید.
    
- PID و PPID را شناسایی کنید.
    
- Processها را متوقف، ادامه و خاتمه دهید.
    
- Processهای Foreground و Background را مدیریت کنید.
    
- با Job Control کار کنید.
    
- مصرف CPU و RAM را بررسی کنید.
    
- اولویت اجرای Processها را تغییر دهید.
    

---

# Lab 01 — مشاهده Processهای سیستم

هدف:

آشنایی با Processهای در حال اجرا.

دستورها:

```bash
ps
```

```bash
ps -e
```

```bash
ps -ef
```

```bash
ps aux
```

سؤالات:

1. تفاوت خروجی `ps` و `ps -ef` چیست؟
    
2. PID فرآیند Shell شما چیست؟
    

---

# Lab 02 — پیدا کردن یک Process

هدف:

جستجوی Process.

دستورها:

```bash
pgrep ssh
```

```bash
pgrep -a ssh
```

```bash
pidof sshd
```

```bash
ps aux | grep ssh
```

تمرین:

به تفاوت خروجی `pgrep` و `grep` دقت کنید.

---

# Lab 03 — مانیتورینگ سیستم

هدف:

کار با top.

دستور:

```bash
top
```

داخل top موارد زیر را امتحان کنید:

- `P` مرتب‌سازی بر اساس CPU
    
- `M` مرتب‌سازی بر اساس RAM
    
- `1` نمایش هسته‌های CPU
    
- `h` راهنما
    
- `q` خروج
    

سؤالات:

1. بیشترین مصرف CPU مربوط به کدام Process است؟
    
2. Load Average را پیدا کنید.
    

---

# Lab 04 — کار با htop

هدف:

آشنایی با htop.

اگر نصب نیست:

```bash
sudo apt install htop
```

سپس:

```bash
htop
```

تمرین:

- جستجو با `F3`
    
- مرتب‌سازی با `F6`
    
- مشاهده Tree با `F5`
    
- خروج با `F10`
    

---

# Lab 05 — اجرای Process در Background

هدف:

شناخت Background.

دستور:

```bash
sleep 300 &
```

اکنون:

```bash
jobs
```

```bash
ps | grep sleep
```

سؤال:

آیا ترمینال آزاد است؟

---

# Lab 06 — انتقال Job بین Foreground و Background

هدف:

کار با Job Control.

ابتدا:

```bash
sleep 300
```

سپس:

```
Ctrl + Z
```

اکنون:

```bash
jobs
```

سپس:

```bash
bg
```

اکنون:

```bash
jobs
```

دوباره:

```bash
fg
```

در پایان:

```
Ctrl + C
```

---

# Lab 07 — خاتمه دادن Process

هدف:

کار با kill.

ابتدا:

```bash
sleep 300 &
```

PID را پیدا کنید:

```bash
pgrep sleep
```

اکنون:

```bash
kill PID
```

بررسی:

```bash
jobs
```

اکنون دوباره اجرا کنید:

```bash
sleep 300 &
```

سپس:

```bash
kill -9 PID
```

سؤال:

تفاوت `kill` و `kill -9` چیست؟

---

# Lab 08 — توقف و ادامه Process

هدف:

شناخت Signalها.

ابتدا:

```bash
sleep 300 &
```

PID را پیدا کنید:

```bash
pgrep sleep
```

توقف:

```bash
kill -STOP PID
```

بررسی:

```bash
ps -o pid,stat,comm | grep sleep
```

ادامه:

```bash
kill -CONT PID
```

---

# Lab 09 — بررسی مصرف CPU

هدف:

تحلیل Processها.

دستور:

```bash
ps aux --sort=-%cpu | head
```

تمرین:

بالاترین مصرف‌کننده CPU را پیدا کنید.

---

# Lab 10 — بررسی مصرف RAM

هدف:

تحلیل حافظه.

دستور:

```bash
ps aux --sort=-%mem | head
```

تمرین:

بیشترین مصرف RAM را پیدا کنید.

---

# Lab 11 — مشاهده درخت Processها

هدف:

درک Parent و Child.

اگر لازم بود:

```bash
sudo apt install psmisc
```

سپس:

```bash
pstree
```

```bash
pstree -p
```

تمرین:

مسیر Bash خود را تا Process شماره 1 دنبال کنید.

---

# Lab 12 — بررسی Nice Value

هدف:

شناخت اولویت Processها.

دستور:

```bash
ps -o pid,ni,comm
```

اکنون:

```bash
nice -n 10 sleep 300 &
```

بررسی:

```bash
ps -o pid,ni,comm | grep sleep
```

سؤال:

Nice Value جدید چیست؟

---

# Lab 13 — تغییر Nice Value

هدف:

کار با renice.

ابتدا PID را پیدا کنید.

سپس:

```bash
sudo renice 5 PID
```

بررسی:

```bash
ps -o pid,ni,comm | grep sleep
```

---

# Lab 14 — بررسی اطلاعات Process

هدف:

آشنایی با `/proc`.

ابتدا PID فرآیند Bash را پیدا کنید:

```bash
echo $$
```

اکنون:

```bash
cat /proc/$$/status
```

سپس:

```bash
readlink /proc/$$/exe
```

```bash
readlink /proc/$$/cwd
```

تمرین:

توضیح دهید هر دستور چه اطلاعاتی نمایش می‌دهد.

---

# Lab 15 — بررسی وضعیت سیستم

هدف:

تحلیل وضعیت کلی سیستم.

دستورها:

```bash
uptime
```

```bash
free -h
```

```bash
lscpu
```

```bash
cat /proc/loadavg
```

سؤالات:

1. سیستم چند دقیقه یا چند ساعت روشن بوده است؟
    
2. چه مقدار RAM آزاد است؟
    
3. سیستم چند هسته CPU دارد؟
    

---

# Lab 16 — Mini Challenge

بدون استفاده از اینترنت:

1. یک Process با `sleep 600` اجرا کنید.
    
2. آن را به Background بفرستید.
    
3. PID آن را پیدا کنید.
    
4. Nice Value آن را مشاهده کنید.
    
5. Nice Value را تغییر دهید.
    
6. Process را متوقف کنید.
    
7. دوباره ادامه دهید.
    
8. آن را به Foreground بیاورید.
    
9. با `Ctrl+C` خاتمه دهید.
    
10. مطمئن شوید دیگر Processی از `sleep` باقی نمانده است.
    

---

# Lab 17 — Challenge واقعی مدیر سیستم

فقط با استفاده از:

- `man`
    
- `--help`
    

پاسخ این سؤال‌ها را پیدا کنید:

1. تفاوت `kill` و `killall` چیست؟
    
2. تفاوت `kill` و `pkill` چیست؟
    
3. چگونه تمام Processهای یک User را مشاهده کنیم؟
    
4. چگونه فقط PID یک Process را پیدا کنیم؟
    
5. چگونه Processها را بر اساس مصرف RAM مرتب کنیم؟
    
6. تفاوت `top` و `htop` چیست؟
    
7. تفاوت Job Number و PID چیست؟
    

---

# پایان Chapter 05

پس از پایان این فصل باید بتوانید:

✅ مفهوم Process و Program را توضیح دهید.

✅ PID، PPID و Process Tree را درک کنید.

✅ با `ps`، `top` و `htop` Processها را تحلیل کنید.

✅ Processها را با Signalهای مناسب مدیریت کنید.

✅ Jobهای Foreground و Background را کنترل کنید.

✅ مصرف CPU و RAM را بررسی کنید.

✅ اولویت اجرای Processها را با `nice` و `renice` مدیریت کنید.

✅ از ساختار `/proc` برای مشاهده اطلاعات Processها استفاده کنید.