# فصل ۴ - مشاهده و ویرایش فایل‌ها | دستورات

## مشاهده فایل
```bash
cat file.txt                # نمایش کامل
cat -n file.txt             # با شماره خط
cat -A file.txt             # نمایش کاراکترهای مخفی
cat file1 file2             # نمایش چند فایل پشت هم

less /var/log/syslog        # مشاهده فایل بزرگ
less +F /var/log/syslog     # مثل tail -f

head file.txt               # ۱۰ خط اول
head -n 20 file.txt         # ۲۰ خط اول
head -c 100 file.txt        # ۱۰۰ بایت اول

tail file.txt               # ۱۰ خط آخر
tail -n 50 file.txt         # ۵۰ خط آخر
tail -f /var/log/syslog     # دنبال‌کردن زنده
tail -f /var/log/nginx/access.log

nl file.txt                 # نمایش با شماره خط
tac file.txt                # نمایش معکوس
strings /bin/ls | head      # رشته‌های قابل خواندن
```

## ویرایش با nano
```bash
nano file.txt               # باز کردن فایل
nano +10 file.txt           # رفتن به خط ۱۰
nano -l file.txt            # نمایش شماره خط

# کلیدهای مهم nano:
# Ctrl+O  → ذخیره
# Ctrl+X  → خروج
# Ctrl+K  → برش خط
# Ctrl+U  → چسباندن
# Ctrl+W  → جستجو
# Ctrl+\  → جستجو و جایگزینی
# Ctrl+G  → راهنما
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]