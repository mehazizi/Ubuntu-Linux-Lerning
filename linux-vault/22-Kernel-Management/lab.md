# فصل ۲۲ - مدیریت هسته | آزمایشگاه

## تمرین ۱: بررسی هسته و ماژول‌ها
```bash
uname -a
lsmod | wc -l               # چند ماژول بارگذاری شده؟
lsmod | head -10
modinfo ext4                # اطلاعات ماژول ext4
```

## تمرین ۲: تنظیم sysctl
```bash
# مشاهده مقادیر فعلی
sysctl vm.swappiness
sysctl net.ipv4.ip_forward
sysctl fs.file-max

# تغییر موقت
sudo sysctl vm.swappiness=20
sysctl vm.swappiness          # تأیید

# تغییر دائمی
sudo tee /etc/sysctl.d/99-custom.conf << 'EOF'
vm.swappiness = 10
net.core.somaxconn = 65535
fs.file-max = 100000
EOF
sudo sysctl -p /etc/sysctl.d/99-custom.conf
```

## تمرین ۳: بررسی هسته‌های نصب‌شده
```bash
dpkg --list | grep linux-image
dpkg --list | grep linux-headers
ls /boot/
```

### ✅ چک‌لیست یادگیری
- [ ] ماژول‌های هسته را بررسی می‌کنم
- [ ] پارامترهای sysctl را تنظیم کرده‌ام
- [ ] می‌دانم چگونه هسته را به‌روز کنم

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]