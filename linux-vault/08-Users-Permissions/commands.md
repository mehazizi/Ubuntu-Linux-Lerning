# فصل ۸ - کاربران و مجوزها | دستورات

## مدیریت کاربران
```bash
adduser username                    # روش تعاملی (توصیه‌شده)
useradd -m -s /bin/bash -G sudo username  # روش اسکریپتی
useradd -m -u 1500 -g developers username # با UID و گروه مشخص
usermod -aG docker username         # اضافه کردن به گروه
usermod -s /bin/zsh username        # تغییر shell
usermod -L username                 # قفل کردن حساب
usermod -U username                 # بازگشایی قفل
userdel username                    # حذف کاربر
userdel -r username                 # حذف با پوشه خانگی
id username                         # اطلاعات کاربر
who                                 # کاربران وارد شده
w                                   # کاربران و کارشان
last                                # تاریخچه ورود
```

## رمز عبور
```bash
passwd username                     # تغییر رمز
passwd -l username                  # قفل رمز
passwd -u username                  # باز کردن قفل
chage -l username                   # اطلاعات انقضای رمز
chage -M 90 username                # انقضا در ۹۰ روز
chage -E 2025-12-31 username        # تاریخ انقضای حساب
```

## مدیریت گروه‌ها
```bash
groupadd devops                     # ساخت گروه
groupmod -n newname devops          # تغییر نام گروه
groupdel devops                     # حذف گروه
groups username                     # گروه‌های کاربر
gpasswd -a user group               # اضافه کردن به گروه
gpasswd -d user group               # حذف از گروه
```

## مجوزها
```bash
chmod 755 file.sh                   # مجوز عددی
chmod u+x file.sh                   # اضافه کردن اجرا برای مالک
chmod g-w file.txt                  # حذف نوشتن از گروه
chmod o=r file.txt                  # فقط خواندن برای دیگران
chmod -R 755 /var/www               # بازگشتی
chown user:group file               # تغییر مالک و گروه
chown -R www-data:www-data /var/www
chgrp developers project/           # فقط تغییر گروه
```

## بیت‌های خاص و umask
```bash
chmod u+s file                      # SUID
chmod g+s directory/                # SGID
chmod +t /tmp                       # Sticky bit
chmod 4755 file                     # SUID + rwxr-xr-x
chmod 1777 /tmp                     # Sticky + rwxrwxrwx
umask                               # مشاهده umask جاری
umask 027                           # تنظیم umask
find / -perm -4000 2>/dev/null      # پیدا کردن فایل‌های SUID
```

## sudo
```bash
sudo command                        # اجرا با دسترسی root
sudo -u otheruser command           # اجرا به‌عنوان کاربر دیگر
sudo -i                             # ورود به root shell
sudo -l                             # لیست مجوزهای sudo
visudo                              # ویرایش امن sudoers
```

## ACL
```bash
getfacl file.txt                    # مشاهده ACL
setfacl -m u:john:rw file.txt       # دسترسی برای کاربر خاص
setfacl -m g:devops:rx dir/         # دسترسی برای گروه
setfacl -x u:john file.txt          # حذف ACL کاربر
setfacl -b file.txt                 # حذف همه ACL
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]