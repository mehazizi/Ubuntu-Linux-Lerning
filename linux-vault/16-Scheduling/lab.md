# فصل ۱۶ - زمان‌بندی وظایف | آزمایشگاه

## تمرین ۱: crontab عملی
```bash
# ساخت اسکریپت
cat > /tmp/log_time.sh << 'EOF'
#!/bin/bash
echo "$(date): اسکریپت اجرا شد" >> /tmp/cron_test.log
EOF
chmod +x /tmp/log_time.sh

# اجرا هر دقیقه
crontab -e
# این خط را اضافه کنید:
# * * * * * /tmp/log_time.sh

# بعد از ۳ دقیقه بررسی کنید:
sleep 180
cat /tmp/cron_test.log

# حذف cron
crontab -e   # خط را پاک کنید
```

## تمرین ۲: systemd timer
```bash
sudo tee /etc/systemd/system/cleanup.service << 'EOF'
[Unit]
Description=Cleanup temp files

[Service]
Type=oneshot
ExecStart=/bin/find /tmp -type f -atime +7 -delete
EOF

sudo tee /etc/systemd/system/cleanup.timer << 'EOF'
[Unit]
Description=Daily cleanup

[Timer]
OnCalendar=daily
Persistent=true

[Install]
WantedBy=timers.target
EOF

sudo systemctl daemon-reload
sudo systemctl enable --now cleanup.timer
systemctl list-timers | grep cleanup
```

### ✅ چک‌لیست یادگیری
- [ ] فرمت crontab را بلدم
- [ ] cron عملی تنظیم کرده‌ام
- [ ] systemd timer ساخته‌ام
- [ ] at را آزمایش کرده‌ام

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]