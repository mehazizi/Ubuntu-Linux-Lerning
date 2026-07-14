# فصل ۱۸ - SSH | دستورات

## اتصال پایه
```bash
ssh user@server
ssh user@server -p 2222             # پورت غیرپیش‌فرض
ssh -i ~/.ssh/mykey user@server     # کلید مشخص
ssh -v user@server                  # verbose (عیب‌یابی)
ssh -X user@server                  # X11 forwarding
ssh -L 8080:localhost:80 user@server  # port forwarding
```

## کلید SSH
```bash
ssh-keygen -t ed25519 -C "user@server"     # ساخت کلید Ed25519
ssh-keygen -t rsa -b 4096 -C "comment"    # کلید RSA
ssh-keygen -t ed25519 -f ~/.ssh/mykey      # نام سفارشی

ssh-copy-id user@server                    # کپی کلید به سرور
ssh-copy-id -i ~/.ssh/mykey.pub user@server
# دستی:
cat ~/.ssh/id_ed25519.pub | ssh user@server "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"
```

## ssh-agent
```bash
eval $(ssh-agent)                   # راه‌اندازی agent
ssh-add ~/.ssh/id_ed25519           # اضافه کردن کلید
ssh-add -l                          # کلیدهای لود شده
ssh-add -D                          # حذف همه کلیدها
```

## انتقال فایل
```bash
scp file.txt user@server:/dest/     # کپی به سرور
scp user@server:/file.txt ./        # کپی از سرور
scp -r directory/ user@server:/dest/  # پوشه
scp -P 2222 file.txt user@server:/ # پورت غیرپیش‌فرض

sftp user@server                    # جلسه تعاملی
sftp> put file.txt                  # آپلود
sftp> get file.txt                  # دانلود
sftp> ls                            # لیست
```

## فایل ~/.ssh/config
```
Host myserver
    HostName 192.168.1.100
    User admin
    Port 2222
    IdentityFile ~/.ssh/mykey
    ServerAliveInterval 60

Host *.internal
    User ubuntu
    IdentityFile ~/.ssh/internal_key
```

## سخت‌سازی sshd_config
```bash
sudo nano /etc/ssh/sshd_config
# تنظیمات مهم:
# Port 2222
# PermitRootLogin no
# PasswordAuthentication no
# PubkeyAuthentication yes
# MaxAuthTries 3
# AllowUsers myuser
# ClientAliveInterval 300

sudo sshd -t                        # تست پیکربندی
sudo systemctl restart sshd
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]