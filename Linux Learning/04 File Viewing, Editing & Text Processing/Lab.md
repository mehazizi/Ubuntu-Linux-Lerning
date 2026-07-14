# Chapter 04 — Lab Exercises

# هدف آزمایش‌ها

در پایان این آزمایش‌ها باید بتوانید:

- فایل‌های متنی را مشاهده و تحلیل کنید.
    
- فایل‌های متنی را ایجاد و ویرایش کنید.
    
- با Nano و Vim کار کنید.
    
- از Pipe و Redirection استفاده کنید.
    
- متن را جستجو، فیلتر و مرتب کنید.
    
- فایل‌های Log را بررسی کنید.
    

---

# Lab 01 — ساخت فایل متنی

هدف:

ایجاد اولین فایل متنی.

دستورها:

```bash
mkdir -p ~/LinuxLab/Chapter04
```

```bash
cd ~/LinuxLab/Chapter04
```

```bash
touch notes.txt
```

```bash
ls -l
```

تمرین:

مطمئن شوید فایل ایجاد شده است.

---

# Lab 02 — نوشتن داخل فایل

هدف:

کار با Redirection.

دستورها:

```bash
echo "Linux Administrator" > notes.txt
```

```bash
cat notes.txt
```

اکنون:

```bash
echo "Ubuntu Server" >> notes.txt
```

```bash
cat notes.txt
```

سؤالات:

1. تفاوت `>` و `>>` چیست؟
    
2. آیا خط اول حذف شد؟
    

---

# Lab 03 — مشاهده فایل

هدف:

استفاده از ابزارهای مشاهده فایل.

دستورها:

```bash
cat notes.txt
```

```bash
head notes.txt
```

```bash
tail notes.txt
```

```bash
less notes.txt
```

تمرین:

در less کلیدهای زیر را امتحان کنید:

- Space
    
- b
    
- /
    
- n
    
- q
    

---

# Lab 04 — Nano

هدف:

ویرایش فایل با Nano.

دستورها:

```bash
nano notes.txt
```

تمرین:

سه خط جدید اضافه کنید.

سپس:

- ذخیره
    
- خروج
    

دوباره بررسی کنید:

```bash
cat notes.txt
```

---

# Lab 05 — Vim مقدماتی

هدف:

آشنایی با Vim.

دستورها:

```bash
vim vim-test.txt
```

تمرین:

1. وارد Insert Mode شوید.
    
2. سه خط متن بنویسید.
    
3. ذخیره کنید.
    
4. خارج شوید.
    

دوباره بررسی کنید:

```bash
cat vim-test.txt
```

---

# Lab 06 — Redirection

هدف:

ذخیره خروجی دستورات.

دستورها:

```bash
ls -l > files.txt
```

```bash
cat files.txt
```

اکنون:

```bash
pwd >> files.txt
```

```bash
date >> files.txt
```

```bash
cat files.txt
```

سؤال:

چرا از `>>` استفاده کردیم؟

---

# Lab 07 — Pipe

هدف:

درک Pipe.

دستورها:

```bash
history
```

اکنون:

```bash
history | less
```

سپس:

```bash
history | grep apt
```

تمرین:

تعداد دستورهای apt را مشاهده کنید.

---

# Lab 08 — grep

هدف:

جستجوی متن.

ابتدا:

```bash
cat notes.txt
```

اکنون:

```bash
grep Linux notes.txt
```

```bash
grep -i linux notes.txt
```

```bash
grep -n Linux notes.txt
```

```bash
grep Ubuntu notes.txt
```

تمرین:

یک کلمه جدید اضافه کنید و آن را جستجو کنید.

---

# Lab 09 — sort و uniq

هدف:

مرتب‌سازی و حذف خطوط تکراری.

ابتدا:

```bash
nano names.txt
```

محتوا:

```text
Ali
Reza
Ali
Sara
Mehdi
Sara
Ali
```

اکنون:

```bash
sort names.txt
```

