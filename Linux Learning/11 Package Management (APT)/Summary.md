# Chapter 11 - Summary(Part 1)

## APT

APT (Advanced Package Tool) سیستم مدیریت Package در Debian و Ubuntu است.

وظایف اصلی APT:

- نصب Package
    
- حذف Package
    
- به‌روزرسانی Packageها
    
- مدیریت Dependencyها
    
- مدیریت Repositoryها
    

---

## Repository

Repository مخزنی است که Packageهای لینوکس در آن نگهداری می‌شوند.

APT Packageها را از Repository دریافت می‌کند.

فایل اصلی Repositoryها:

/etc/apt/sources.list

Repositoryهای اضافه شده توسط نرم‌افزارهای دیگر:

/etc/apt/sources.list.d/

---

## Repositoryهای Ubuntu

چهار Repository مهم:

- jammy
    
- jammy-updates
    
- jammy-security
    
- jammy-backports
    

تفاوت آنها:

**jammy**

نسخه اولیه Ubuntu هنگام انتشار.

**jammy-updates**

رفع Bugها و افزایش Stability.

**jammy-security**

به‌روزرسانی‌های امنیتی.

**jammy-backports**

نسخه‌های جدیدتر بعضی نرم‌افزارها که به صورت اختیاری ارائه می‌شوند.

---

## Componentهای Repository

چهار Component اصلی:

- main
    
- restricted
    
- universe
    
- multiverse
    

**main**

Packageهای رسمی Ubuntu که توسط Canonical پشتیبانی می‌شوند.

**restricted**

Driverها و Firmwareهایی که کاملاً Open Source نیستند.

**universe**

بزرگ‌ترین Repository Ubuntu که اکثر نرم‌افزارهای عمومی در آن قرار دارند.

**multiverse**

نرم‌افزارهایی که محدودیت License یا حقوقی دارند.

---

## Update و Upgrade

apt update

لیست Packageهای موجود در Repository را دانلود می‌کند.

هیچ Packageی نصب یا Upgrade نمی‌شود.

---

apt upgrade

Packageهای نصب شده را به آخرین نسخه موجود ارتقا می‌دهد.

---

## Dependency

Dependency یعنی Packageهایی که برنامه برای اجرا به آنها نیاز دارد.

APT قبل از نصب Package، Dependencyها را بررسی می‌کند.

در صورت نیاز آنها را نیز نصب می‌کند.

---

## Cache

Packageهای دانلود شده در مسیر زیر ذخیره می‌شوند:

/var/cache/apt/archives/

با دستور:

apt clean

این فایل‌ها حذف می‌شوند.

---

## Repository Index

لیست Packageهای Repository در مسیر زیر نگهداری می‌شود:

/var/lib/apt/lists/

---

## GPG Signature

APT برای اطمینان از صحت Packageها از امضای دیجیتال استفاده می‌کند.

دو نوع Key وجود دارد:

Private Key

فقط نزد سازنده Repository است و برای Sign کردن Package استفاده می‌شود.

Public Key

روی سیستم کاربر قرار دارد و فقط برای Verify کردن Package استفاده می‌شود.

---

## HTTPS و GPG

HTTPS امنیت مسیر انتقال اطلاعات را تأمین می‌کند.

GPG صحت و اصالت خود Package را بررسی می‌کند.

این دو مکمل یکدیگر هستند.

---

## نصب فایل محلی

اگر Package را دانلود کرده باشیم:

apt install ./package.deb

یا

apt install /path/to/package.deb

استفاده می‌شود.

مزیت آن نسبت به dpkg:

Dependencyها نیز بررسی و نصب می‌شوند.

---

## حذف Package

remove

فقط Package حذف می‌شود.

---

purge

Package و فایل‌های تنظیمات حذف می‌شوند.

---

autoremove

Dependencyهای بلااستفاده حذف می‌شوند.

---

## مسیرهای مهم

Repository اصلی

/etc/apt/sources.list

Repositoryهای اضافه

/etc/apt/sources.list.d/

GPG Keys

/etc/apt/keyrings/

Cache

/var/cache/apt/archives/

Repository Lists

/var/lib/apt/lists/

# Chapter 11 - Summary (Part 2)

# Update و Upgrade

یکی از رایج‌ترین اشتباهات کاربران لینوکس، اشتباه گرفتن update و upgrade است.

---

## apt update

دستور:

sudo apt update

وظیفه:

