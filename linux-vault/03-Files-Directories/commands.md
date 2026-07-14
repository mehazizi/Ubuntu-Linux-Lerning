# فصل ۳ - فایل‌ها و پوشه‌ها | دستورات

## ساخت فایل و پوشه
```bash
touch file.txt              # ساخت فایل خالی یا به‌روزرسانی زمان
touch -t 202401011200 f.txt # تنظیم زمان دستی
mkdir mydir                 # ساخت پوشه
mkdir -p a/b/c              # ساخت پوشه‌های تودرتو
mkdir -m 755 secure_dir     # ساخت با مجوز مشخص
```

## کپی، انتقال، حذف
```bash
cp file.txt backup.txt      # کپی فایل
cp -r dir/ dir_backup/      # کپی بازگشتی پوشه
cp -p file.txt dest/        # حفظ مجوز و زمان
mv file.txt /tmp/           # انتقال فایل
mv old_name.txt new_name.txt # تغییر نام
rm file.txt                 # حذف فایل
rm -r mydir/                # حذف پوشه بازگشتی
rm -ri mydir/               # حذف با تأیید
rmdir emptydir/             # حذف پوشه خالی
```

## لینک
```bash
ln file.txt hardlink.txt        # ساخت Hard Link
ln -s /path/to/file symlink.txt # ساخت Soft Link
ln -s /var/www/html webroot     # لینک به پوشه
ls -la                          # مشاهده لینک‌ها
readlink symlink.txt            # مقصد لینک
```

## جستجو
```bash
find / -name "passwd"           # جستجو بر اساس نام
find /home -type f -name "*.log"
find / -size +100M              # فایل‌های بزرگ
find / -mtime -7                # تغییر در ۷ روز اخیر
find /tmp -type f -delete       # جستجو و حذف
find / -user john               # متعلق به کاربر
find / -perm -4000 2>/dev/null  # فایل‌های SUID
which bash                      # محل دستور
whereis python3                 # محل باینری و man page
locate filename                 # جستجوی سریع از پایگاه داده
updatedb                        # به‌روزرسانی پایگاه locate
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]