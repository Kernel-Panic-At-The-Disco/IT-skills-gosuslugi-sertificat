# Linux_middle

## Вопрос 1  
В директории /var/log вы хотите найти все текстовые файлы с расширением .log, в содержимом которых есть слово timeout, и получить список их имён. Какую команду используете?  

- grep -rl "timeout" /var/log -exec find -name "*.log"  
- find /var/log -type f -grep "timeout" > "*.log"  
- grep -l "timeout" $(find /var/log -type d -name "*.log")  
- find /var/log -name "*.log" | grep -r "timeout"  
- find /var/log -type f -name "*.log" -exec grep -l "timeout" {} \;  

---

## Вопрос 2  
Процесс с PID 7342 завис, но вы хотите попытаться завершить его корректно, прежде чем прибегать к принудительному завершению.  
Какую команду следует использовать на этом этапе?  

- killall -9 7342  
- shutdown 7342  
- kill -9 7342  
- kill -15 7342  
- kill -HALT 7342  

---

## Вопрос 3  
Вы заметили, что процесс с PID 5421 потребляет слишком много CPU, но не хотите его завершать, но хотите снизить влияние этого процесса на систему. Какой командой воспользуетесь?  

- nice -n 10 5421  
- renice +10 5421  
- top -p 5421  
- kill -STOP 5421  
- cpulimit -p 5421 -l 50  

---

## Вопрос 4  
Вам нужно найти все файлы в текущем каталоге и его подкаталогах, которые были изменены за последние 7 дней. Какую команду вы используете?  

- find . -mtime -7  
- find . -atime -7  
- find . -ctime -7  
- find . -mmin -10080  
- find . -daystart -mtime -7  

---

## Вопрос 5  
Вы хотите создать архив всех файлов в каталоге /home/user/data, исключая файлы с расширением .tmp, и сохранить его как /tmp/archive.tar.gz. Какую команду вы используете?  

- tar -czvf /tmp/archive.tar.gz /home/user/data --exclude "*.tmp"  
- tar -cvf /tmp/archive.tar.gz /home/user/data | grep -v ".tmp"  
- zip -r /tmp/archive.tar.gz /home/user/data -x "*.tmp"  
- gzip /home/user/data -o /tmp/archive.tar.gz -e ".tmp"  
- tar -cf /tmp/archive.tar.gz /home/user/data -exclude-from <(find /home/user/data -name "*.tmp")  

---

## Вопрос 6  
Какой утилитой удобно пользоваться для создания и управления виртуальными дисками (loop devices) в Linux?  

- fdisk  
- parted  
- mkfs  
- losetup  
- mount  

---

## Вопрос 7  
Вам нужно просмотреть содержимое файла /var/log/messages, но при этом пропускать все строки, содержащие слово "debug". Какую команду вы используете?  

- cat /var/log/messages | grep -v "debug"  
- less /var/log/messages | exclude "debug"  
- tail /var/log/messages | sed '/debug/d'  
- awk '!/debug/' /var/log/messages  
- grep -invert-match "debug" /var/log/messages  

---

## Вопрос 8  
Вы разрабатываете скрипт на Bash, который должен выполнять несколько команд последовательно. Вам нужно, чтобы следующая команда выполнялась только в том случае, если предыдущая завершилась успешно. Какой оператор для этого используется?  

- ;  
- &&  
- ||  
- |  
- &  

---

## Вопрос 9  
Какой командой можно получить информацию о сетевых интерфейсах, включая IP-адреса, MAC-адреса и статус интерфейса, в современных дистрибутивах Linux (например, Ubuntu 20.04+)?  

- ifconfig -a  
- netstat -rn  
- ip a  
- route -n  
- nmcli device show  

---

## Вопрос 10  
Соединение с хостом 8.8.8.8 работает, но некоторые крупные пакеты не проходят, что указывает на возможную проблему с MTU. Какую команду лучше всего использовать, чтобы проверить доступность хоста и одновременно протестировать прохождение пакетов разного размера, не превышая 50 попыток?  

- hping3 -c 50 --data 1500 8.8.8.8  
- nmap -c 50 --mtu 1472 8.8.8.8  
- ping -c 50 -s 1472 -M do 8.8.8.8  
- traceroute -n -m 50 -s 1500 8.8.8.8  
- ping -c 50 -t 1472 8.8.8.8  

---

## Вопрос 11  
Вы выполнили команду traceroute 8.8.8.8 и получили следующий фрагмент вывода:

3 \*\*\*  
4 10.0.0.1 15.3 ms 15.5 ms 15.1 ms

Что наиболее вероятно объясняет появление \*\*\* на 3-м хопе?

- Устройство на 3-м хопе приняло пакет и переслало его без подтверждения  
- TTL пакета увеличился и устройство его проигнорировало  
- Устройство на 3-м хопе вернуло ICMP-сообщение с кодом 11  
- Пакет дошёл до 3-го хопа, но не был отправлен обратно  
- Устройство на 3-м хопе отбросило пакет из-за проблем с сетью  

---

