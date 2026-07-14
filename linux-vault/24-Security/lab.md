# فصل ۲۴ - امنیت | آزمایشگاه

## تمرین ۱: بررسی امنیتی سیستم
```bash
echo "=== فایل‌های SUID ==="
find / -perm -4000 -type f 2>/dev/null

echo "=== کاربران با shell ==="
grep -v "nologin\|false" /etc/passwd | cut -d: -f1,7

echo "=== ورودهای ناموفق اخیر ==="
lastb | head -10

echo "=== پورت‌های باز ==="
ss -tulnp
```

## تمرین ۲: نصب و تنظیم auditd
```bash
sudo apt install auditd

# قوانین ممیزی
sudo auditctl -w /etc/passwd -p wa -k passwd_changes
sudo auditctl -w /etc/sudoers -p wa -k sudoers_changes
sudo auditctl -w /var/log/auth.log -p r -k auth_log_read

# ایجاد رویداد آزمایشی
sudo cat /etc/passwd > /dev/null

# جستجو
sudo ausearch -k passwd_changes
sudo aureport --summary
```

## تمرین ۳: بررسی لاگ‌های امنیتی
```bash
grep "Failed password" /var/log/auth.log |   awk '{print $11}' | sort | uniq -c | sort -rn | head -10

grep "sudo" /var/log/auth.log | tail -20

last | head -20
```

### ✅ چک‌لیست یادگیری
- [ ] فایل‌های SUID مشکوک را شناسایی می‌کنم
- [ ] سیاست رمز عبور تنظیم کرده‌ام
- [ ] auditd را راه‌اندازی و پرس‌وجو کرده‌ام
- [ ] SSH را سخت‌سازی کرده‌ام

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]