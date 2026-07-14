# فصل ۹ - پیکربندی شبکه | دستورات

## مشاهده وضعیت شبکه
```bash
ip addr show                        # همه رابط‌ها
ip addr show eth0                   # یک رابط خاص
ip link show                        # وضعیت لایه ۲
ip route show                       # جدول مسیریابی
ip neigh show                       # جدول ARP
ss -tulnp                           # پورت‌های باز
```

## پیکربندی موقت (ip)
```bash
sudo ip addr add 192.168.1.10/24 dev eth0
sudo ip addr del 192.168.1.10/24 dev eth0
sudo ip link set eth0 up
sudo ip link set eth0 down
sudo ip route add default via 192.168.1.1
sudo ip route add 10.0.0.0/8 via 192.168.1.254
sudo ip link set eth0 mtu 9000
```

## Netplan - پیکربندی دائمی
```bash
ls /etc/netplan/
sudo nano /etc/netplan/00-installer-config.yaml
sudo netplan try              # آزمایش (برگشت خودکار)
sudo netplan apply            # اعمال تغییرات
sudo netplan generate         # تولید پیکربندی
```

## DNS و Hostname
```bash
cat /etc/resolv.conf
resolvectl status             # وضعیت DNS
resolvectl query google.com   # تست DNS
sudo hostnamectl set-hostname myserver
sudo nano /etc/hosts
```

## ابزارهای تشخیص
```bash
ping -c 4 8.8.8.8             # تست اتصال
ping -I eth0 8.8.8.8          # از رابط خاص
traceroute 8.8.8.8            # مسیر بسته
tracepath 8.8.8.8             # مشابه traceroute
dig google.com                # بررسی DNS
dig @8.8.8.8 google.com       # با DNS مشخص
dig -x 8.8.8.8                # PTR record
nslookup google.com
ss -s                         # خلاصه اتصالات
ss -tnp state established     # اتصالات برقرار
```

## VLAN و Bridge
```bash
sudo ip link add link eth0 name eth0.100 type vlan id 100
sudo ip addr add 192.168.100.1/24 dev eth0.100
sudo ip link set eth0.100 up

sudo ip link add br0 type bridge
sudo ip link set eth0 master br0
sudo ip link set br0 up
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]