1. Initialize the MySql Docker
```docker run --name mysqldb -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql:latest```
2. connect to running container
```docker exec -it mysqldb /bin/bash```
3. connect to mysql client
```mysql -uroot -p123456```
4. do some sql stuff
```CREATE DATABASE GamesDB``
```connect GamesDB```
```CREATE TABLE game_info(
    id int primary key not null auto_increment,
    name text NOT NULL,
    price int NOT NULL)
```
The following doesn't work:
```INSERT INTO game_info (name, price) values ('Apex', 'Free');```
But this does.
```INSERT INTO game_info (name, price) values ('Apex', 10);```
OR
```INSERT INTO game_info (name, price) values ('Apex', '10');```
Strict mode supported as of 5.6 / 5.7 STRICT_TRANS_TABLES
```\dt;```
```\l to list available databases```

### older version test
1. Initialize the MySql Docker
```docker run --name mysqldb5.5 -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql:5.5```
2. connect to running container
```docker exec -it mysqldb5.5 /bin/bash```
3. connect to mysql client
```mysql -uroot -p123456```
4. do some sql stuff
```CREATE DATABASE GamesDB``
```connect GamesDB```
```CREATE TABLE game_info(
    id int primary key not null auto_increment,
    name text NOT NULL,
    price int NOT NULL)
```
```INSERT INTO game_info (name) values ('Apex');```
```INSERT INTO game_info (name, price) values ('Apex', 'Free');```
```INSERT INTO game_info (name, price) values ('Apex', 10);```
OR
```INSERT INTO game_info (name, price) values ('Apex', '10');```
Strict mode supported as of 5.6 / 5.7 STRICT_TRANS_TABLES
```\dt;```
```\l to list available databases```

To set strict mode pre-5.6
(outside of db)
`SHOW VARIABLES LIKE 'sql_mode';`