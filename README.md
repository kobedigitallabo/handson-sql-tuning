# handson-sql-tuning
KDLのSQLチューニングハンズオンで利用するDokcerの定義ファイルです。cloneして使ってください。

# 事前準備
- dockerおよびdocker-composeをインストールして使えるようにしてください。
- 以下のソースのMYSQL_ROOT_PASSWORDの値を、ご自身の好きな値にしてください。
  - `./ver5.7/mysql/mysql.env`
  - `./ver8.0/mysql/mysql.env`

# インストール

```
$ cd ver8.0
$ docker-compose build
$ docker-compose up -d
$ docker exec -it test_tuning_db /bin/bash

# mysql -u root -p
Enter password:   ./mysql/mysql.envのMYSQL_ROOT_PASSWORDを参照
mysql> use sakila;

Database changed
mysql> SHOW FULL TABLES;
+----------------------------+------------+
| Tables_in_sakila           | Table_type |
+----------------------------+------------+
| actor                      | BASE TABLE |
| actor_info                 | VIEW       |
| address                    | BASE TABLE |
| category                   | BASE TABLE |
| city                       | BASE TABLE |
| country                    | BASE TABLE |
| customer                   | BASE TABLE |
| customer_list              | VIEW       |
| film                       | BASE TABLE |
| film_actor                 | BASE TABLE |
| film_category              | BASE TABLE |
| film_list                  | VIEW       |
| film_text                  | BASE TABLE |
| inventory                  | BASE TABLE |
| language                   | BASE TABLE |
| nicer_but_slower_film_list | VIEW       |
| payment                    | BASE TABLE |
| rental                     | BASE TABLE |
| sales_by_film_category     | VIEW       |
| sales_by_store             | VIEW       |
| staff                      | BASE TABLE |
| staff_list                 | VIEW       |
| store                      | BASE TABLE |
+----------------------------+------------+
23 rows in set (0.00 sec)

mysql> SELECT COUNT(*) FROM film;
+----------+
| COUNT(*) |
+----------+
|     1000 |
+----------+
1 row in set (0.00 sec)

mysql> SELECT COUNT(*) FROM film_text;
+----------+
| COUNT(*) |
+----------+
|     1000 |
+----------+
1 row in set (0.00 sec)
```