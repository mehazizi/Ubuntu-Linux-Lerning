# فصل ۳ - فایل‌ها و پوشه‌ها | آزمایشگاه

## تمرین ۱: ساخت ساختار پروژه
```bash
mkdir -p ~/project/{src,docs,tests,backup}
touch ~/project/src/{main.py,utils.py}
touch ~/project/docs/README.md
ls -R ~/project
```

## تمرین ۲: کار با لینک‌ها
```bash
cd ~/project
echo "محتوای اصلی" > original.txt
ln original.txt hardlink.txt
ln -s original.txt softlink.txt
ls -la
stat original.txt hardlink.txt  # inode یکسان دارند؟
rm original.txt
cat hardlink.txt    # هنوز کار می‌کند؟
cat softlink.txt    # شکسته شده؟
```

## تمرین ۳: جستجوی پیشرفته
```bash
# فایل‌های بزرگتر از ۱ مگابایت
find /var -size +1M 2>/dev/null

# فایل‌های تغییرکرده در ۲۴ ساعت اخیر
find /etc -mtime -1 2>/dev/null

# فایل‌های لاگ
find /var/log -name "*.log" -type f
```

### ✅ چک‌لیست یادگیری
- [ ] تفاوت Hard Link و Soft Link را می‌دانم
- [ ] می‌توانم با find فایل‌های خاص را پیدا کنم
- [ ] دستورات cp، mv، rm را با گزینه‌هایشان بلدم

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]