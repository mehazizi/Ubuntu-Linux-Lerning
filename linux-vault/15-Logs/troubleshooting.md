# فصل ۱۵ - لاگ‌ها | عیب‌یابی

## مشکل: /var/log پر شده
```bash
df -h /var/log
du -sh /var/log/* | sort -rh | head -10
sudo journalctl --vacuum-size=200M
sudo logrotate -f /etc/logrotate.conf
find /var/log -name "*.gz" -mtime +30 -delete
```

## مشکل: journald لاگ ذخیره نمی‌کند
```bash
sudo systemctl status systemd-journald
cat /etc/systemd/journald.conf | grep Storage
# Storage=persistent را تنظیم کنید
sudo mkdir -p /var/log/journal
sudo systemd-tmpfiles --create --prefix /var/log/journal
sudo systemctl restart systemd-journald
```

## مشکل: لاگ‌ها خیلی سریع چرخش می‌کنند
```bash
cat /etc/logrotate.d/service_name
# daily را به weekly تغییر دهید
# rotate را افزایش دهید
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]