## Вопрос 12  
Вам нужно узнать, какие порты открыты и какие приложения их используют на вашей локальной системе. Какую команду вы используете?  

- ss -tunlp  
- netstat -ano  
- lsof -i  
- nmap localhost  
- firewall-cmd --list-ports  

---

## Вопрос 13  
Вы хотите автоматически перезагружать сервис "my_service" каждый раз, когда система загружается. Какую команду вы используете для включения автозапуска сервиса?  

- systemctl start my_service  
- systemctl disable my_service  
- systemctl enable my_service  
- systemctl restart my_service  
- systemctl daemon-reload  

---

## Вопрос 14  
Вам нужно изменить владельца файла "document.txt" с текущего пользователя на пользователя "newuser" и группу "devs". Какую команду вы используете?  

- chown newuser:devs document.txt  
- chmod newuser:devs document.txt  
- chgrp devs document.txt  
- usermod -G devs newuser document.txt  
- setfacl -m u:newuser:rwx,g:devs:rwx document.txt  

---

## Вопрос 15  
Вы хотите узнать, какие системные вызовы делает запущенный процесс с PID 1234. Какую команду вы используете?  

- top -p 1234  
- ps -ef | grep 1234  
- strace -p 1234  
- lsof -p 1234  
- stat /proc/1234  

---

## Вопрос 16  
Вы хотите временно изменить сетевую настройку, а именно добавить дополнительный IP-адрес 192.168.1.100/24 на интерфейс eth0, без сохранения изменений после перезагрузки. Какую команду вы используете?  

- ifconfig eth0 192.168.1.100 netmask 255.255.255.0  
- ip addr add 192.168.1.100/24 dev eth0  
- netplan apply  
- nmcli connection modify eth0 ipv4.addresses 192.168.1.100/24  
- route add -host 192.168.1.100 dev eth0  

---

## Вопрос 17  
Какой командой вы воспользуетесь, чтобы найти и отобразить только уникальные строки в файле access.log, игнорируя регистр символов?  

- sort access.log | uniq -i  
- cat access.log | sort | uniq  
- uniq -c access.log  
- grep -o access.log | sort -u  
- awk '!seen[$0]++' access.log  

---

## Вопрос 18  
Вам нужно создать символическую ссылку с именем "mylink" на файл "/home/user/document.pdf". Какую команду вы используете?  

- ln /home/user/document.pdf mylink  
- ln -s /home/user/document.pdf mylink  
- cp -s /home/user/document.pdf mylink  
- mv /home/user/document.pdf mylink  
- link /home/user/document.pdf mylink  

---

## Вопрос 19  
Какой командой в Linux можно узнать время работы (uptime) системы?  

- w  
- who  
- uptime  
- last  
- top  

---

## Вопрос 20  
Вы хотите просмотреть список всех установленных пакетов в вашей системе, использующей менеджер пакетов `dpkg`. Какую команду вы используете?  

- apt list  
- dpkg -l  
- apt show installed  
- rpm -qa  
- yum list installed  

---

## Вопрос 21  
Какая команда используется для проверки целостности файловой системы Linux на предмет ошибок?  

- fsck  
- tune2fs  
- badblocks  
- dumpe2fs  
- e2fsck -n  

---

## Вопрос 22  
Вы хотите создать нового пользователя "testuser" в системе Linux. Какую команду вы используете?  

- userdel testuser  
- passwd testuser  
- groupadd testuser  
- adduser testuser  
- usermod testuser  

---

## Вопрос 23  
Вы хотите увидеть содержимое каталога `/etc` вместе с скрытыми файлами и подробной информацией (права доступа, владелец, размер, дата изменения). Какую команду вы используете?  

- ls -a /etc  
- ls -l /etc  
- ls -F /etc  
- ls -R /etc  
- ls -la /etc  

---

## Вопрос 24  
Вам нужно временно изменить переменную окружения `PATH` так, чтобы каталог `/opt/custom_bins` был добавлен в начало `PATH` только для текущей сессии терминала. Какую команду вы используете?  

- export PATH=$PATH:/opt/custom_bins  
- PATH=/opt/custom_bins:$PATH  
- set PATH=/opt/custom_bins:$PATH  
- export PATH=/opt/custom_bins:$PATH  
- env PATH=/opt/custom_bins:$PATH  

---

## Вопрос 25  
Какой командой вы воспользуетесь, чтобы найти все процессы, запущенные от пользователя "www-data"?  

- ps aux | grep www-data  
- top -u www-data  
- pgrep -u www-data  
- users | grep www-data  
- find /proc -user www-data  

---

## Вопрос 26  
С помощью какой команды можно создать архив из каталога `project` в формате `.tar.gz`?  

- gzip project > project.tar.gz  
- zip project.tar.gz project  
- tar -czf project.tar.gz project  
- tar -cvf project.tar.gz project  
- archive project > project.tar.gz  

---

## Вопрос 27  
Какой из указанных инструментов используется для создания резервной копии всего каталога с сохранением структуры подкаталогов?  

- diff  
- gzip  
- mv  
- unzip  
- rsync  