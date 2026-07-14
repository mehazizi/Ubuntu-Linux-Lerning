# فصل ۱۸ - SSH | عیب‌یابی

## مشکل: Connection refused
```bash
ssh -v user@server 2>&1 | head -30   # verbose mode
sudo systemctl status sshd            # آیا سرویس روشن است؟
ss -tulnp | grep :22                  # آیا پورت باز است؟
sudo ufw status                        # آیا فایروال مسدود کرده؟
```

## مشکل: Permission denied (publickey)
```bash
ssh -v user@server                    # بررسی مرحله احراز هویت
ls -la ~/.ssh/                        # مجوزهای فایل‌های کلید
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_ed25519
chmod 644 ~/.ssh/id_ed25519.pub

# در سرور:
ls -la ~/.ssh/authorized_keys
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```

## مشکل: Host key verification failed
```bash
ssh-keygen -R server_ip              # حذف کلید قدیمی
ssh user@server                      # اتصال مجدد
```

## مشکل: SSH قطع می‌شود
```bash
# در ~/.ssh/config:
ServerAliveInterval 60
ServerAliveCountMax 3
# یا هنگام اتصال:
ssh -o ServerAliveInterval=60 user@server
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]