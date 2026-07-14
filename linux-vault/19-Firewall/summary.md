# فصل ۱۹ - فایروال | خلاصه

## لایه‌های فایروال لینوکس
```
Application Layer
      ↓
nftables / iptables (Kernel)
      ↓
Network Interface
```

## ابزارها
| ابزار | توضیح |
|-------|-------|
| **nftables** | جایگزین مدرن iptables |
| **iptables** | قدیمی، هنوز پرکاربرد |
| **ufw** | رابط ساده برای iptables/nftables |
| **Fail2ban** | بلاک خودکار IP‌های مشکوک |

## مفاهیم UFW
- **Default deny**: همه ترافیک ورودی بسته
- **Default allow**: همه ترافیک خروجی باز
- **Rule**: قانون برای اجازه یا بلاک ترافیک

## Fail2ban
- لاگ‌ها را بررسی می‌کند
- IP‌هایی که تلاش زیاد دارند را بلاک می‌کند
- قابل تنظیم برای هر سرویس

---
[[commands|← دستورات]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]