# فصل ۱۶ - زمان‌بندی وظایف | عیب‌یابی

## مشکل: cron اجرا نمی‌شود
```bash
sudo systemctl status cron
grep CRON /var/log/syslog | tail -20
# بررسی لاگ خطا
# اطمینان از مسیر کامل در crontab (نه PATH نسبی)
# ✗ اشتباه: backup.sh
# ✓ درست: /opt/backup.sh
```

## مشکل: اسکریپت دستی کار می‌کند اما cron نه
```bash
# محیط cron محدود است، PATH را در اسکریپت تنظیم کنید:
#!/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
# ... ادامه اسکریپت
```

## مشکل: cron دو بار اجرا می‌شود
```bash
# بررسی crontab کاربر و /etc/cron.d/
crontab -l
ls /etc/cron.d/
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]