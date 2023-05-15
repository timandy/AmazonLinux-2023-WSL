# Amazon Linux 2023 WSL
Amazon Linux 2023 on WSL (Windows 10 FCU or later)
based on [wsldl](https://github.com/yuk7/wsldl)

![screenshot](https://raw.githubusercontent.com/yosukes-dev/AmazonWSL/master/img/screenshot.png)


[![Github All Releases](https://img.shields.io/github/downloads/rlove/AmazonLinux-2023-WSL/total.svg?style=flat-square)](https://github.com/rlove/AmazonLinux-2023-WSL/releases)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

### [Download](https://github.com/rlove/AmazonWSL-2023-wsl/releases)

## An instruction on AWS Developer Tools Blog
The following link is to an article on the AWS Developer Tools Blog describing development with AmazonWSL v2, and still applies to AmazonLinux-2023-WSL.    
[Developing on Amazon Linux 2 using Windows - AWS Developer Tools Blog](https://aws.amazon.com/jp/blogs/developer/developing-on-amazon-linux-2-using-windows/)

## Requirements
* Windows 10 Fall Creators Update x64 or later. 
* Windows Subsystem for Linux feature is enabled.

## Install
#### 1. [Download](https://github.com/rlove/AmazonWSL-2023-wsl/releases) installer zip

#### 2. Extract all files in zip file to same directory

#### 3.Run AL2023.exe to Extract rootfs and Register to WSL
Exe filename is using to the instance name to register.
If you rename it you can register with a diffrent name and have multiple installs.

## Icon settings for Windows Terminal

The following is an example of `profiles.json` if you extracted to `C:\`
```
{
    "guid": "{98c7f3f4-4eb6-4dd0-9568-0de8589151d4}",
    "hidden": false,
    "name": "Amazon Linux 2023",
    "source": "Windows.Terminal.Wsl",
    "icon": "C:\\Amazon2023\\assets\\icon.png"
}
```

## How-to-Use(for Installed Instance)
#### exe Usage
```dos
Usage :
    <no args>
      - Open a new shell with your default settings.

    run <command line>
      - Run the given command line in that distro. Inherit current directory.

    runp <command line (includes windows path)>
      - Run the path translated command line in that distro.

    config [setting [value]]
      - `--default-user <user>`: Set the default user for this distro to <user>
      - `--default-uid <uid>`: Set the default user uid for this distro to <uid>
      - `--append-path <on|off>`: Switch of Append Windows PATH to $PATH
      - `--mount-drive <on|off>`: Switch of Mount drives
      - `--default-term <default|wt|flute>`: Set default terminal window

    get [setting]
      - `--default-uid`: Get the default user uid in this distro
      - `--append-path`: Get on/off status of Append Windows PATH to $PATH
      - `--mount-drive`: Get on/off status of Mount drives
      - `--wsl-version`: Get WSL Version 1/2 for this distro
      - `--default-term`: Get Default Terminal for this distro launcher
      - `--lxguid`: Get WSL GUID key for this distro

    backup [contents]
      - `--tgz`: Output backup.tar.gz to the current directory using tar command
      - `--reg`: Output settings registry file to the current directory

    clean
      - Uninstall the distro.

    help
      - Print this usage message.
```

#### Just Run exe
```cmd
>AL2023.exe
[root@PC-NAME user]#
```

#### Run with command line
```cmd
>AL2023.exe run uname -r
4.4.0-43-Microsoft
```

#### Run with command line with path translation
```cmd
>AL2023.exe runp echo C:\Windows\System32\cmd.exe
/mnt/c/Windows/System32/cmd.exe
```

#### Change Default User(id command required)

The following is an example of adding a user to the "users" and "wheel" groups and setting it as the default user

_Note: Replace `user` with your chosen user name._

```cmd
>AL2023.exe run useradd -m -g users -G wheel -s /bin/bash user

>AL2023.exe config --default-user user

>AL2023.exe
[user@PC-NAME dir]$
```

#### Set "Windows Terminal" as default terminal
```cmd
>AL2023.exe config --default-term wt
```

#### How to uninstall instance
```dos
>AL2023.exe clean

```
