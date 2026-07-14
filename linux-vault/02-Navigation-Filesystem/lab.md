# فصل ۲ - ناوبری و فایل‌سیستم | آزمایشگاه

## تمرین ۱: کشف ساختار فایل‌سیستم
```bash
ls -la /
ls /etc | head -20
ls /var
du -sh /var/* 2>/dev/null | sort -rh | head -10
```

## تمرین ۲: ناوبری با مسیر مطلق و نسبی
```bash
cd /var/log
pwd
cd ../../etc
pwd
cd ~
pwd
cd -
pwd
```

## تمرین ۳: کار با Wildcards
```bash
ls /etc/*.conf
ls /var/log/*.log
ls /etc/[a-d]*
ls /usr/bin/py*
```

## تمرین ۴: اطلاعات فایل
```bash
stat /etc/passwd
file /bin/bash
file /etc/passwd
tree /etc -L 1
```

### ✅ چک‌لیست یادگیری
- [ ] ساختار FHS را می‌شناسم
- [ ] تفاوت مسیر مطلق و نسبی را می‌دانم
- [ ] Wildcards را در عمل استفاده کرده‌ام
- [ ] دستورات ls، cd، pwd، stat را بلدم

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]