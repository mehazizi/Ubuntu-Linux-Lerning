# فصل ۱۲ - ذخیره‌سازی | عیب‌یابی

## مشکل: دیسک پر شده
```bash
df -h
du -h / 2>/dev/null | sort -rh | head -20
find / -size +500M -type f 2>/dev/null
journalctl --disk-usage
sudo journalctl --vacuum-time=7d
sudo apt clean
```

## مشکل: mount نمی‌شود
```bash
lsblk -f                            # بررسی فایل‌سیستم
sudo fsck /dev/sdb1                 # بررسی سلامت
dmesg | tail -20                    # خطاهای هسته
```

## مشکل: سیستم boot نمی‌شود (fstab اشتباه)
```
در recovery mode:
mount -o remount,rw /
nano /etc/fstab    # اصلاح خطا
mount -a           # تست
reboot
```

## مشکل: inode تمام شده
```bash
df -i                               # بررسی inode
find / -xdev -printf '%h
' 2>/dev/null | sort | uniq -c | sort -rn | head
# پیدا کردن پوشه با فایل‌های زیاد
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]