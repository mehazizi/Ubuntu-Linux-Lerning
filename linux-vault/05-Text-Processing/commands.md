# فصل ۵ - پردازش متن | دستورات

## grep
```bash
grep "error" /var/log/syslog        # جستجوی ساده
grep -i "ERROR" file.txt            # بدون حساسیت به بزرگی
grep -r "config" /etc/              # جستجوی بازگشتی
grep -n "pattern" file.txt          # با شماره خط
grep -v "comment" file.txt          # خطوطی که pattern ندارند
grep -c "error" file.txt            # تعداد تطابق
grep -l "error" /var/log/*.log      # فقط نام فایل‌ها
grep -E "err|warn|crit" syslog      # regex پیشرفته (مثل egrep)
grep -A 2 -B 2 "error" file.txt    # ۲ خط قبل و بعد
```

## cut، sort، uniq، wc
```bash
cut -d: -f1 /etc/passwd             # ستون اول با جداکننده :
cut -d, -f1,3 data.csv              # ستون ۱ و ۳
cut -c1-10 file.txt                 # کاراکترهای ۱ تا ۱۰

sort file.txt                       # مرتب‌سازی الفبایی
sort -n numbers.txt                 # مرتب‌سازی عددی
sort -r file.txt                    # معکوس
sort -t: -k3 -n /etc/passwd         # بر اساس ستون ۳

uniq file.txt                       # حذف خطوط تکراری متوالی
uniq -c file.txt                    # شمارش هر خط
uniq -d file.txt                    # فقط تکراری‌ها

wc file.txt                         # خط، کلمه، بایت
wc -l file.txt                      # فقط خط
wc -w file.txt                      # فقط کلمه
```

## tr، tee، xargs، paste
```bash
tr 'a-z' 'A-Z' < file.txt          # تبدیل به بزرگ
tr -d '' < win_file.txt           # حذف carriage return
echo "hello world" | tr ' ' '
'   # فضا به خط جدید

ls /etc/*.conf | tee file_list.txt  # ذخیره و نمایش همزمان

find /tmp -name "*.log" | xargs rm  # حذف فایل‌های یافت‌شده
cat list.txt | xargs -I{} mkdir {}  # ساخت پوشه از لیست

paste file1.txt file2.txt           # ادغام ستونی
paste -d, file1.txt file2.txt       # با جداکننده ,
```

## sed و awk مقدماتی
```bash
sed 's/old/new/' file.txt           # جایگزینی اول هر خط
sed 's/old/new/g' file.txt          # جایگزینی همه
sed -i 's/old/new/g' file.txt       # ویرایش درجا
sed -n '5,10p' file.txt             # نمایش خطوط ۵ تا ۱۰
sed '/^#/d' file.txt                # حذف خطوط کامنت

awk '{print $1}' file.txt           # ستون اول
awk -F: '{print $1,$3}' /etc/passwd # با جداکننده :
awk '{sum += $1} END {print sum}'   # جمع ستون
awk 'NR>1 && $3>100' data.txt       # فیلتر شرطی
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]