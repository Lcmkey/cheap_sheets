# [Reference][Postgresql-rederence-link]

&thinsp;


# Config file location (Ubuntu)
`
/etc/postgresql/10/main/pg_hba.conf
`

### __Set Password for admin account__
1. open the file `pg_hba.conf` for Ubuntu it will be in `/etc/postgresql/9.x/main` and change this line:

|local|all|posgres|peer|
|---|---|---|---|---|
| - | - | - | - | - |

to

|local|all|posgres|trust|
|---|---|---|---|---|
| - | - | - | - | - |

2. Restart the server
   
        $ sudo service postgresql restart

3. Login into psql and set your password

        $ sudo -u postgres psql postgres
        $ ALTER USER postgres with password 'your-pass';

4. Finally change the `pg_hba.conf` from

|local|all|posgres|trust|
|---|---|---|---|---|
| - | - | - | - | - |

to

|local|all|posgres|md5|
|---|---|---|---|---|
| - | - | - | - | - |

1. Restart the server

> After restarting the postgresql server, you can access it with your own password


Authentication methods details:
> trust: anyone who can connect to the server is authorized to access the database
>
> peer: use client's operating system user name as database 
user name to access it.
>
> md5: password-base authentication

# PostgreSql Service Management

Check Status

    $ service postgresql status

Start Service

    $ sudo service postgresql start

Stop Service

    $ sudo service postgresql stop

Restart Service

    $ sudo service postgresql restart


# PostgreSQL Data Types

__PostgreSQL supports the following data types:__
 -  `Boolean`
 -  `Character` types such as `char`, `varchar`, and `text`
 -  `Numeric` types such as `integer` and `floating-point number`.
 -  `Temporal` types such as `date`, `time`, `timestamp`, and `interval`
 -  `UUID` for storing Universally Unique Identifiers
 -  `Array` for storing array `strings`, `numbers`, etc.
 -  `JSON` stores JSON data
 -  `hstore` stores key-value pair
 -  Special types such as network address and geometric data.

__Boolean: A Boolean data type can hold one of three possible values: `true`, `false` or `null`.__
    
 - 1, yes, y, t, true values are converted to true
 - 0, no, false, f values are converted to false.

Character: `CHAR(n)`, `VARCHAR(n)`, and `TEXT`

- `CHAR(n)` is the fixed-length character with space padded. If you insert a string that is shorter than the length of the column, PostgreSQL pads spaces. __*If you insert a string that is longer than the length of the column, PostgreSQL will issue an error*__.
  
- `VARCHAR(n)` is the variable-length character string.  With `VARCHAR(n)`,  you can store up to n characters. PostgreSQL does not pad spaces when the stored string is shorter than the length of the column.
  
- `TEXT` is the variable-length character string. Theoretically, text data is a character string with __*unlimited length*__.

__Numeric:__
- integers
  
    There are three kinds of integers in PostgreSQL

    - Small integer ( `SMALLINT` ) is 2-byte signed integer that has a range from -32,768 to 32,767.
  
    - Integer ( `INT` ) is a 4-byte integer that has a range from -2,147,483,648 to 2,147,483,647.

    - `Serial` is the same as integer except that PostgreSQL will automatically generate and populate values into the __*SERIAL*__ column. This is similar to `AUTO_INCREMENT` column in MySQL or `AUTOINCREMENT` column in SQLite.


- floating-point numbers

    There three main types of floating-point numbers:

    - `float(n)` is a floating-point number whose precision, at least, n, up to a maximum of 8 bytes.

    - realor `float8` is a 4-byte floating-point number.

    - `numeric` or `numeric(p,s)` is a real number with p digits with s number after the decimal point. The numeric(p,s) is the exact number.


__Temporal data types: The temporal data types allow you to store date and /or  time data.__

- `DATE` stores the dates only.
  
- `TIME` stores the time of day values.
  
- `TIMESTAMP` stores both date and time values.
  
- `TIMESTAMPTZ` is a timezone-aware timestamp data type. It is the abbreviation for timestamp with the time zone.
  
- `INTERVAL` stores periods of time.

__Arrays__
In PostgreSQL, you can store an `array` of strings, an array of integers, etc., in array columns. The array comes in handy in some situations e.g., storing days of the week, months of the year.

__JSON__
PostgreSQL provides two JSON data types: `JSON` and `JSONB` for storing JSON data.


__UUID:__

The `UUID` data type allows you to store Universal Unique Identifiers defined by `RFC 4122` . The `UUID` values guarantee a better uniqueness than SERIAL and can be used to hide sensitive data exposed to the public such as values of `id` in URL.

__Special data types:__
- box– a rectangular box.
- line – a set of points.
- point– a geometric pair of numbers.
- lseg– a line segment.
- polygon– a closed geometric.
- inet– an IP4 address.
- macaddr– a MAC address.

# PostgreSql Commands / Shell Script

### __Connect to PostgreSQL database__
Login With administrative user

    $ sudo -u postgres psql postgres

Login Without administrative user

    $ psql -U "sam.leung" -h 127.0.0.1 ${database}

> The default configuration of PostgreSQL allows "local" access to a database only to database users which have the same name as the OS user. "local" means without any IP traffic using only the Unix-Domain sockets. See the documentation for the configuration file pg_hba.conf especially the lines starting with "local" and the authentication method "peer" or "ident".
>
> On the other hand accessing postgres using an IP transport channels is by default configured to use passwords IF there IS a password. Therefore this should help youfor normal users.

&thinsp;

### __CHECK CONNECTION INFO__
Confirm the current connection and user information.

    postgres=# \conninfo

&thinsp;

