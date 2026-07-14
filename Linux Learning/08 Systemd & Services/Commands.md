# Chapter 08 - Commands

## بررسی وضعیت سرویس

systemctl status SERVICE

مثال:

systemctl status ssh

---

## شروع سرویس

systemctl start SERVICE

---

## توقف سرویس

systemctl stop SERVICE

---

## راه‌اندازی مجدد سرویس

systemctl restart SERVICE

---

## بازخوانی تنظیمات سرویس

systemctl reload SERVICE

---

## فعال‌سازی در بوت

systemctl enable SERVICE

---

## غیرفعال‌سازی در بوت

systemctl disable SERVICE

---

## جلوگیری کامل از اجرا

systemctl mask SERVICE

---

## حذف Mask

systemctl unmask SERVICE

---

## بررسی وضعیت فعلی سرویس

systemctl is-active SERVICE

---

## بررسی وضعیت بوت

systemctl is-enabled SERVICE

---

## مشاهده Target پیش‌فرض

systemctl get-default

---

## مشاهده وابستگی‌های Target

systemctl list-dependencies TARGET

مثال:

systemctl list-dependencies multi-user.target

---

## مشاهده لاگ‌های سیستم

journalctl

---

## مشاهده آخرین لاگ‌ها

journalctl -n 20

---

## مشاهده لاگ زنده

journalctl -f

---

## مشاهده لاگ یک سرویس

journalctl -u SERVICE

مثال:

journalctl -u ssh

---

## مشاهده لاگ زنده یک سرویس

journalctl -u SERVICE -f

---

## مشاهده لاگ بوت جاری

journalctl -b

---

## مشاهده خطاهای بوت

journalctl -p err -b

# Chapter 08 — Additional Commands (Missing Commands)

# User Information

نمایش نام کاربر فعلی

```bash
whoami
```

---

نمایش UID، GID و Groupهای کاربر

```bash
id
```

---

نمایش Groupهای کاربر فعلی

```bash
groups
```

---

نمایش Groupهای یک کاربر مشخص

```bash
groups username
```

---

# Password Management

تغییر رمز عبور کاربر فعلی

```bash
passwd
```

---

تغییر رمز عبور یک کاربر دیگر (نیازمند Root)

```bash
sudo passwd username
```

---

قفل کردن حساب کاربری

```bash
sudo passwd -l username
```

---

باز کردن قفل حساب کاربری

```bash
sudo passwd -u username
```

---

حذف Password کاربر

```bash
sudo passwd -d username
```

---

# Password Aging

نمایش وضعیت Password

```bash
sudo chage -l username
```

---

تعیین تاریخ انقضای Password

```bash
sudo chage -M 90 username
```

---

اجبار به تغییر Password در اولین Login

```bash
sudo chage -d 0 username
```

---

تعیین حداقل فاصله بین تغییر Password

```bash
sudo chage -m 7 username
```

---

تعیین زمان هشدار قبل از انقضای Password

```bash
sudo chage -W 7 username
```

---

# Best Practice

برای مشاهده اطلاعات هویتی کاربر:

```bash
whoami
id
groups
```

---

برای بررسی وضعیت Password یک کاربر:

```bash
sudo chage -l username
```

---

برای تغییر Password کاربران همیشه از:

```bash
sudo passwd username
```

استفاده کنید، نه ویرایش مستقیم فایل‌های:

```text
/etc/passwd
/etc/shadow
```