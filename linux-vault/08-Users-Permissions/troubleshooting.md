# فصل ۸ - کاربران و مجوزها | عیب‌یابی

## مشکل: Permission denied
```bash
ls -la file.txt              # مشاهده مجوزها
id                           # کاربر و گروه‌های جاری
stat file.txt                # اطلاعات کامل
getfacl file.txt             # ACL را هم بررسی کنید
```

## مشکل: sudo کار نمی‌کند
```bash
groups username              # آیا در گروه sudo است؟
sudo -l -U username          # مجوزهای sudo کاربر
cat /etc/sudoers             # فایل پیکربندی
# اضافه کردن به گروه sudo:
sudo usermod -aG sudo username
# کاربر باید logout و login کند
```

## مشکل: کاربر نمی‌تواند به پوشه مشترک بنویسد
```bash
ls -la /shared/              # مجوزهای پوشه
groups user                  # آیا در گروه درست است؟
# اگر تازه به گروه اضافه شده باید دوباره login کند
newgrp groupname             # تغییر گروه بدون logout
```

## مشکل: فایل‌های SUID مشکوک
```bash
find / -perm -4000 -type f 2>/dev/null
# لیست را با لیست پیش‌فرض مقایسه کنید
# هر SUID غیرمنتظره باید بررسی شود
```

## مشکل: رمز عبور منقضی شده
```bash
chage -l username            # بررسی وضعیت
chage -M 99999 username      # غیرفعال کردن انقضا
passwd username              # تنظیم رمز جدید
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]