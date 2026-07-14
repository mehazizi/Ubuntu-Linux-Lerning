# فصل ۱۲ - ذخیره‌سازی | آزمایشگاه

## تمرین ۱: بررسی وضعیت دیسک
```bash
lsblk -f
blkid
df -h
du -sh /var/* 2>/dev/null | sort -rh | head -10
swapon --show
```

## تمرین ۲: اضافه کردن دیسک جدید (شبیه‌سازی با فایل)
```bash
# ساخت دیسک مجازی با فایل
sudo dd if=/dev/zero of=/tmp/virtual_disk.img bs=1M count=100
sudo losetup /dev/loop0 /tmp/virtual_disk.img
lsblk

# پارتیشن‌بندی
sudo fdisk /dev/loop0
# n → p → 1 → Enter → Enter → w

# فرمت
sudo mkfs.ext4 /dev/loop0p1

# مانت
sudo mkdir -p /mnt/virtual
sudo mount /dev/loop0p1 /mnt/virtual
df -h /mnt/virtual

# پاک‌سازی
sudo umount /mnt/virtual
sudo losetup -d /dev/loop0
sudo rm /tmp/virtual_disk.img
```

## تمرین ۳: swap file
```bash
sudo fallocate -l 512M /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
swapon --show
free -h
sudo swapoff /swapfile
sudo rm /swapfile
```

### ✅ چک‌لیست یادگیری
- [ ] تفاوت MBR و GPT را می‌دانم
- [ ] دیسک را پارتیشن‌بندی و فرمت کرده‌ام
- [ ] fstab را پیکربندی کرده‌ام
- [ ] swap را مدیریت کرده‌ام

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]