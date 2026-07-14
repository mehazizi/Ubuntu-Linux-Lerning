# Process Management - Summary

- Process = برنامه در حال اجرا
    
- PID = شناسه یکتای Process
    
- PPID = شناسه Parent Process
    
- Parent Process می‌تواند Child Process ایجاد کند
    
- Child Process توسط Parent ساخته می‌شود
    
- Orphan Process = فرزندی که Parent آن از بین رفته است
    
- Zombie Process = Process مرده‌ای که هنوز توسط Parent جمع‌آوری نشده است
    
- هر Service در نهایت یک یا چند Process است
    
- systemd مدیر Serviceها و Processهای سیستمی است
    

### وضعیت‌های مهم Process

- R = Running
    
- S = Sleeping
    
- T = Stopped
    
- Z = Zombie
    
- D = Uninterruptible Sleep
    

### Job Control

- Foreground = برنامه کنترل ترمینال را در اختیار دارد
    
- Background = برنامه در پس‌زمینه اجرا می‌شود
    
- Ctrl+C = خاتمه Process
    
- Ctrl+Z = توقف موقت Process
    
- bg = ادامه اجرای Process در Background
    
- fg = انتقال Process به Foreground
    

### Signals مهم

- SIGHUP (1) = قطع Session
    
- SIGINT (2) = Ctrl+C
    
- SIGKILL (9) = خاتمه اجباری
    
- SIGTERM (15) = خاتمه عادی
    
- SIGCONT (18) = ادامه اجرا
    
- SIGTSTP (20) = Ctrl+Z
    

### نکات مهم

- kill در واقع Signal ارسال می‌کند
    
- kill -9 آخرین راه‌حل است
    
- ابتدا از kill یا kill -15 استفاده می‌شود
    
- nohup باعث ادامه اجرای برنامه بعد از قطع SSH می‌شود