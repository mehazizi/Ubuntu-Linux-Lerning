# Chapter 06 — Commands

# Package Search

جستجوی Package در Repositoryها

```bash
apt search package
```

مثال:

```bash
apt search nginx
```

---

جستجوی دقیق

```bash
apt search ^nginx
```

---

جستجو بدون حساسیت به حروف

```bash
apt search NGINX
```

---

# Package Information

نمایش اطلاعات Package

```bash
apt show package
```

مثال:

```bash
apt show nmap
```

---

نمایش تمام رکوردهای موجود

```bash
apt show -a package
```

---

نمایش سیاست نسخه‌ها

```bash
apt policy package
```

مثال:

```bash
apt policy nginx
```

---

# Update Repository Database

بروزرسانی فهرست Packageها

```bash
sudo apt update
```

---

# Upgrade Packages

بروزرسانی Packageهای نصب‌شده

```bash
sudo apt upgrade
```

---

بروزرسانی کامل سیستم

```bash
sudo apt full-upgrade
```

---

# Install Packages

نصب Package

```bash
sudo apt install package
```

مثال:

```bash
sudo apt install nmap
```

---

نصب همزمان چند Package

```bash
sudo apt install package1 package2 package3
```

---

نصب بدون سؤال تأیید

```bash
sudo apt install -y package
```

---

شبیه‌سازی نصب

```bash
sudo apt install --dry-run package
```

---

دانلود بدون نصب

```bash
sudo apt install --download-only package
```

---

# Remove Packages

حذف Package

```bash
sudo apt remove package
```

---

حذف کامل همراه فایل‌های تنظیمات

```bash
sudo apt purge package
```

---

حذف Packageهای بدون استفاده

```bash
sudo apt autoremove
```

---

حذف Cache قدیمی

```bash
sudo apt autoclean
```

---

حذف کامل Cache

```bash
sudo apt clean
```

---

# Reinstall

نصب مجدد Package

```bash
sudo apt reinstall package
```

---

# Installed Packages

بررسی نصب بودن Package

```bash
dpkg -l | grep package
```

مثال:

```bash
dpkg -l | grep htop
```

---

بررسی وضعیت Package

```bash
dpkg -s package
```

---

نمایش فایل‌های نصب‌شده Package

```bash
dpkg -L package
```

---

بررسی اینکه یک فایل متعلق به کدام Package است

```bash
dpkg -S /path/file
```

مثال:

```bash
dpkg -S /usr/bin/nmap
```

---

# Executable Location

پیدا کردن مسیر فایل اجرایی

```bash
which command
```

مثال:

```bash
which nmap
```

---

نمایش تمام مسیرهای ممکن

```bash
whereis command
```

---

# Package Cache

محل ذخیره Packageهای دانلودشده

```text
/var/cache/apt/archives/
```

---

مشاهده Cache

```bash
ls -lh /var/cache/apt/archives/
```

---

# Repository Files

نمایش Repository اصلی

```bash
cat /etc/apt/sources.list
```

---

ویرایش Repository

```bash
sudo nano /etc/apt/sources.list
```

---

نمایش Repositoryهای اضافه

```bash
ls -l /etc/apt/sources.list.d/
```

---

نمایش فایل‌های Repository اضافه

```bash
ls /etc/apt/sources.list.d/
```

---

# Local Installation (.deb)

نصب فایل محلی

```bash
sudo apt install ./program.deb
```

---

نصب فایل با مسیر کامل

```bash
sudo apt install /path/to/program.deb
```

مثال:

```bash
sudo apt install /media/mehdi/KINGSTON/vscode.deb
```

---

# Low-Level Installation

نصب با dpkg

```bash
sudo dpkg -i program.deb
```

---

رفع Dependencyهای ناقص

```bash
sudo apt -f install
```

---

# Download Package Only

دانلود Package

```bash
apt download package
```

---

# Repository Policy

نمایش Repository انتخاب‌شده

```bash
apt policy
```

