### backup

#### on the source server

```
cd frappe-bench
bench restore --with-files
```


### restore

#### on the target server

if you have an existing instance

1. login to mysql
`mysql -u root -p -h localhost`

2. identify the database name
`SHOW DATABASES;`

3. drop existing database
`DROP DATABASE [db_name];`
_(this can take a while to finish)_

4. check the database is gone with
`SHOW DATABASES;`

5. log out from mysql
`exit`

6. restore from sql file with files

```
cd ~/frappe-bench
bench --site [site_name] restore --with-public-files [/path/to/file.tar] --with-private-files [/path/to/file.tar] [/path/to/file.sql]
```
_(that as well may take a while. You'll also have to provide the MySQL root password_

7. test whether it work by
`bench mariadb`
if you are being logged in to the database, at least the restore seems to have worked


