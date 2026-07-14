# فصل ۱۷ - آرشیو و فشرده‌سازی | عیب‌یابی

## مشکل: tar استخراج نمی‌شود
```bash
file backup.tar.gz                  # آیا واقعاً gzip است؟
tar -tzf backup.tar.gz              # آیا آرشیو سالم است؟
gunzip -t backup.tar.gz             # بررسی یکپارچگی gzip
```

## مشکل: فضا کافی نیست
```bash
df -h
# استخراج در یک مرحله بدون فایل tar میانی:
ssh user@server "tar -czf - /path" | tar -xzf - -C /local/dest/
```

## مشکل: مجوزها بعد از استخراج اشتباه است
```bash
# هنگام ساخت باید -p استفاده کنید:
sudo tar -czpf backup.tar.gz /etc
# هنگام استخراج:
sudo tar -xzpf backup.tar.gz
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]