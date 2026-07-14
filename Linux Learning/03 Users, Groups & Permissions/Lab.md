# Chapter 03 — Complete Lab Exercises

# هدف آزمایش‌ها

در پایان این آزمایش‌ها باید بتوانید:

- کاربران و گروه‌های لینوکس را شناسایی کنید.
    
- تفاوت Root و User عادی را در عمل مشاهده کنید.
    
- فایل‌های مربوط به کاربران را بررسی کنید.
    
- مالک (Owner) و گروه (Group) فایل‌ها را تغییر دهید.
    
- Permissionها را بخوانید و تغییر دهید.
    
- مفهوم Permission عددی و نمادین را در عمل درک کنید.
    
- با sudo به‌صورت صحیح کار کنید.
    

---

# Lab 01 — شناسایی کاربر فعلی

هدف:

بررسی اطلاعات کاربر فعلی.

دستورها:

```bash
whoami
```

```bash
id
```

```bash
groups
```

سؤالات:

1. Username شما چیست؟
    
2. UID شما چیست؟
    
3. عضو چه Groupهایی هستید؟
    

---

# Lab 02 — بررسی کاربران سیستم

هدف:

شناخت فایل passwd.

دستورها:

```bash
cat /etc/passwd
```

اکنون فقط Usernameها را نمایش دهید:

```bash
cut -d: -f1 /etc/passwd
```

اکنون Username و UID را نمایش دهید:

```bash
awk -F: '{print $1,$3}' /etc/passwd
```

سؤالات:

1. اولین User چیست؟
    
2. Root چه UID دارد؟
    
3. User شما چه UID دارد؟
    

---

# Lab 03 — بررسی فایل Shadow

هدف:

شناخت محل Passwordها.

دستور:

```bash
sudo cat /etc/shadow
```

سؤالات:

1. آیا کاربران معمولی اجازه مشاهده این فایل را دارند؟
    
2. چرا؟
    

---

# Lab 04 — بررسی Groupها

هدف:

شناخت Groupها.

دستورها:

```bash
cat /etc/group
```

نمایش اطلاعات گروه sudo:

```bash
getent group sudo
```

سؤال:

آیا User شما عضو گروه sudo است؟

---

# Lab 05 — بررسی Home Directory

هدف:

شناخت Home کاربران.

دستورها:

```bash
echo $HOME
```

```bash
getent passwd $USER
```

سؤالات:

1. Home Directory شما چیست؟
    
2. Shell پیش‌فرض شما چیست؟
    

---

# Lab 06 — ساخت فایل آزمایشی

هدف:

ایجاد فایل برای تمرین Permissionها.

دستورها:

```bash
mkdir -p ~/LinuxLab/Chapter03
```

```bash
cd ~/LinuxLab/Chapter03
```

```bash
touch test.txt
```

```bash
ls -l
```

سؤال:

Owner فایل چه کسی است؟

---

# Lab 07 — بررسی Permissionها

هدف:

خواندن Permission.

دستور:

```bash
ls -l test.txt
```

تمرین:

Permission را به صورت زیر تحلیل کنید:

- Owner
    
- Group
    
- Others
    

---

# Lab 08 — تغییر Permission عددی

هدف:

کار با chmod.

دستورها:

```bash
chmod 644 test.txt
```

```bash
ls -l test.txt
```

اکنون:

```bash
chmod 600 test.txt
```

```bash
ls -l test.txt
```

اکنون:

```bash
chmod 755 test.txt
```

```bash
ls -l test.txt
```

تمرین:

تغییرات Permission را تحلیل کنید.

---

# Lab 09 — تغییر Permission نمادین

هدف:

درک Symbolic Mode.

دستورها:

```bash
chmod o-r test.txt
```

```bash
ls -l
```

اکنون:

```bash
chmod g+w test.txt
```

```bash
ls -l
```

اکنون:

```bash
chmod u+x test.txt
```

```bash
ls -l
```

سؤال:

هر دستور چه تغییری ایجاد کرد؟

---

