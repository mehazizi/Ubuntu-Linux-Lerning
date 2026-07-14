# فصل ۱۶ - زمان‌بندی وظایف | دستورات

## crontab
```bash
crontab -e                          # ویرایش crontab کاربر جاری
crontab -l                          # نمایش crontab
crontab -r                          # حذف crontab
sudo crontab -e -u username         # crontab یک کاربر
sudo crontab -l -u username
ls /etc/cron.d/                     # cron‌های سیستمی
```

## نمونه‌های crontab
```bash
# پشتیبان‌گیری هر شب ساعت ۲
0 2 * * * /opt/backup.sh >> /var/log/backup.log 2>&1

# به‌روزرسانی هر یکشنبه
0 3 * * 0 apt update && apt upgrade -y >> /var/log/apt-auto.log 2>&1

# بررسی سلامت هر ۵ دقیقه
*/5 * * * * /opt/health_check.sh

# پاک‌سازی tmp هر روز
0 4 * * * find /tmp -type f -atime +7 -delete
```

## systemd timer
```bash
systemctl list-timers               # لیست تایمرها
systemctl list-timers --all
# ساخت تایمر (فصل ۱۱ را ببینید)
```

## at - اجرای یک‌بار
```bash
sudo apt install at
at 22:00                            # ورودی تعاملی
at now + 1 hour
at midnight
at 02:00 tomorrow
echo "command" | at 10:00

atq                                 # لیست صف at
atrm 1                              # حذف job شماره ۱
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]