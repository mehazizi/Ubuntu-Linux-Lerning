# Chapter 02 — Commands

# Current Directory

نمایش مسیر فعلی

```bash
pwd
```

---

# List Files & Directories

نمایش محتویات پوشه

```bash
ls
```

---

نمایش لیست کامل

```bash
ls -l
```

---

نمایش فایل‌های مخفی

```bash
ls -a
```

---

نمایش کامل همراه فایل‌های مخفی

```bash
ls -la
```

---

نمایش خوانا (حجم فایل‌ها)

```bash
ls -lh
```

---

نمایش بر اساس زمان

```bash
ls -lt
```

---

نمایش بازگشتی

```bash
ls -R
```

---

# Change Directory

ورود به پوشه

```bash
cd directory
```

---

بازگشت به Home

```bash
cd
```

یا

```bash
cd ~
```

---

رفتن به Root

```bash
cd /
```

---

بازگشت یک پوشه

```bash
cd ..
```

---

بازگشت دو پوشه

```bash
cd ../..
```

---

بازگشت به پوشه قبلی

```bash
cd -
```

---

# Show Directory Tree

نمایش ساختار درختی

```bash
tree
```

---

نمایش فقط Directoryها

```bash
tree -d
```

---

اگر نصب نبود:

```bash
sudo apt install tree
```

---

# Create Directories

ساخت یک پوشه

```bash
mkdir test
```

---

ساخت چند پوشه

```bash
mkdir dir1 dir2 dir3
```

---

ساخت پوشه تو در تو

```bash
mkdir -p backup/2026/june
```

---

# Remove Directories

حذف پوشه خالی

```bash
rmdir test
```

---

حذف پوشه همراه محتویات

```bash
rm -r test
```

---

حذف اجباری

```bash
rm -rf test
```

⚠️ بسیار خطرناک

---

# Create Files

ساخت فایل خالی

```bash
touch file.txt
```

---

ساخت چند فایل

```bash
touch file1 file2 file3
```

---

# Copy Files

کپی فایل

```bash
cp source.txt destination.txt
```

---

کپی فایل داخل پوشه

```bash
cp file.txt backup/
```

---

کپی پوشه

```bash
cp -r source destination
```

---

# Move Files

جابجایی فایل

```bash
mv file.txt backup/
```

---

تغییر نام فایل

```bash
mv old.txt new.txt
```

---

تغییر نام پوشه

```bash
mv olddir newdir
```

---

# Remove Files

حذف فایل

```bash
rm file.txt
```

---

حذف چند فایل

```bash
rm file1 file2
```

---

حذف با تأیید

```bash
rm -i file.txt
```

---

# View File Content

نمایش فایل

```bash
cat file.txt
```

---

نمایش ابتدای فایل

```bash
head file.txt
```

---

نمایش ۱۰ خط اول

```bash
head -10 file.txt
```

---

نمایش انتهای فایل

```bash
tail file.txt
```

---

نمایش ۲۰ خط آخر

```bash
tail -20 file.txt
```

---

نمایش زنده Log

```bash
tail -f logfile.log
```

---

صفحه‌بندی فایل

```bash
less file.txt
```

---

نمایش صفحه‌ای

```bash
more file.txt
```

---

# Find Files

جستجو در مسیر

```bash
find /path -name filename
```

مثال

```bash
find /etc -name hosts
```

---

جستجوی فایل با پسوند

```bash
find . -name "*.conf"
```

---

جستجوی Directory

```bash
find . -type d
```

---

جستجوی فایل

```bash
find . -type f
```

---

# Locate

جستجوی سریع فایل

```bash
locate filename
```

---

به‌روزرسانی Database

```bash
sudo updatedb
```

---

# Disk Usage

حجم فایل یا پوشه

```bash
du -sh directory
```

---

حجم تمام زیرپوشه‌ها

```bash
du -h
```

---

فضای فایل‌سیستم

```bash
df -h
```

---

# Mount Information

نمایش Mountها

```bash
mount
```

---

نمایش Block Deviceها

```bash
lsblk
```

---

نمایش UUID دیسک‌ها

```bash
blkid
```

---

# Hidden Files

نمایش فایل‌های مخفی

```bash
ls -la
```

---

ساخت فایل مخفی

```bash
touch .hiddenfile
```

---

# Path Navigation

نمایش Home

```bash
echo $HOME
```

---

نمایش مسیر فعلی

```bash
pwd
```

---

# Help

راهنمای دستورات

```bash
man ls
```

---

```bash
man cd
```

---

```bash
man mkdir
```

---

```bash
man cp
```

---

```bash
man mv
```

---

```bash
man rm
```

---

```bash
man find
```

---

# Best Practice

قبل از اجرای دستورات مخرب مانند:

```bash
rm -rf
```

ابتدا با:

```bash
pwd
```

و

```bash
ls
```

اطمینان حاصل کنید در مسیر صحیح قرار دارید.

---

برای حذف پوشه‌های مهم هیچ‌گاه از Autocomplete بدون بررسی استفاده نکنید.

---

همیشه برای کپی پوشه‌ها از:

```bash
cp -r
```

استفاده کنید.

---

برای مشاهده فایل‌های بزرگ از:

```bash
less
```

به جای

```bash
cat
```

استفاده کنید؛ زیرا حافظه کمتری مصرف می‌کند و امکان جستجو و پیمایش دارد.