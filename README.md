# sql
lab exercises
mysql> use movie;
Database changed
mysql> create table celebs(id int primary key auto_increment,movie_name varchar(20) unique,released_year int(10) not null,language default'tamil');
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'default'tamil')' at line 1
mysql> create table celebs(id int primary key auto_increment,movie_name varchar(20) unique,released_year int(10) not null,language default 'tamil');
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'default 'tamil')' at line 1
mysql> create table celebs(id int primary key auto_increment,movie_name varchar(20) unique,released_year int(10) not null,language default 'tamil');
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'default 'tamil')' at line 1
mysql> create table celebs(id int primary key auto_increment,movie_name varchar(20) unique,released_year int(10) not null,language varchar(20) default'tamil');
Query OK, 0 rows affected, 1 warning (0.05 sec)

mysql> desc celebs;
+---------------+-------------+------+-----+---------+----------------+
| Field         | Type        | Null | Key | Default | Extra          |
+---------------+-------------+------+-----+---------+----------------+
| id            | int         | NO   | PRI | NULL    | auto_increment |
| movie_name    | varchar(20) | YES  | UNI | NULL    |                |
| released_year | int         | NO   |     | NULL    |                |
| language      | varchar(20) | YES  |     | tamil   |                |
+---------------+-------------+------+-----+---------+----------------+
4 rows in set (0.00 sec)

mysql> insert into celebs(id,movie_name,released_year) values(1,'kaithi',2020);
Query OK, 1 row affected (0.01 sec)

mysql> select*from celebs;
+----+------------+---------------+----------+
| id | movie_name | released_year | language |
+----+------------+---------------+----------+
|  1 | kaithi     |          2020 | tamil    |
+----+------------+---------------+----------+
1 row in set (0.01 sec)

mysql> insert into celebs(movie_name,released_year) values('asuran',2021),('vada_chennai'2021),('master',2021),('anniyan',2017);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '2021),('master',2021),('anniyan',2017)' at line 1
mysql> insert into celebs(movie_name,released_year) values('asuran',2021),('vada_chennai',2021),('master',2021),('anniyan',2017);
Query OK, 4 rows affected (0.01 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> select*from celebs;
+----+--------------+---------------+----------+
| id | movie_name   | released_year | language |
+----+--------------+---------------+----------+
|  1 | kaithi       |          2020 | tamil    |
|  2 | asuran       |          2021 | tamil    |
|  3 | vada_chennai |          2021 | tamil    |
|  4 | master       |          2021 | tamil    |
|  5 | anniyan      |          2017 | tamil    |
+----+--------------+---------------+----------+
5 rows in set (0.00 sec)



mysql> select movie_name from celebs where movie_name like 'a%';
+------------+
| movie_name |
+------------+
| anniyan    |
| asuran     |
+------------+
2 rows in set (0.01 sec)


mysql> select * from celebs order by movie_name;
+----+--------------+---------------+----------+
| id | movie_name   | released_year | language |
+----+--------------+---------------+----------+
|  5 | anniyan      |          2017 | tamil    |
|  2 | asuran       |          2021 | tamil    |
|  1 | kaithi       |          2020 | tamil    |
|  4 | master       |          2021 | tamil    |
|  3 | vada_chennai |          2021 | tamil    |
+----+--------------+---------------+----------+
5 rows in set (0.00 sec)

mysql> select * from celebs order by id desc;
+----+--------------+---------------+----------+
| id | movie_name   | released_year | language |
+----+--------------+---------------+----------+
|  5 | anniyan      |          2017 | tamil    |
|  4 | master       |          2021 | tamil    |
|  3 | vada_chennai |          2021 | tamil    |
|  2 | asuran       |          2021 | tamil    |
|  1 | kaithi       |          2020 | tamil    |
+----+--------------+---------------+----------+
5 rows in set (0.00 sec)

mysql> select * from celebs order by released_year asc;
+----+--------------+---------------+----------+
| id | movie_name   | released_year | language |
+----+--------------+---------------+----------+
|  5 | anniyan      |          2017 | tamil    |
|  1 | kaithi       |          2020 | tamil    |
|  2 | asuran       |          2021 | tamil    |
|  3 | vada_chennai |          2021 | tamil    |
|  4 | master       |          2021 | tamil    |
+----+--------------+---------------+----------+
5 rows in set (0.00 sec)
mysql> select * from celebs limit 2,3;
+----+--------------+---------------+----------+
| id | movie_name   | released_year | language |
+----+--------------+---------------+----------+
|  3 | vada_chennai |          2021 | tamil    |
|  4 | master       |          2021 | tamil    |
|  5 | anniyan      |          2017 | tamil    |
+----+--------------+---------------+----------+
3 rows in set (0.00 sec)
mysql> select released_year from celebs;
+---------------+
| released_year |
+---------------+
|          2020 |
|          2021 |
|          2021 |
|          2021 |
|          2017 |
+---------------+
5 rows in set (0.00 sec)
mysql> select distinct released_year from celebs;
+---------------+
| released_year |
+---------------+
|          2020 |
|          2021 |
|          2017 |
+---------------+
3 rows in set (0.00 sec)
mysql> select movie_name from celebs where released_year<=2018 and language = 'tamil';
+------------+
| movie_name |
+------------+
| anniyan    |
+------------+
1 row in set (0.00 sec)
mysql> select max(released_year) from celebs;
+--------------------+
| max(released_year) |
+--------------------+
|               2021 |
+--------------------+
1 row in set (0.00 sec)
mysql> select min(released_year) from celebs;
+--------------------+
| min(released_year) |
+--------------------+
|               2017 |
+--------------------+
1 row in set (0.00 sec)
mysql> select avg(released_year) from celebs;
+--------------------+
| avg(released_year) |
+--------------------+
|          2020.0000 |
+--------------------+
1 row in set (0.00 sec)
mysql> select round(avg(released_year)) from celebs;
+---------------------------+
| round(avg(released_year)) |
+---------------------------+
|                      2020 |
+---------------------------+
1 row in set (0.00 sec)
mysql> desc star;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| imdb  | int         | NO   |     | NULL    |       |
| genre | varchar(20) | NO   |     | NULL    |       |
| s_no  | int         | YES  | MUL | NULL    |       |
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
