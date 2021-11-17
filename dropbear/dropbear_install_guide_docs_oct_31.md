# Install docs for dropbear on ubuntu in my VM

## Used this guide:
* https://linuxconfig.org/how-to-install-and-configure-dropbear-on-linux

## Pre install task:
* ssh in to my VM ubuntu with git bash on my windows 10 laptop.

## Install dropbear
  
* Use apt to install dropbear

sudo apt install dropbear

```
thor@thor-server:~/src-code/python$ sudo apt install dropbear
[sudo] password for thor:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  dropbear-bin dropbear-initramfs libtomcrypt1 libtommath1
Suggested packages:
  runit
The following NEW packages will be installed:
  dropbear dropbear-bin dropbear-initramfs libtomcrypt1 libtommath1
0 upgraded, 5 newly installed, 0 to remove and 25 not upgraded.
Need to get 543 kB of archives.
After this operation, 1,682 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://archive.ubuntu.com/ubuntu focal/main amd64 libtommath1 amd64 1.2.0-3 [53.0 kB]
Get:2 http://archive.ubuntu.com/ubuntu focal/universe amd64 libtomcrypt1 amd64 1.18.2-3 [360 kB]
Get:3 http://archive.ubuntu.com/ubuntu focal/universe amd64 dropbear-bin amd64 2019.78-2build1 [113 kB]
Get:4 http://archive.ubuntu.com/ubuntu focal/universe amd64 dropbear all 2019.78-2build1 [8,084 B]
Get:5 http://archive.ubuntu.com/ubuntu focal/universe amd64 dropbear-initramfs all 2019.78-2build1 [8,992 B]
Fetched 543 kB in 2s (243 kB/s)
Selecting previously unselected package libtommath1:amd64.
(Reading database ... 107930 files and directories currently installed.)
Preparing to unpack .../libtommath1_1.2.0-3_amd64.deb ...
Unpacking libtommath1:amd64 (1.2.0-3) ...
Selecting previously unselected package libtomcrypt1:amd64.
Preparing to unpack .../libtomcrypt1_1.18.2-3_amd64.deb ...
Unpacking libtomcrypt1:amd64 (1.18.2-3) ...
Selecting previously unselected package dropbear-bin.
Preparing to unpack .../dropbear-bin_2019.78-2build1_amd64.deb ...
Unpacking dropbear-bin (2019.78-2build1) ...
Selecting previously unselected package dropbear.
Preparing to unpack .../dropbear_2019.78-2build1_all.deb ...
Unpacking dropbear (2019.78-2build1) ...
Selecting previously unselected package dropbear-initramfs.
Preparing to unpack .../dropbear-initramfs_2019.78-2build1_all.deb ...
Unpacking dropbear-initramfs (2019.78-2build1) ...
Setting up libtommath1:amd64 (1.2.0-3) ...
Setting up libtomcrypt1:amd64 (1.18.2-3) ...
Setting up dropbear-bin (2019.78-2build1) ...
Setting up dropbear (2019.78-2build1) ...
Generating Dropbear DSS host key.  Please wait.
Generating 1024 bit dss key, this may take a while...
1024 SHA256:+YU4wm70TH1tTSxJgqvEsBGehbwDCqNHlaDhsmuhJ28 root@thor-server (DSA)
+---[DSA 1024]----+
|. .o.o.o.  .. .  |
|+o. o.=o  .  o o |
|+= . .o*   .  o o|
|o.o  .+ o+.. . + |
|.o    +oS.o o o .|
|...  o =.o o .   |
|+..   o o .      |
|.+E  .           |
| ..              |
+----[SHA256]-----+
Generating Dropbear RSA host key.  Please wait.
Generating 2048 bit rsa key, this may take a while...
2048 SHA256:E0nypVBcPSyGBU9FA5rv5VV/8QZGxvtmBu2AoPiVCG8 root@thor-server (RSA)
+---[RSA 2048]----+
|      oo+=**+.o  |
|      .=oO+ ++.  |
|       +B+.+ oo+.|
|      . Eoo ..+o=|
|       oS.. . .==|
|        .o o . .B|
|          . .  + |
|                 |
|                 |
+----[SHA256]-----+
Generating Dropbear ECDSA host key.  Please wait.
Generating 256 bit ecdsa key, this may take a while...
256 SHA256:XycZ0zsT5S1psLafVX0Gf9/R4SljxAteeC/U/REK08E root@thor-server (ECDSA)
+---[ECDSA 256]---+
|           o*o+o+|
|           o+EoOB|
|          . X=O+&|
|           o.Oo*O|
|        S   = * +|
|         . . + = |
|          .   o  |
|                 |
|                 |
+----[SHA256]-----+
OpenSSH appears to be installed.  Setting /etc/default/dropbear so that
Dropbear will not start by default.  Edit this file to change this behaviour.

Setting up dropbear-initramfs (2019.78-2build1) ...
Generating Dropbear DSS host key.  Please wait.
Generating 1024 bit dss key, this may take a while...
1024 SHA256:wr0YL5ObyTGTomiZldVcdtJgj+oDeVKsbHKk2AhzHQ8 root@thor-server (DSA)
+---[DSA 1024]----+
|    E    oo      |
|   . +. .+oo     |
|o . ..+oo.o.     |
|.o+ +o++.        |
| o +oO+oS        |
|   o+ =B .       |
|  + . Xoo        |
| = . o X.        |
|o .   =          |
+----[SHA256]-----+
Generating Dropbear RSA host key.  Please wait.
Generating 2048 bit rsa key, this may take a while...
2048 SHA256:CQZ058U6rTYln74Ws/w+tEkKMGP/NWtmvrLWVpOKc1w root@thor-server (RSA)
+---[RSA 2048]----+
|   .o . ...      |
|     o o ..      |
|      o .o       |
|     .=.+.o      |
|     . =S* .   . |
|        * = = E  |
|       . * % O . |
|          % #    |
|         oo#=o   |
+----[SHA256]-----+
Generating Dropbear ECDSA host key.  Please wait.
Generating 256 bit ecdsa key, this may take a while...
256 SHA256:T8Qi8J86KS8bdDR2O/RmSQpdUxbZwlWAeHhPguAHrJ0 root@thor-server (ECDSA)
+---[ECDSA 256]---+
|    .  .o.o*+*oo.|
|     o o.++oO o  |
|      Bo*.=o =   |
|     o.BEX .  .  |
|    . . S *      |
|   . . o *       |
|    o +   .      |
|    .+ .         |
|    .o.          |
+----[SHA256]-----+
update-initramfs: deferring update (trigger activated)
Dropbear has been added to the initramfs. Don't forget to check
your "ip=" kernel bootparameter to match your desired initramfs
ip configuration.

Processing triggers for systemd (245.4-4ubuntu3.11) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.2) ...
Processing triggers for initramfs-tools (0.136ubuntu6.6) ...
update-initramfs: Generating /boot/initrd.img-5.4.0-88-generic
dropbear: WARNING: Invalid authorized_keys file, remote unlocking of cryptroot via SSH won't work!
thor@thor-server:~/src-code/python$

```

