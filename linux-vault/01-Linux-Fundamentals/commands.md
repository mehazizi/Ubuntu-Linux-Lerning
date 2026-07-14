# فصل ۱ - مبانی لینوکس | دستورات

## سیستم راهنما
```bash
man ls                  # راهنمای کامل دستور ls
man -k search_term      # جستجو در همه man pageها
info bash               # راهنمای info (مفصل‌تر از man)
whatis ls               # توضیح یک‌خطی دستور
apropos keyword         # جستجوی دستورات مرتبط با کلمه کلیدی
```

## اطلاعات سیستم
```bash
uname -a                # اطلاعات کامل هسته و سیستم
uname -r                # فقط نسخه هسته
uname -m                # معماری (x86_64 و ...)
hostnamectl             # اطلاعات هاست و سیستم‌عامل
lsb_release -a          # اطلاعات توزیع
cat /etc/os-release     # اطلاعات توزیع از فایل
```

## Shell و محیط
```bash
echo $SHELL             # Shell جاری
echo $PATH              # مسیرهای جستجوی دستور
env                     # همه متغیرهای محیطی
printenv HOME           # مقدار یک متغیر خاص
export MY_VAR="value"   # تعریف متغیر محیطی
echo $?                 # exit status آخرین دستور
```

## تاریخچه و میانبرها
```bash
history                 # لیست دستورات قبلی
history 20              # ۲۰ دستور آخر
!42                     # اجرای دستور شماره ۴۲
!!                      # اجرای آخرین دستور
!ls                     # آخرین دستوری که با ls شروع شد
Ctrl+R                  # جستجوی معکوس در تاریخچه
Ctrl+C                  # لغو دستور جاری
Ctrl+D                  # خروج از Shell
Ctrl+L                  # پاک کردن صفحه
Tab                     # تکمیل خودکار
```

## متغیرهای محیطی
```bash
echo $HOME              # پوشه خانگی
echo $USER              # نام کاربر
echo $PWD               # پوشه جاری
echo $OLDPWD            # پوشه قبلی
echo $HOSTNAME          # نام هاست
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]
