# Домашнее задание к занятию "`Система мониторинга Zabbix`" - `Гусев Алексей`


### Инструкция по выполнению домашнего задания

   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. В личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
      
1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

### Задание 1

`Установите Zabbix Server с веб-интерфейсом`

1. `sudo apt update && sudo apt install -y postgresql`
2. `wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_latest_6.0+debian11_all.deb`
3. `dpkg -i zabbix-release_latest_6.0+debian11_all.deb`
4. `apt update`
5. `apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent`
6. `sudo -u postgres createuser --pwprompt zabbix`
7. `sudo -u postgres createdb -O zabbix zabbix`
8. `zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix`
9. `sudo nano /etc/zabbix/zabbix_server.conf DBPassword=***`
10. `systemctl restart zabbix-server zabbix-agent apache2`
11. `systemctl enable zabbix-server zabbix-agent apache2`

![Скриншот Web-интерфейс zabbix](https://github.com/netolearning777/gitzabbix-hw/blob/main/img/2026-07-16_13-05-47.png)


---

### Задание 2

`Установите Zabbix Agent на два хоста.`

1. `sudo wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_6.0+ubuntu24.04_all.deb`
2. `sudo dpkg -i zabbix-release_latest_6.0+ubuntu24.04_all.deb`
3. `sudo apt update`
4. `sudo apt install zabbix-agent`
5. `sudo systemctl restart zabbix-agent`
6. `sudo systemctl enable zabbix-agent`
7. `sudo nano /etc/zabbix/zabbix_agentd.conf` `Указать в параметр Server= IP адрес сервера zabbix` `перезапустить агент sudo systemctl restart zabbix-agent`
8. `sudo zabbix_agentd -R log_level_increase` `повышает детализацию лога`
9. `sudo tail -f /var/log/zabbix/zabbix_agentd.log`

`Скриншоты`
![hosts](https://github.com/netolearning777/gitzabbix-hw/blob/main/img/2026-07-16_16-41-32.png)

![Latest data удаленной машины](https://github.com/netolearning777/gitzabbix-hw/blob/main/img/2026-07-16_16-44-46.png)

![Latest data zabbix servera](https://github.com/netolearning777/gitzabbix-hw/blob/main/img/2026-07-16_16-45-28.png)

![zabbix_agentd.conf](https://github.com/netolearning777/gitzabbix-hw/blob/main/img/VirtualBox_ubuntu-desktop-24_16_07_2026_16_34_59.png)

![tail -f /var/log/zabbix/zabbix_agentd.log](https://github.com/netolearning777/gitzabbix-hw/blob/main/img/VirtualBox_ubuntu-desktop-24_17_07_2026_09_16_01.png)

![tail -f /var/log/zabbix/zabbix_agentd.log 2](https://github.com/netolearning777/gitzabbix-hw/blob/main/img/VirtualBox_ubuntu-desktop-24_17_07_2026_09_18_35.png)

```
Поле для вставки кода...
....



