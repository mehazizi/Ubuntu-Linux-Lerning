# فصل ۱۱ - Systemd و سرویس‌ها | آزمایشگاه

## تمرین ۱: بررسی وضعیت سیستم
```bash
systemctl list-units --failed
systemd-analyze blame | head -10
journalctl -p err -b | tail -20
```

## تمرین ۲: ساخت سرویس سفارشی
```bash
sudo tee /etc/systemd/system/hello.service << 'EOF'
[Unit]
Description=Hello World Service
After=network.target

[Service]
Type=simple
ExecStart=/bin/bash -c 'while true; do echo "سلام $(date)"; sleep 5; done'
Restart=always

[Install]
WantedBy=multi-user.target
EOF

sudo systemctl daemon-reload
sudo systemctl start hello
sudo systemctl status hello
journalctl -u hello -f
sudo systemctl stop hello
sudo systemctl disable hello
sudo rm /etc/systemd/system/hello.service
sudo systemctl daemon-reload
```

## تمرین ۳: تحلیل زمان بوت
```bash
systemd-analyze
systemd-analyze blame | head -15
systemd-analyze critical-chain
```

### ✅ چک‌لیست یادگیری
- [ ] سرویس‌ها را مدیریت می‌کنم
- [ ] سرویس سفارشی ساخته‌ام
- [ ] با journalctl لاگ می‌خوانم
- [ ] زمان بوت را تحلیل کرده‌ام

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]