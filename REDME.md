# Домашнее задание к занятию "Система мониторинга Zabbix" - Кузнецов Арсений

# Установите Zabbix Server с веб-интерфейсом.

* sudo -s
* wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_6.0+ubuntu24.04_all.deb
* dpkg -i zabbix-release_latest_6.0+ubuntu24.04_all.deb
* apt update
* apt install zabbix-server-pgsql zabbix-frontend-php php8.3-pgsql zabbix-nginx-conf zabbix-sql-scripts zabbix-agent    
* sudo -u postgres createuser --pwprompt zabbix
* sudo -u postgres createdb -O zabbix zabbix
* zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
* Настройте базу данных для сервера Zabbix
    * Отредактируйте файл /etc/zabbix/zabbix_server.conf
    * DBPassword=password
* Настройте PHP для интерфейса Zabbix
    * Отредактируйте файл /etc/zabbix/nginx.conf, раскомментируйте и задайте директивы «listen» и «server_name». 
    * listen 8080;
    * server_name example.com;   
* systemctl restart zabbix-server zabbix-agent nginx php8.3-fpm
* systemctl enable zabbix-server zabbix-agent nginx php8.3-fpm         


## Images

![This is an alt text.](https://github.com/ArsKuz27/Zabbix_Server/blob/main/Screenshot_1.png?raw=true)
![This is an alt text.](https://github.com/ArsKuz27/Zabbix_Server/blob/main/Screenshot_2.png?raw=true)
![This is an alt text.](https://github.com/ArsKuz27/Zabbix_Server/blob/main/Screenshot_4.png?raw=true)

# Установите Zabbix Agent на два хоста.

* sudo -s
* wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_6.0+ubuntu24.04_all.deb
* dpkg -i zabbix-release_latest_6.0+ubuntu24.04_all.deb
* apt update
* apt install zabbix-agent
* systemctl restart zabbix-agent
* systemctl enable zabbix-agent

## Images

![This is an alt text.](https://github.com/ArsKuz27/Zabbix_Server/blob/main/Screenshot_5.png?raw=true)
![This is an alt text.](https://github.com/ArsKuz27/Zabbix_Server/blob/main/Screenshot_7.png?raw=true)
![This is an alt text.](https://github.com/ArsKuz27/Zabbix_Server/blob/main/Screenshot_6.png?raw=true)
