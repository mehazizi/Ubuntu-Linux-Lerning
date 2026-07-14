# فصل ۲۵ - کانتینر و Docker | عیب‌یابی

## مشکل: کانتینر شروع نمی‌شود
```bash
docker ps -a                    # وضعیت کانتینر
docker logs container_name      # لاگ خطا
docker inspect container_name   # اطلاعات کامل
# بررسی exit code:
docker inspect container_name | grep ExitCode
```

## مشکل: پورت در دسترس نیست
```bash
ss -tulnp | grep :8080          # آیا پورت اشغال است؟
docker ps                       # port mapping صحیح؟
sudo ufw allow 8080/tcp         # فایروال را بررسی کنید
```

## مشکل: فضای دیسک Docker زیاد است
```bash
docker system df                # استفاده فضا
docker system prune             # پاک‌سازی همه چیز غیرفعال
docker system prune -a          # شامل imageهای بلااستفاده
docker volume prune             # حذف volumeهای بلااستفاده
```

## مشکل: کانتینرها با هم ارتباط ندارند
```bash
docker network ls               # بررسی networkها
docker inspect container_name | grep Network
# هر دو باید در یک network باشند
docker network connect mynet container_name
```

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[lab|← آزمایشگاه]]