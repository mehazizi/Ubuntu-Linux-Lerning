# فصل ۱۹ - فایروال | عیب‌یابی

## مشکل: UFW SSH را بلاک کرد
```bash
# از کنسول محلی:
sudo ufw allow ssh
sudo ufw status
# یا غیرفعال کردن:
sudo ufw disable
```

## مشکل: سرویس در دسترس نیست
```bash
ss -tulnp | grep :PORT            # آیا سرویس روشن است؟
sudo ufw status verbose           # آیا UFW اجازه داده؟
sudo ufw allow PORT/tcp
# تست از خارج:
nc -zv server_ip port
```

## مشکل: Fail2ban IP اشتباه بلاک کرده
```bash
sudo fail2ban-client status sshd  # بررسی لیست بلاک
sudo fail2ban-client unban IP_ADDRESS
# جلوگیری از بلاک IP خودتان:
echo "ignoreip = 127.0.0.1/8 YOUR_IP" | sudo tee -a /etc/fail2ban/jail.local
sudo systemctl restart fail2ban
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]