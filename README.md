# Домашнее задание к занятию "`Операции с данными в SQL`" - `Кудряшов Андрей`


### Задание 1
```
sudo apt update && sudo apt upgrade -y
```
```
sudo apt install mysql-server -y
```
```
sudo apt install unzip -y
```
```
cd /tmp
wget https://downloads.mysql.com/docs/sakila-db.zip
unzip sakila-db.zip
```
```
sudo mysql -u root
```
```
CREATE USER 'kudryashov'@'localhost' IDENTIFIED BY 'test_passwd_123';
GRANT ALL PRIVILEGES ON *.* TO 'kudryashov'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```
```
mysql -u kudryashov -p sakila
```
```
SOURCE /tmp/sakila-db/sakila-schema.sql;
SOURCE /tmp/sakila-db/sakila-data.sql;
```
```
SHOW DATABASES;
```
```
SELECT DISTINCT district
FROM address
WHERE district LIKE 'K%a'
  AND district NOT LIKE '% %';
```
```
EXIT;
```


---

### Задание 2
```
SELECT *
FROM payment
WHERE payment_date >= '2005-06-15'
  AND payment_date < '2005-06-19'
  AND amount > 10.00;
```


---

### Задание 3

```
SELECT *
FROM rental
ORDER BY rental_date DESC
LIMIT 5;
```


---

### Задание 4

```
SELECT 
  REPLACE(LOWER(first_name), 'll', 'pp') AS first_name,
  LOWER(last_name) AS last_name
FROM customer
WHERE active = 1
  AND (first_name = 'Kelly' OR first_name = 'Willie');
```


---

### Задание 5

```
SELECT
  SUBSTRING_INDEX(email, '@', 1) AS local_part,
  SUBSTRING_INDEX(email, '@', -1) AS domain_part
FROM customer;
```



---


### Задание 6

```
SELECT
  CONCAT(
    UPPER(LEFT(LOWER(SUBSTRING_INDEX(email, '@', 1)), 1)),
    SUBSTRING(LOWER(SUBSTRING_INDEX(email, '@', 1)), 2)
  ) AS local_part_capitalized,
  CONCAT(
    UPPER(LEFT(LOWER(SUBSTRING_INDEX(email, '@', -1)), 1)),
    SUBSTRING(LOWER(SUBSTRING_INDEX(email, '@', -1)), 2)
  ) AS domain_part_capitalized
FROM customer;
```


---

Сохранить результат для отчёта:
```
mysql -u root -p sakila -e "SELECT DISTINCT district FROM address WHERE district LIKE 'K%a' AND district NOT LIKE '% %';" > task1.txt
```
