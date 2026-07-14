# فصل ۲۶ - مجازی‌سازی با KVM | آزمایشگاه

## تمرین ۱: بررسی پشتیبانی
```bash
egrep -c '(vmx|svm)' /proc/cpuinfo
lsmod | grep kvm
sudo kvm-ok
```

## تمرین ۲: نصب و بررسی
```bash
sudo apt install qemu-kvm libvirt-daemon-system libvirt-clients
sudo systemctl status libvirtd
virsh list --all
virsh net-list --all
virsh net-info default
```

## تمرین ۳: ساخت VM آزمایشی
```bash
# دانلود ISO (مثال با Alpine که سبک است)
wget -P /tmp https://dl-cdn.alpinelinux.org/alpine/v3.19/releases/x86_64/alpine-standard-3.19.0-x86_64.iso

sudo virt-install   --name alpine-test   --ram 512   --vcpus 1   --disk path=/var/lib/libvirt/images/alpine-test.qcow2,size=2   --cdrom /tmp/alpine-standard-3.19.0-x86_64.iso   --network network=default   --graphics vnc

virsh list
virsh dominfo alpine-test
virsh snapshot-create-as alpine-test "قبل از تنظیمات"
virsh snapshot-list alpine-test
```

### ✅ چک‌لیست یادگیری
- [ ] پشتیبانی CPU از مجازی‌سازی را بررسی کرده‌ام
- [ ] libvirt را نصب و راه‌اندازی کرده‌ام
- [ ] با virsh VM را مدیریت می‌کنم
- [ ] Snapshot ساخته‌ام

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]