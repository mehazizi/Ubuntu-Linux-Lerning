# فصل ۹ - پیکربندی شبکه | عیب‌یابی

## مشکل: اتصال اینترنت ندارم
```bash
# لایه‌به‌لایه بررسی کنید:
ip addr show                  # آدرس دارم؟
ip route show                 # gateway تعریف شده؟
ping -c 2 $(ip route | grep default | awk '{print $3}')  # gateway پاسخ می‌دهد؟
ping -c 2 8.8.8.8             # اینترنت بدون DNS کار می‌کند؟
dig google.com @8.8.8.8       # DNS گوگل کار می‌کند؟
```

## مشکل: DNS کار نمی‌کند
```bash
cat /etc/resolv.conf
resolvectl status
ping 8.8.8.8                  # اگر این کار می‌کند مشکل DNS است
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf
```

## مشکل: netplan apply خطا می‌دهد
```bash
sudo netplan generate         # بررسی syntax
sudo cat /etc/netplan/*.yaml  # بررسی دستی
# YAML به فاصله حساس است، از tab استفاده نکنید
```

## مشکل: رابط شبکه بالا نمی‌آید
```bash
ip link show                  # وضعیت رابط
sudo ip link set eth0 up
dmesg | grep -i eth           # لاگ هسته
lspci | grep -i network       # بررسی سخت‌افزار
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]