# فصل ۲۱ - پایش دیسک و عملکرد | آزمایشگاه

## تمرین ۱: اسکریپت گزارش جامع سرور
```bash
cat > ~/server_report.sh << 'EOF'
#!/bin/bash
echo "========== گزارش سرور =========="
echo "تاریخ: $(date)"
echo "آپتایم: $(uptime -p)"
echo ""

echo "--- Load Average ---"
uptime | awk -F'load average:' '{print $2}'

echo ""
echo "--- حافظه ---"
free -h

echo ""
echo "--- دیسک ---"
df -h | grep -v tmpfs

echo ""
echo "--- ۵ فرآیند پرمصرف CPU ---"
ps aux --sort=-%cpu | head -6

echo ""
echo "--- سرویس‌های ناموفق ---"
systemctl list-units --failed --no-legend
echo "================================"
EOF
chmod +x ~/server_report.sh
~/server_report.sh
```

## تمرین ۲: پایش I/O دیسک
```bash
sudo apt install sysstat iotop
iostat -x 1 5
sudo iotop -o -n 5    # فقط فرآیندهای فعال
```

## تمرین ۳: یافتن پوشه‌های حجیم
```bash
du -h / 2>/dev/null | sort -rh | head -15
find / -type f -size +100M 2>/dev/null | head -10
```

### ✅ چک‌لیست یادگیری
- [ ] Load Average را تفسیر می‌کنم
- [ ] تفاوت free و available در حافظه را می‌دانم
- [ ] iostat را برای بررسی I/O استفاده کرده‌ام
- [ ] اسکریپت گزارش سرور نوشته‌ام

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]