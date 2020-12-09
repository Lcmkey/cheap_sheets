# Linux

### __Setting up Time Zone and Enabling Network Time Sync (NTP) on Linux__

__CentOS__

1. Configure the system clock in CentOS server.

    ```properties
    $ timedatectl
    ```

2. Display the current time and date.

    ```properties
    $ timedatectl status
    ```

3. Display all available Time zones.

    ```properties
    $ timedatectl list-timezones
    ```

4. Display a particular Time zone under Asia starting with alphabet H.

    ```properties
    $ timedatectl list-timezones | grep  -o "Asia/H.*"
    ```

5. To change or set a Time zone you can use the below command. E.g. Change to Hong Kong.

    ```properties
    $ timedatectl set-timezone Asia/Hong_Kong
    ```

6. To enable NTP to synchronize time with Internet time.

    ```properties
    $ timedatectl set-ntp yes
    ```

__Ubuntu & Debian__

steps 1 - 5 same as `Centos`

1. To enable NTP to synchronize time with Internet time.

    ```properties
    $ timedatectl set-ntp on
    ```

__Fedora__

steps 1 - 5 same as `Centos`

6. To enable NTP to synchronize time with Internet time.

    ```properties
    $ timedatectl set-ntp yes
    ```
---

# Restarting Apache on CentOS 7

### Prerequisites
- Access to a user account with `sudo` privileges
- An installed and configured Apache installation
- Access to a command line / terminal window (Menu > Applications > Utilities > Terminal)

&thinsp;

### Method 1: Restart Apache Server Using Systemctl Command

Open a terminal window and enter the following:

```properties
$ sudo systemctl restart httpd.service
```

The service should restart.

The restart command can take several moments to complete, depending on the complexity of your server configuration. If you’re running a large or complex server configuration, this can cause disruptions for users who rely on the server.

&thinsp;

# Method 2: Restart HTTPD Server Using Apachectl Command Script

Apache recommends using a control script to pass commands to the httpd process.

To restart Apache in this manner, enter the following:


```properties
$ sudo apachectl –k restart
```

To  instruct the Apache service to terminate all child processes and itself, run the following command:

```properties
$ apachectl –k stop
```

Use the below-mentioned command to exit child processes after they finish a task and then launch new instances. The service will reload configuration files as well.

```properties
$ apachectl –k graceful
```

Use `-k restart` to force child processes to exit. The parent process stays running, and reloads configuration files.

```properties
$ apachectl –k restart
```

Use `-k graceful-stop` to force parent process to stop child processes as they complete their tasks. Once all child processes are stopped, the parent process exits.

```properties
$ apachectl –k graceful–stop
```
For more information on the `apachectl` command, see the [Apache documentation][Apache documentation].

### Other Commands to Use with Systemctl

To start the Apache service:

```properties
$ sudo systemctl start httpd.service
```

Stop the Apache service with:

```properties
$ sudo systemctl stop httpd.service
```

Force Apache to refresh the configuration files:

```properties
$ sudo systemctl reload httpd.service
```

Set Apache to run when the system boots:

```properties
sudo systemctl enable httpd.service
```

Prevent Apache from loading when the system boots:

```properties
$ sudo systemctl disable httpd.service
```

The `reload` command is faster and creates much less disruption than restart. However, this only performs a soft refresh of the configuration files. Some services and dependencies may not be included in the refresh.

One good practice is to weigh the benefits against the costs of each process. If you have several clients depending on access to your server, try to refresh first. If that doesn’t work, or if the disruption is minimal, use restart.

<!-- Reference -->
[Apache documentation]: https://httpd.apache.org/docs/2.4/stopping.html

[Apache Best Practices]: https://phoenixnap.com/kb/how-to-restart-apache-centos-linux
