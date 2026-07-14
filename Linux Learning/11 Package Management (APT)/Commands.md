# Chapter 11 - Commands

# Repository

مشاهده Repositoryها

cat /etc/apt/sources.list

---

مشاهده Repositoryهای اضافه

ls /etc/apt/sources.list.d/

---

ویرایش Repository

sudo nano /etc/apt/sources.list

---

پشتیبان‌گیری از Repository

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak

---

# Update

sudo apt update

---

# Upgrade

sudo apt upgrade

---

sudo apt full-upgrade

---

# Install

sudo apt install package-name

---

نصب فایل محلی

sudo apt install ./package.deb

---

sudo apt install /path/to/package.deb

---

# Remove

sudo apt remove package-name

---

sudo apt purge package-name

---

sudo apt autoremove

---

sudo apt clean

---

# Search

apt search package-name

---

apt show package-name

---

apt depends package-name

---

apt rdepends package-name

---

apt policy package-name

---

apt list --installed

---

apt list --upgradable

---

# Download

apt download package-name

---

# dpkg

dpkg -L package-name

---

dpkg -S /path/to/file

---

dpkg -l

---

dpkg -l | grep package-name

---

# Program

which program

---

type -a program

---

# Cache

ls /var/cache/apt/archives/

---

du -sh /var/cache/apt/archives/

---

# GPG

ls /etc/apt/keyrings/