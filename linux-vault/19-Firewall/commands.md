# فصل ۱۹ - فایروال | دستورات

## UFW
```bash
sudo ufw status
sudo ufw status verbose
sudo ufw status numbered            # با شماره قانون
sudo ufw enable
sudo ufw disable
sudo ufw reset                      # حذف همه قوانین

sudo ufw default deny incoming
sudo ufw default allow outgoing

sudo ufw allow ssh
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw allow 8080:8090/tcp        # محدوده پورت
sudo ufw allow from 192.168.1.0/24  # از یک شبکه
sudo ufw allow from 192.168.1.0/24 to any port 3306  # MySQL فقط از LAN
sudo ufw deny 23/tcp
sudo ufw delete allow 80/tcp        # حذف قانون
sudo ufw delete 3                   # حذف بر اساس شماره
```

## nftables
```bash
sudo nft list ruleset               # نمایش همه قوانین
sudo nft list tables                # لیست جداول
cat /etc/nftables.conf
sudo systemctl status nftables
sudo systemctl enable nftables
```

## iptables (آشنایی)
```bash
sudo iptables -L -n -v              # نمایش قوانین
sudo iptables -L INPUT -n -v        # فقط chain ورودی
sudo iptables-save                  # ذخیره قوانین
sudo iptables-restore < rules.v4    # بازیابی
```

## Fail2ban
```bash
sudo apt install fail2ban
sudo systemctl enable --now fail2ban
sudo fail2ban-client status         # وضعیت کلی
sudo fail2ban-client status sshd    # وضعیت jail
sudo fail2ban-client unban IP       # رفع بلاک
sudo fail2ban-client set sshd banip IP  # بلاک دستی
tail -f /var/log/fail2ban.log
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]