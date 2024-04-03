# Домашнее задание к занятию «Работа с данными (DDL/DML)»" - Файзиев Давлат.

---

Задание можно выполнить как в любом IDE, так и в командной строке.

### Задание 1
1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.

1.2. Создайте учётную запись sys_temp. 

1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)

1.4. Дайте все права для пользователя sys_temp. 

1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

1.6. Переподключитесь к базе данных от имени sys_temp.

Для смены типа аутентификации с sha2 используйте запрос: 
```sql
ALTER USER 'sys_test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```
1.7. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.

1.8. Восстановите дамп в базу данных.

1.9. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)

*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*

---
### Решение 1
Список выполненных запросов:
```
# п.1.2
CREATE USER 'sys_temp'@'localhost' IDENTIFIED BY 'tempass';

# п.1.3
SELECT user,authentication_string,host FROM mysql.user;

# п.1.4
GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'localhost';

# п.1.5
SHOW GRANTS FOR 'sys_temp'@'localhost';

# п.1.7
CREATE DATABASE `sakila`;
exit
mysql -u sys_temp -p sakila < sakila-schema.sql
mysql -u sys_temp -p sakila < sakila-data.sql

```
  
Cкриншот запроса на получение cписка пользователей в базе данных:
![Скриншот 1](img/1_1.png)
  
Cкриншот запрос на получение списка прав для пользователя sys_temp:
![Скриншот 2](img/1_2.png)
  
Cкриншот ER-диаграммы получившейся базы данных:
![Скриншот 3](img/1_3.png)


---
### Задание 2
Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)
```
Название таблицы | Название первичного ключа
customer         | customer_id
```

---
## Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.

### Задание 3*
3.1. Уберите у пользователя sys_temp права на внесение, изменение и удаление данных из базы sakila.

3.2. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*

---
