# فصل ۱۱ - Systemd و سرویس‌ها | خلاصه

## Systemd چیست؟
اولین فرآیند سیستم (PID 1) که مسئول راه‌اندازی و مدیریت همه سرویس‌هاست.

## انواع Unit
| نوع | پسوند | کاربرد |
|-----|-------|---------|
| Service | .service | سرویس‌های معمول |
| Timer | .timer | زمان‌بندی (جایگزین cron) |
| Socket | .socket | سوکت‌محور |
| Target | .target | گروه‌بندی unit‌ها |
| Mount | .mount | مانت فایل‌سیستم |

## فرآیند بوت با Systemd
```
BIOS/UEFI → Bootloader → Kernel → initramfs → systemd → Targets → Login
```

## Target‌های مهم
| Target | معادل Runlevel |
|--------|---------------|
| poweroff.target | 0 |
| rescue.target | 1 |
| multi-user.target | 3 |
| graphical.target | 5 |
| reboot.target | 6 |

## ساختار فایل .service
```ini
[Unit]
Description=توضیح سرویس
After=network.target

[Service]
Type=simple
User=www-data
ExecStart=/usr/bin/app
Restart=on-failure
RestartSec=5

[Install]
WantedBy=multi-user.target
```

---
[[commands|← دستورات]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]