# فصل ۶ - مدیریت بسته | آزمایشگاه

## تمرین ۱: نصب و بررسی بسته
```bash
sudo apt update
sudo apt install tree
tree --version
dpkg -L tree
which tree
apt show tree
```

## تمرین ۲: مدیریت مخازن
```bash
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
apt-cache policy nginx    # از کجا نصب می‌شود؟
```

## تمرین ۳: تاریخچه عملیات apt
```bash
cat /var/log/apt/history.log | tail -50
grep "Install" /var/log/apt/history.log | tail -10
```

## تمرین ۴: یافتن فایل‌های یک بسته
```bash
dpkg -L bash
dpkg -S /bin/ls
```

### ✅ چک‌لیست یادگیری
- [ ] تفاوت apt و dpkg را می‌دانم
- [ ] می‌توانم بسته را نصب، حذف و جستجو کنم
- [ ] مخازن را می‌شناسم
- [ ] می‌دانم وابستگی‌ها چیست

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]