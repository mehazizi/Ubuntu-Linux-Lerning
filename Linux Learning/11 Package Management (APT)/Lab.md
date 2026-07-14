# Chapter 11 - Lab Exercises

## Lab 1

Repositoryهای سیستم را بررسی کن.

cat /etc/apt/sources.list

---

## Lab 2

Repositoryهای اضافه را بررسی کن.

ls /etc/apt/sources.list.d/

---

## Lab 3

Packageهای قابل Upgrade را مشاهده کن.

apt list --upgradable

---

## Lab 4

اطلاعات Package مربوط به nmap را مشاهده کن.

apt show nmap

---

## Lab 5

Dependencyهای curl را بررسی کن.

apt depends curl

---

## Lab 6

Reverse Dependency مربوط به nginx را مشاهده کن.

apt rdepends nginx

---

## Lab 7

Packageهای nginx را جستجو کن.

apt search ^nginx

---

## Lab 8

بررسی کن فایل /bin/ls متعلق به کدام Package است.

dpkg -S /bin/ls

---

## Lab 9

تمام فایل‌های Package مربوط به coreutils را مشاهده کن.

dpkg -L coreutils

---

## Lab 10

لیست تمام Packageهای نصب شده را مشاهده کن.

dpkg -l

---

## Lab 11

بررسی کن آیا htop نصب است یا خیر.

dpkg -l | grep htop

---

## Lab 12

محل فایل اجرایی ls را پیدا کن.

which ls

---

## Lab 13

تمام مسیرهای اجرای ls را مشاهده کن.

type -a ls

---

## Lab 14

یک نصب آزمایشی انجام بده.

sudo apt install --dry-run nmap

خروجی را تحلیل کن.

---

## Lab 15

Cache را بررسی کن.

ls /var/cache/apt/archives/

سپس:

sudo apt clean

و دوباره محتویات پوشه را بررسی کن.

---

## Lab 16

فرض کن فایل زیر روی فلش قرار دارد.

/media/mehdi/KINGSTON/vscode.deb

دستور صحیح نصب آن را بنویس.

sudo apt install /media/mehdi/KINGSTON/vscode.deb

---

## Lab 17

تفاوت remove و purge را به صورت عملی بررسی کن.

---

## Lab 18

بعد از حذف یک Package، autoremove را اجرا کن و نتیجه را بررسی کن.

---

## Lab 19

یک نسخه پشتیبان از فایل sources.list تهیه کن.

---

## Lab 20

توضیح بده تفاوت دستورات زیر چیست.

apt install nginx

apt install ./nginx.deb