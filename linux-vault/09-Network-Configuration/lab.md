# فصل ۹ - پیکربندی شبکه | آزمایشگاه

## تمرین ۱: بررسی کامل شبکه
```bash
ip addr show
ip route show
cat /etc/resolv.conf
resolvectl status
ss -tulnp
```

## تمرین ۲: پیکربندی آدرس استاتیک با Netplan
```yaml
# sudo nano /etc/netplan/00-installer-config.yaml
network:
  version: 2
  ethernets:
    ens3:
      addresses:
        - 192.168.1.100/24
      routes:
        - to: default
          via: 192.168.1.1
      nameservers:
        addresses: [8.8.8.8, 1.1.1.1]
```
```bash
sudo netplan try
sudo netplan apply
ip addr show ens3
```

## تمرین ۳: عیب‌یابی اتصال لایه‌به‌لایه
```bash
ip addr show                  # لایه ۳: آدرس دارم؟
ping -c 2 192.168.1.1         # لایه ۳: Gateway در دسترس؟
ping -c 2 8.8.8.8             # لایه ۳: اینترنت دارم؟
dig google.com                # لایه ۷: DNS کار می‌کند؟
curl -I https://google.com    # لایه ۷: HTTPS کار می‌کند؟
```

## تمرین ۴: بررسی پورت‌های باز
```bash
ss -tulnp
ss -tulnp | grep :22          # آیا SSH باز است؟
ss -tulnp | grep :80          # آیا HTTP باز است؟
```

### ✅ چک‌لیست یادگیری
- [ ] رابط‌های شبکه را شناسایی می‌کنم
- [ ] Netplan را پیکربندی کرده‌ام
- [ ] DNS را بررسی می‌کنم
- [ ] عیب‌یابی لایه‌به‌لایه را انجام داده‌ام

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]