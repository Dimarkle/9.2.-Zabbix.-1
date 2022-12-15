# 9.2.-Zabbix. Часть 1. Рогачев Дмитрий


# Задание 1

1. Уставливаем PostgreSQL
Sudo apt install postgresql

2. Установливаем репозиторий Zabbix
wget https://repo.zabbix.com/zabbix/6.2/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.2-4%2Bubuntu22.04_all.deb
dpkg -i zabbix-release_6.2-4+ubuntu22.04_all.deb
apt updat

3. Установливаем Zabbix сервер, веб-интерфейс и агент
apt install zabbix-server-pgsql zabbix-frontend-php php8.1-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent

4. Создаем базу данных
sudo -u postgres createuser --pwprompt zabbix
sudo -u postgres createdb -O zabbix zabbix

5. На хосте Zabbix сервера импортируем начальную схему и данные. Вводим недавно созданный пароль
zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix

6. Настраимаем базу данных для Zabbix сервера
Редактируем файл /etc/zabbix/zabbix_server.conf
DBPassword=password

7. Запускаем процессы Zabbix сервера и агента
systemctl restart zabbix-server zabbix-agent apache2
systemctl enable zabbix-server zabbix-agent apache2



![Без имени](https://user-images.githubusercontent.com/118626944/207937755-0a01f541-6e7b-451e-810a-49369ec43165.jpg)




# Задание 2







# Задание 3
