# فصل ۱۰ - مدیریت فرآیندها | آزمایشگاه

## تمرین ۱: بررسی فرآیندها
```bash
ps aux | head -10
ps aux --sort=-%cpu | head -5
pstree -p | head -20
```

## تمرین ۲: کار با پس‌زمینه
```bash
sleep 200 &
sleep 300 &
jobs
fg %1
# Ctrl+Z برای توقف
bg %1
jobs
kill %2
jobs
```

## تمرین ۳: سیگنال‌ها
```bash
sleep 1000 &
PID=$!
echo "PID: $PID"
ps aux | grep $PID
kill -15 $PID       # درخواست خاتمه
sleep 0.5
ps aux | grep $PID  # آیا هنوز هست؟
```

## تمرین ۴: htop
```bash
htop
# در htop تمرین کنید:
# F6 برای مرتب‌سازی
# F9 برای ارسال سیگنال
# F5 برای نمایش درختی
# q برای خروج
```

### ✅ چک‌لیست یادگیری
- [ ] تفاوت ps و top و htop را می‌دانم
- [ ] فرآیند را در پس‌زمینه اجرا کرده‌ام
- [ ] سیگنال‌های مختلف را آزمایش کرده‌ام
- [ ] مفهوم Nice و اولویت را می‌فهمم

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]