# فصل ۷ - ویرایشگر Vim | دستورات

## باز کردن و خروج
```bash
vim file.txt            # باز کردن فایل
vim +42 file.txt        # باز کردن در خط ۴۲
vim -R file.txt         # فقط خواندنی
vim file1 file2         # چند فایل
vimtutor                # آموزش تعاملی داخلی
```

## Command Mode (:)
```vim
:w                      " ذخیره
:q                      " خروج
:wq   یا  :x  یا  ZZ   " ذخیره و خروج
:q!                     " خروج بدون ذخیره
:w filename             " ذخیره با نام جدید

:set number             " نمایش شماره خط
:set nonumber           " پنهان کردن شماره خط
:set hlsearch           " هایلایت نتایج جستجو
:syntax on              " فعال کردن رنگ‌بندی

:n                      " فایل بعدی
:prev                   " فایل قبلی
:e file.txt             " باز کردن فایل جدید
```

## جستجو و جایگزینی
```vim
/pattern                " جستجوی رو به جلو
?pattern                " جستجوی رو به عقب
n                       " نتیجه بعدی
N                       " نتیجه قبلی

:%s/old/new/g           " جایگزینی در کل فایل
:%s/old/new/gc          " با تأیید هر مورد
:5,10s/old/new/g        " فقط خطوط ۵ تا ۱۰
```

## Visual Mode
```vim
v                       " انتخاب کاراکتری
V                       " انتخاب خطی
Ctrl+v                  " انتخاب بلوکی

" بعد از انتخاب:
d                       " حذف
y                       " کپی
>                       " indent
<                       " outdent
```

## فایل ~/.vimrc
```vim
set number              " شماره خط
set tabstop=4           " عرض tab
set expandtab           " tab به space
set autoindent          " تورفتگی خودکار
set hlsearch            " هایلایت جستجو
set incsearch           " جستجوی تدریجی
syntax on               " رنگ‌بندی
colorscheme desert      " تم رنگی
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]