# فصل ۲۲ - مدیریت هسته | عیب‌یابی

## مشکل: ماژول بارگذاری نمی‌شود
```bash
dmesg | tail -20                # خطای هسته
modinfo module_name             # آیا موجود است؟
sudo apt install linux-modules-extra-$(uname -r)
```

## مشکل: بعد از به‌روزرسانی هسته، سرویسی کار نمی‌کند
```bash
uname -r                        # نسخه هسته جاری
dmesg | grep -i "error\|fail"   # خطاهای هسته
# اگر مشکل از driver است:
sudo apt install linux-modules-extra-$(uname -r)
```

## مشکل: هسته قدیمی می‌خواهم boot کنم
```
در هنگام بوت Shift را نگه دارید
در منوی GRUB گزینه Advanced را انتخاب کنید
هسته مورد نظر را انتخاب کنید
```

## مشکل: /boot پر شده
```bash
df -h /boot
dpkg --list | grep linux-image  # هسته‌های نصب‌شده
sudo apt autoremove --purge     # حذف هسته‌های قدیمی
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]