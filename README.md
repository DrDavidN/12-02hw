# 12.2 «Работа с данными (DDL/DML)» - Дрибноход Давид

### Задание 1
1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.

1.2. Создайте учётную запись sys_temp. 
```sql
CREATE USER 'sys_temp'@'localhost' IDENTIFIED BY '987654321';
```

1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)
![image](https://github.com/DrDavidN/12-02hw/assets/128225763/88ca9f9d-f199-44ae-aea5-2a0175f54678)

1.4. Дайте все права для пользователя sys_temp. 
```sql
GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'localhost';
```

1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)
![image](https://github.com/DrDavidN/12-02hw/assets/128225763/80c207ec-a8d4-446b-b59e-588288840c9f)

1.6. Переподключитесь к базе данных от имени sys_temp.
```bash
mysql -usys_temp -p
```

Для смены типа аутентификации с sha2 используйте запрос: 
```sql
ALTER USER 'sys_test'@'localhost' IDENTIFIED WITH mysql_native_password BY '987654321';
```
1.6. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.
```bash
wget https://downloads.mysql.com/docs/sakila-db.zip
unzip sakila-db.zip
```

1.7. Восстановите дамп в базу данных.
```sql
source /root/sakila-db/sakila-schema.sql;
source /root/sakila-db/sakila-data.sql;
```

1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)
![image](https://github.com/DrDavidN/12-02hw/assets/128225763/511d1e39-a88a-44d5-a719-55183b92de65)

*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*


### Задание 2
Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)
```
Название таблицы | Название первичного ключа
customer         | customer_id
```

```
Название таблицы   | Название первичного ключа
actor              | actor_id
address            | address_id
category           | category_id
city               | city_id
country            | country_id
customer           | customer_id
film               | film_id
film_actor         | actor_id, film_id
film_category      | film_id, category_id
film_text          | film_id
inventory          | inventory_id
language           | language_id
payment            | payment_id
rental             | rental_id
staff              | staff_id
store              | store_id
```


### Задание 3*
3.1. Уберите у пользователя sys_temp права на внесение, изменение и удаление данных из базы sakila.
```sql
revoke insert, update, alter, delete on sakila.* from 'sys_temp'@'%';
```

3.2. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)
![image](https://github.com/DrDavidN/12-02hw/assets/128225763/089a519e-f761-4061-8fe6-5c5a1bcea9c4)

*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*
