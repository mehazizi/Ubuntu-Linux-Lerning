# فصل ۱۰ - مدیریت فرآیندها | دستورات

## مشاهده فرآیندها
```bash
ps aux                          # همه فرآیندها
ps aux --sort=-%cpu | head      # مرتب بر اساس CPU
ps aux --sort=-%mem | head      # مرتب بر اساس حافظه
ps -ef                          # نمایش PPID
ps -u username                  # فرآیندهای یک کاربر
pstree                          # نمایش درختی
pstree -p                       # با PID
top                             # نمایش پویا
htop                            # نمایش پویای پیشرفته
```

## جستجوی فرآیند
```bash
pgrep nginx                     # PID فرآیندهای nginx
pgrep -u www-data               # فرآیندهای یک کاربر
pgrep -a nginx                  # با نام کامل
pidof nginx                     # PID برنامه
```

## مدیریت پیش/پس‌زمینه
```bash
command &                       # اجرا در پس‌زمینه
jobs                            # لیست کارهای جاری
fg %1                           # آوردن به پیش‌زمینه
bg %1                           # ادامه در پس‌زمینه
Ctrl+Z                          # توقف و رفتن به پس‌زمینه
Ctrl+C                          # لغو فرآیند پیش‌زمینه
nohup command &                 # ادامه بعد از logout
disown %1                       # جدا کردن از ترمینال
```

## ارسال سیگنال
```bash
kill PID                        # SIGTERM (15)
kill -9 PID                     # SIGKILL - اجباری
kill -1 PID                     # SIGHUP - reload
kill -15 PID                    # SIGTERM - درخواست خاتمه
pkill nginx                     # بر اساس نام
pkill -9 -u baduser             # همه فرآیندهای یک کاربر
killall nginx                   # همه فرآیندهای nginx
```

## Nice و اولویت
```bash
nice -n 10 command              # اجرا با اولویت 10
nice -n -5 command              # اولویت بالا (نیاز به sudo)
renice -n 5 -p PID             # تغییر اولویت فرآیند
renice -n 10 -u username        # تغییر اولویت همه فرآیندهای کاربر
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]