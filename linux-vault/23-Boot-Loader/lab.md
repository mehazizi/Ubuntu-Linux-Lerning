# فصل ۲۳ - بوت‌لودر | آزمایشگاه

## تمرین ۱: بررسی تنظیمات GRUB
```bash
cat /etc/default/grub
cat /proc/cmdline
grep menuentry /boot/grub/grub.cfg | head -10
```

## تمرین ۲: تغییر timeout و به‌روزرسانی
```bash
sudo cp /etc/default/grub /etc/default/grub.bak
sudo sed -i 's/GRUB_TIMEOUT=.*/GRUB_TIMEOUT=3/' /etc/default/grub
cat /etc/default/grub | grep TIMEOUT
sudo update-grub
```

## تمرین ۳: تحلیل زمان بوت
```bash
systemd-analyze
systemd-analyze blame | head -15
systemd-analyze critical-chain
journalctl -b | grep "Startup finished"
```

## سناریوی عیب‌یابی: رمز root را فراموش کرده‌ام
```
۱. ریبوت کنید
۲. در GRUB Shift را نگه دارید
۳. Advanced options → recovery mode
۴. root را انتخاب کنید
۵. mount -o remount,rw /
۶. passwd username
۷. reboot
```

### ✅ چک‌لیست یادگیری
- [ ] فرآیند بوت را توضیح می‌دهم
- [ ] GRUB را پیکربندی کرده‌ام
- [ ] می‌دانم چگونه وارد Recovery Mode شوم

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]