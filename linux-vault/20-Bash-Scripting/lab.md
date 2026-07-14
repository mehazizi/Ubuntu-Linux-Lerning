# فصل ۲۰ - Bash Scripting | آزمایشگاه

## تمرین ۱: اسکریپت بررسی سرویس‌ها
```bash
cat > ~/check_services.sh << 'EOF'
#!/bin/bash
SERVICES=("ssh" "cron" "ufw")

for service in "${SERVICES[@]}"; do
    if systemctl is-active --quiet "$service"; then
        echo "✓ $service در حال اجراست"
    else
        echo "✗ $service متوقف است"
    fi
done
EOF
chmod +x ~/check_services.sh
~/check_services.sh
```

## تمرین ۲: اسکریپت پشتیبان‌گیری
```bash
cat > ~/backup.sh << 'EOF'
#!/bin/bash
set -euo pipefail

BACKUP_DIR="/tmp/backups"
SOURCE="${1:-/etc}"
DATE=$(date +%Y%m%d)

mkdir -p "$BACKUP_DIR"
tar -czf "$BACKUP_DIR/backup_${DATE}.tar.gz" "$SOURCE"
echo "پشتیبان ساخته شد: $BACKUP_DIR/backup_${DATE}.tar.gz"

find "$BACKUP_DIR" -name "*.tar.gz" -mtime +7 -delete
echo "پشتیبان‌های قدیمی پاک شدند"
EOF
chmod +x ~/backup.sh
~/backup.sh /etc
```

## تمرین ۳: اسکریپت با ورودی کاربر
```bash
cat > ~/user_info.sh << 'EOF'
#!/bin/bash
read -p "نام کاربر را وارد کنید: " USERNAME
if id "$USERNAME" &>/dev/null; then
    echo "اطلاعات کاربر $USERNAME:"
    id "$USERNAME"
    echo "پوشه خانگی: $(getent passwd $USERNAME | cut -d: -f6)"
else
    echo "کاربر $USERNAME وجود ندارد"
    exit 1
fi
EOF
chmod +x ~/user_info.sh
~/user_info.sh
```

### ✅ چک‌لیست یادگیری
- [ ] اسکریپت با set -euo pipefail نوشته‌ام
- [ ] از if، for، while استفاده کرده‌ام
- [ ] تابع با آرگومان و return نوشته‌ام
- [ ] ورودی کاربر را پردازش کرده‌ام

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]