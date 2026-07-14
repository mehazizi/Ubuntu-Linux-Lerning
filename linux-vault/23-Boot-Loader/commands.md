# فصل ۲۳ - بوت‌لودر | دستورات

## مدیریت GRUB
```bash
cat /etc/default/grub           # مشاهده تنظیمات
sudo nano /etc/default/grub     # ویرایش تنظیمات
sudo update-grub                # به‌روزرسانی grub.cfg
sudo grub-install /dev/sda      # نصب مجدد GRUB روی دیسک
```

## بررسی ورودی‌های GRUB
```bash
grep -i "menuentry" /boot/grub/grub.cfg    # لیست ورودی‌ها
awk -F' '/menuentry / {print $2}' /boot/grub/grub.cfg
```

## پارامترهای هسته جاری
```bash
cat /proc/cmdline               # پارامترهای بوت جاری
```

## Recovery Mode
```
۱. در هنگام بوت Shift را نگه دارید
۲. در GRUB گزینه "Advanced options" را انتخاب کنید
۳. "(recovery mode)" را انتخاب کنید
۴. در منو:
   - root: دسترسی به shell
   - fsck: بررسی فایل‌سیستم
   - network: فعال کردن شبکه
```

## دستورات در Recovery Shell
```bash
mount -o remount,rw /           # مانت خواندنی-نوشتنی
passwd username                 # تغییر رمز عبور
fsck -y /dev/sda1               # بررسی و اصلاح فایل‌سیستم
dpkg --configure -a             # پیکربندی بسته‌های ناتمام
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]