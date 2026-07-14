# فصل ۱۷ - آرشیو و فشرده‌سازی | آزمایشگاه

## تمرین ۱: مقایسه روش‌های فشرده‌سازی
```bash
# ساخت فایل آزمایشی
dd if=/dev/urandom of=/tmp/testfile bs=1M count=10

time gzip -k /tmp/testfile
time bzip2 -k /tmp/testfile
time xz -k /tmp/testfile

ls -lh /tmp/testfile*
# کدام کوچک‌تر است؟ کدام سریع‌تر؟
rm /tmp/testfile*
```

## تمرین ۲: پشتیبان‌گیری با tar
```bash
# پشتیبان /etc
sudo tar -czpf /tmp/etc_backup_$(date +%Y%m%d).tar.gz /etc
ls -lh /tmp/etc_backup_*.tar.gz
tar -tzf /tmp/etc_backup_*.tar.gz | head -20
```

## تمرین ۳: استخراج انتخابی
```bash
tar -tzf /tmp/etc_backup_*.tar.gz | grep "sshd_config"
tar -xzf /tmp/etc_backup_*.tar.gz -C /tmp/ etc/ssh/sshd_config
cat /tmp/etc/ssh/sshd_config
```

### ✅ چک‌لیست یادگیری
- [ ] آرشیو با tar ساخته و استخراج کرده‌ام
- [ ] تفاوت gzip، bzip2 و xz را می‌دانم
- [ ] با گزینه --exclude کار کرده‌ام

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]