# Discover Linux users having bash environment.

Utilize the file /etc/passwd and JavaScript preprocessing feature to feed the file into low-level discovery. This will allow us to monitor some files per user profile.

[![IMAGE ALT TEXT](https://i9.ytimg.com/vi/iPLeS1Kq8kk/maxresdefault.jpg?sqp=CNyP-ukF&rs=AOn4CLA-t4xlMGGhfHeCVmg0t1oaNR81eA&time=1564379349868)](https://www.youtube.com/watch?v=iPLeS1Kq8kk "Discover Linux users with Zabbix")


## Dependencies

### Zabbix server

Must have at least version 4.2 because of "JavaScript preprocessing feature" and "Discard unchanged" feature.

### Zabbix agent

It is suggested to run Zabbix agent under the root environment to be able to access anything in each user profile.
```
AllowRoot=1
```

### Items

Pick up bash history:
```
logrt[{#PATH}/.bash_history*,,utf8]
```

Pick up MySQL history:
```
logrt[{#PATH}/.mysql_history*,,utf8]
```

Take a backup of .bashrc file. Usefull if you invent your own command alias
```
vfs.file.contents[{#PATH}/.bashrc,utf8]
```
