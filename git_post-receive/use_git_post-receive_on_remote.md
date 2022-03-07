# Docs for using post-receive on remote.

* This is based on https://daveceddia.com/deploy-git-repo-to-server/ that was used as a base for doing this process.

This is to use post-receive to do something after push to this repo. In this case 
using --work-tree to deply repo to another part of remote.

## Remote setup
All command in this part is on remote and remote in this exempel is a VM with ubuntu.

- cd to where you want the git to be.

In this case 
```
thor@thor:~/docs$ pwd
/home/thor/docs
```

- Run "git init --bare /path/to/bare_project.git" to create a bare repo
```
thor@thor:~/docs$ git init --bare docs_bare_project.git
Initialized empty Git repository in /home/thor/docs/docs_bare_project.git/
thor@thor:~/docs$ ls
docs_bare_project.git
thor@thor:~/docs$
```

- Go to hooks folder in new bare git repo and create file called post-receive
```
thor@thor:~/docs$ cd docs_bare_project.git/
thor@thor:~/docs/docs_bare_project.git$ cd hooks/
thor@thor:~/docs/docs_bare_project.git/hooks$ touch post-receive
thor@thor:~/docs/docs_bare_project.git/hooks$ ls
applypatch-msg.sample      pre-applypatch.sample      pre-rebase.sample
commit-msg.sample          pre-commit.sample          pre-receive.sample
fsmonitor-watchman.sample  pre-merge-commit.sample    update.sample
post-receive               prepare-commit-msg.sample
post-update.sample         pre-push.sample
thor@thor:~/docs/docs_bare_project.git/hooks$
```

- Edit post-receive to have. I used nano.
```
#!/bin/sh

# Check out the files
git --work-tree=/home/thor/docs/output_docs --git-dir=/home/thor/docs/docs_bare_project.git checkout -f
```
Gives me this.
```
thor@thor:~/docs/docs_bare_project.git/hooks$ nano post-receive
thor@thor:~/docs/docs_bare_project.git/hooks$ cat post-receive
#!/bin/sh

# Check out the files
git --work-tree=/home/thor/docs/output_docs --git-dir=/home/thor/docs/docs_bare_project.git checkout -f
thor@thor:~/docs/docs_bare_project.git/hooks$

```
This will make /var/www/deployed_project have content of repo someone push to this repo.

- To make use it can be executable, lets run "chmod +x post-receive" in hooks folder. And then ll to check post-receive permissions.
```
thor@thor:~/docs/docs_bare_project.git/hooks$ chmod +x post-receive
thor@thor:~/docs/docs_bare_project.git/hooks$ ll
total 64
drwxrwxr-x 2 thor thor 4096 Mar  7 13:32 ./
drwxrwxr-x 7 thor thor 4096 Mar  7 13:03 ../
-rwxrwxr-x 1 thor thor  478 Mar  7 13:03 applypatch-msg.sample*
-rwxrwxr-x 1 thor thor  896 Mar  7 13:03 commit-msg.sample*
-rwxrwxr-x 1 thor thor 3079 Mar  7 13:03 fsmonitor-watchman.sample*
-rwxrwxr-x 1 thor thor  125 Mar  7 13:32 post-receive*
-rwxrwxr-x 1 thor thor  189 Mar  7 13:03 post-update.sample*
-rwxrwxr-x 1 thor thor  424 Mar  7 13:03 pre-applypatch.sample*
-rwxrwxr-x 1 thor thor 1638 Mar  7 13:03 pre-commit.sample*
-rwxrwxr-x 1 thor thor  416 Mar  7 13:03 pre-merge-commit.sample*
-rwxrwxr-x 1 thor thor 1492 Mar  7 13:03 prepare-commit-msg.sample*
-rwxrwxr-x 1 thor thor 1348 Mar  7 13:03 pre-push.sample*
-rwxrwxr-x 1 thor thor 4898 Mar  7 13:03 pre-rebase.sample*
-rwxrwxr-x 1 thor thor  544 Mar  7 13:03 pre-receive.sample*
-rwxrwxr-x 1 thor thor 3610 Mar  7 13:03 update.sample*
thor@thor:~/docs/docs_bare_project.git/hooks$
```

## local setup

All command in this part is on local which in this case is on windows 10.

- Make use you are in folder for git repo on local that you wish to push to remote.
```
$ pwd
/c/Users/Nicklas/src-code/chas/docs/docs
```

- Run "git remote add live 'thor@555.555.5.555:/home/thor/docs/docs_bare_project.git'" with ip for remote 
insted of all 5 followed by "git remote -v" to check its been added. Change remote_name to what you wish to call it.
```
Nicklas@LAPTOP-LJIORLSB MINGW64 ~/src-code/chas/docs/docs (main)
$ git remote add remote_name 'thor@1555.555.5.555:/docs/docs_bare_project.git'   
Nicklas@LAPTOP-LJIORLSB MINGW64 ~/src-code/chas/docs/docs (main)
$ git remote -v
origin  https://github.com/geard8/docs.git (fetch)
origin  https://github.com/geard8/docs.git (push)
remote_name     thor@555.555.5.555:/home/thor/docs/docs_bare_project.git (fetch)
remote_name     thor@555.555.5.555:/home/thor/docs/docs_bare_project.git (push)

Nicklas@LAPTOP-LJIORLSB MINGW64 ~/src-code/chas/docs/docs (main)
$
```

- Run "git push remote_name" to push local repo to repo on remote.
```
Nicklas@LAPTOP-LJIORLSB MINGW64 ~/src-code/chas/docs/docs (main)
$ git push remote_name
thor@192.168.8.123's password:
Enumerating objects: 16, done.
Counting objects: 100% (16/16), done.
Delta compression using up to 8 threads
Compressing objects: 100% (14/14), done.
Writing objects: 100% (16/16), 6.91 KiB | 884.00 KiB/s, done.
Total 16 (delta 2), reused 0 (delta 0), pack-reused 0
remote: fatal: not a git repository: '/docs/docs_bare_project.git'
To 192.168.8.123:/home/thor/docs/docs_bare_project.git
 * [new branch]      main -> main

Nicklas@LAPTOP-LJIORLSB MINGW64 ~/src-code/chas/docs/docs (main)
```
