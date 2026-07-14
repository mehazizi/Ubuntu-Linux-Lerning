# فصل ۲۳ - بوت‌لودر | عیب‌یابی

## مشکل: GRUB Rescue prompt
```bash
# در grub rescue:
ls                              # لیست دیسک‌ها
ls (hd0,1)/                     # محتوای پارتیشن
set root=(hd0,1)
set prefix=(hd0,1)/boot/grub
insmod normal
normal
# بعد از بوت:
sudo update-grub
sudo grub-install /dev/sda
```

## مشکل: سیستم فایل‌سیستم خراب شده
```
در Recovery Mode:
fsck -y /dev/sda1
reboot
```

## مشکل: بعد از تغییر grub سیستم بوت نمی‌کند
```
در Recovery Mode:
mount -o remount,rw /
cp /etc/default/grub.bak /etc/default/grub
update-grub
reboot
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]