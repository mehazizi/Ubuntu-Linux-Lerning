# فصل ۱۴ - RAID | آزمایشگاه

## تمرین ۱: ساخت RAID 1
```bash
# ساخت دیسک‌های مجازی
sudo dd if=/dev/zero of=/tmp/raid1.img bs=1M count=100
sudo dd if=/dev/zero of=/tmp/raid2.img bs=1M count=100
sudo losetup /dev/loop3 /tmp/raid1.img
sudo losetup /dev/loop4 /tmp/raid2.img

# ساخت RAID 1
sudo mdadm --create /dev/md1 --level=1 --raid-devices=2 /dev/loop3 /dev/loop4

# بررسی
cat /proc/mdstat
sudo mdadm --detail /dev/md1

# فرمت و مانت
sudo mkfs.ext4 /dev/md1
sudo mkdir /mnt/raid_test
sudo mount /dev/md1 /mnt/raid_test
```

## تمرین ۲: شبیه‌سازی خرابی دیسک
```bash
sudo mdadm --fail /dev/md1 /dev/loop3
cat /proc/mdstat                    # یک دیسک failed
sudo mdadm --remove /dev/md1 /dev/loop3
sudo mdadm --add /dev/md1 /dev/loop3  # اضافه مجدد
watch cat /proc/mdstat              # بررسی rebuild
```

## تمرین ۳: پاک‌سازی
```bash
sudo umount /mnt/raid_test
sudo mdadm --stop /dev/md1
sudo losetup -d /dev/loop3 /dev/loop4
sudo rm /tmp/raid1.img /tmp/raid2.img
```

### ✅ چک‌لیست یادگیری
- [ ] تفاوت سطوح RAID را می‌دانم
- [ ] RAID نرم‌افزاری ساخته‌ام
- [ ] شکست دیسک را شبیه‌سازی و بازیابی کرده‌ام

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]