- دانلود لیست جدید Packageها از Repository
    
- به‌روزرسانی Index محلی
    
- نصب یا Upgrade هیچ Packageی انجام نمی‌شود.
    

به زبان ساده:

APT فقط متوجه می‌شود چه نسخه‌های جدیدی منتشر شده‌اند.

---

## apt upgrade

دستور:

sudo apt upgrade

وظیفه:

Packageهایی که نسخه جدید آنها در Repository وجود دارد را Upgrade می‌کند.

در این مرحله ممکن است ده‌ها Package سیستم به نسخه جدید ارتقا پیدا کنند.

---

## apt full-upgrade

دستور:

sudo apt full-upgrade

برخلاف upgrade، اگر لازم باشد:

- Package جدید نصب کند.
    
- Package قدیمی حذف کند.
    

این کار را انجام می‌دهد.

در Upgradeهای بزرگ سیستم‌عامل معمولاً از full-upgrade استفاده می‌شود.

---

# Cache

APT بعد از دانلود Packageها آنها را حذف نمی‌کند.

فایل‌های دانلود شده در مسیر زیر ذخیره می‌شوند.

/var/cache/apt/archives/

مزیت Cache:

اگر همان Package دوباره نصب شود، معمولاً نیازی به دانلود مجدد نیست.

---

## پاک کردن Cache

sudo apt clean

تمام فایل‌های دانلود شده حذف می‌شوند.

خود Packageهای نصب شده حذف نمی‌شوند.

فقط فضای دیسک آزاد می‌شود.

---

# GPG Signature

APT قبل از نصب Packageها صحت آنها را بررسی می‌کند.

این کار توسط GPG انجام می‌شود.

هدف GPG:

- اطمینان از اصالت Package
    
- جلوگیری از دستکاری فایل‌ها
    

---

## Private Key

فقط نزد سازنده Repository است.

با آن Packageها Sign می‌شوند.

کاربر هیچ وقت به Private Key دسترسی ندارد.

---

## Public Key

روی سیستم کاربر نصب می‌شود.

تنها وظیفه آن Verify کردن Signature است.

با Public Key نمی‌توان Package جدید ساخت.

---

# HTTPS و GPG

این دو جایگزین یکدیگر نیستند.

HTTPS

از مسیر انتقال اطلاعات محافظت می‌کند.

GPG

از صحت و اصالت خود Package محافظت می‌کند.

حتی اگر فایل از روی فلش نصب شود، GPG همچنان می‌تواند صحت آن را بررسی کند.

---

# Repository شخص ثالث

بسیاری از نرم‌افزارها داخل Repository رسمی Ubuntu نیستند.

مانند:

- Docker
    
- Microsoft VS Code
    
- Google Chrome
    
- Tailscale
    
- Hashicorp
    
- GitHub CLI
    

برای اضافه کردن Repository جدید معمولاً چهار مرحله انجام می‌شود:

1- دانلود GPG Key

2- ساخت فایل Repository

3- اجرای apt update

4- نصب Package

---

# نصب فایل محلی

اگر Package را قبلاً دانلود کرده باشیم:

sudo apt install ./package.deb

یا

sudo apt install /path/to/package.deb

استفاده می‌شود.

مزیت این روش نسبت به dpkg:

APT تمام Dependencyها را نیز بررسی و نصب می‌کند.

---

# Remove ، Purge و Autoremove

## Remove

Package حذف می‌شود.

فایل‌های تنظیمات معمولاً باقی می‌مانند.

---

## Purge

Package و فایل‌های تنظیمات حذف می‌شوند.

---

## Autoremove

Dependencyهایی که دیگر هیچ Packageای از آنها استفاده نمی‌کند حذف می‌شوند.

---

# Best Practice

برای سرورهای Production:

- همیشه قبل از Upgrade از سیستم Backup تهیه کن.
    
- بعد از تغییر Repository حتماً apt update اجرا کن.
    
- از Repositoryهای ناشناس استفاده نکن.
    
- قبل از حذف Packageها Dependencyهای آنها را بررسی کن.
    
- برای نصب فایل‌های محلی از apt install استفاده کن، نه dpkg -i.
    

---

# مسیرهای مهم

Repository اصلی

/etc/apt/sources.list

Repositoryهای اضافه

/etc/apt/sources.list.d/

GPG Keys

/etc/apt/keyrings/

Package Cache

/var/cache/apt/archives/

Repository Index

/var/lib/apt/lists/