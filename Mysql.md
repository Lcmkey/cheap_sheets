# MySql

### __Service management__

__Check service status__

    $ service mysql status

__Start MySql Service__

    $service mysql start

__Stop MySql Service__

    $service mysql stop

__Restart MySql Service__

    $service mysql restart

### __Mysql script__

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