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

Использовал следующие команды

 Установил репозиторий Zabbix
 
wget https://repo.zabbix.com/zabbix/6.2/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.2-4%2Bubuntu22.04_all.deb
dpkg -i zabbix-release_6.2-4+ubuntu22.04_all.deb
apt update

Установил Zabbix агент

apt install zabbix-agent

Перезапуск
systemctl restart zabbix-agent и systemctl enable zabbix-agent

![download](https://user-images.githubusercontent.com/118626944/207966826-6931d173-c55a-46ba-bd45-c6f3d1e2d4c0.png)

![Без имени2](https://user-images.githubusercontent.com/118626944/207967204-d61148e9-f223-4579-bacf-a4eca7b17b73.jpg)


![Без имени 3jpg](https://user-images.githubusercontent.com/118626944/207967215-58487ed3-69d5-4a89-b250-3e860a26b85e.jpg)

![Без имени4](https://user-images.githubusercontent.com/118626944/207967229-531bf502-0b08-4237-9777-a48329cd9ee8.jpg)


![Без имени5](https://user-images.githubusercontent.com/118626944/207967240-0abb330e-db53-47a5-8834-49b08b919d9a.jpg)

![Без имени6](https://user-images.githubusercontent.com/118626944/207967269-b7a70390-513e-42be-9489-874cc29e29bc.jpg)




