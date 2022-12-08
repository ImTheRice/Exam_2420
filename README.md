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
