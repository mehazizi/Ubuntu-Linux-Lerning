# فصل ۱۲ - ذخیره‌سازی | خلاصه

## مفاهیم پایه
- **Block Device**: دستگاه ذخیره‌سازی (sda، nvme0n1)
- **Partition**: بخش منطقی دیسک
- **Filesystem**: ساختار ذخیره داده روی پارتیشن
- **Mount Point**: نقطه اتصال فایل‌سیستم به درخت
- **UUID**: شناسه منحصربه‌فرد پارتیشن

## جدول پارتیشن
| نوع | محدودیت | توضیح |
|-----|---------|-------|
| MBR | حداکثر ۴ پارتیشن اصلی، دیسک تا ۲TB | قدیمی |
| GPT | تا ۱۲۸ پارتیشن، دیسک نامحدود | مدرن |

## فایل‌سیستم‌های رایج
| نوع | کاربرد |
|-----|---------|
| ext4 | پیش‌فرض لینوکس |
| xfs | کارایی بالا، فایل‌های بزرگ |
| btrfs | snapshot، RAID داخلی |
| swap | حافظه مجازی |

## ساختار /etc/fstab
```
UUID=xxx  /mount/point  fstype  options  dump  pass
UUID=abc  /             ext4    defaults  0     1
UUID=def  /boot/efi     vfat    umask=0077  0   1
/dev/sdb1 /data         xfs     defaults  0     2
```

---
[[commands|← دستورات]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]