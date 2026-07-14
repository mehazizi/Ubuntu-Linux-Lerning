# فصل ۵ - پردازش متن | آزمایشگاه

## تمرین ۱: تحلیل لاگ با grep
```bash
# پیدا کردن خطاها در سیستم
grep -i "error" /var/log/syslog | tail -20

# شمارش تلاش‌های ورود ناموفق SSH
grep "Failed password" /var/log/auth.log | wc -l

# پرتکرارترین IP در تلاش‌های ناموفق
grep "Failed password" /var/log/auth.log |   grep -oE "[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+" |   sort | uniq -c | sort -rn | head -5
```

## تمرین ۲: پردازش /etc/passwd
```bash
# لیست کاربران با shell آن‌ها
cut -d: -f1,7 /etc/passwd

# کاربرانی که bash دارند
grep "/bin/bash" /etc/passwd | cut -d: -f1

# مرتب‌سازی بر اساس UID
sort -t: -k3 -n /etc/passwd | head -10
```

## تمرین ۳: ترکیب ابزارها
```bash
# ۱۰ دستور پرتکرار از تاریخچه
history | awk '{print $2}' | sort | uniq -c | sort -rn | head -10

# پسوند فایل‌های پرتعداد در /usr/bin
ls /usr/bin | grep -oE '\.[^.]+$' | sort | uniq -c | sort -rn
```

### ✅ چک‌لیست یادگیری
- [ ] با grep الگوهای پیچیده جستجو کرده‌ام
- [ ] از pipe برای ترکیب ابزارها استفاده کرده‌ام
- [ ] sed را برای جایگزینی متن استفاده کرده‌ام
- [ ] با awk ستون‌های خاص را استخراج کرده‌ام

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]