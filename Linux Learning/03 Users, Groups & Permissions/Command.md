# Chapter 03 — Commands

# Current User

نمایش نام کاربر فعلی

```bash
whoami
```

---

نمایش اطلاعات کامل کاربر

```bash
id
```

---

نمایش کاربران وارد شده به سیستم

```bash
who
```

---

نمایش کاربران فعال و فعالیت آنها

```bash
w
```

---

نمایش نام Login کاربر

```bash
logname
```

---

# User Information

نمایش اطلاعات کاربر

```bash
finger username
```

> اگر نصب نبود:

```bash
sudo apt install finger
```

---

نمایش شناسه عددی کاربر

```bash
id username
```

---

# List Users

نمایش کاربران سیستم

```bash
cat /etc/passwd
```

---

نمایش فقط Usernameها

```bash
cut -d: -f1 /etc/passwd
```

---

نمایش کاربران با UID

```bash
awk -F: '{print $1,$3}' /etc/passwd
```

---

# Groups

نمایش Groupهای کاربر فعلی

```bash
groups
```

---

نمایش Groupهای یک کاربر

```bash
groups username
```

---

نمایش اطلاعات Group

```bash
cat /etc/group
```

---

نمایش اعضای یک Group

```bash
getent group sudo
```

---

# Home Directory

نمایش Home کاربر

```bash
echo $HOME
```

---

نمایش اطلاعات کاربر

```bash
getent passwd username
```

---

# Password Files

نمایش فایل کاربران

```bash
cat /etc/passwd
```

---

نمایش فایل Passwordها

```bash
sudo cat /etc/shadow
```

---

نمایش فایل Groupها

```bash
cat /etc/group
```

---

# File Ownership

نمایش Owner فایل

```bash
ls -l
```

---

نمایش Owner پوشه

```bash
ls -ld directory
```

---

تغییر Owner

```bash
sudo chown mehdi file.txt
```

---

تغییر Owner و Group

```bash
sudo chown mehdi:developers file.txt
```

---

تغییر Owner بازگشتی

```bash
sudo chown -R mehdi:developers Project/
```

---

# Change Group

تغییر Group فایل

```bash
sudo chgrp developers file.txt
```

---

تغییر Group بازگشتی

```bash
sudo chgrp -R developers Project/
```

---

# File Permissions

نمایش Permission

```bash
ls -l
```

---

نمایش Permission پوشه

```bash
ls -ld directory
```

---

# chmod (Numeric)

خواندن و نوشتن برای Owner

```bash
chmod 600 file.txt
```

---

Owner کامل

Group و Others فقط خواندن

```bash
chmod 744 file.txt
```

---

Permission رایج فایل

```bash
chmod 644 file.txt
```

---

Permission رایج Script

```bash
chmod 755 script.sh
```

---

Permission کامل

```bash
chmod 777 file.txt
```

⚠️ فقط برای آزمایش

---

حذف تمام Permissionها

```bash
chmod 000 file.txt
```

---

# chmod (Symbolic)

اضافه کردن Execute

```bash
chmod +x script.sh
```

---

حذف Execute

```bash
chmod -x script.sh
```

---

اضافه کردن Write برای Group

```bash
chmod g+w file.txt
```

---

حذف Write از Others

```bash
chmod o-w file.txt
```

---

دادن Read به Owner

```bash
chmod u+r file.txt
```

---

دادن Permission کامل به Owner

```bash
chmod u+rwx file.txt
```

---

دادن Execute به همه

```bash
chmod a+x script.sh
```

---

# Sudo

اجرای دستور با Root

```bash
sudo command
```

مثال

```bash
sudo apt update
```

---

ورود به Shell روت

```bash
sudo -i
```

یا

```bash
sudo su
```

---

خروج از Root

```bash
exit
```

---

بررسی دسترسی sudo

```bash
sudo -l
```

---

# Password

تغییر Password کاربر فعلی

```bash
passwd
```

---

تغییر Password یک کاربر

```bash
sudo passwd username
```

---

قفل کردن Password

```bash
sudo passwd -l username
```

---

باز کردن Password

```bash
sudo passwd -u username
```

---

# File Type

نمایش نوع فایل

```bash
file filename
```

---

# Permission Calculation

نمونه‌های رایج

```text
777 = rwxrwxrwx

755 = rwxr-xr-x

750 = rwxr-x---

700 = rwx------

644 = rw-r--r--

640 = rw-r-----

600 = rw-------

400 = r--------
```

---

# Help

راهنمای chmod

```bash
man chmod
```

---

راهنمای chown

```bash
man chown
```

---

راهنمای chgrp

```bash
man chgrp
```

---

راهنمای passwd

```bash
man passwd
```

---

راهنمای sudo

```bash
man sudo
```

---

# Best Practice

قبل از تغییر Permission همیشه بررسی کنید:

```bash
ls -l
```

---

قبل از تغییر Owner بررسی کنید:

```bash
id username
```

---

برای فایل‌های معمولی معمولاً از:

```text
644
```

استفاده می‌شود.

---

برای Scriptها معمولاً:

```text
755
```

---

برای کلید خصوصی SSH:

```text
600
```

---

تا حد امکان از Permission **777** استفاده نکنید.

---

برای کارهای مدیریتی فقط همان دستور موردنیاز را با `sudo` اجرا کنید و از ورود دائمی به حساب Root خودداری کنید.