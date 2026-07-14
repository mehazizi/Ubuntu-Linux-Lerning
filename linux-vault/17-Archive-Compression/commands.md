# فصل ۱۷ - آرشیو و فشرده‌سازی | دستورات

## tar
```bash
tar -czf backup.tar.gz /var/www          # آرشیو + gzip
tar -cjf backup.tar.bz2 /var/www         # آرشیو + bzip2
tar -cJf backup.tar.xz /var/www          # آرشیو + xz
tar -cf backup.tar /var/www              # فقط آرشیو

tar -xzf backup.tar.gz                   # استخراج در پوشه جاری
tar -xzf backup.tar.gz -C /restore/     # استخراج در مسیر مشخص
tar -xzf backup.tar.gz -C /tmp/ var/www/html/index.html  # فقط یک فایل

tar -tzf backup.tar.gz                   # لیست محتوا
tar -tzf backup.tar.gz | grep ".conf"   # جستجو در آرشیو

tar -czf backup.tar.gz --exclude="*.log" --exclude="cache/" /var/www
tar -czpf backup.tar.gz /etc             # با حفظ مجوزها
```

## gzip، bzip2، xz
```bash
gzip file.txt                           # فشرده (file.txt.gz ساخته می‌شود)
gzip -d file.txt.gz                     # استخراج
gzip -k file.txt                        # حفظ فایل اصلی
gzip -9 file.txt                        # حداکثر فشرده‌سازی
gunzip file.txt.gz                      # استخراج

bzip2 file.txt
bunzip2 file.txt.bz2

xz file.txt
unxz file.txt.xz
xz -k file.txt                          # حفظ فایل اصلی
```

## zip
```bash
zip archive.zip file1 file2             # فشرده کردن
zip -r archive.zip directory/           # پوشه
zip -e secure.zip file.txt              # با رمز عبور
unzip archive.zip                       # استخراج
unzip archive.zip -d /destination/      # مسیر مشخص
unzip -l archive.zip                    # لیست محتوا
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]