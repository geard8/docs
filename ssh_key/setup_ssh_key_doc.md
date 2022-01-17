# Install docs for ufw on ubuntu in my VM

## This is made after dropbear is installed and config to listen to port 30042.

* Using "https://linuxhint.com/advanced_ufw_firewall_configuration_ubuntu/" a base info to install and config ufw

* How to install ufw
 
Run "sudo apt-get install ufw" to install ufw

gives me this output
```
thor@thor-server:~$ sudo apt install ufw
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  ufw
1 upgraded, 0 newly installed, 0 to remove and 42 not upgraded.
Need to get 147 kB of archives.
After this operation, 3,072 B of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 ufw all 0.36-6ubuntu1 [147 kB]
Fetched 147 kB in 2s (84.4 kB/s)
Preconfiguring packages ...
(Reading database ... 144404 files and directories currently installed.)
Preparing to unpack .../ufw_0.36-6ubuntu1_all.deb ...
Unpacking ufw (0.36-6ubuntu1) over (0.36-6) ...
Setting up ufw (0.36-6ubuntu1) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for rsyslog (8.2001.0-1ubuntu1.1) ...
Processing triggers for systemd (245.4-4ubuntu3.11) ...
thor@thor-server:~$ 
```

* How to check ufw status

Run "sudo ufw status verbose" to check ufw status

gives me this output

```
thor@thor-server:~$ sudo ufw status verbose
Status: inactive
thor@thor-server:~$

```

* open a port in ufw with "sudo ufw allow 30042/tcp" that open 30042 but can be an other port, but be carrful with port you open.

gives me this output

```
thor@thor-server:~$ sudo ufw allow 30042/tcp
[sudo] password for thor:
Rules updated
Rules updated (v6)
thor@thor-server:~$
```

* activate ufw with "sudo ufw enable"

gives me this output

```
thor@thor-server:~$ sudo ufw enable
Firewall is active and enabled on system startup
thor@thor-server:~$
```

* Check ufw status now that it is enable

Run "sudo ufw status verbose" to check ufw status

gives me this output

```
thor@thor-server:~$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
30042/tcp                  ALLOW IN    Anywhere
30042/tcp (v6)             ALLOW IN    Anywhere (v6)

thor@thor-server:~$
```

* Run "sudo ufw default allow outgoing" to allow outgoing data traffic.

gives me this output

```

```

