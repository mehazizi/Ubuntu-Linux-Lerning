# فصل ۱۸ - SSH | آزمایشگاه

## تمرین ۱: ساخت و تنظیم کلید SSH
```bash
ssh-keygen -t ed25519 -C "$(whoami)@$(hostname)" -f ~/.ssh/test_key
ls -la ~/.ssh/
cat ~/.ssh/test_key.pub
```

## تمرین ۲: پیکربندی ~/.ssh/config
```bash
mkdir -p ~/.ssh
chmod 700 ~/.ssh
cat >> ~/.ssh/config << 'EOF'
Host localhost-test
    HostName 127.0.0.1
    User $USER
    Port 22
    IdentityFile ~/.ssh/test_key
EOF
chmod 600 ~/.ssh/config
cat ~/.ssh/config
```

## تمرین ۳: سخت‌سازی SSH (محیط آزمایشی)
```bash
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak

# بررسی تنظیمات فعلی
grep -E "^(Port|PermitRoot|PasswordAuth|MaxAuth)" /etc/ssh/sshd_config

# تست پیکربندی بدون اعمال
sudo sshd -t
```

## تمرین ۴: Port Forwarding
```bash
# forward کردن پورت ۸۰۸۰ محلی به پورت ۸۰ سرور
ssh -L 8080:localhost:80 user@server &
curl http://localhost:8080
kill %1
```

### ✅ چک‌لیست یادگیری
- [ ] کلید Ed25519 ساخته‌ام
- [ ] ~/.ssh/config پیکربندی کرده‌ام
- [ ] scp و sftp را استفاده کرده‌ام
- [ ] سخت‌سازی sshd را می‌شناسم

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]