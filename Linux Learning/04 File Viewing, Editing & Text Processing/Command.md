# Chapter 04 — Commands

# View File Contents

نمایش کل فایل

```bash
cat file.txt
```

---

نمایش فایل همراه با شماره خطوط

```bash
cat -n file.txt
```

---

نمایش فایل همراه با نمایش کاراکترهای خاص

```bash
cat -A file.txt
```

---

نمایش ابتدای فایل

```bash
head file.txt
```

---

نمایش 20 خط اول

```bash
head -20 file.txt
```

---

نمایش انتهای فایل

```bash
tail file.txt
```

---

نمایش 30 خط آخر

```bash
tail -30 file.txt
```

---

نمایش زنده فایل Log

```bash
tail -f /var/log/syslog
```

---

نمایش فایل به صورت صفحه‌ای

```bash
less file.txt
```

کلیدهای مهم داخل less

```
↑ ↓      حرکت
Space    صفحه بعد
b         صفحه قبل
g         ابتدای فایل
G         انتهای فایل
/word     جستجو
n         نتیجه بعدی
N         نتیجه قبلی
q         خروج
```

---

نمایش فایل با more

```bash
more file.txt
```

---

# Create & Write Files

ساخت فایل خالی

```bash
touch file.txt
```

---

نوشتن داخل فایل

```bash
echo "Hello Linux" > file.txt
```

---

اضافه کردن به انتهای فایل

```bash
echo "Second Line" >> file.txt
```

---

ساخت فایل چند خطی

```bash
cat > file.txt
```

پایان ورود متن:

```
Ctrl + D
```

---

# Nano Editor

باز کردن فایل

```bash
nano file.txt
```

---

ساخت فایل جدید

```bash
nano newfile.txt
```

---

کلیدهای مهم Nano

```
Ctrl + O    ذخیره

Ctrl + X    خروج

Ctrl + K    Cut Line

Ctrl + U    Paste

Ctrl + W    Search

Ctrl + G    Help

Ctrl + C    نمایش شماره خط

Ctrl + \    Replace
```

---

# Vim Editor (Basic)

باز کردن فایل

```bash
vim file.txt
```

---

حالت Insert

```
i
```

---

بازگشت به Normal Mode

```
Esc
```

---

ذخیره

```
:w
```

---

خروج

```
:q
```

---

ذخیره و خروج

```
:wq
```

یا

```
ZZ
```

---

خروج بدون ذخیره

```
:q!
```

---

حذف یک خط

```
dd
```

---

کپی یک خط

```
yy
```

---

Paste

```
p
```

---

Undo

```
u
```

---

Redo

```
Ctrl + r
```

---

جستجو

```
/word
```

---

نتیجه بعدی

```
n
```

---

نتیجه قبلی

```
N
```

---

رفتن به ابتدای فایل

```
gg
```

---

رفتن به انتهای فایل

```
G
```

---

# Output Redirection

ذخیره خروجی

```bash
ls > files.txt
```

---

اضافه کردن خروجی

```bash
ls >> files.txt
```

---

نوشتن خروجی خطا

```bash
command 2> error.log
```

---

ذخیره خروجی و خطا

```bash
command > output.log 2>&1
```

---

حذف خروجی

```bash
command > /dev/null
```

---

حذف فقط خطا

```bash
command 2> /dev/null
```

---

حذف خروجی و خطا

```bash
command > /dev/null 2>&1
```

---

# Pipe

اتصال دو دستور

```bash
command1 | command2
```

---

مثال

```bash
ls -l | less
```

---

```bash
cat file.txt | grep Linux
```

---

```bash
history | less
```

---

# grep

جستجوی متن

```bash
grep word file.txt
```

---

بدون حساسیت به حروف

```bash
grep -i word file.txt
```

---

شماره خطوط

```bash
grep -n word file.txt
```

---

جستجوی بازگشتی

```bash
grep -r word /etc
```

---

عدم نمایش خطوط شامل متن

```bash
grep -v word file.txt
```

---

جستجوی چند فایل

```bash
grep word *.conf
```

---

# sort

مرتب‌سازی

```bash
sort file.txt
```

---

مرتب‌سازی معکوس

```bash
sort -r file.txt
```

---

مرتب‌سازی عددی

```bash
sort -n numbers.txt
```

---

# uniq

حذف خطوط تکراری

```bash
uniq file.txt
```

---

شمارش خطوط تکراری

```bash
uniq -c file.txt
```

---

ترکیب با sort

```bash
sort file.txt | uniq
```

---

# wc

تعداد خطوط

```bash
wc -l file.txt
```

---

تعداد کلمات

```bash
wc -w file.txt
```

---

تعداد کاراکترها

```bash
wc -m file.txt
```

---

نمایش همه اطلاعات

```bash
wc file.txt
```

---

# cut

نمایش ستون اول

```bash
cut -d: -f1 /etc/passwd
```

---

نمایش ستون اول و سوم

```bash
cut -d: -f1,3 /etc/passwd
```

---

# tee

نمایش و ذخیره همزمان

```bash
ls | tee files.txt
```

---

اضافه کردن

```bash
ls | tee -a files.txt
```

---

# Log Files

نمایش Log سیستم

```bash
less /var/log/syslog
```

---

مشاهده زنده Log

```bash
tail -f /var/log/syslog
```

---

جستجوی SSH

```bash
grep ssh /var/log/auth.log
```

---

# History

نمایش History

```bash
history
```

---

جستجو در History

```bash
history | grep apt
```

---

# Help

راهنمای Nano

```bash
man nano
```

---

راهنمای Vim

```bash
man vim
```

---

راهنمای grep

```bash
man grep
```

---

راهنمای less

```bash
man less
```

---

راهنمای tail

```bash
man tail
```

---

راهنمای head

```bash
man head
```

---

راهنمای tee

```bash
man tee
```

---

# Best Practice

برای مشاهده فایل‌های بزرگ:

```bash
less file.txt
```

به جای:

```bash
cat file.txt
```

---

برای مانیتورینگ سرویس‌ها:

```bash
tail -f logfile
```

---

برای فیلتر خروجی همیشه از Pipe استفاده کنید:

```bash
command | grep keyword
```

---

قبل از ویرایش فایل‌های مهم:

```bash
cp file.conf file.conf.bak
```

---

برای فایل‌های تنظیماتی ابتدا از **Nano** استفاده کنید و پس از تسلط کامل، کارهای حرفه‌ای‌تر را با **Vim** انجام دهید.

---

برای جلوگیری از حذف ناخواسته اطلاعات:

- از `>>` برای اضافه کردن به فایل استفاده کنید.
    
- از `>` فقط زمانی استفاده کنید که مطمئن هستید می‌خواهید محتوای قبلی فایل جایگزین شود.