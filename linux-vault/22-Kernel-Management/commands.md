# فصل ۲۲ - مدیریت هسته | دستورات

## اطلاعات هسته
```bash
uname -r                        # نسخه هسته
uname -a                        # اطلاعات کامل
uname -m                        # معماری
cat /proc/version               # جزئیات هسته
dpkg --list | grep linux-image  # هسته‌های نصب‌شده
```

## ماژول‌ها
```bash
lsmod                           # ماژول‌های بارگذاری‌شده
lsmod | grep module_name        # جستجوی ماژول
modinfo module_name             # اطلاعات ماژول
sudo modprobe module_name       # بارگذاری ماژول
sudo modprobe -r module_name    # حذف ماژول
sudo insmod /path/module.ko     # بارگذاری از فایل
sudo rmmod module_name          # حذف ماژول
# بارگذاری دائمی:
echo "module_name" | sudo tee -a /etc/modules
```

## sysctl
```bash
sysctl -a                       # همه پارامترها
sysctl vm.swappiness            # مقدار یک پارامتر
sudo sysctl vm.swappiness=10    # تغییر موقت
sudo sysctl -w vm.swappiness=10 # تغییر موقت
# تغییر دائمی:
echo "vm.swappiness=10" | sudo tee -a /etc/sysctl.conf
sudo sysctl -p                  # اعمال فایل
sudo sysctl -p /etc/sysctl.d/99-custom.conf
```

## به‌روزرسانی هسته
```bash
sudo apt update
sudo apt install linux-image-generic
sudo apt upgrade
sudo reboot
# بعد از reboot:
uname -r                        # نسخه جدید
# حذف هسته قدیمی:
sudo apt autoremove --purge
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]