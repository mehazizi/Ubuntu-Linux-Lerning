# Process Management - Commands

## مشاهده Processها

ps aux

ps -ef

pstree -p

top

## اجرای برنامه در Background

sleep 1000 &

## مشاهده Jobها

jobs

jobs -l

## انتقال Job به Background

bg %1

## انتقال Job به Foreground

fg %1

## مشاهده وضعیت Process

ps -o pid,stat,cmd

## خاتمه Process

kill PID

kill -15 PID

kill -9 PID

## مشاهده Signalها

kill -l

## اجرای برنامه مستقل از SSH

nohup command &

## مشاهده خروجی nohup

cat nohup.out

tail -f nohup.out