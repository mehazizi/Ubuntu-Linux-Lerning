# Chapter 06 — Complete Lab Exercises

# هدف آزمایش‌ها

در پایان این آزمایش‌ها باید بتوانید:

- Packageها را جستجو کنید.
    
- اطلاعات Packageها را بررسی کنید.
    
- Package نصب و حذف کنید.
    
- نصب را قبل از اجرا شبیه‌سازی کنید.
    
- Repositoryها را بررسی کنید.
    
- Cache مربوط به APT را مدیریت کنید.
    
- Packageهای نصب‌شده را بررسی کنید.
    
- فایل‌های محلی `.deb` را نصب کنید.
    

---

# Lab 01 — بررسی Repositoryها

هدف:

آشنایی با منابع دریافت Packageها.

دستورها:

```bash
cat /etc/apt/sources.list
```

سپس:

```bash
ls -l /etc/apt/sources.list.d/
```

سؤالات:

1. سیستم از چند Repository استفاده می‌کند؟
    
2. آیا Repository اضافی نصب شده است؟
    

---

# Lab 02 — بروزرسانی فهرست Packageها

هدف:

درک عملکرد `apt update`

دستور:

```bash
sudo apt update
```

تمرین:

بررسی کنید:

- چند Repository بررسی شد؟
    
- آیا Package جدیدی پیدا شد؟
    

---

# Lab 03 — جستجوی Package

هدف:

جستجو در Repositoryها.

دستورها:

```bash
apt search nginx
```

سپس:

```bash
apt search ^nginx
```

سؤال:

تفاوت دو خروجی چیست؟

---

# Lab 04 — مشاهده اطلاعات Package

هدف:

بررسی اطلاعات Package.

دستور:

```bash
apt show nmap
```

موارد زیر را پیدا کنید:

- Version
    
- Depends
    
- Download Size
    
- Repository
    
- Description
    

---

# Lab 05 — بررسی نسخه‌ها

هدف:

شناخت apt policy

دستور:

```bash
apt policy nmap
```

سؤالات:

1. Candidate Version چیست؟
    
2. Installed Version چیست؟
    
3. از کدام Repository نصب خواهد شد؟
    

---

# Lab 06 — شبیه‌سازی نصب

هدف:

کار با Dry Run.

دستور:

```bash
sudo apt install --dry-run nmap
```

تمرین:

مشخص کنید:

- چند Package نصب خواهد شد؟
    
- چه Dependencyهایی نیاز است؟
    

---

# Lab 07 — نصب واقعی Package

هدف:

نصب نرم‌افزار.

دستور:

```bash
sudo apt install nmap
```

بررسی:

```bash
which nmap
```

سپس:

```bash
nmap localhost
```

تمرین:

نتیجه Scan را بررسی کنید.

---

# Lab 08 — بررسی نصب بودن Package

هدف:

بررسی وضعیت نصب.

دستورها:

```bash
dpkg -l | grep nmap
```

سپس:

```bash
dpkg -s nmap
```

تمرین:

وضعیت Package را بررسی کنید.

---

# Lab 09 — بررسی فایل‌های Package

هدف:

شناخت فایل‌های نصب‌شده.

دستور:

```bash
dpkg -L nmap
```

تمرین:

مسیر فایل اجرایی را پیدا کنید.

---

# Lab 10 — بررسی مالک فایل اجرایی

هدف:

شناخت Package مربوط به یک فایل.

دستور:

```bash
dpkg -S /usr/bin/nmap
```

---

# Lab 11 — بررسی Cache

هدف:

آشنایی با Cache.

دستور:

```bash
ls -lh /var/cache/apt/archives/
```

تمرین:

بررسی کنید آیا فایل‌های دانلودشده وجود دارند یا خیر.

---

# Lab 12 — پاک کردن Cache

هدف:

کار با clean و autoclean.

ابتدا:

```bash
sudo apt autoclean
```

سپس:

```bash
sudo apt clean
```

اکنون دوباره بررسی کنید:

```bash
ls -lh /var/cache/apt/archives/
```

سؤال:

چه چیزی حذف شد؟

---

# Lab 13 — حذف Package

هدف:

کار با remove.

ابتدا:

```bash
sudo apt remove --dry-run nmap
```

اکنون:

```bash
sudo apt remove nmap
```

بررسی:

```bash
which nmap
```

---

# Lab 14 — حذف کامل

هدف:

شناخت purge.

دستور:

```bash
sudo apt purge nmap
```

سپس:

```bash
sudo apt autoremove
```

تمرین:

توضیح دهید تفاوت remove و purge چیست.

---

# Lab 15 — نصب مجدد

هدف:

کار با reinstall.

ابتدا:

```bash
sudo apt install nmap
```

سپس:

```bash
sudo apt reinstall nmap
```

---

# Lab 16 — نصب فایل محلی (.deb)

هدف:

نصب Local Package.

فرض کنید فایل زیر را دانلود کرده‌اید:

```text
/home/mehdi/Downloads/vscode.deb
```

یا روی فلش:

```text
/media/mehdi/KINGSTON/vscode.deb
```

نصب:

```bash
sudo apt install /home/mehdi/Downloads/vscode.deb
```

یا

```bash
sudo apt install /media/mehdi/KINGSTON/vscode.deb
```

سؤال:

چرا از `apt install` استفاده می‌کنیم و نه `dpkg -i`؟

---

# Lab 17 — دانلود بدون نصب

هدف:

آشنایی با دانلود Package.

دستور:

```bash
apt download htop
```

بررسی:

```bash
ls
```

تمرین:

فایل دانلودشده را پیدا کنید.

---

# Lab 18 — Mini Challenge

بدون استفاده از اینترنت:

1. Repositoryهای سیستم را بررسی کنید.
    
2. `apt update` اجرا کنید.
    
3. Package `tree` را جستجو کنید.
    
4. اطلاعات آن را ببینید.
    
5. با `--dry-run` نصب را بررسی کنید.
    
6. Package را نصب کنید.
    
7. محل فایل اجرایی را پیدا کنید.
    
8. نسخه آن را بررسی کنید.
    
9. Package را حذف کنید.
    
10. در پایان `autoremove` را اجرا کنید.
    

---

# Lab 19 — Challenge واقعی مدیر سیستم

فقط با استفاده از:

- `man`
    
- `--help`
    

پاسخ این سؤال‌ها را پیدا کنید:

1. تفاوت `apt install` و `dpkg -i` چیست؟
    
2. تفاوت `remove` و `purge` چیست؟
    
3. تفاوت `clean` و `autoclean` چیست؟
    
4. تفاوت `upgrade` و `full-upgrade` چیست؟
    
5. چگونه فقط Package را دانلود کنیم؟
    
6. چگونه نصب را بدون اجرا شبیه‌سازی کنیم؟
    
7. چگونه Repositoryهای سیستم را مشاهده کنیم؟
    

---

# پایان Chapter 06

پس از پایان این فصل باید بتوانید:

✅ ساختار Package Management اوبونتو را توضیح دهید.

✅ از Repositoryها نرم‌افزار جستجو و نصب کنید.

✅ قبل از نصب، تغییرات را با `--dry-run` بررسی کنید.

✅ Packageهای نصب‌شده را با `dpkg` بررسی کنید.

✅ Cache مربوط به APT را مدیریت کنید.

✅ تفاوت `remove`، `purge`، `clean` و `autoclean` را بدانید.

✅ فایل‌های `.deb` را به روش صحیح با `apt install` نصب کنید.

✅ تفاوت APT و dpkg را به‌صورت عملی درک کنید.