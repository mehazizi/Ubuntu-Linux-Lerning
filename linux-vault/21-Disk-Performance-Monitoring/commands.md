# فصل ۲۱ - پایش دیسک و عملکرد | دستورات

## دیسک
```bash
df -h                           # فضای دیسک به صورت خوانا
df -i                           # وضعیت inode
df -hT                          # با نوع فایل‌سیستم
du -sh /var/*                   # حجم پوشه‌ها
du -sh * | sort -rh | head -10  # مرتب بر اساس حجم
du -ah /var/log | sort -rh | head -20  # همه فایل‌ها
```

## حافظه
```bash
free -h                         # وضعیت حافظه
free -h -s 2                    # هر ۲ ثانیه
cat /proc/meminfo               # اطلاعات کامل
```

## vmstat
```bash
vmstat                          # یک گزارش لحظه‌ای
vmstat 2                        # هر ۲ ثانیه
vmstat 2 10                     # ۱۰ بار با فاصله ۲ ثانیه
vmstat -s                       # خلاصه آماری
vmstat -d                       # آمار دیسک
```

## iostat
```bash
sudo apt install sysstat
iostat                          # گزارش اولیه
iostat -x 2                     # آمار پیشرفته هر ۲ ثانیه
iostat -x -d sda 2              # فقط دیسک sda
# ستون‌های مهم:
# %util  → درصد اشغال دیسک
# await  → میانگین زمان انتظار
# r/s    → خواندن در ثانیه
# w/s    → نوشتن در ثانیه
```

## sar
```bash
sar                             # گزارش روز جاری
sar -u 2 5                      # CPU هر ۲ ثانیه ۵ بار
sar -r 2 5                      # حافظه
sar -d 2 5                      # دیسک
sar -n DEV 2 5                  # شبکه
sar -f /var/log/sysstat/sa01    # از فایل ذخیره‌شده
```

## uptime و dmesg
```bash
uptime                          # آپتایم و load average
uptime -p                       # فقط مدت زمان
dmesg                           # همه پیام‌های هسته
dmesg | tail -20                # آخرین پیام‌ها
dmesg -T                        # با timestamp خوانا
dmesg | grep -i "error\|warn\|fail"
dmesg -w                        # پیام‌های زنده
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]