# فصل ۸ - کاربران و مجوزها | آزمایشگاه

## تمرین ۱: ساخت کاربر و گروه
```bash
sudo groupadd webteam
sudo adduser --ingroup webteam developer1
id developer1
groups developer1
sudo usermod -aG sudo developer1
groups developer1
```

## تمرین ۲: تنظیم مجوز پوشه مشترک
```bash
sudo mkdir /var/www/project
sudo chown root:webteam /var/www/project
sudo chmod 2775 /var/www/project
ls -la /var/www/
# SGID بیت را می‌بینید؟ (drwxrwsr-x)
```

## تمرین ۳: درک umask
```bash
umask
touch testfile
mkdir testdir
ls -la testfile testdir
# مجوزها را با umask مقایسه کنید
umask 077
touch private_file
ls -la private_file
umask 022    # برگشت به حالت عادی
```

## تمرین ۴: ACL پیشرفته
```bash
touch /tmp/shared_doc.txt
setfacl -m u:$USER:rw /tmp/shared_doc.txt
getfacl /tmp/shared_doc.txt
ls -la /tmp/shared_doc.txt   # علامت + را می‌بینید؟
```

## تمرین ۵: بررسی sudo
```bash
sudo -l
sudo cat /etc/shadow | head -3
```

### ✅ چک‌لیست یادگیری
- [ ] ساختار فایل passwd و shadow را می‌فهمم
- [ ] مجوزهای عددی را محاسبه می‌کنم
- [ ] SUID، SGID، Sticky را می‌شناسم
- [ ] ACL را پیکربندی کرده‌ام
- [ ] umask را درک می‌کنم

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]