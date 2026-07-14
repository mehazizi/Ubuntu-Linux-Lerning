# Chapter 05 — Process & Job Management

# Summary

# هدف این Chapter

در پایان این فصل باید بتوانید:

- مفهوم Process را در Linux درک کنید.
    
- تفاوت Program و Process را بدانید.
    
- Processهای در حال اجرا را مشاهده کنید.
    
- Processها را مدیریت و خاتمه دهید.
    
- اولویت اجرای Processها را تغییر دهید.
    
- مفهوم Foreground و Background را درک کنید.
    
- Jobها را مدیریت کنید.
    
- مصرف CPU و RAM را تحلیل کنید.
    

---

# Process چیست؟

هر برنامه‌ای که در حال اجرا باشد، یک **Process** است.

به عبارت دیگر:

**Program + Execution = Process**

مثال:

فایل برنامه:

```text
/bin/ls
```

وقتی اجرا شود:

```bash
ls
```

یک Process ایجاد می‌شود.

---

# تفاوت Program و Process

Program

فایلی است که روی Disk قرار دارد.

Process

نسخه در حال اجرای همان Program در RAM است.

مثال:

Firefox یک Program است.

اگر سه پنجره Firefox باز کنید:

سه Process جداگانه خواهید داشت.

---

# هر Process چه اطلاعاتی دارد؟

هر Process دارای اطلاعاتی مانند:

- PID
    
- PPID
    
- Owner
    
- CPU Usage
    
- Memory Usage
    
- Start Time
    
- Status
    
- Priority
    

است.

---

# PID چیست؟

PID

(Process ID)

شناسه یکتای هر Process است.

نمونه:

```text
PID = 2538
```

هیچ دو Process فعالی PID یکسان ندارند.

---

# PPID چیست؟

Parent Process ID

هر Process توسط یک Process دیگر ایجاد می‌شود.

آن Process را Parent می‌نامند.

---

# Init / systemd

اولین Process سیستم همیشه:

```text
PID = 1
```

است.

در Ubuntu امروزی:

```text
systemd
```

می‌باشد.

تقریباً تمام Processهای سیستم به صورت مستقیم یا غیرمستقیم فرزند PID 1 هستند.

---

# مشاهده Processها

Linux ابزارهای متعددی برای مشاهده Processها دارد.

مهم‌ترین آنها:

- ps
    
- top
    
- htop
    

---

# ps

نمایش Snapshot از Processها.

یعنی وضعیت لحظه‌ای سیستم را نشان می‌دهد.

---

# top

نمایش زنده Processها.

اطلاعات دائماً به‌روزرسانی می‌شوند.

---

# htop

نسخه پیشرفته‌تر top.

ویژگی‌ها:

- رابط کاربری بهتر
    
- رنگی
    
- جستجو
    
- مرتب‌سازی
    
- انتخاب Process با صفحه‌کلید
    

---

# وضعیت Processها

نمونه Statusها:

```text
R
```

Running

---

```text
S
```

Sleeping

---

```text
D
```

Uninterruptible Sleep

---

```text
T
```

Stopped

---

```text
Z
```

Zombie

---

# Zombie Process

گاهی Process اصلی (Child) تمام می‌شود اما Parent هنوز وضعیت آن را دریافت نکرده است.

در این حالت Process به Zombie تبدیل می‌شود.

Zombieها معمولاً RAM بسیار کمی مصرف می‌کنند اما زیاد شدن آنها نشانه وجود مشکل در برنامه است.

---

# Foreground Process

وقتی برنامه را اجرا می‌کنیم:

```bash
nano file.txt
```

ترمینال تا پایان برنامه در اختیار آن Process قرار می‌گیرد.

به این حالت:

Foreground

گفته می‌شود.

---

# Background Process

گاهی می‌خواهیم برنامه اجرا شود اما ترمینال آزاد بماند.

به این حالت:

Background

می‌گویند.

---

# Job چیست؟

Job همان Processی است که توسط Shell مدیریت می‌شود.

Shell برای هر Job شماره اختصاصی می‌دهد.

مثال:

```text
[1]

[2]

[3]
```

---

# Signal چیست؟

Linux برای ارتباط با Processها از Signal استفاده می‌کند.

مشهورترین آنها:

SIGTERM

SIGKILL

SIGSTOP

SIGCONT

---

# SIGTERM

درخواست خاتمه محترمانه.

برنامه فرصت دارد:

- فایل‌ها را ذخیره کند.
    
- منابع را آزاد کند.
    
- سپس خارج شود.
    

---

# SIGKILL

خاتمه اجباری.

Kernel فوراً Process را متوقف می‌کند.

هیچ فرصتی برای Cleanup وجود ندارد.

---

# اولویت Process

Linux Scheduler تصمیم می‌گیرد CPU را به کدام Process بدهد.

هر Process دارای Priority است.

---

# Nice Value

محدوده:

```text
-20

تا

19
```

عدد کمتر

اولویت بیشتر

عدد بیشتر

اولویت کمتر

---

# مصرف CPU

هر Process بخشی از CPU را مصرف می‌کند.

Processهای سنگین:

Rendering

Compilation

Compression

Virtual Machine

ممکن است درصد بالایی از CPU را اشغال کنند.

---

# مصرف RAM

هر Process بخشی از حافظه را مصرف می‌کند.

RAM آزاد بیشتر معمولاً به معنی عملکرد بهتر سیستم نیست.

Linux از RAM آزاد برای Cache نیز استفاده می‌کند.

---

# Process Tree

تمام Processها به صورت درختی به هم متصل هستند.

نمونه:

```text
systemd
 ├── sshd
 │     └── bash
 │            └── top
 ├── NetworkManager
 └── cron
```

---

# Daemon چیست؟

Daemon

برنامه‌ای است که در Background اجرا می‌شود.

نمونه‌ها:

- sshd
    
- cron
    
- nginx
    
- docker
    
- systemd-journald
    

---

# Best Practices

- قبل از Kill کردن Process ابتدا دلیل مشکل را بررسی کنید.
    
- ابتدا از SIGTERM استفاده کنید؛ فقط در صورت نیاز از SIGKILL استفاده کنید.
    
- Processهای ناشناس با مصرف CPU یا RAM بالا را بررسی کنید.
    
- برای مانیتورینگ روزانه، **htop** یکی از بهترین ابزارها است.
    
- هنگام اجرای برنامه‌های طولانی، از Background یا ابزارهایی مانند `screen` و `tmux` (در فصل‌های بعد) استفاده کنید.
    

---

# Common Mistakes

- استفاده مستقیم از `kill -9` بدون تلاش برای خاتمه عادی.
    
- اشتباه گرفتن PID با Job Number.
    
- تصور اینکه بستن ترمینال همیشه باعث پایان تمام Processها می‌شود.
    
- تغییر بی‌دلیل Nice Value Processهای سیستمی.
    
- حذف Processهای حیاتی مانند `systemd` یا `sshd` بدون شناخت کافی.
    

---

# Production Tips

- اولین قدم در عیب‌یابی کندی سیستم معمولاً بررسی مصرف CPU، RAM و Processها با `top` یا `htop` است.
    
- Processهایی با وضعیت **D** که برای مدت طولانی باقی بمانند، ممکن است نشان‌دهنده مشکل در دیسک یا I/O باشند.
    
- وجود تعداد زیاد Zombie Process معمولاً نشانه وجود باگ در یک برنامه یا اسکریپت است، نه کمبود منابع سیستم.
    
- همیشه قبل از Kill کردن یک Process، بررسی کنید که آیا سرویس مهمی به آن وابسته نیست.