### __Magic words__
- `-E`: will describe the underlaying queries of the `\` commands (cool for learning!)
- `-l`: psql will list all databases and then exit (useful if the user you connect with doesn't has a default database, like at AWS RDS)

Most `\d` commands support additional param of `__schema__.name__` and accept wildcards like `*.*`

- `\q`: Quit/Exit
- `\c __database__`: Connect to a database
- `\d __table__`: Show table definition (columns, etc.) including triggers
- `\d+ __table__`: More detailed table definition including description and physical disk size
- `\l`: List databases
- `\d table_name`: To describe a table such as a column, type, modifiers of columns, etc
- `\dy`: List events
- `\df`: List functions
- `\di`: List indexes
- `\dn`: List schemas
- `\dt`: List all tables in the current database
- `\dt *.*`: List tables from all schemas (if `*.*` is omitted will only show SEARCH_PATH ones)
- `\dT+`: List all data types
- `\dv`: List views
- `\dx`: List all extensions installed
- `\df+ __function__` : Show function SQL code. 
- `\x`: Pretty-format query results instead of the not-so-useful ASCII tables
- `\copy (SELECT * FROM __table_name__) TO 'file_path_and_name.csv' WITH CSV`: Export a table as CSV
- `\des+`: List all foreign servers
- `\dE[S+]`: List all foreign tables
- `SELECT version();`: To retrieve the current version of PostgreSQL server
- `\g`:  You want to save time typing the previous command again
- `\s`: To display command history
- `\s filename`: If you want to save the command history to a file, you need to specify the file name followed the command
- `\i filename`: In case you want to execute psql commands from a file
- `\?`: To know all available psql commands
- `\timing`: To turn on query execution time
  
User Related:
- `\du`: List users
- `\du __username__`: List a username if present.
- `create role __test1__`: Create a role with an existing username.
- `create role __test2__ noinherit login password __passsword__;`: Create a role with username and password.
- `set role __test__;`: Change role for current session to `__test__`.
- `grant __test2__ to __test1__;`: Allow `__test1__` to set its role as `__test2__`.
- `\deu+`: List all user mapping on server

&thinsp;

### __CREATE USER__

Use Cmd to create user

    $ sudo -u postgres createuser <username>

Create a user with no password:

    postgres=# CREATE USER "sam.leung";

Create a user with a password:

    postgres=# CREATE USER "sam.leung" WITH PASSWORD 'your-pass';

Create a user with a password that is valid until the end of 2020. After one second has ticked in 2021, the password is no longer valid.

    postgres=#  CREATE USER "sam.leung" WITH PASSWORD 'your-pass' VALID UNTIL '2021-01-01';

Create an account where the user can create databases:

    postgres=#  CREATE USER "sam.leung" WITH PASSWORD 'your-pass' CREATEDB;

&thinsp;

### __ALTER USER__
Change a user's password:

    postgres=#  ALTER USER "sam.leung" WITH PASSWORD 'your-pass';


    postgres=# ALTER USER ${username} with encrypted password 'your-pass';

Change the expiration date of the user's password:

    postgres=#  ALTER USER "sam.leung" VALID UNTIL '2021-01-01';

Make a password valid forever:

    postgres=#  ALTER USER "sam.leung" VALID UNTIL 'infinity';

Give a user the ability to create other users and new databases:

    postgres=#  ALTER USER miriam CREATEUSER CREATEDB;

&thinsp;

### __GRANT PRIVILEGES__

Granting privileges on database

    postgres=#  grant all privileges on database ${db_name} to ${username};

&thinsp;

### __CREATE DATABASE__

Use Cmd to create db

    $ sudo -u postgres createdb <dbname>

Use Shell Script to create db

    postgres=#  create database ${db_name};

&thinsp;

### __CREATE TABLE__

You can create a new table by specifying the `table name`, along with all `column names` and their `types`:

```


postgres=# CREATE TABLE users_test(
	id serial PRIMARY KEY,
	name VARCHAR(80),            --  user name
	description TEXT,            --  user desc
	card NUMERIC                 --  ID card no
);

postgres=# CREATE TABLE role (
	id INT NOT NULL PRIMARY KEY,
	code VARCHAR (5),
    description TEXT
);

postgres=# CREATE TABLE users (
	id serial PRIMARY KEY,
	name VARCHAR (255) NOT NULL,
	role_id INT NOT NULL,
	FOREIGN KEY (role_id) REFERENCES role (id)
);
```

&thinsp;

### __DROP TABLE__

Syntax

`DROP TABLE` [`IF EXISTS`] table_name [`CASCADE` | RESTRICT];
    
1. You specify the table name after the DROP TABLE keyword to remove the table permanently from the database.
   
2. If you remove a non-existent table, PostgreSQL issues an error. To avoid this situation, you can use the `IF EXISTS`parameter followed by the `DROP` TABLE clause.
   
3. In case the table that you want to remove is used in views, constraints or any other objects, the `CASCADE` allows you to remove those dependent objects together with the table automatically.
   
4. `RESTRICT` refuses to drop table if there is any object depends on it. PostgreSQL uses `RESTRICT` by default.

5. You can put a list of tables after the `DROP TABLE` to remove multiple tables at once, each table separated by a comma.

6. Notice that only superuser, schema owner, and table owner have sufficient privilege to remove the table.

Examples

    postgres=# DROP TABLE user;

>PostgreSQL issues an error because the users table does not exist.
>
>[Err] ERROR:  table "author" does not exist

To avoid this error, you can use the IF EXISTS parameter.

    postgres=# DROP TABLE IF EXISTS user;


[Postgresql-rederence-link]: https://www.postgresqltutorial.com/