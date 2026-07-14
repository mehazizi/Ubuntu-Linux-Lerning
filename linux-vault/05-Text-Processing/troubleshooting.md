# فصل ۵ - پردازش متن | عیب‌یابی

## مشکل: grep نتیجه نمی‌دهد
```bash
# آیا فایل وجود دارد؟
ls -la file.txt
# آیا pattern درست است؟
grep -i "pattern" file.txt   # بدون حساسیت به حروف
# آیا فایل خالی است؟
wc -l file.txt
```

## مشکل: sed تغییری ایجاد نمی‌کند
```bash
# تست بدون -i اول
sed 's/old/new/g' file.txt
# اگر نتیجه درست بود، با -i اعمال کنید
sed -i.bak 's/old/new/g' file.txt   # با پشتیبان
```

## مشکل: خروجی pipe نادرست است
```bash
# هر مرحله را جداگانه آزمایش کنید
cat file.txt | head -5
cat file.txt | grep "pattern" | head -5
cat file.txt | grep "pattern" | sort | head -5
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]