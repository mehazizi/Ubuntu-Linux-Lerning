# فصل ۱۵ - لاگ‌ها | آزمایشگاه

## تمرین ۱: کار با journalctl
```bash
journalctl -p err -b | tail -20
journalctl --since "1 hour ago" | wc -l
journalctl -u ssh --since "today"
journalctl --disk-usage
```

## تمرین ۲: تنظیم logrotate سفارشی
```bash
sudo tee /etc/logrotate.d/myapp << 'EOF'
/var/log/myapp/*.log {
    daily
    missingok
    rotate 14
    compress
    delaycompress
    notifempty
    create 0640 www-data adm
}
EOF
sudo logrotate -d /etc/logrotate.d/myapp
```

## تمرین ۳: تحلیل لاگ SSH
```bash
grep "Failed password" /var/log/auth.log |   awk '{print $11}' | sort | uniq -c | sort -rn | head -10
grep "Accepted" /var/log/auth.log | tail -10
```

### ✅ چک‌لیست یادگیری
- [ ] با journalctl لاگ‌های دقیق می‌خوانم
- [ ] logrotate را پیکربندی کرده‌ام
- [ ] لاگ‌های امنیتی را تحلیل کرده‌ام

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]