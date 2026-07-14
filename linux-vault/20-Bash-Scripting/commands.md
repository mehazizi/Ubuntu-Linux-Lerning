# فصل ۲۰ - Bash Scripting | دستورات

## متغیرها
```bash
NAME="Ali"
echo "سلام $NAME"
echo "سلام ${NAME}!"        # بدون ابهام
AGE=$((25 + 1))             # محاسبه
FILES=$(ls /etc | wc -l)    # خروجی دستور
```

## شرط‌ها
```bash
if [ "$VAR" = "value" ]; then
    echo "برابر است"
elif [ "$VAR" = "other" ]; then
    echo "دیگری"
else
    echo "نه این نه آن"
fi

# بررسی فایل
if [ -f "/etc/passwd" ]; then echo "فایل وجود دارد"; fi
if [ -d "/tmp" ]; then echo "پوشه وجود دارد"; fi
if [ -z "$VAR" ]; then echo "خالی است"; fi
if [ -n "$VAR" ]; then echo "مقدار دارد"; fi

# مقایسه عددی
if [ $NUM -gt 10 ]; then echo "بزرگتر از ۱۰"; fi
# -eq, -ne, -lt, -le, -gt, -ge
```

## حلقه‌ها
```bash
# for
for i in 1 2 3 4 5; do echo $i; done
for file in /etc/*.conf; do echo "$file"; done
for i in $(seq 1 10); do echo $i; done
for ((i=0; i<5; i++)); do echo $i; done

# while
while [ $COUNT -lt 10 ]; do
    echo $COUNT
    ((COUNT++))
done

# read از فایل
while IFS= read -r line; do
    echo "$line"
done < /etc/passwd
```

## تابع
```bash
greet() {
    local name="$1"           # متغیر محلی
    echo "سلام $name"
    return 0
}
greet "Ali"

# تابع با exit code
check_file() {
    if [ -f "$1" ]; then
        return 0
    else
        return 1
    fi
}
if check_file "/etc/passwd"; then echo "وجود دارد"; fi
```

## نمونه اسکریپت
```bash
#!/bin/bash
set -euo pipefail

LOG="/var/log/myapp.log"
BACKUP_DIR="/backup"

log() { echo "[$(date '+%Y-%m-%d %H:%M:%S')] $1" | tee -a "$LOG"; }

if [ $# -lt 1 ]; then
    echo "استفاده: $0 <source>"
    exit 1
fi

SOURCE="$1"
if [ ! -d "$SOURCE" ]; then
    log "خطا: پوشه $SOURCE وجود ندارد"
    exit 1
fi

DATE=$(date +%Y%m%d_%H%M%S)
tar -czf "$BACKUP_DIR/backup_$DATE.tar.gz" "$SOURCE"
log "پشتیبان‌گیری موفق: backup_$DATE.tar.gz"
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]