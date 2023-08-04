## Install MySQL
```
$ sudo apt install mysql-server -y
$ sudo systemctl status mysql // check if system is running
```

## Access MySql
```
$ sudo mysql
```

## MySQL Commands
```
$ show databases; // list default databases
$ create database <database_name>; // create 
$ use <database_name>;
$ show tables 
$ creat table <table_name> (
id int, 
name varchar(255),
region varchar(255),
roast varchar(255)
);
$ describe <table_name> // covers more info from table
$ insert into <table_name> values (1, "default route", "ethiopia", "light");
$ select * from <table_name>; // select data from all columns 
$ select name from <table_name>;
$ delete from <table_name> where first_name = "jeff";
$ update <table_name> set last_name = NULL where first_name = "groot";
```
