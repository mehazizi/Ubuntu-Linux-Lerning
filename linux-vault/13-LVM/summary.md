# فصل ۱۳ - LVM | خلاصه

## LVM چیست؟
Logical Volume Manager - لایه انتزاعی بین دیسک فیزیکی و فایل‌سیستم که انعطاف بالایی برای مدیریت فضا می‌دهد.

## معماری LVM
```
Physical Disks  →  Physical Volumes (PV)
                        ↓
                  Volume Group (VG)
                        ↓
               Logical Volumes (LV)
                        ↓
                   Filesystem
```

## مزایای LVM
- گسترش حجم بدون downtime
- کاهش حجم (با احتیاط)
- Snapshot برای پشتیبان‌گیری
- ترکیب چند دیسک در یک VG
- انتقال داده بین دیسک‌ها

## اصطلاحات
| اصطلاح | توضیح |
|---------|-------|
| PV (Physical Volume) | دیسک یا پارتیشن آماده‌شده برای LVM |
| VG (Volume Group) | گروهی از PV‌ها |
| LV (Logical Volume) | حجم منطقی روی VG |
| PE (Physical Extent) | واحد تخصیص (پیش‌فرض ۴MB) |

---
[[commands|← دستورات]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]