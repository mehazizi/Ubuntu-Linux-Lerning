# فصل ۱۱ - Systemd و سرویس‌ها | عیب‌یابی

## مشکل: سرویس start نمی‌شود
```bash
sudo systemctl status service-name
journalctl -u service-name -n 50
journalctl -u service-name --since "5 min ago"
# بررسی مسیر ExecStart
which app_name
ls -la /path/to/app
```

## مشکل: سرویس بعد از بوت بالا نمی‌آید
```bash
systemctl is-enabled service-name
sudo systemctl enable service-name
# بررسی وابستگی‌ها
systemctl list-dependencies service-name
```

## مشکل: تغییر فایل .service اعمال نمی‌شود
```bash
sudo systemctl daemon-reload
sudo systemctl restart service-name
```

## مشکل: journalctl فضا زیادی گرفته
```bash
journalctl --disk-usage
sudo journalctl --vacuum-size=500M
sudo journalctl --vacuum-time=30d
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]