## Configurate dropbear
  
* Use nano to edit config for dropbear

sudo nano /etc/default/dropbear

It start out looking like
```
# disabled because OpenSSH is installed
# change to NO_START=0 to enable Dropbear
NO_START=1
# the TCP port that Dropbear listens on
DROPBEAR_PORT=22

# any additional arguments for Dropbear
DROPBEAR_EXTRA_ARGS=

# specify an optional banner file containing a message to be
# sent to clients before they connect, such as "/etc/issue.net"
DROPBEAR_BANNER=""

# RSA hostkey file (default: /etc/dropbear/dropbear_rsa_host_key)
#DROPBEAR_RSAKEY="/etc/dropbear/dropbear_rsa_host_key"

# DSS hostkey file (default: /etc/dropbear/dropbear_dss_host_key)
#DROPBEAR_DSSKEY="/etc/dropbear/dropbear_dss_host_key"

# ECDSA hostkey file (default: /etc/dropbear/dropbear_ecdsa_host_key)
#DROPBEAR_ECDSAKEY="/etc/dropbear/dropbear_ecdsa_host_key"

# Receive window size - this is a tradeoff between memory and
# network performance
DROPBEAR_RECEIVE_WINDOW=65536
```

* Change in dropbear config

Change DROPBEAR_PORT to 30042

```
DROPBEAR_PORT=30042 # was 22
```

Change NO_START to 0

```
NO_START=0 # was 1
```

It now looking like this
```
# disabled because OpenSSH is installed
# change to NO_START=0 to enable Dropbear
NO_START=0
# the TCP port that Dropbear listens on
DROPBEAR_PORT=30042

# any additional arguments for Dropbear
DROPBEAR_EXTRA_ARGS=

# specify an optional banner file containing a message to be
# sent to clients before they connect, such as "/etc/issue.net"
DROPBEAR_BANNER=""

# RSA hostkey file (default: /etc/dropbear/dropbear_rsa_host_key)
#DROPBEAR_RSAKEY="/etc/dropbear/dropbear_rsa_host_key"

# DSS hostkey file (default: /etc/dropbear/dropbear_dss_host_key)
#DROPBEAR_DSSKEY="/etc/dropbear/dropbear_dss_host_key"

# ECDSA hostkey file (default: /etc/dropbear/dropbear_ecdsa_host_key)
#DROPBEAR_ECDSAKEY="/etc/dropbear/dropbear_ecdsa_host_key"

# Receive window size - this is a tradeoff between memory and
# network performance
DROPBEAR_RECEIVE_WINDOW=65536
```

## check if dropbear is enable and running.

* Run this command to check
  
systemctl is-active dropbear

systemctl is-enabled dropbear

this gave this output

```
thor@thor-server:~/src-code/python$ systemctl is-active dropbear
active
thor@thor-server:~/src-code/python$ systemctl is-enabled dropbear
dropbear.service is not a native service, redirecting to systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install is-enabled dropbear
enabled
thor@thor-server:~/src-code/python$
```

* Use this command if needed to start or enable them manually 

```
# Start the service
$ sudo systemctl start dropbear

# Enable the service at boot
$ sudo systemctl enable dropbear
```

Whenever we change a configuration parameter, we need to restart the server. All we have to do is to run:

```
$ sudo systemctl restart dropbear
```

## Verifie that you can ssh in to VM

* In a new git bash instans that is not already ssh in to anything run: 

ssh -p 30042 thor@[VM ubuntu ip adress ex 192.168.1.12]

gave me this output

```
$ ssh -p 30042 thor@192.168.1.12
The authenticity of host '[192.168.1.12]:30042 ([192.168.1.12]:30042)' can't be established.
ECDSA key fingerprint is SHA256:XycZ0zsT5S1psLafVX0Gf9/R4SljxAteeC/U/REK08E.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[192.168.1.12]:30042' (ECDSA) to the list of known hosts.
thor@192.168.1.12's password:
thor@thor-server:~$ 
```