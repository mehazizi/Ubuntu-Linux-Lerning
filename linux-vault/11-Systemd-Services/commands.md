# فصل ۱۱ - Systemd و سرویس‌ها | دستورات

## مدیریت سرویس
```bash
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx
sudo systemctl reload nginx         # بدون قطع اتصال
sudo systemctl status nginx
sudo systemctl enable nginx         # فعال در بوت
sudo systemctl disable nginx
sudo systemctl enable --now nginx   # فعال + راه‌اندازی
sudo systemctl is-active nginx
sudo systemctl is-enabled nginx
```

## بررسی سیستم
```bash
systemctl list-units --type=service
systemctl list-units --failed
systemctl list-unit-files --type=service
systemctl list-dependencies nginx
systemctl show nginx                # همه مشخصات
sudo systemctl daemon-reload        # بعد از تغییر فایل .service
```

## Journal - مشاهده لاگ
```bash
journalctl                          # همه لاگ‌ها
journalctl -u nginx                 # لاگ یک سرویس
journalctl -u nginx -f              # لاگ زنده
journalctl -u nginx --since "1h ago"
journalctl -u nginx --since "2024-01-01" --until "2024-01-02"
journalctl -p err                   # فقط خطاها
journalctl -p warning               # هشدار و بالاتر
journalctl -b                       # بوت جاری
journalctl -b -1                    # بوت قبلی
journalctl --disk-usage
journalctl --vacuum-time=30d        # حذف لاگ‌های قدیمی
```

## تحلیل زمان بوت
```bash
systemd-analyze                     # زمان کل بوت
systemd-analyze blame               # کندترین سرویس‌ها
systemd-analyze critical-chain      # زنجیره بحرانی
systemd-analyze plot > boot.svg     # نمودار بوت
```

## Timer
```bash
systemctl list-timers               # لیست همه تایمرها
systemctl list-timers --all
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]