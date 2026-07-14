# Process Management - Lab Exercises

## Lab 1 - ساخت Process در Background

sleep 1000 &

jobs -l

---

## Lab 2 - مشاهده Processها

ps aux | grep sleep

ps -ef | grep sleep

pstree -p

---

## Lab 3 - انتقال به Foreground

sleep 1000 &

jobs -l

fg %1

Ctrl+C

---

## Lab 4 - توقف Process

sleep 1000

Ctrl+Z

jobs -l

---

## Lab 5 - ادامه Process متوقف شده

sleep 1000

Ctrl+Z

bg %1

jobs -l

---

## Lab 6 - خاتمه Process

sleep 1000 &

jobs -l

kill PID

jobs -l

---

## Lab 7 - خاتمه اجباری

sleep 1000 &

kill -9 PID

---

## Lab 8 - تست nohup

nohup sleep 1000 &

ps -ef | grep sleep

قطع SSH

اتصال مجدد

ps -ef | grep sleep

---

## Lab 9 - بررسی وضعیت Process

sleep 1000 &

ps -o pid,stat,cmd -p PID

sleep 1000

Ctrl+Z

ps -o pid,stat,cmd -p PID

مشاهده تفاوت وضعیت‌های S و T