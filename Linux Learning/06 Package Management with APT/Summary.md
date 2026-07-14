# Chapter 06 — Package Management with APT

# Summary

# هدف این Chapter

در پایان این فصل باید بتوانید:

- معماری Package Management در Ubuntu را درک کنید.
    
- تفاوت APT، dpkg و Repository را بدانید.
    
- Packageها را جستجو، نصب، حذف و بروزرسانی کنید.
    
- Dependencyها را مدیریت کنید.
    
- وضعیت Packageها را بررسی کنید.
    
- Cache مربوط به APT را مدیریت کنید.
    
- Repositoryها را بشناسید و مدیریت کنید.
    
- Packageها را از فایل محلی (.deb) نصب کنید.
    
- تفاوت نصب از Repository و نصب Local را درک کنید.
    

---

# Package چیست؟

Package یک فایل نرم‌افزاری است که شامل موارد زیر است:

- فایل‌های برنامه
    
- کتابخانه‌ها (Libraries)
    
- فایل‌های تنظیمات
    
- مستندات
    
- اطلاعات نسخه
    
- وابستگی‌ها (Dependencies)
    

در Ubuntu معمولاً پسوند Packageها:

```text
.deb
```

است.

---

# Package Manager چیست؟

Package Manager سیستمی است که:

- نصب نرم‌افزار
    
- حذف نرم‌افزار
    
- بروزرسانی
    
- مدیریت وابستگی‌ها
    
- بررسی نسخه‌ها
    

را انجام می‌دهد.

در Ubuntu این وظیفه بر عهده APT است.

---

# APT چیست؟

APT

Advanced Package Tool

لایه مدیریتی بالای dpkg است.

APT وظایف زیر را انجام می‌دهد:

- دانلود Package
    
- پیدا کردن Dependencyها
    
- بررسی Repository
    
- بروزرسانی Packageها
    
- حذف Packageها
    

---

# dpkg چیست؟

dpkg ابزار سطح پایین مدیریت Packageهای Debian است.

وظیفه آن:

فقط نصب یا حذف فایل‌های .deb

است.

برخلاف APT:

- Dependency دانلود نمی‌کند.
    
- Repository را نمی‌شناسد.
    
- Package جدید پیدا نمی‌کند.
    

---

# Repository چیست؟

Repository یک مخزن نرم‌افزاری است.

APT هنگام نصب Package ابتدا Repositoryها را بررسی می‌کند.

اگر Package وجود داشته باشد:

- دانلود می‌شود.
    
- صحت آن بررسی می‌شود.
    
- نصب می‌شود.
    

---

# چرا Repository؟

مزایا:

- نسخه‌های معتبر
    
- بروزرسانی خودکار
    
- امنیت بیشتر
    
- مدیریت Dependencyها
    
- نصب سریع
    

---

# فایل Repositoryها

محل اصلی:

```text
/etc/apt/sources.list
```

Repositoryهای اضافی:

```text
/etc/apt/sources.list.d/
```

---

# ساختار یک Repository

نمونه:

```text
deb http://ir.archive.ubuntu.com/ubuntu jammy main
```

تحلیل:

**deb**

Packageهای Binary

---

