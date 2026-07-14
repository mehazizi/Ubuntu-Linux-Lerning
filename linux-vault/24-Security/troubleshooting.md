# فصل ۲۴ - امنیت | عیب‌یابی

## مشکل: کاربر نمی‌تواند sudo کند
```bash
groups username                 # آیا در گروه sudo است؟
sudo -l -U username             # مجوزهای sudo
cat /var/log/auth.log | grep "username.*sudo"
```

## مشکل: رمز عبور انقضا گرفته
```bash
chage -l username               # بررسی وضعیت
sudo chage -M 99999 username    # غیرفعال کردن انقضا
sudo passwd username            # تنظیم رمز جدید
```

## مشکل: auditd فضا زیادی می‌گیرد
```bash
sudo aureport --summary
sudo service auditd rotate      # چرخش لاگ
# تنظیم در /etc/audit/auditd.conf:
# max_log_file_action = rotate
# num_logs = 5
```

## مشکل: حساب کاربری قفل شده
```bash
sudo pam_tally2 --user username         # تعداد تلاش‌های ناموفق
sudo pam_tally2 --user username --reset # رفع قفل
sudo passwd -u username                 # باز کردن قفل رمز
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]