# Lab 10 — اجرای فایل

هدف:

شناخت Execute Permission.

دستورها:

```bash
echo "echo Hello Linux" > script.sh
```

```bash
chmod +x script.sh
```

```bash
./script.sh
```

اکنون Execute را حذف کنید:

```bash
chmod -x script.sh
```

دوباره اجرا کنید.

سؤال:

چه اتفاقی افتاد؟

---

# Lab 11 — تغییر Owner

هدف:

بررسی مالک فایل.

دستور:

```bash
ls -l
```

سپس (در صورت داشتن یک User دیگر روی سیستم):

```bash
sudo chown username test.txt
```

یا فقط دستور را Dry Run ذهنی بررسی کنید.

سؤال:

چه چیزی تغییر کرد؟

---

# Lab 12 — تغییر Group

هدف:

تغییر Group فایل.

دستور:

```bash
sudo chgrp sudo test.txt
```

سپس:

```bash
ls -l
```

سؤال:

کدام قسمت خروجی تغییر کرد؟

---

# Lab 13 — بررسی دسترسی sudo

هدف:

شناخت دسترسی مدیریتی.

دستور:

```bash
sudo -l
```

سؤال:

کاربر شما اجازه اجرای چه دستوراتی را دارد؟

---

# Lab 14 — تغییر Password

هدف:

آشنایی با مدیریت Password.

فقط Manual را مطالعه کنید:

```bash
man passwd
```

سپس Password خود را تغییر دهید (اختیاری):

```bash
passwd
```

---

# Lab 15 — بررسی نوع فایل

هدف:

شناخت دستور file.

دستورها:

```bash
file test.txt
```

```bash
file script.sh
```

```bash
file /bin/ls
```

سؤال:

نوع هر فایل چیست؟

---

# Lab 16 — محاسبه Permissionها

هدف:

درک Permission عددی.

برای هر Permission عدد معادل را بنویسید:

```text
rwxr-xr-x

rw-r--r--

rw-------

rwx------

rwxrwx---
```

سپس برعکس:

```text
755

644

600

700

770
```

---

# Lab 17 — Mini Challenge

بدون استفاده از اینترنت:

1. یک پوشه به نام:
    

```text
SecurityLab
```

بسازید.

2. داخل آن سه فایل ایجاد کنید.
    
3. یکی را Permission 600 بدهید.
    
4. یکی را Permission 644 بدهید.
    
5. یکی را Permission 755 بدهید.
    
6. خروجی `ls -l` را تحلیل کنید.
    
7. یکی از فایل‌ها را Script کنید و اجرا نمایید.
    
8. Permission اجرای آن را حذف کنید.
    
9. دوباره اجرا کنید.
    
10. دلیل خطا را توضیح دهید.
    

---

# Lab 18 — Challenge واقعی مدیر سیستم

بدون استفاده از Google یا ChatGPT، فقط با استفاده از:

- `man`
    
- `--help`
    

پاسخ این سؤال‌ها را پیدا کنید:

1. تفاوت `chmod 755` و `chmod u+rwx,g+rx,o+rx` چیست؟
    
2. تفاوت `chown` و `chgrp` چیست؟
    
3. چگونه Owner و Group را همزمان تغییر دهیم؟
    
4. چگونه Permission یک پوشه را به‌صورت بازگشتی تغییر دهیم؟
    
5. چگونه Owner یک پوشه را به‌صورت بازگشتی تغییر دهیم؟
    

---

# پایان Chapter 03

پس از پایان این فصل باید بتوانید:

✅ تفاوت User، Group و Root را توضیح دهید.

✅ فایل‌های `/etc/passwd`، `/etc/shadow` و `/etc/group` را تحلیل کنید.

✅ Permissionهای لینوکس را بخوانید و محاسبه کنید.

✅ با `chmod`، `chown` و `chgrp` کار کنید.

✅ از `sudo` به‌درستی استفاده کنید.

✅ امنیت فایل‌ها را بر اساس اصل **Least Privilege** مدیریت کنید.