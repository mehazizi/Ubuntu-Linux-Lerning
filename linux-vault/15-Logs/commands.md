# فصل ۱۵ - لاگ‌ها | دستورات

## journalctl
```bash
journalctl                          # همه لاگ‌ها
journalctl -f                       # لاگ زنده
journalctl -u nginx                 # لاگ یک سرویس
journalctl -u nginx -f              # لاگ زنده یک سرویس
journalctl -p err                   # سطح خطا و بالاتر
journalctl -p warning..err          # بین دو سطح
journalctl --since "1 hour ago"
journalctl --since "2024-01-01 00:00" --until "2024-01-02 00:00"
journalctl -b                       # بوت جاری
journalctl -b -1                    # بوت قبلی
journalctl -n 50                    # ۵۰ خط آخر
journalctl --disk-usage
journalctl --vacuum-time=30d
journalctl --vacuum-size=500M
```

## rsyslog
```bash
sudo systemctl status rsyslog
cat /etc/rsyslog.conf
ls /etc/rsyslog.d/
sudo systemctl restart rsyslog
# تست ارسال لاگ:
logger "پیام آزمایشی"
logger -p auth.info "تست احراز هویت"
```

## logrotate
```bash
sudo logrotate -d /etc/logrotate.conf   # شبیه‌سازی
sudo logrotate -f /etc/logrotate.conf   # اجرای اجباری
cat /etc/logrotate.d/nginx              # پیکربندی nginx
```

## جستجو در لاگ
```bash
grep "error" /var/log/syslog | tail -20
grep "Failed password" /var/log/auth.log | awk '{print $11}' | sort | uniq -c | sort -rn
tail -f /var/log/nginx/access.log | grep " 500 "
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]