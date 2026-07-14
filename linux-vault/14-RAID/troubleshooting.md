# فصل ۱۴ - RAID | عیب‌یابی

## مشکل: یک دیسک RAID failed شده
```bash
cat /proc/mdstat                    # بررسی وضعیت
sudo mdadm --detail /dev/md0        # کدام دیسک مشکل دارد؟
# بعد از تعویض فیزیکی:
sudo mdadm --remove /dev/md0 /dev/sdc_failed
sudo mdadm --add /dev/md0 /dev/sdc_new
watch cat /proc/mdstat              # منتظر rebuild
```

## مشکل: RAID در بوت شناسایی نمی‌شود
```bash
sudo mdadm --assemble --scan
cat /etc/mdadm/mdadm.conf
sudo mdadm --detail --scan | sudo tee /etc/mdadm/mdadm.conf
sudo update-initramfs -u
```

## مشکل: rebuild خیلی کند است
```bash
cat /proc/mdstat                    # بررسی سرعت
# افزایش سرعت rebuild:
echo 50000 | sudo tee /proc/sys/dev/raid/speed_limit_min
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]