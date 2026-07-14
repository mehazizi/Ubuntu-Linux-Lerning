# فصل ۲۴ - امنیت | دستورات

## بررسی مجوزهای حساس
```bash
find / -perm -4000 -type f 2>/dev/null     # فایل‌های SUID
find / -perm -2000 -type f 2>/dev/null     # فایل‌های SGID
find / -perm -0002 -type f 2>/dev/null     # قابل‌نوشتن برای همه
find /etc -newer /etc/passwd 2>/dev/null   # فایل‌های تازه‌تغییریافته
```

## PAM
```bash
ls /etc/pam.d/                  # پیکربندی PAM
cat /etc/pam.d/sshd             # PAM برای SSH
cat /etc/pam.d/common-password  # سیاست رمز عبور
sudo apt install libpam-pwquality
```

## سیاست رمز عبور
```bash
sudo nano /etc/security/pwquality.conf
# minlen = 12
# dcredit = -1    (حداقل یک عدد)
# ucredit = -1    (حداقل یک حرف بزرگ)
# lcredit = -1    (حداقل یک حرف کوچک)
# ocredit = -1    (حداقل یک نماد)

chage -l username               # وضعیت انقضای رمز
sudo chage -M 90 username       # انقضا در ۹۰ روز
sudo chage -W 7 username        # هشدار ۷ روز قبل
```

## sudo Hardening
```bash
sudo visudo
# تنظیمات مهم:
# Defaults    requiretty
# Defaults    logfile=/var/log/sudo.log
# Defaults    log_input, log_output
# username ALL=(ALL:ALL) /usr/bin/systemctl restart nginx
```

## auditd
```bash
sudo apt install auditd
sudo systemctl enable --now auditd
sudo auditctl -l                # لیست قوانین
sudo auditctl -w /etc/passwd -p wa -k passwd_watch  # نظارت روی فایل
sudo auditctl -w /etc/sudoers -p wa -k sudo_watch
sudo ausearch -k passwd_watch   # جستجو در لاگ ممیزی
sudo aureport --summary         # گزارش خلاصه
sudo aureport --auth            # گزارش احراز هویت
```

## SSH Hardening
```bash
sudo nano /etc/ssh/sshd_config
# Port 2222
# PermitRootLogin no
# PasswordAuthentication no
# MaxAuthTries 3
# LoginGraceTime 20
# AllowUsers myuser
# Protocol 2
# X11Forwarding no
sudo sshd -t && sudo systemctl restart sshd
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]