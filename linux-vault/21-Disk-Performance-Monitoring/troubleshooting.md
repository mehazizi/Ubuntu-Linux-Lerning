# فصل ۲۱ - پایش دیسک و عملکرد | عیب‌یابی

## مشکل: سرور کند است
```bash
uptime                          # Load Average چقدر است؟
top                             # کدام فرآیند مقصر است؟
iostat -x 1                     # آیا دیسک گلوگاه است؟
free -h                         # آیا حافظه کم است؟
ss -s                           # آیا اتصالات شبکه زیاد است؟
```

## مشکل: دیسک پر شده
```bash
df -h
du -h / 2>/dev/null | sort -rh | head -20
journalctl --disk-usage
sudo journalctl --vacuum-time=7d
find /var/log -name "*.gz" -mtime +30 -delete
sudo apt clean
```

## مشکل: حافظه پر شده
```bash
free -h
ps aux --sort=-%mem | head -10
# فعال کردن swap:
sudo fallocate -l 2G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```

## مشکل: Load Average بالاست
```bash
nproc                           # تعداد CPU
uptime
top                             # فرآیند مقصر
ps aux | grep " D "             # فرآیندهای D state (I/O wait)
iostat -x 1                     # بررسی دیسک
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]