# فصل ۱۳ - LVM | آزمایشگاه

## تمرین ۱: راه‌اندازی LVM
```bash
# ساخت دیسک‌های مجازی
sudo dd if=/dev/zero of=/tmp/disk1.img bs=1M count=200
sudo dd if=/dev/zero of=/tmp/disk2.img bs=1M count=200
sudo losetup /dev/loop1 /tmp/disk1.img
sudo losetup /dev/loop2 /tmp/disk2.img

# ساخت PV
sudo pvcreate /dev/loop1 /dev/loop2
sudo pvs

# ساخت VG
sudo vgcreate test_vg /dev/loop1 /dev/loop2
sudo vgs

# ساخت LV
sudo lvcreate -L 100M -n test_lv test_vg
sudo lvs

# ساخت فایل‌سیستم و مانت
sudo mkfs.ext4 /dev/test_vg/test_lv
sudo mkdir /mnt/lvm_test
sudo mount /dev/test_vg/test_lv /mnt/lvm_test
df -h /mnt/lvm_test
```

## تمرین ۲: گسترش LV
```bash
df -h /mnt/lvm_test
sudo lvextend -r -L +50M test_vg/test_lv
df -h /mnt/lvm_test       # فضا افزایش یافت؟
```

## تمرین ۳: پاک‌سازی
```bash
sudo umount /mnt/lvm_test
sudo lvremove test_vg/test_lv
sudo vgremove test_vg
sudo pvremove /dev/loop1 /dev/loop2
sudo losetup -d /dev/loop1 /dev/loop2
sudo rm /tmp/disk1.img /tmp/disk2.img
```

### ✅ چک‌لیست یادگیری
- [ ] معماری PV→VG→LV را می‌فهمم
- [ ] LVM از صفر راه‌اندازی کرده‌ام
- [ ] LV را بدون downtime گسترش داده‌ام
- [ ] Snapshot را می‌شناسم

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]