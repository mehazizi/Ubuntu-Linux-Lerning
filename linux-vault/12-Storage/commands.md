# فصل ۱۲ - ذخیره‌سازی | دستورات

## مشاهده دیسک‌ها
```bash
lsblk                               # نمایش درختی دیسک‌ها
lsblk -f                            # با نوع فایل‌سیستم
blkid                               # UUID و نوع همه پارتیشن‌ها
blkid /dev/sdb1                     # یک پارتیشن
fdisk -l                            # جزئیات همه دیسک‌ها
```

## پارتیشن‌بندی
```bash
sudo fdisk /dev/sdb                 # MBR - ابزار تعاملی
# دستورات fdisk: n=new, d=delete, p=print, t=type, w=write, q=quit

sudo parted /dev/sdb                # GPT - ابزار پیشرفته
sudo parted /dev/sdb mklabel gpt    # ساخت جدول GPT
sudo parted /dev/sdb mkpart primary ext4 1MiB 50GiB
```

## ساخت فایل‌سیستم
```bash
sudo mkfs.ext4 /dev/sdb1
sudo mkfs.ext4 -L "mydata" /dev/sdb1    # با برچسب
sudo mkfs.xfs /dev/sdb1
sudo mkfs.xfs -L "fastdata" /dev/sdb1
sudo mkswap /dev/sdb2               # ساخت swap
sudo swapon /dev/sdb2               # فعال کردن swap
sudo swapoff /dev/sdb2
swapon --show                       # وضعیت swap
```

## مانت
```bash
sudo mount /dev/sdb1 /mnt/data
sudo mount -t ext4 /dev/sdb1 /mnt/data
sudo mount -o ro /dev/sdb1 /mnt/data       # فقط خواندنی
sudo mount -o remount,rw /mnt/data         # تغییر گزینه
sudo umount /mnt/data
sudo umount -l /mnt/data                   # lazy umount
mount | grep sdb                           # مانت‌های فعال
```

## fstab - مانت دائمی
```bash
# پیدا کردن UUID
sudo blkid /dev/sdb1
# ویرایش fstab
sudo nano /etc/fstab
# تست fstab بدون reboot
sudo mount -a
# بررسی خطاها
sudo findmnt --verify
```

## بررسی دیسک
```bash
df -h                               # فضای استفاده‌شده
df -i                               # استفاده inode
du -sh /var/*                       # حجم پوشه‌ها
sudo fsck /dev/sdb1                 # بررسی سلامت (باید unmount باشد)
sudo e2fsck -f /dev/sdb1
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]