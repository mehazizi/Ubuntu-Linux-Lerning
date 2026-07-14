# فصل ۱ - مبانی لینوکس | عیب‌یابی

## مشکل: دستور پیدا نمی‌شود
```
bash: command_name: command not found
```
**دلایل و راه‌حل:**
```bash
# آیا دستور نصب است؟
which command_name
type command_name

# آیا PATH درست است؟
echo $PATH

# پیدا کردن محل دستور
find /usr -name "command_name" 2>/dev/null
```

## مشکل: Permission denied هنگام اجرای اسکریپت
```bash
# اضافه کردن مجوز اجرا
chmod +x script.sh
./script.sh
```

## مشکل: Shell تغییر متغیر را نگه نمی‌دارد
```bash
# اشتباه: فقط در session جاری
MY_VAR="value"

# درست: در فایل پیکربندی ذخیره کنید
echo 'export MY_VAR="value"' >> ~/.bashrc
source ~/.bashrc
```

## مشکل: تاریخچه ذخیره نمی‌شود
```bash
# بررسی تنظیمات
echo $HISTSIZE        # تعداد دستورات در حافظه
echo $HISTFILESIZE    # تعداد دستورات در فایل
echo $HISTFILE        # محل فایل تاریخچه

# ذخیره فوری تاریخچه
history -w
```

## مشکل: man page نمایش داده نمی‌شود
```bash
# نصب man pages
sudo apt install man-db
sudo mandb             # به‌روزرسانی پایگاه داده man
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]
