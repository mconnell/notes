# Ubuntu Base

Basic notes on setting up a fresh install of ubuntu on a VPS. Not a complete guide as it doesn't cover things like iptables but enough to get the server going and a little more secure than the default.

This example:
    'apples' is the server name.
    '12.34.56.78' is the public IP address of the server
    'bob' is the new user we are creating

## Basic config

SSH in as root and change your password:

    passwd

Set the timezone to be whatever is local eg. 'Europe/London'
    dpkg-reconfigure tzdata

Set server name:
    echo "apples" > /etc/hostname
    hostname -F /etc/hostname

Configure /etc/hosts
    127.0.0.1      localhost.localdomain localhost
    12.34.56.78    apples.yourdomain.com apples

## APT

check apt sources list:
    /etc/apt/sources.list

then update so we have a list of packages:
    apt-get update

## Securing the server

Add user:
    adduser bob

Setup user to have sudo powers:
    visudo

add:
    bob   ALL=(ALL) ALL

### Copy public key over:
    scp ~/.ssh/id_rsa.pub bob@12.34.56.78:/home/bob/
    mv /home/bob/id_rsa.pub /home/bob/.ssh/authorized_keys

update permissions:
    chown -R bob:bob /home/bob/.ssh
    chmod 700 /home/bob/.ssh
    chmod 600 /home/bob/.ssh/authorized_keys

Secure SSH:
    nano /etc/ssh/sshd_config

make sure the following are set:
    Protocol 2
    PermitRootLogin no
    PasswordAuthentication no
    X11Forwarding no
    UsePAM no
    UseDNS no
    AllowUsers demo

reload SSH:
    /etc/init.d/ssh reload

Pull in build-essential because it tends to be handy:
    sudo aptitude install build-essential
