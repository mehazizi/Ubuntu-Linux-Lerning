# فصل ۶ - مدیریت بسته | دستورات

## apt - عملیات اصلی
```bash
sudo apt update                      # به‌روزرسانی لیست بسته‌ها
sudo apt upgrade                     # ارتقای بسته‌های نصب‌شده
sudo apt full-upgrade                # ارتقا با حذف بسته‌های قدیمی
sudo apt install nginx               # نصب بسته
sudo apt install -y nginx git curl   # نصب بدون تأیید
sudo apt remove nginx                # حذف بدون پیکربندی
sudo apt purge nginx                 # حذف کامل با پیکربندی
sudo apt autoremove                  # حذف وابستگی‌های اضافه
sudo apt clean                       # پاک کردن کش
sudo apt autoclean                   # پاک کردن کش قدیمی
```

## apt - جستجو و اطلاعات
```bash
apt search nginx                     # جستجوی بسته
apt show nginx                       # اطلاعات بسته
apt list --installed                 # بسته‌های نصب‌شده
apt list --upgradable               # بسته‌های قابل ارتقا
apt depends nginx                    # وابستگی‌های بسته
apt rdepends nginx                   # چه بسته‌هایی به این نیاز دارند
```

## dpkg - مدیریت سطح پایین
```bash
sudo dpkg -i package.deb             # نصب فایل deb
sudo dpkg -r package_name            # حذف بسته
sudo dpkg -l                         # لیست همه بسته‌ها
sudo dpkg -l | grep nginx            # جستجو
dpkg -L nginx                        # فایل‌های یک بسته
dpkg -S /usr/bin/nginx               # بسته مالک یک فایل
sudo dpkg --configure -a             # پیکربندی بسته‌های ناتمام
sudo apt install -f                  # رفع وابستگی‌های مشکل‌دار
```

## مخازن و GPG
```bash
sudo add-apt-repository ppa:ondrej/php
sudo add-apt-repository --remove ppa:ondrej/php
# افزودن مخزن دستی:
echo "deb [arch=amd64] https://repo.example.com focal main" |   sudo tee /etc/apt/sources.list.d/example.list
# افزودن GPG key:
curl -fsSL https://repo.example.com/key.gpg | sudo apt-key add -
sudo apt update
```

## نصب از tar
```bash
tar -xzf app-1.0.tar.gz
cd app-1.0
./configure --prefix=/usr/local
make -j$(nproc)
sudo make install
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]