# فصل ۲۰ - Bash Scripting | عیب‌یابی

## مشکل: اسکریپت اجرا نمی‌شود
```bash
chmod +x script.sh
bash -n script.sh              # بررسی syntax بدون اجرا
bash -x script.sh              # اجرا با نمایش هر خط
```

## مشکل: متغیر خالی است
```bash
set -u                         # خطا برای متغیر تعریف‌نشده
echo "${VAR:-default_value}"   # مقدار پیش‌فرض اگر خالی بود
```

## مشکل: اسکریپت در cron کار نمی‌کند
```bash
# در ابتدای اسکریپت PATH را تنظیم کنید:
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
# لاگ خطاها را بررسی کنید:
* * * * * /path/script.sh >> /tmp/cron.log 2>&1
```

## مشکل: خطای Windows line endings
```bash
file script.sh                 # آیا CRLF دارد؟
dos2unix script.sh             # تبدیل به Unix
sed -i 's///' script.sh     # جایگزین دستی
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]