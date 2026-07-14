# Chapter 08 - Systemd & Service Management

## Systemd

- PID 1 سیستم لینوکس معمولاً Systemd است.
    
- Systemd سرویس‌ها، فرآیند بوت و وابستگی‌ها را مدیریت می‌کند.
    
- بسیاری از توزیع‌های مدرن لینوکس از Systemd استفاده می‌کنند.
    

## Service

- Service مجموعه‌ای از Processها است که یک وظیفه مشخص را انجام می‌دهد.
    
- مثال‌ها:
    
    - ssh.service
        
    - cron.service
        
    - rsyslog.service
        

## وضعیت سرویس‌ها

### Active

وضعیت فعلی سرویس را نشان می‌دهد.

نمونه‌ها:

- active (running)
    
- inactive
    
- failed
    

### Enabled

مشخص می‌کند سرویس در بوت بعدی اجرا شود یا خیر.

نمونه‌ها:

- enabled
    
- disabled
    
- static
    
- masked
    

## Active vs Enabled

- Active = وضعیت فعلی سرویس
    
- Enabled = وضعیت اجرای خودکار در بوت بعدی
    

چهار حالت ممکن:

- active + enabled
    
- active + disabled
    
- inactive + enabled
    
- inactive + disabled
    

## Reload vs Restart

### Restart

- سرویس متوقف و مجدداً اجرا می‌شود.
    
- PID معمولاً تغییر می‌کند.
    

### Reload

- سرویس بدون توقف، تنظیمات جدید را بازخوانی می‌کند.
    
- PID معمولاً تغییر نمی‌کند.
    

## Mask

قوی‌ترین روش جلوگیری از اجرای سرویس است.

ویژگی‌ها:

- سرویس قابل Start شدن نیست.
    
- حتی اجرای دستی Start نیز رد می‌شود.
    
- با Unmask قابل بازگشت است.
    

## Journal

Journal سیستم ثبت لاگ‌های Systemd است.

قابلیت‌ها:

- مشاهده لاگ کل سیستم
    
- مشاهده لاگ یک سرویس خاص
    
- مشاهده لاگ بوت جاری
    
- مشاهده لاگ زنده
    

## Target

Targetها مقصد نهایی بوت سیستم هستند.

Targetهای مهم:

- multi-user.target
    
- graphical.target
    
- rescue.target
    

## Dependency Tree

Dependency Tree با Process Tree متفاوت است.

مثال:

graphical.target

└── multi-user.target

یعنی graphical.target برای اجرا به multi-user.target وابسته است.

## Process Tree vs Dependency Tree

### Process Tree

رابطه Parent و Child Processها را نشان می‌دهد.

مثال:

systemd  
└── sshd  
└── bash

### Dependency Tree

وابستگی سرویس‌ها و Targetها را نشان می‌دهد.

مثال:

graphical.target  
└── multi-user.target

## Troubleshooting Workflow

برای بررسی یک سرویس:

1. بررسی وضعیت سرویس
    
2. بررسی لاگ‌ها
    
3. تحلیل خطا
    
4. اعمال اصلاحات