# فصل ۲۳ - بوت‌لودر | خلاصه

## فرآیند بوت
```
روشن شدن → BIOS/UEFI → GRUB → Kernel → initramfs → systemd → Login
```

## GRUB چیست؟
Grand Unified Bootloader - بوت‌لودر پیش‌فرض لینوکس که اجازه می‌دهد هسته انتخاب شود.

## فایل‌های مهم GRUB
| فایل | کاربرد |
|------|---------|
| `/etc/default/grub` | تنظیمات اصلی GRUB |
| `/etc/grub.d/` | اسکریپت‌های تولید پیکربندی |
| `/boot/grub/grub.cfg` | فایل نهایی (ویرایش نکنید) |

## پارامترهای مهم /etc/default/grub
| پارامتر | کاربرد |
|---------|---------|
| `GRUB_TIMEOUT` | زمان انتظار منو |
| `GRUB_DEFAULT` | ورودی پیش‌فرض |
| `GRUB_CMDLINE_LINUX` | پارامترهای هسته |
| `GRUB_DISABLE_RECOVERY` | مخفی کردن recovery |

## پارامترهای هسته رایج
| پارامتر | کاربرد |
|---------|---------|
| `quiet splash` | بوت بی‌سر و صدا |
| `nomodeset` | غیرفعال کردن KMS |
| `ro` / `rw` | فایل‌سیستم فقط‌خواندنی/خواندنی‌نوشتنی |
| `single` | حالت تک‌کاربره |

---
[[commands|← دستورات]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]