# فصل ۴ - مشاهده و ویرایش فایل‌ها | عیب‌یابی

## مشکل: فایل باینری با cat خروجی عجیب دارد
```bash
# از strings استفاده کنید
strings binary_file | head -30
# یا از xxd برای hex dump
xxd binary_file | head -20
```

## مشکل: tail -f آپدیت نمی‌شود
```bash
# برخی ابزارها فایل را می‌بندند و دوباره می‌سازند
tail -F logfile.log   # با F بزرگ، فایل جدید را هم دنبال می‌کند
```

## مشکل: nano فایل را ذخیره نمی‌کند
```bash
# بررسی مجوز نوشتن
ls -la file.txt
# اگر مجوز ندارید:
sudo nano file.txt
```

## مشکل: فایل خط جدید ندارد (no newline at end)
```bash
cat -A file.txt   # $ در آخر هر خط نشان‌دهنده newline است
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]