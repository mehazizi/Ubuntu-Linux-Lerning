# Chapter 02 — Lab Exercises

# هدف آزمایش‌ها

در پایان این فصل باید بتوانید:

- در ساختار Filesystem لینوکس به‌راحتی حرکت کنید.
    
- مسیرهای Absolute و Relative را تشخیص دهید.
    
- فایل‌ها و پوشه‌ها را ایجاد، کپی، انتقال و حذف کنید.
    
- فایل‌های مخفی را مدیریت کنید.
    
- محل مناسب ذخیره فایل‌ها را بشناسید.
    
- ساختار کلی Filesystem را درک کنید.
    

---

# Lab 01 — شناخت Filesystem

هدف:

مشاهده ساختار اصلی لینوکس.

دستورها:

```bash
cd /
```

```bash
pwd
```

```bash
ls
```

سؤالات:

1. اکنون در چه مسیری قرار دارید؟
    
2. چند Directory مشاهده می‌کنید؟
    
3. آیا پوشه Home را مشاهده می‌کنید؟
    

---

# Lab 02 — بررسی Directoryهای مهم

هدف:

آشنایی با Directoryهای اصلی.

دستورها:

```bash
ls /
```

سپس وارد Directoryهای زیر شوید:

```bash
cd /etc
pwd
```

```bash
cd /home
pwd
```

```bash
cd /var
pwd
```

```bash
cd /tmp
pwd
```

```bash
cd /
```

سؤالات:

1. کدام Directory مربوط به تنظیمات سیستم است؟
    
2. فایل‌های کاربران کجا قرار می‌گیرند؟
    
3. Logهای سیستم معمولاً در کدام مسیر هستند؟
    

---

# Lab 03 — حرکت بین مسیرها

هدف:

تمرین استفاده از cd

دستورها:

```bash
cd
```

```bash
pwd
```

```bash
cd /
```

```bash
cd ..
```

```bash
cd -
```

```bash
cd ~
```

سؤالات:

1. دستور `cd -` چه کاری انجام می‌دهد؟
    
2. تفاوت `cd` و `cd /` چیست؟
    
3. تفاوت `cd ~` و `cd /home/username` چیست؟
    

---

# Lab 04 — ساخت Directory

هدف:

ساخت پوشه‌ها.

دستورها:

```bash
mkdir LinuxLab
```

```bash
cd LinuxLab
```

```bash
mkdir Projects
```

```bash
mkdir Backup
```

```bash
mkdir -p Notes/Chapter01
```

```bash
tree
```

سؤالات:

1. تفاوت `mkdir` و `mkdir -p` چیست؟
    
2. ساختار ایجاد شده را بررسی کنید.
    

---

# Lab 05 — ساخت فایل

هدف:

ایجاد فایل‌های خالی.

دستورها:

```bash
touch note.txt
```

```bash
touch file1 file2 file3
```

```bash
ls -l
```

تمرین:

یک فایل مخفی نیز ایجاد کنید.

---

# Lab 06 — فایل‌های مخفی

هدف:

شناخت Hidden Files

دستورها:

```bash
touch .secret
```

```bash
ls
```

```bash
ls -a
```

سؤالات:

1. چرا فایل `.secret` ابتدا دیده نمی‌شود؟
    
2. چگونه فایل‌های مخفی نمایش داده می‌شوند؟
    

---

# Lab 07 — کپی فایل

هدف:

تمرین cp

دستورها:

```bash
cp note.txt Backup/
```

```bash
ls Backup
```

```bash
cp file1 Backup/file1-copy
```

تمرین:

بررسی کنید فایل اصلی هنوز وجود دارد یا خیر.

---

# Lab 08 — انتقال فایل

هدف:

تمرین mv

دستورها:

```bash
mv file2 Backup/
```

```bash
mv file3 newfile
```

```bash
ls
```

```bash
ls Backup
```

سؤالات:

1. تفاوت Copy و Move چیست؟
    
