# MySql

### __Service management__

__Check service status__

    $ service mysql status
    $ sudo systemctl status mysql.service

__Start MySql Service__

    $ service mysql start

__Stop MySql Service__

    $ service mysql stop

__Restart MySql Service__

    $ service mysql restart
    $ sudo systemctl restart mysql.service

### __Mysql script__

__Show current Database__

    mysql> SELECT DATABASE();

__Show variables__

    mysql> select @@lower_case_table_names;
    mysql> select @@global.max_allowed_packet;
    mysql> SHOW VARIABLES LIKE 'sql_safe_updates'
    mysql> select @@sql_safe_updates;
    mysql> SHOW VARIABLES LIKE '%wait%';
    mysql> show variables like "%timeout%";
    mysql> SHOW VARIABLES LIKE 'open%';
    mysql> show global status like 'uptime';

    <!-- Note, if the value is 0 that means there is no timeout enabled -->
    mysql> SELECT @@GLOBAL.MAX_EXECUTION_TIME, @@SESSION.MAX_EXECUTION_TIME;



__Set max allowed packet__

    mysql> **SET GLOBAL max_allowed_packet=1073741824**;

__Set net read timeout__
    mysql> SET GLOBAL net_read_timeout=60;
    mysql> SET @@NET_READ_TIMEOUT=200;

__Set SQL safe update__

    mysql> SET SQL_SAFE_UPDATES = 0;

__Show sql time zone info__

    mysql admin@ip:db> SHOW VARIABLES LIKE '%time_zone%';
    mysql admin@ip:db> SELECT @@global.time_zone, @@session.time_zone;

__select now time__

    mysql admin@ip:db> select now();

__update time zone__

    mysql admin@ip:db> SET GLOBAL time_zone = "Asia/Hong_Kong";
    mysql admin@ip:db> SET time_zone='+08:00';
    mysql admin@ip:db> SET GLOBAL time_zone = '+8:00';

OR

Edit the MySQL config file

    $ sudo nano /etc/mysql/my.cnf

Scroll and add these to the bottom. Change to relevant time zone

```properties
[mysqld]
default-time-zone = "+08:00"
```

Restart the server

    $ sudo service mysql restart

# Export && Import Data

Export data from database
```properties
$ SELECT * FROM ${TABLE_NAME} INTO OUTFILE '${output/to/path}';
```

Import data to database
```properties
$ LOAD DATA INFILE '${file/path}' INTO TABLE ${TABLE_NAME};
```

# Export && Import Data (CSV format)

Export Data
```properties
mysql> SELECT * FROM ${TABLE_NAME} INTO OUTFILE '/file/path/name.csv' FIELDS TERMINATED BY ',';
```

Import Data
```properties
mysql> LOAD DATA INFILE '/file/path/name.csv' INTO TABLE ${TABLE_NAME} FIELDS TERMINATED BY ',';
```

```properties
 mysql> LOAD DATA LOCAL INFILE '/file/path/name.csv' INTO TABLE ${TABLE_NAME} FIELDS TERMINATED BY ';'  ENCLOSED BY '"' LINES TERMINATED BY '\n' IGNORE 1 ROWS;
```

# MyCLI

MyCLI is a command line client for MySQL and MariaDB that allows you to auto-complete and helps with the syntax of your SQL commands.

### __Install (Ubuntu)__

    $ sudo apt-get install mycli


Find your version of MyCLI and its usage using following two commands.

    $ mycli --version

### How to connect db through the mycli

Examples:
- mycli my_database
- mycli -u my_user -h my_host.com my_database
- mycli mysql://my_user@my_host.com:3306/my_database
...
