## Requirements
* Windows 10 1709 Fall Creators Update 64bit or later.
* Windows Subsystem for Linux feature is enabled.

## Install
#### 1. [Download](https://github.com/yuk7/ArchWSL/releases/latest) installer zip

#### 2. Extract all files in zip file to same directory

#### 3.Run Arch.exe to Extract rootfs and Register to WSL
Exe filename is using to the instance name to register.
If you rename it you can register with a diffrent name.

## Setting for Arch
#### 1.Setting root password
```
>Arch.exe
[root@PC-NAME user]# passwd
```

#### 2.Setup default user  (Please see ArchWiki [Sudo](https://wiki.archlinux.org/index.php/Sudo#Example_entries) and [User and groups](https://wiki.archlinux.org/index.php/Users_and_groups) pages.)
```
>Arch.exe
[root@PC-NAME]# EDITOR=nano visudo
    %wheel      ALL=(ALL) ALL
    (setup sudoers file.)

[root@PC-NAME]# useradd -m -G wheel -s /bin/bash {username}
(add user)

[root@PC-NAME user]# passwd {username}
(set default user password)

[root@PC-NAME user]# exit

>Arch.exe config --default-user {username}
    (setting to default user)
````
If the default user has not been changed(issue [#7](https://github.com/yuk7/ArchWSL/issues/7)), please reboot the computer or alternatively, restart the LxssManager in an Admin command prompt
`net stop lxssmanager && net start lxssmanager`

#### 3.Initialize keyring
Please excute these commands for initialize keyring.(This step is necessary for use pacman)
```shell
>Arch.exe
[user@PC-NAME]$ sudo pacman-key --init

[root@PC-NAME]$ sudo pacman-key --populate
```