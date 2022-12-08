# 2420 Exam

Robeen Maharjan

### How could you update most of the software on your Ubuntu OS?

`sudo apt update` & `sudo apt upgrade`

### Fix the code with vim 

`%s/eco/echo/g` & `%s/V/C/g`

Used insert for the `-eq 0` and `numbs` 

### Journalctl

 ![Bootlog](/Images/bootlog.png)
 
 `/current`
 
 ![Priority](/Images/priority.png)
 
 `/priority`
 
 ![Json](/Images/jsonpretty.png)
 
 `/json`
 
 Full command:
 
 `sudo journalctl PRIORITY=4 -b -o json-pretty`
 
 ![Journalctl command](/Images/journalctl.png)
 
 output looks like
 
 ![Output Json](/Images/outputjson.png)
 
 ### Find users
 
 Add user
 
 ![New User](/Images/newuser.png)

 Output:
 
 ![User Output](/Images/outputusers.png)
 
 Move the file somewhere else 

 `sudo mv ./vagrant_data/users /opt/`
 
 File
 
 ```
 #!/bin/bash
 
echo -e "Regular users on the system are:\n$(cat /etc/passwd | awk -F: '$3 >= 1000 && $3 <= 5000 {print $1 "\t" $3 "\t" $7}')\n\nUsers currently logged in are:\n$(sudo who | awk '{ print $1 }')" > /etc/motd

exit 0
```

### Service File

File

```
[Unit]
Decription=Display regular users on the system and logged in users

[Service]
Type=oneshot
ExecStart=/opt/users

[Install]
WantedBy=multi-user.target
```

Move the service file

`sudo mv users.service /etc/systemd/system`

Enable, Start, Status

![Output status](/Images/systemctlservice.png)

### Timer

Status

![Timer status](/Images/timerstatus.png)

File

```
[Unit]
Description=Timer to start the user.service one minute after boot once a day.

[Timer]
OnBootSec=1 m
Unit=users.service
Persistent=true

[Install]
WantedBy=timers.target
```
