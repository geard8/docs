# Setup docs for creating and using ssh key from my window 10 desktop to ubuntu in my VM.

* This is based on https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-20-04 that was used as a base for doing this process.

## Create ssh key

* First i move to .shh folder in my own user folder. A common place to store ssh key files
 
Run "cd C:\Users\Nicklas\.ssh" on window 10

gives me this output
```
PS C:\Users\Nicklas> cd C:\Users\Nicklas\.ssh
PS C:\Users\Nicklas\.ssh>
```


* Create ssh key to be use on may window 10
 
Run "ssh-keygen" on window 10 and give optional input for file namn and optional passpgrase.

gives me this output
```
PS C:\Users\Nicklas\.ssh> ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (C:\Users\Nicklas/.ssh/id_rsa): my_ssh_key
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in my_ssh_key.
Your public key has been saved in my_ssh_key.pub.
The key fingerprint is:
SHA256:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx nicklas@LAPTOP-LJIORLSB
The key's randomart image is:
+---[RSA 3072]----+
|xxxxxxxxxxxxxxxxx|
|xxxxxxxxxxxxxxxxx|
|xxxxxxxxxxxxxxxxx|
|xxxxxxxxxxxxxxxxx|
|xxxxxxxxxxxxxxxxx|
|xxxxxxxxxxxxxxxxx|
|xxxxxxxxxxxxxxxxx|
|xxxxxxxxxxxxxxxxx|
|xxxxxxxxxxxxxxxxx|
+----[SHA256]-----+
PS C:\Users\Nicklas\.ssh>
```
observe that i give input "my_ssh_key" here for my ssh key and no passpgrase. If no input for ssh key it will get a default for "id_rsa" instead of my own input of "my_ssh_key".

* This has created 2 new files

```
-a----         1/17/2022   7:41 PM           2610 my_ssh_key
-a----         1/17/2022   7:41 PM            578 my_ssh_key.pub
```

* Now it time to copy "my_ssh_key.pub" file on my window 10 to my ubuntu to a new file called "authorized_keys" with path "~/.ssh/authorized_keys" in my ubuntu.


Run 'type my_ssh_key.pub | ssh thor@555.555.5.555 "mkdir -p ~/.ssh && touch ~/.ssh/authorized_keys && chmod -R go= ~/.ssh && cat >> ~/.ssh/authorized_keys"' on window 10.

The "thor@555.555.5.555" part need to be change where "thor" part is name of a user you can use on ubuntu and "555.555.5.555" change to ip or domain that leads to your ubuntu.

gives me this output
```
PS C:\Users\Nicklas\.ssh> type my_ssh_key.pub | ssh thor@555.555.5.555 "mkdir -p ~/.ssh && touch ~/.ssh/authorized_keys && chmod -R go= ~/.ssh && cat >> ~/.ssh/authorized_keys"
thor@555.555.5.555's password:
PS C:\Users\Nicklas\.ssh>
```
observe "thor@555.555.5.555's password:" will need input of password for the user you using for ubuntu

* Check and verify that it went well in ubuntu by checking what's in .ssh folder in ubuntu

Run 'ls -l' when in .ssh folder on ubuntu
```
thor@thor:~/.ssh$ ls -l
total 4
-rw------- 1 thor thor 578 Jan 17 19:05 authorized_keys
thor@thor:~/.ssh$
```
And there it is, authorized_keys seems to be there. Check that the time and date seems to be right to avoid it's an older version from before this time.

* Now we can ssh from window 10 to ubuntu using the my_ssh_key and without using the password for the ubuntu user.

Run 'ssh -i my_ssh_key thor@555.555.5.555' when in .ssh folder on window 10. 

Where "-i my_ssh_key" part is for specifying what ssh key to use. If you use default "id_rsa" as name for ssh key the "-i my_ssh_key" part can be skiped and "id_rsa" will be used automatically.
```
PS C:\Users\Nicklas\.ssh> ssh -i my_ssh_key thor@555.555.5.555
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 5.4.0-81-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Mon 17 Jan 2022 07:55:33 PM UTC

  System load:             0.0
  Usage of /:              42.1% of 8.79GB
  Memory usage:            10%
  Swap usage:              0%
  Processes:               107
  Users logged in:         1
  IPv4 address for enp0s3: 555.555.5.555
  IPv6 address for enp0s3: 5555:5555:5555:5555:555:5555:5555:5555


0 updates can be applied immediately.

Failed to connect to https://changelogs.ubuntu.com/meta-release-lts. Check your Internet connection or proxy settings


Last login: Mon Jan 17 19:51:25 2022 from 555.555.5.555
thor@thor:~$
```
And now we have ssh in on our ubuntu from our window 10 with ssh key.