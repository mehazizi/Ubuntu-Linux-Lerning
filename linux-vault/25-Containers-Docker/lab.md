# فصل ۲۵ - کانتینر و Docker | آزمایشگاه

## تمرین ۱: اولین کانتینر
```bash
docker run hello-world
docker run -it ubuntu:22.04 bash
# داخل کانتینر:
apt update && apt install -y curl
curl https://ifconfig.me
exit
docker ps -a
```

## تمرین ۲: وب‌سرور با Nginx
```bash
docker run -d -p 8080:80 --name myweb nginx
docker ps
curl http://localhost:8080
docker logs myweb
docker exec -it myweb bash
# داخل: ls /usr/share/nginx/html/
exit
docker stop myweb
docker rm myweb
```

## تمرین ۳: Dockerfile سفارشی
```bash
mkdir ~/myapp && cd ~/myapp
cat > Dockerfile << 'EOF'
FROM ubuntu:22.04
RUN apt-get update && apt-get install -y nginx && rm -rf /var/lib/apt/lists/*
COPY index.html /var/www/html/
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
EOF

echo "<h1>سلام از Docker!</h1>" > index.html
docker build -t mywebsite:1.0 .
docker run -d -p 8080:80 mywebsite:1.0
curl http://localhost:8080
```

## تمرین ۴: Docker Compose
```bash
mkdir ~/compose-test && cd ~/compose-test
cat > docker-compose.yml << 'EOF'
version: '3.8'
services:
  web:
    image: nginx:alpine
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/share/nginx/html

  db:
    image: mysql:8.0
    environment:
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: mydb
    volumes:
      - db_data:/var/lib/mysql

volumes:
  db_data:
EOF

mkdir html && echo "<h1>Compose Test</h1>" > html/index.html
docker-compose up -d
docker-compose ps
docker-compose logs
docker-compose down -v
```

### ✅ چک‌لیست یادگیری
- [ ] تفاوت Image و Container را می‌دانم
- [ ] Dockerfile نوشته‌ام
- [ ] Volume و Network را پیکربندی کرده‌ام
- [ ] با Docker Compose کار کرده‌ام

---
[[summary|← خلاصه]] | [[commands|← دستورات]] | [[troubleshooting|← عیب‌یابی]]