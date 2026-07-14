# فصل ۱۳ - LVM | عیب‌یابی

## مشکل: VG در بوت شناسایی نمی‌شود
```bash
sudo vgscan
sudo vgchange -ay                   # فعال کردن همه VG
sudo lvscan
```

## مشکل: LV پر شده و سرویس crash کرده
```bash
df -h                               # بررسی فضا
sudo lvextend -r -l +100%FREE vg/lv # گسترش فوری
# اگر فضا در VG نیست، دیسک جدید اضافه کنید:
sudo pvcreate /dev/sdc
sudo vgextend vg_name /dev/sdc
sudo lvextend -r -l +100%FREE vg/lv
```

## مشکل: Snapshot پر شده
```bash
sudo lvdisplay lv_snap              # بررسی Data%
# اگر به ۱۰۰% رسید، snapshot معتبر نیست
sudo lvremove lv_snap               # حذف و ساخت مجدد
```

## مشکل: resize2fs خطا می‌دهد
```bash
sudo e2fsck -f /dev/vg/lv          # بررسی فایل‌سیستم اول
sudo resize2fs /dev/vg/lv
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]