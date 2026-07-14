# فصل ۳ - فایل‌ها و پوشه‌ها | عیب‌یابی

## مشکل: rm نمی‌تواند فایل را حذف کند
```bash
# بررسی مجوز
ls -la file.txt
# بررسی ویژگی‌های خاص
lsattr file.txt
# حذف ویژگی تغییرناپذیر
sudo chattr -i file.txt
sudo rm file.txt
```

## مشکل: پوشه خالی نیست و rmdir کار نمی‌کند
```bash
ls -la mydir/          # چه چیزی داخل است؟
rm -ri mydir/          # حذف با تأیید هر فایل
```

## مشکل: فضای دیسک پر شده
```bash
df -h                                    # بررسی فضا
du -h / 2>/dev/null | sort -rh | head -20  # پوشه‌های بزرگ
find / -size +500M -type f 2>/dev/null   # فایل‌های بزرگ
```

## مشکل: لینک شکسته (broken symlink)
```bash
find / -xtype l 2>/dev/null   # پیدا کردن لینک‌های شکسته
ls -la symlink.txt             # هدف لینک را ببینید
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]