# فصل ۱۰ - مدیریت فرآیندها | عیب‌یابی

## مشکل: فرآیند زامبی (Zombie)
```bash
ps aux | grep Z                 # پیدا کردن زامبی‌ها
ps -o ppid= -p ZOMBIE_PID      # پیدا کردن والد
kill -CHLD PARENT_PID           # سیگنال به والد
# اگر زامبی زیاد است، والد را restart کنید
```

## مشکل: kill -9 کار نمی‌کند
```bash
# بررسی وضعیت فرآیند
ps aux | grep PID
# D state (disk wait) را نمی‌توان kill کرد
# باید منتظر ماند یا سیستم را reboot کرد
cat /proc/PID/status | grep State
```

## مشکل: پردازنده 100% است
```bash
top                             # کدام فرآیند؟
ps aux --sort=-%cpu | head -5
strace -p PID                   # چه کاری می‌کند؟
lsof -p PID                     # چه فایل‌هایی باز کرده؟
```

## مشکل: فرآیند بعد از logout می‌میرد
```bash
nohup command > output.log 2>&1 &
# یا
screen -S mysession
# دستور را اجرا کنید
# Ctrl+A D برای detach
screen -r mysession             # برگشت به session
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]