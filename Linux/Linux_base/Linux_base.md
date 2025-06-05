# Linux_base

## Вопрос 1  
Вы работаете в терминале и хотите увидеть, в каком каталоге находитесь сейчас. Какую команду нужно использовать?  

- cd  
- pwd  
- ls  
- hostname  
- echo $PATH  

---

## Вопрос 2  
Вы находитесь в каталоге /home/user/docs/reports. Какой командой можно перейти в директорию /home/user/docs?  

- cd ..  
- cd ./docs  
- cd root  
- cd /  
- cd ~  

---

## Вопрос 3  
Какая команда НЕ используется для работы с файлами и каталогами как объектами файловой системы?  

- mv  
- grep  
- rm  
- mkdir  
- cp  

---

## Вопрос 4  
Вы подготовили файл summary.txt и хотите создать резервную копию этого файла в каталоге /home/user/backups. Какую команду используете?  

- mkdir /home/user/backups/summary.txt  
- copy summary.txt /home/user/backups/  
- mv summary.txt /home/user/backups/  
- cp summary.txt /home/user/backups/  
- rm summary.txt && touch /home/user/backups/summary.txt  

---

## Вопрос 5  
Вы находитесь в домашнем каталоге пользователя и хотите найти файл report.txt. Какую команду следует использовать?  

- Применить ps aux | grep report.txt  
- Использовать grep по пути для поиска имени файла  
- Использовать find с опцией -name и поиском в текущем каталоге  
- Использовать команду whereis report.txt для поиска по всей системе  
- Просмотреть права доступа на каждый каталог  

---

## Вопрос 6  
Вы хотите найти все строки, содержащие слово "ERROR", в файлах с расширением .log, находящихся в текущем каталоге и его подкаталогах. Какая команда подойдёт лучше всего?  

- grep "ERROR" *.log  
- locate "*.log" | grep "ERROR"  
- find . -name "*.log" | grep "ERROR"  
- cat *.log | grep "ERROR"  
- grep -r "ERROR" --include="*.log"  

---

## Вопрос 7  
Чем отличается оператор >> от оператора > в командной строке Linux?  

- >> создаёт файл, а > записывает в уже существующий  
- >> выводит только ошибки, а > обычный вывод  
- >> используется только в пайплайнах.  
- >> добавляет вывод в конец файла, а > перезаписывает файл  
- > работает только с текстовыми файлами  

---

## Вопрос 8  
Вам нужно сохранить список всех видимых файлов и папок в текущем каталоге в файл list.txt для дальнейшего анализа. Какую команду нужно ввести?  

- ls list.txt  
- ls -a > list.txt  
- ls > list.txt  
- cat list.txt > ls  
- echo list.txt > ls  

---

## Вопрос 9  
Как называется учётная запись в Linux, которая обладает полным доступом ко всем файлам и операциям в системе?  

- owner  
- root  
- admin  
- user  
- guest  

---

## Вопрос 10  
Вы создали новый файл my_script.sh и хотите сделать его исполняемым, чтобы запускать его как программу. Какой командой вы воспользуетесь?  

- chmod +x my_script.sh  
- chown my_script.sh  
- exec my_script.sh  
- sudo my_script.sh  
- ./my_script.sh  

---

## Вопрос 11  
Вы хотите просмотреть содержимое файла example.log в реальном времени, то есть, чтобы новые строки появлялись сразу же, как только они добавляются в файл. Какую команду вы используете?  

- less example.log  
- more example.log  
- cat example.log  
- tail -f example.log  
- head example.log  

---

## Вопрос 12  
Вам нужно удалить каталог old_files и всё его содержимое, включая подкаталоги и файлы. Какую команду вы будете использовать?  

- rm old_files  
- rmdir old_files  
- rm -r old_files  
- del old_files  
- clear old_files  

---

## Вопрос 13  
Какая команда используется для проверки сетевого подключения к удаленному хосту по IP-адресу или доменному имени?  

- ifconfig  
- ip addr  
- ping  
- netstat  
- route  

---

## Вопрос 14  
Вы хотите узнать, какие процессы в данный момент запущены в вашей системе. Какая команда отобразит список всех активных процессов?  

- top  
- kill  
- pstree  
- bg  
- fg  

---

## Вопрос 15  
Какой командой вы воспользуетесь для установки нового программного пакета в вашей системе Linux, используя менеджер пакетов apt?  

- apt remove package_name  
- apt update package_name  
- apt search package_name  
- apt install package_name  
- apt purge package_name  

---

## Вопрос 16  
Вы хотите узнать, какие системные службы запущены и работают в вашей системе Linux. Какая команда для этого подойдет?  

- ps aux  
- top  
- systemctl status  
- systemctl list-units --type=service  
- journalctl -f  

---

## Вопрос 17  
Какой командой вы воспользуетесь, чтобы узнать объем свободного места на жестком диске?  

- df -h  
- du -h  
- free -h  
- ls -lh  
- fdisk -l  

---

## Вопрос 18  
Вам нужно просмотреть список последних 10 записей в системном журнале. Какую команду следует использовать?  

- cat /var/log/syslog | head -n 10  
- tail -n 10 /var/log/syslog  
- less /var/log/syslog  
- more /var/log/syslog  
- grep -n 10 /var/log/syslog  

---

## Вопрос 19  
Вы хотите узнать, какой пользователь в данный момент вошел в систему. Какую команду следует использовать?  

- whoami  
- id  
- finger  
- logname  
- env  

---

## Вопрос 20  
Вам нужно создать пустой файл с именем "empty_file.txt". Какую команду вы будете использовать?  

- echo > empty_file.txt  
- new empty_file.txt  
- touch empty_file.txt  
- create empty_file.txt  
- cp /dev/null empty_file.txt  

---

## Вопрос 21  
Какой протокол используется для защищенного удаленного подключения к серверу Linux через командную строку?  

- FTP  
- Telnet  
- HTTP  
- SSH  
- RDP  

---

## Вопрос 22  
Вы хотите остановить процесс с PID 1234. Какой командой вы воспользуетесь?  

- kill -9 1234  
- kill -15 1234  
- stop 1234  
- terminate 1234  
- halt 1234  

---

## Вопрос 23  
Как изменить права доступа к файлу script.sh, чтобы только владелец имел полные права (чтение, запись, выполнение), а все остальные не имели никаких прав?  

- chmod 700 script.sh  
- chmod 777 script.sh  
- chmod 644 script.sh  
- chmod 755 script.sh  
- chmod +x script.sh  

---

## Вопрос 24  
Вы хотите создать новый каталог "my_project" и сразу же перейти в него. Какой командой вы это сделаете?  

- mkdir my_project && cd my_project  
- cd my_project && mkdir my_project  
- make my_project ; cd my_project  
- mkdir my_project | cd my_project  
- newdir my_project && goto my_project