---

نمایش نسخه‌های موجود یک Package

```bash
apt policy package
```

---

# Verify Package

بررسی وجود فایل اجرایی

```bash
which package
```

---

اجرای برنامه

```bash
package --version
```

یا

```bash
package
```

---

# Help

راهنمای APT

```bash
man apt
```

---

راهنمای apt-install

```bash
man apt-get
```

---

راهنمای dpkg

```bash
man dpkg
```

---

راهنمای sources.list

```bash
man sources.list
```

---

راهنمای apt-cache

```bash
man apt-cache
```

---

# Best Practice Workflow

بهترین ترتیب نصب نرم‌افزار

```bash
sudo apt update
```

↓

```bash
apt search package
```

↓

```bash
apt show package
```

↓

```bash
sudo apt install --dry-run package
```

↓

```bash
sudo apt install package
```

↓

```bash
which package
```

↓

```bash
package --version
```

---

# Best Practice — حذف نرم‌افزار

ابتدا بررسی کنید چه چیزی حذف خواهد شد

```bash
sudo apt remove --dry-run package
```

سپس:

```bash
sudo apt remove package
```

یا برای حذف کامل:

```bash
sudo apt purge package
```

در پایان:

```bash
sudo apt autoremove
```

---

# Best Practice — نصب فایل محلی

اگر فایل `.deb` را خودتان دانلود کرده‌اید:

```bash
sudo apt install ./file.deb
```

یا:

```bash
sudo apt install /full/path/file.deb
```

از این روش استفاده کنید، زیرا APT وابستگی‌ها را نیز مدیریت می‌کند.

از `dpkg -i` فقط زمانی استفاده کنید که دلیل مشخصی برای استفاده از آن دارید.

# Chapter 06 — Additional Commands (Missing Commands)

# Installed Package List

نمایش تمام Packageهای نصب‌شده

```bash
apt list --installed
```

---

نمایش Packageهای قابل بروزرسانی

```bash
apt list --upgradable
```

---

# Fix Broken Packages

رفع Dependencyهای خراب

```bash
sudo apt --fix-broken install
```

یا

```bash
sudo apt -f install
```

---

# Remove Downloaded Package

دانلود Package بدون نصب

```bash
apt download package
```

حذف فایل دانلود شده

```bash
rm package*.deb
```

---

# Download Only

دانلود Package بدون نصب

```bash
sudo apt install --download-only package
```

---

# Package Dependencies

نمایش وابستگی‌ها

```bash
apt depends package
```

---

نمایش وابستگی‌های معکوس

```bash
apt rdepends package
```

---

# Check Executable

پیدا کردن فایل اجرایی

```bash
which command
```

---

نمایش تمام مسیرهای مرتبط

```bash
whereis command
```

---

# Verify Installed Files

نمایش فایل‌های Package

```bash
dpkg -L package
```

---

بررسی اینکه فایل متعلق به چه Packageای است

```bash
dpkg -S /path/to/file
```

---

# Repository Files

ویرایش Repository اصلی

```bash
sudo nano /etc/apt/sources.list
```

---

نمایش Repositoryهای اضافه

```bash
ls -l /etc/apt/sources.list.d/
```

---

# APT Cache

نمایش حجم Cache

```bash
du -sh /var/cache/apt/archives/
```

---

نمایش فایل‌های Cache

```bash
ls -lh /var/cache/apt/archives/
```

---

# APT History

مشاهده تاریخچه نصب‌ها

```bash
less /var/log/apt/history.log
```

---

مشاهده عملیات اخیر APT

```bash
less /var/log/apt/term.log
```

---

# Package Version

نمایش نسخه برنامه

```bash
program --version
```

مثال

```bash
nmap --version
```

---

# Best Practice Workflow

```text
1. apt update

2. apt search

3. apt show

4. apt policy

5. apt install --dry-run

6. apt install

7. which

8. program --version

9. dpkg -L

10. apt autoremove (در صورت نیاز)
```