```bash
sort names.txt | uniq
```

```bash
sort names.txt | uniq -c
```

سؤال:

چرا قبل از uniq از sort استفاده کردیم؟

---

# Lab 10 — wc

هدف:

شمارش خطوط و کلمات.

دستورها:

```bash
wc notes.txt
```

```bash
wc -l notes.txt
```

```bash
wc -w notes.txt
```

```bash
wc -m notes.txt
```

تمرین:

نتایج را با هم مقایسه کنید.

---

# Lab 11 — cut

هدف:

استخراج ستون‌ها.

دستورها:

```bash
cut -d: -f1 /etc/passwd
```

اکنون:

```bash
cut -d: -f1,3 /etc/passwd
```

تمرین:

بررسی کنید ستون سوم چیست.

---

# Lab 12 — tee

هدف:

نمایش و ذخیره همزمان.

دستورها:

```bash
ls | tee list.txt
```

اکنون:

```bash
cat list.txt
```

سپس:

```bash
pwd | tee -a list.txt
```

```bash
cat list.txt
```

---

# Lab 13 — بررسی Logها

هدف:

مشاهده Log سیستم.

دستورها:

```bash
ls /var/log
```

اکنون:

```bash
less /var/log/syslog
```

یا در صورت وجود:

```bash
less /var/log/auth.log
```

سپس:

```bash
grep ssh /var/log/auth.log
```

اگر فایل وجود نداشت، فقط بررسی کنید چه Logهایی روی سیستم شما موجود هستند.

---

# Lab 14 — ترکیب دستورات

هدف:

استفاده همزمان از چند ابزار.

دستورها:

```bash
cat /etc/passwd | less
```

```bash
cat /etc/passwd | grep bash
```

```bash
cat /etc/passwd | grep bash | wc -l
```

سؤال:

چند کاربر Bash دارند؟

---

# Lab 15 — Mini Challenge

بدون استفاده از اینترنت:

1. یک فایل به نام:
    

```text
linux.txt
```

بسازید.

2. حداقل ۱۰ خط داخل آن بنویسید.
    
3. آن را با Nano ویرایش کنید.
    
4. همان فایل را با Vim باز کنید.
    
5. فقط خطوط شامل Linux را پیدا کنید.
    
6. تعداد خطوط فایل را محاسبه کنید.
    
7. تعداد کلمات فایل را محاسبه کنید.
    
8. خروجی `ls -l` را داخل فایل دیگری ذخیره کنید.
    
9. تاریخ سیستم را به انتهای همان فایل اضافه کنید.
    
10. فایل نهایی را با `less` بررسی کنید.
    

---

# Lab 16 — Challenge واقعی مدیر سیستم

بدون استفاده از Google یا ChatGPT، فقط با استفاده از:

- `man`
    
- `--help`
    

پاسخ این سؤال‌ها را پیدا کنید:

1. چگونه فقط ۵ خط آخر فایل را نمایش دهیم؟
    
2. چگونه grep را بدون حساسیت به حروف اجرا کنیم؟
    
3. چگونه خروجی را به انتهای فایل اضافه کنیم؟
    
4. چگونه هم خروجی را ببینیم و هم داخل فایل ذخیره کنیم؟
    
5. چگونه داخل less جستجو کنیم؟
    

---

# پایان Chapter 04

پس از پایان این فصل باید بتوانید:

✅ فایل‌های متنی را ایجاد، مشاهده و ویرایش کنید.

✅ با Nano به‌صورت کامل کار کنید.

✅ عملیات پایه Vim را انجام دهید.

✅ از Pipe و Redirection به‌درستی استفاده کنید.

✅ متن را با grep، sort، uniq، wc و cut پردازش کنید.

✅ فایل‌های Log را بررسی و تحلیل کنید.

✅ بدون نیاز به ابزارهای گرافیکی، فایل‌های متنی لینوکس را به‌صورت حرفه‌ای مدیریت کنید.