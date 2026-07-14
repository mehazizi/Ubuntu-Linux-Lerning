# فصل ۱۴ - RAID | دستورات

## ساخت RAID
```bash
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb /dev/sdc
sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb /dev/sdc /dev/sdd
sudo mdadm --create /dev/md0 --level=10 --raid-devices=4 /dev/sdb /dev/sdc /dev/sdd /dev/sde
```

## بررسی وضعیت
```bash
cat /proc/mdstat                    # وضعیت RAID
sudo mdadm --detail /dev/md0        # جزئیات کامل
sudo mdadm --query /dev/sdb         # وضعیت یک دیسک
watch cat /proc/mdstat              # نظارت زنده
```

## مدیریت
```bash
sudo mdadm --stop /dev/md0          # توقف RAID
sudo mdadm --assemble /dev/md0 /dev/sdb /dev/sdc  # راه‌اندازی مجدد
sudo mdadm --fail /dev/md0 /dev/sdc     # علامت‌گذاری خراب
sudo mdadm --remove /dev/md0 /dev/sdc   # حذف دیسک خراب
sudo mdadm --add /dev/md0 /dev/sde      # اضافه کردن دیسک جدید
```

## پیکربندی دائمی
```bash
sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf
sudo update-initramfs -u
```

## بازیابی
```bash
sudo mdadm --examine /dev/sdb       # بررسی دیسک
sudo mdadm --assemble --scan        # یافتن و راه‌اندازی خودکار
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]