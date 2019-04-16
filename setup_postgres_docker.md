1. Initialize the Postgres Docker
```docker run --name postgresdb -d -e POSTGRES_PASSWORD=123456 postgres```
2. connect to running container (directly to psql instead of bash)
```docker exec -it postgresdb psql -U postgres```
3. do some sql stuff
```CREATE DATABASE GamesDB``
```\c GamesDB```
```CREATE TABLE game_info(
    id int primary key not null auto_increment,
    name text NOT NULL,
    price int NOT NULL)
```
The following doesn't work:
```INSERT INTO game_info (name, price) values ('Apex', 'Free');```
But this does.
```INSERT INTO game_info (name, price) values ('Apex', 10);```
```\dt;```