**[http://ir.archive.ubuntu.com/ubuntu](http://ir.archive.ubuntu.com/ubuntu)**

آدرس Repository

---

**jammy**

نسخه Ubuntu

---

**main**

بخش Repository

---

# بخش‌های Repository

## Main

رسمی‌ترین Packageهای Ubuntu

- بیشترین پایداری
    
- بیشترین تست
    
- پشتیبانی رسمی Canonical
    

---

## Restricted

نرم‌افزارهای دارای License محدود

معمولاً Driverها

---

## Universe

نرم‌افزارهای متن‌باز جامعه لینوکس

پشتیبانی رسمی محدودتر

---

## Multiverse

نرم‌افزارهایی با محدودیت License یا Patent

---

# مخزن Security

نمونه:

```text
jammy-security
```

فقط بروزرسانی‌های امنیتی را ارائه می‌دهد.

---

# مخزن Updates

```text
jammy-updates
```

رفع Bugها و نسخه‌های جدیدتر Packageهای همان نسخه Ubuntu.

---

# مخزن Backports

```text
jammy-backports
```

نسخه‌های جدیدتر بعضی Packageها بدون ارتقای کل سیستم.

---

# چرا Repositoryها معمولاً HTTP هستند؟

بیشتر Mirrorهای Ubuntu هنوز از HTTP استفاده می‌کنند.

امنیت انتقال توسط امضای دیجیتال Packageها تأمین می‌شود.

APT قبل از نصب:

- امضای Repository
    
- امضای Package
    
- Checksum فایل‌ها
    

را بررسی می‌کند.

بنابراین حتی اگر ارتباط HTTP باشد، فایل جعلی نصب نخواهد شد.

---

# Update چیست؟

```bash
apt update
```

هیچ برنامه‌ای را نصب یا بروزرسانی نمی‌کند.

فقط فهرست Packageهای Repository را بروزرسانی می‌کند.

---

# Upgrade چیست؟

```bash
apt upgrade
```

Packageهای نصب‌شده را به آخرین نسخه موجود ارتقا می‌دهد.

---

# Full Upgrade

```bash
apt full-upgrade
```

در صورت نیاز Package حذف یا جایگزین نیز می‌کند.

---

# Search

APT می‌تواند Repositoryها را جستجو کند.

مثال:

```bash
apt search nginx
```

جستجو روی **Repository** انجام می‌شود، نه روی نرم‌افزارهای نصب‌شده.

---

# Show

```bash
apt show package
```

نمایش اطلاعات Package:

- Version
    
- Dependencies
    
- Download Size
    
- Repository
    
- Description
    

---

# نصب Package

```bash
sudo apt install package
```

APT ابتدا:

- Repository
    
- Dependency
    
- نسخه
    

را بررسی می‌کند.

سپس نصب را انجام می‌دهد.

---

# Dry Run

قبل از نصب واقعی:

```bash
sudo apt install --dry-run package
```

APT نشان می‌دهد:

- چه Packageهایی نصب می‌شوند.
    
- چه Dependencyهایی نیاز است.
    
- چه تغییری ایجاد خواهد شد.
    

بدون اینکه چیزی نصب شود.

---

# حذف Package

```bash
sudo apt remove package
```

فایل‌های تنظیمات باقی می‌مانند.

---

# Purge

```bash
sudo apt purge package
```

هم Package

هم فایل‌های تنظیمات حذف می‌شوند.

---

# Autoremove

```bash
sudo apt autoremove
```

Dependencyهایی که دیگر استفاده نمی‌شوند حذف می‌شوند.

---

# Cache

Packageهای دانلودشده در:

```text
/var/cache/apt/archives/
```

ذخیره می‌شوند.

اگر همان نسخه دوباره نصب شود، APT در صورت وجود فایل در Cache می‌تواند از آن استفاده کند و نیازی به دانلود مجدد نیست.

---

# Clean

```bash
apt clean
```

کل Cache را حذف می‌کند.

---

# Autoclean

```bash
apt autoclean
```

فقط Packageهای قدیمی و غیرقابل استفاده را حذف می‌کند.

---

# Dependency

بیشتر Packageها به Packageهای دیگر نیاز دارند.

APT این وابستگی‌ها را به صورت خودکار مدیریت می‌کند.

---

# Local Installation (.deb)

اگر فایل را خودتان دانلود کرده باشید:

```bash
sudo apt install ./program.deb
```

یا

```bash
sudo apt install /path/to/program.deb
```

APT علاوه بر نصب فایل، Dependencyهای موردنیاز را نیز از Repository دانلود می‌کند.

---

# نصب با dpkg

```bash
sudo dpkg -i program.deb
```

Dependencyها را نصب نمی‌کند.

در صورت کمبود Dependency ممکن است نصب ناقص شود.

---

# نصب از Archive

بعضی نرم‌افزارها به صورت:

```text
.tar

.tar.gz

.tar.xz
```

منتشر می‌شوند.

این فایل‌ها Package نیستند.

معمولاً باید:

- استخراج شوند.
    
- دستورالعمل نصب آنها اجرا شود.
    
- یا فایل اجرایی مستقیماً استفاده شود.
    

در فصل‌های آینده به طور کامل این روش را یاد خواهیم گرفت.

---

# Best Practices

- همیشه قبل از نصب، `apt update` اجرا کنید.
    
- قبل از نصب نرم‌افزارهای مهم، از `--dry-run` استفاده کنید.
    
- تا حد امکان از Repositoryهای رسمی استفاده کنید.
    
- برای حذف کامل نرم‌افزار از `purge` استفاده کنید.
    
- پس از حذف نرم‌افزارها، `autoremove` را اجرا کنید.
    
- قبل از افزودن Repository جدید، اعتبار آن را بررسی کنید.
    

---

# Common Mistakes

- اجرای `apt upgrade` بدون `apt update`.
    
- استفاده مستقیم از `dpkg` برای Packageهایی که Dependency دارند.
    
- اضافه کردن Repositoryهای نامعتبر.
    
- حذف دستی فایل‌های داخل `/var/cache/apt`.
    
- اشتباه گرفتن `remove` و `purge`.
    
- تصور اینکه `apt search` فقط نرم‌افزارهای نصب‌شده را نمایش می‌دهد.
    

---

# Production Tips

- ابتدا Repositoryها را بشناسید؛ بدانید سیستم دقیقاً از کجا Package دریافت می‌کند.
    
- در سرورهای Production تا حد امکان از Repositoryهای رسمی و پایدار استفاده کنید.
    
- هنگام نصب فایل‌های `.deb`، استفاده از `apt install ./file.deb` را به `dpkg -i` ترجیح دهید، زیرا Dependencyها را نیز مدیریت می‌کند.
    
- قبل از هر نصب یا ارتقای مهم، خروجی `--dry-run` را بررسی کنید تا از تغییرات احتمالی آگاه باشید.
    
- پاک کردن Cache باعث حذف نرم‌افزارهای نصب‌شده نمی‌شود؛ فقط فایل‌های دانلودشده حذف خواهند شد.