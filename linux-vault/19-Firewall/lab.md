# فصل ۱۹ - فایروال | آزمایشگاه

## تمرین ۱: راه‌اندازی UFW
```bash
sudo ufw status
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw allow http
sudo ufw allow https
sudo ufw enable
sudo ufw status verbose
```

## تمرین ۲: قوانین پیشرفته
```bash
# MySQL فقط از شبکه داخلی
sudo ufw allow from 192.168.0.0/16 to any port 3306

# نمایش با شماره
sudo ufw status numbered

# حذف یک قانون
sudo ufw delete allow http
sudo ufw status numbered
```

## تمرین ۳: Fail2ban
```bash
sudo apt install fail2ban

sudo tee /etc/fail2ban/jail.local << 'EOF'
[DEFAULT]
bantime  = 1h
findtime = 10m
maxretry = 3

[sshd]
enabled = true
EOF

sudo systemctl restart fail2ban
sudo fail2ban-client status sshd
```

### ✅ چک‌لیست یادگیری
- [ ] UFW را پیکربندی کرده‌ام
- [ ] قوانین پیشرفته با محدودیت IP ساخته‌ام
- [ ] Fail2ban را راه‌اندازی کرده‌ام

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]