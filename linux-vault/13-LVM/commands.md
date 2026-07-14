# فصل ۱۳ - LVM | دستورات

## Physical Volume
```bash
sudo pvcreate /dev/sdb              # ساخت PV
sudo pvcreate /dev/sdb /dev/sdc     # چند دیسک
sudo pvdisplay                      # اطلاعات کامل
sudo pvs                            # خلاصه
sudo pvremove /dev/sdb              # حذف PV
```

## Volume Group
```bash
sudo vgcreate data_vg /dev/sdb      # ساخت VG
sudo vgcreate data_vg /dev/sdb /dev/sdc  # از چند PV
sudo vgextend data_vg /dev/sdd      # اضافه کردن PV
sudo vgreduce data_vg /dev/sdd      # حذف PV
sudo vgdisplay                      # اطلاعات کامل
sudo vgs                            # خلاصه
sudo vgremove data_vg               # حذف VG
```

## Logical Volume
```bash
sudo lvcreate -L 20G -n lv_data data_vg     # با اندازه مشخص
sudo lvcreate -l 100%FREE -n lv_data data_vg # تمام فضا
sudo lvcreate -l 50%VG -n lv_data data_vg   # ۵۰٪ VG
sudo lvdisplay                              # اطلاعات کامل
sudo lvs                                    # خلاصه
sudo lvremove data_vg/lv_data              # حذف LV

# مسیر LV
/dev/data_vg/lv_data    یا    /dev/mapper/data_vg-lv_data
```

## گسترش LV
```bash
sudo lvextend -L +10G data_vg/lv_data       # اضافه کردن ۱۰G
sudo lvextend -L 50G data_vg/lv_data        # رساندن به ۵۰G
sudo lvextend -l +100%FREE data_vg/lv_data  # همه فضای آزاد

# گسترش فایل‌سیستم (بدون umount)
sudo resize2fs /dev/data_vg/lv_data         # ext4
sudo xfs_growfs /mount/point                # xfs

# هر دو کار را با هم:
sudo lvextend -r -L +10G data_vg/lv_data    # -r برای resize خودکار
```

## Snapshot
```bash
sudo lvcreate -L 5G -s -n lv_snap data_vg/lv_data  # ساخت snapshot
sudo lvdisplay data_vg/lv_snap               # بررسی
sudo lvconvert --merge data_vg/lv_snap       # برگشت به snapshot
sudo lvremove data_vg/lv_snap                # حذف snapshot
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]