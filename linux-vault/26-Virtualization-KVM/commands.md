# فصل ۲۶ - مجازی‌سازی با KVM | دستورات

## نصب
```bash
sudo apt install qemu-kvm libvirt-daemon-system   libvirt-clients bridge-utils virt-manager
sudo usermod -aG libvirt $USER
sudo usermod -aG kvm $USER
newgrp libvirt
sudo systemctl enable --now libvirtd
```

## virsh - مدیریت VM
```bash
virsh list                      # VMهای در حال اجرا
virsh list --all                # همه VMها
virsh start vm-name             # راه‌اندازی
virsh shutdown vm-name          # خاموش کردن مؤدبانه
virsh destroy vm-name           # خاموش اجباری
virsh reboot vm-name            # ریبوت
virsh suspend vm-name           # تعلیق
virsh resume vm-name            # ادامه
virsh autostart vm-name         # راه‌اندازی خودکار
virsh autostart --disable vm-name
```

## اطلاعات و بررسی
```bash
virsh dominfo vm-name           # اطلاعات VM
virsh domstate vm-name          # وضعیت
virsh vcpuinfo vm-name          # CPU
virsh dommemstat vm-name        # حافظه
virsh domblklist vm-name        # دیسک‌ها
virsh net-list                  # شبکه‌های مجازی
virsh net-list --all
```

## Snapshot
```bash
virsh snapshot-create-as vm-name snap1 "توضیح"
virsh snapshot-list vm-name
virsh snapshot-revert vm-name snap1
virsh snapshot-delete vm-name snap1
```

## ساخت VM با virt-install
```bash
sudo virt-install   --name ubuntu-server   --ram 2048   --vcpus 2   --disk path=/var/lib/libvirt/images/ubuntu.qcow2,size=20   --os-variant ubuntu22.04   --network bridge=virbr0   --graphics none   --console pty,target_type=serial   --location 'http://archive.ubuntu.com/ubuntu/dists/jammy/main/installer-amd64/'
```

## Clone و Migration
```bash
sudo virt-clone --original vm-name --name vm-clone --auto-clone
virsh migrate --live vm-name qemu+ssh://target-host/system
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]