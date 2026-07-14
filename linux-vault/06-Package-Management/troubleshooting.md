# فصل ۶ - مدیریت بسته | عیب‌یابی

## مشکل: dpkg lock
```
E: Could not get lock /var/lib/dpkg/lock
```
```bash
sudo rm /var/lib/dpkg/lock-frontend
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a
sudo apt install -f
```

## مشکل: وابستگی‌های مشکل‌دار
```bash
sudo apt install -f           # رفع خودکار
sudo dpkg --configure -a      # پیکربندی ناتمام‌ها
sudo apt --fix-broken install
```

## مشکل: GPG key error
```
The following signatures couldn't be verified because the public key is not available
```
```bash
# پیدا کردن key ID از خطا (مثلاً ABCDEF01)
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys ABCDEF01
sudo apt update
```

## مشکل: apt update با خطای 404
```bash
# مخزن منقضی شده یا تغییر کرده
sudo apt update 2>&1 | grep "Failed"
# بررسی و اصلاح sources.list
sudo nano /etc/apt/sources.list
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]