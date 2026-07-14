# Chapter 02 — Linux Filesystem

# Summary

# هدف این Chapter

در پایان این فصل باید بتوانید:

- ساختار Linux Filesystem را درک کنید.
    
- تفاوت Linux و Windows در مدیریت فایل‌ها را بدانید.
    
- مفهوم Mount را متوجه شوید.
    
- وظیفه هر Directory مهم را بدانید.
    
- مسیر مناسب ذخیره فایل‌های مختلف را تشخیص دهید.
    
- علت وجود فقط یک Root Directory را توضیح دهید.
    

---

# Linux Filesystem چیست؟

در Linux تمام اطلاعات به صورت یک ساختار درختی (Tree Structure) سازمان‌دهی می‌شوند.

برخلاف Windows، هیچ درایوی مانند C: یا D: وجود ندارد.

همه چیز از یک نقطه شروع می‌شود.

آن نقطه:

```
/
```

نام دارد.

به آن Root Directory گفته می‌شود.

---

# Root Directory (/)

Root بالاترین نقطه Filesystem است.

تمام Directoryها و فایل‌ها در نهایت زیر Root قرار می‌گیرند.

مثال:

```
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

---

# همه چیز فایل است

یکی از مهم‌ترین فلسفه‌های Linux:

**Everything is a file**

تقریباً همه چیز می‌تواند به صورت فایل دیده شود.

مانند:

- فایل‌های معمولی
    
- Directoryها
    
- Hard Diskها
    
- USB
    
- Network Socket
    
- Printer
    
- Keyboard
    
- Mouse
    
- Pipe
    
- Deviceها
    

به همین دلیل ابزارهای Linux تقریباً روی همه چیز قابل استفاده هستند.

---

# تفاوت Linux و Windows

Windows

```
C:
D:
E:
```

هر Disk یک Drive جداگانه است.

---

Linux

```
/
```

همه Diskها در یک ساختار واحد قرار می‌گیرند.

---

# Mount چیست؟

برای استفاده از یک Storage باید آن را به Filesystem متصل کنیم.

به این عمل:

Mount

گفته می‌شود.

مثلاً یک USB می‌تواند در مسیر زیر Mount شود:

```
/media/mehdi/KINGSTON
```

یا یک هارد جدید:

```
/backup
```

کاربر هیچ تفاوتی احساس نمی‌کند.

فقط وارد مسیر می‌شود.

---

# Directoryهای مهم Linux

## /

ریشه Filesystem

---

## /bin

برنامه‌های ضروری کاربران

نمونه:

- ls
    
- cp
    
- mv
    
- rm
    
- cat
    

---

## /sbin

برنامه‌های مدیریتی سیستم

نمونه:

- reboot
    
- shutdown
    
- fsck
    

---

## /boot

فایل‌های Boot

- Kernel
    
- GRUB
    
- initramfs
    

---

## /dev

Device Fileها

نمونه:

```
/dev/sda

/dev/sdb

/dev/null

/dev/zero
```

---

## /etc

مهم‌ترین پوشه تنظیمات سیستم.

تقریباً تمام فایل‌های Configuration اینجا قرار دارند.

نمونه:

```
/etc/hosts

/etc/fstab

/etc/passwd

/etc/shadow

/etc/netplan

/etc/systemd
```

یک مدیر سیستم تقریباً هر روز با این پوشه کار می‌کند.

---

## /home

اطلاعات کاربران عادی

مثال:

```
/home/mehdi
```

---

## /root

Home مربوط به کاربر Root

تفاوت:

```
/root
```

با

```
/
```

بسیار مهم است.

---

## /lib

کتابخانه‌های اشتراکی

Shared Libraries

تقریباً معادل DLL در Windows.

---

## /media

محل Mount خودکار

مانند:

USB

DVD

External HDD

---

## /mnt

محل Mount دستی

معمولاً مدیر سیستم Storageها را اینجا Mount می‌کند.

---

## /opt

نرم‌افزارهای جانبی

مانند:

- VMware Tools
    
- بعضی نرم‌افزارهای اختصاصی
    

---

## /proc

Filesystem مجازی

اطلاعات Kernel و Processها

هیچ فایل واقعی داخل آن وجود ندارد.

همه چیز توسط Kernel تولید می‌شود.

---

## /run

اطلاعات موقت سرویس‌ها

پس از Restart پاک می‌شود.

---

## /srv

اطلاعات سرویس‌ها

مثلاً:

FTP

HTTP

---

## /sys

Filesystem مجازی مربوط به Kernel

برای مدیریت سخت‌افزار استفاده می‌شود.

---

## /tmp

فایل‌های موقت

هر برنامه‌ای می‌تواند از آن استفاده کند.

ممکن است هنگام Boot پاک شود.

نباید فایل مهم داخل آن نگهداری شود.

---

## /usr

بزرگ‌ترین Directory سیستم

شامل:

- برنامه‌ها
    
- Libraryها
    
- Documentation
    
- Manualها
    

بیشتر نرم‌افزارهای نصب شده اینجا قرار می‌گیرند.

---

## /var

اطلاعاتی که دائماً تغییر می‌کنند.

نمونه:

- Logها
    
- Cache
    
- Mail Queue
    
- Database
    
- Web Cache
    

---

# Absolute Path

مسیری که از Root شروع می‌شود.

مثال:

```
/etc/hosts
```

```
/home/mehdi/file.txt
```

همیشه با

```
/
```

شروع می‌شود.

---

# Relative Path

مسیری که نسبت به مکان فعلی نوشته می‌شود.

مثال:

```
Documents/file.txt
```

یا

```
../backup
```

---

# Current Working Directory

دایرکتوری فعلی که داخل آن قرار داریم.

در آینده با دستور pwd آن را مشاهده خواهیم کرد.

---

# Hidden Files

فایل‌هایی که با نقطه شروع می‌شوند.

مثال:

```
.bashrc

.profile

.gitconfig
```

به صورت پیش‌فرض نمایش داده نمی‌شوند.

---

# Best Practices

- فایل‌های سیستمی را فقط در مسیر مناسب نگهداری کنید.
    
- هیچ‌گاه فایل شخصی داخل /etc قرار ندهید.
    
- اطلاعات کاربران داخل /home نگهداری شود.
    
- Backupها را داخل /backup یا /mnt/backup قرار دهید.
    
- فایل‌های موقت را داخل /tmp ذخیره کنید.
    
- تفاوت / و /root را همیشه به خاطر داشته باشید.
    

---

# Common Mistakes

- اشتباه گرفتن `/` با `/root`
    
- ذخیره فایل شخصی داخل `/etc`
    
- تصور اینکه `/dev` فایل واقعی نگهداری می‌کند.
    
- تصور اینکه `/proc` روی هارد ذخیره شده است.
    
- استفاده از `/tmp` برای نگهداری فایل‌های مهم.
    
- تصور اینکه Linux نیز مانند Windows دارای Drive Letter است.
    

---

# Production Tips

- قبل از تغییر فایل‌های داخل `/etc` همیشه Backup تهیه کنید.
    
- Logها معمولاً داخل `/var/log` قرار دارند؛ هنگام عیب‌یابی اولین جایی است که باید بررسی شود.
    
- برای Mount دستی دیسک‌های جدید معمولاً از `/mnt` یا مسیرهای اختصاصی مانند `/backup` استفاده کنید.
    
- شناخت صحیح ساختار Filesystem سرعت عیب‌یابی و مدیریت سرور را به‌طور چشمگیری افزایش می‌دهد.