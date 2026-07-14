# فصل ۲۵ - کانتینر و Docker | دستورات

## نصب Docker
```bash
curl -fsSL https://get.docker.com | bash
sudo usermod -aG docker $USER
newgrp docker
docker --version
```

## مدیریت Image
```bash
docker images                   # لیست imageها
docker pull nginx               # دانلود image
docker pull nginx:1.24          # نسخه مشخص
docker pull ubuntu:22.04
docker rmi nginx                # حذف image
docker image prune              # حذف imageهای بلااستفاده
docker build -t myapp:1.0 .     # ساخت از Dockerfile
docker tag myapp:1.0 myapp:latest
```

## مدیریت Container
```bash
docker run nginx                # اجرا (foreground)
docker run -d nginx             # در پس‌زمینه
docker run -d -p 80:80 nginx    # با port mapping
docker run -d -p 80:80 --name webserver nginx
docker run -it ubuntu bash      # تعاملی
docker run --rm ubuntu echo hi  # حذف بعد از اجرا

docker ps                       # کانتینرهای در حال اجرا
docker ps -a                    # همه کانتینرها
docker stop webserver
docker start webserver
docker restart webserver
docker rm webserver             # حذف کانتینر
docker rm -f webserver          # حذف اجباری
```

## بررسی و عیب‌یابی
```bash
docker logs webserver           # لاگ کانتینر
docker logs -f webserver        # لاگ زنده
docker exec -it webserver bash  # ورود به کانتینر
docker exec webserver ls /etc
docker inspect webserver        # اطلاعات کامل
docker stats                    # مصرف منابع زنده
docker top webserver            # فرآیندهای داخل
```

## Volume
```bash
docker volume create mydata
docker volume ls
docker volume inspect mydata
docker run -d -v mydata:/var/lib/mysql mysql
docker run -d -v /host/path:/container/path nginx
docker volume rm mydata
docker volume prune
```

## Network
```bash
docker network ls
docker network create mynet
docker run -d --network mynet --name db mysql
docker run -d --network mynet --name web nginx
docker network inspect mynet
```

## Docker Compose
```bash
docker-compose up -d            # راه‌اندازی
docker-compose down             # توقف و حذف
docker-compose down -v          # با حذف volume
docker-compose ps               # وضعیت
docker-compose logs -f          # لاگ زنده
docker-compose restart web      # restart یک سرویس
docker-compose pull             # به‌روزرسانی imageها
docker-compose build            # ساخت مجدد
```

## Rootless Docker
```bash
dockerd-rootless-setuptool.sh install
export DOCKER_HOST=unix://$XDG_RUNTIME_DIR/docker.sock
docker run hello-world
```

---
[[summary|← خلاصه]] | [[lab|← آزمایشگاه]] | [[troubleshooting|← عیب‌یابی]]