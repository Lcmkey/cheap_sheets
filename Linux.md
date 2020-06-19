# Linux

### __Setting up Time Zone and Enabling Network Time Sync (NTP) on Linux__

__CentOS__

1. Configure the system clock in CentOS server.

        $ timedatectl

2. Display the current time and date.

        $ timedatectl status

3. Display all available Time zones.

        $ timedatectl list-timezones

4. Display a particular Time zone under Asia starting with alphabet H.

        $ timedatectl list-timezones | grep  -o "Asia/H.*"

5. To change or set a Time zone you can use the below command. E.g. Change to Hong Kong.

        $ timedatectl set-timezone Asia/Hong_Kong

6. To enable NTP to synchronize time with Internet time.

        $ timedatectl set-ntp yes

__Ubuntu & Debian__

steps 1 - 5 same as `Centos`

1. To enable NTP to synchronize time with Internet time.

        $ timedatectl set-ntp on

__Fedora__

steps 1 - 5 same as `Centos`

6. To enable NTP to synchronize time with Internet time.

        $ timedatectl set-ntp yes