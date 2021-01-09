# Set firewall

Check the `firewall` status with below cli

```basg
$ sudo ufw status
```

output:

```
Status: inactive
```

> Ubuntu defaul firewall tools `UFW`, default: inactive

```properties
<!-- Deny all incoming request -->
$ sudo ufw default deny incoming

<!-- Allow All Exteenal network request -->
$ sudo ufw default allow outgoing

<!-- Allow user use ssh to remote -->
$ sudo ufw allow 22/tcp

<!-- Only allow internal subnet ip: 192.168.59.100 to access mongodb -->
$ sudo ufw allow from 192.168.59.100 to any port 27017

<!-- Enable Firewall -->
$ sudo ufw enable
```
