# Links

+ <https://mockazoo.com>  :: Generate mock data.


# Postgres

## QuickStart

```
docker pull postgres:14.2-alpine
docker run --name postgres -p 5432:5432 -e POSTGRES_PASSWORD=pass -d postgres:14.2-alpine
docker exec -it postgres bash
psql -U postgres
psql -U hw3a -d hw3a
\l                 # List databases.
CREATE DATABASE hw3a;
DROP DATABASE hw3a;
psql --help
psql -h localhost -p 5432 -U hw3a test
\c test            # Connect to database.
\d person          # Describe person.
\dt                # List tables.
\x                 # Detail mode.
\copy (SELECT * FROM person) TO '/data/person.csv' DELIMITER ',' CSV HEADER     # Export to file.
\df                # List functions.
\du                # List roles.
\q
CREATE ROLE hw3a WITH SUPERUSER CREATEDB CREATEROLE LOGIN ENCRYPTED PASSWORD 'hw3a';
```

## How to install and run?

```bash
docker pull postgres:14.2-alpine
docker run --name postgres -p 5432:5432 -e POSTGRES_PASSWORD=pass -d postgres:14.2-alpine
```

## How to connect?

```bash
docker exec -it postgres bash
psql -U postgres
```

## How to create table?

```
CREATE TABLE person (
    id bigserial NOT NULL PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    gender VARCHAR(6) NOT NULL,
    date_of_birth DATE,
    email VARCHAR(150),
    car_id BIGINT REFERENCES car(id),
    UNIQUE(car_id)
)
```

## How to drop table?

```
DROP TABLE person;
```

## How to alter table?

```
ALTER TABLE person ADD COLUMN car_id BIGINT;
ALTER TABLE person DROP CONSTRAINT person_pkey;
ALTER TABLE person ADD PRIMARY KEY(id);
ALTER TABLE person ADD CONSTRAINT unique_email_address UNIQUE(email);
ALTER TABLE person ADD UNIQUE(email);
ALTER TABLE person ADD CONSTRAINT car_id_fkey FOREIGN KEY(car_id) REFERENCES car(id);
ALTER TABLE person ADD CONSTRAINT gender_constraint CHECK(gender = 'Female' OR gender = 'Male');
```

## How to insert data?

```
INSERT INTO person(
    first_name,
    last_name,
    gender,
    date_of_birth,
    email
) VALUES (
    'John',
    'Smith',
    'FEMALE',
    DATE '1988-01-09',
    'john@gmail.com'
);
```

```
INSERT INTO person(id, name) VALUES(1, 'Jeff') ON CONFLICT(id) DO NOTHING;     # When primary key conflict, do noting instead of throwing an exception.
                                                                               # This must be paired with primary key or unique constraint, or else will throw exception.
INSERT INTO person(id, name) VALUES(1, 'Jeff') ON CONFLICT(id) DO UPDATE SET name = EXCLUDED.name;           # Like merge in oracle.
```

## How to use offset keyword?

```
SELECT * FROM person OFFSET 20 LIMIT 10;
SELECT * FROM person OFFSET 20 FETCH FIRST 10 ROWS ONLY;
```

## How to use coalesce?

coalesce means default, can accept multiple arguments. If the previous argument is null, then get the next argument.
```
SELECT COALESCE(email, 'Email not provided') FROM person;
SELECT COALESCE(email, auxmail, 'Email not provided') FROM person;
```

## How to use nullif?

nullif accept two arguments. If the second argument is equal to the first argument then return the first argument, otherwise return null.
```
SELECT COALESCE(10 / NULLIF(0, 0), 0);           # 10 / 0 => 0
```

## How to deal with date and time?

```
SELECT NOW();
SELECT NOW()::DATE;          # Cast to date.
SELECT NOW()::TIME;          # Cast to time.
SELECT NOW() - INTERVAL '1 YEAR'       # One year before.
SELECT NOW() + INTERVAL '10 DAY'       # Ten days later.
SELECT EXTRACT(YEAR FROM NOW());       # Current year.
SELECT EXTRACT(DOW FROM NOW());        # Day of the week.
SELECT AGE(NOW(), date_of_birth) FROM person;
```

## How to join?

```
select * from person join car on person.car_id = car.id;
select *
from person
left join car on person.car_id = car.id;
```

## How to use sequence?

```
ALTER SEQUENCE person_id_seq RESTART WITH 9;
```

## How to use extensions?

```
SELECT * FROM pg_available_extensions;
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";
SELECT uuid_generate_v4();
```

## How to use pgadmin?

```
docker pull dpage/pgadmin4
docker run -p 5050:80 \
  --name pgadmin
  -e 'PGADMIN_DEFAULT_EMAIL=wearehw3a@gmail.com' \
  -e 'PGADMIN_DEFAULT_PASSWORD=pass' \ 
  -d dpage/pgadmin4

docker inspect postgres | grep IPAddress         # Use this ip address to connect to postgres, not localhost.
```


# Mysql

## QuickStart

```
docker pull arm64v8/mysql:8.0.29-oracle
docker run --name mysql -p 3306:3306 -v /Users/jeff/learning/database_sandbox:/data -e MYSQL_ROOT_PASSWORD=pass -d arm64v8/mysql:8.0.29-oracle
docker exec -it mysql bash
mysql -uroot -p
\h
CREATE USER 'hw3a' IDENTIFIED BY 'hw3a';
GRANT ALL PRIVILEGES ON *.* TO 'hw3a';
CREATE DATABASE hw3a;
USE hw3a;
DROP DATABASE hw3a;
SHOW DATABASES;
SHOW TABLES;
DESCRIBE person;
\. /data/person.sql;
\q
```

## How to create table?

```
CREATE TABLE IF NOT EXISTS person1 (
    id INT AUTO_INCREMENT,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    gender VARCHAR(6) NOT NULL,
    date_of_birth DATE,
    email VARCHAR(150),
    salary DECIMAL(13, 2),
    description TEXT,
    PRIMARY KEY (id),
    UNIQUE (email)
);
```