2. آیا file2 هنوز در پوشه اصلی وجود دارد؟
    

---

# Lab 09 — حذف فایل

هدف:

تمرین rm

دستورها:

```bash
rm newfile
```

```bash
rm -i note.txt
```

تمرین:

به پیام تأیید دقت کنید.

---

# Lab 10 — حذف Directory

هدف:

تمرین حذف پوشه‌ها.

دستورها:

```bash
mkdir TestDelete
```

```bash
rmdir TestDelete
```

اکنون:

```bash
mkdir TestDelete
```

```bash
touch TestDelete/file.txt
```

```bash
rmdir TestDelete
```

سؤال:

چرا حذف انجام نشد؟

اکنون:

```bash
rm -r TestDelete
```

---

# Lab 11 — مشاهده فایل‌ها

هدف:

تمرین مشاهده محتویات فایل.

دستورها:

```bash
echo "Linux Administrator" > info.txt
```

```bash
cat info.txt
```

```bash
head info.txt
```

```bash
tail info.txt
```

```bash
less info.txt
```

تمرین:

در less با کلیدهای زیر کار کنید:

- ↑ ↓
    
- Space
    
- b
    
- /
    
- q
    

---

# Lab 12 — جستجوی فایل

هدف:

تمرین find

دستورها:

```bash
find . -name info.txt
```

```bash
find . -type f
```

```bash
find . -type d
```

تمرین:

تمام فایل‌های با پسوند txt را پیدا کنید.

---

# Lab 13 — بررسی فضای دیسک

هدف:

بررسی حجم فایل‌ها.

دستورها:

```bash
du -sh .
```

```bash
df -h
```

```bash
lsblk
```

سؤالات:

1. حجم پوشه فعلی چقدر است؟
    
2. فضای آزاد سیستم چقدر است؟
    
3. چند Disk مشاهده می‌کنید؟
    

---

# Lab 14 — بررسی Mountها

هدف:

شناخت Mount Pointها.

دستورها:

```bash
mount
```

```bash
lsblk
```

```bash
blkid
```

تمرین:

بررسی کنید Root روی کدام Partition قرار دارد.

---

# Lab 15 — Absolute Path و Relative Path

هدف:

درک تفاوت مسیرها.

فرض کنید اکنون داخل:

```text
/home/mehdi/LinuxLab
```

قرار دارید.

تمرین کنید:

```bash
cd Backup
```

بازگردید:

```bash
cd ..
```

اکنون:

```bash
cd /home/mehdi/LinuxLab/Backup
```

سؤالات:

1. کدام دستور Relative Path بود؟
    
2. کدام دستور Absolute Path بود؟
    

---

# Lab 16 — Mini Challenge

بدون استفاده از اینترنت، مراحل زیر را انجام دهید:

1. یک پوشه به نام:
    

```text
LinuxPractice
```

بسازید.

2. داخل آن سه پوشه ایجاد کنید:
    

```text
Docs
Backup
Config
```

3. دو فایل ایجاد کنید.
    
4. یکی را به Backup کپی کنید.
    
5. دیگری را Rename کنید.
    
6. یک فایل مخفی ایجاد کنید.
    
7. با `find` فایل مخفی را پیدا کنید.
    
8. حجم پوشه را بررسی کنید.
    
9. ساختار پوشه را با `tree` نمایش دهید.
    
10. در پایان کل پوشه را حذف کنید.
    

---

# پایان Chapter 02

پس از پایان این فصل باید بتوانید:

✅ در Filesystem لینوکس به‌راحتی حرکت کنید.

✅ مسیرهای Absolute و Relative را تشخیص دهید.

✅ فایل‌ها و پوشه‌ها را مدیریت کنید.

✅ فایل‌های مخفی را بشناسید.

✅ از دستورات اصلی مدیریت فایل‌ها بدون نیاز به اینترنت استفاده کنید.

✅ ساختار Filesystem لینوکس را درک کنید و بدانید هر نوع فایل باید در کدام مسیر قرار بگیرد.