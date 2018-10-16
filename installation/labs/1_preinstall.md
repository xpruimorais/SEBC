# VM Setup

## Azure VM type and OS

Since I'm using Azure, I chose the most similar VM type to AWS m3.xlarge: **Standard D4s v3 (4 vcpus, 16 GB memory)**.

Operating System is **CentOS-based 7.3**.


## Setup user
Created ssh keys for user `rdsm` and distributed them to all cluster nodes:

```
[rdsm@sebc-node01 ~]$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/rdsm/.ssh/id_rsa):
Created directory '/home/rdsm/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/rdsm/.ssh/id_rsa.
Your public key has been saved in /home/rdsm/.ssh/id_rsa.pub.
The key fingerprint is:
9b:a9:4f:c9:2a:63:7c:37:9f:01:87:6f:8e:74:f2:94 rdsm@sebc-node01

(...)

[rdsm@sebc-node01 ~]$ ssh-copy-id -i .ssh/id_rsa.pub node01
[rdsm@sebc-node01 ~]$ ssh-copy-id -i .ssh/id_rsa.pub node02
[rdsm@sebc-node01 ~]$ ssh-copy-id -i .ssh/id_rsa.pub node03
[rdsm@sebc-node01 ~]$ ssh-copy-id -i .ssh/id_rsa.pub node04
[rdsm@sebc-node01 ~]$ ssh-copy-id -i .ssh/id_rsa.pub node05
```


Configured my user as a password-less sudoer, via `visudo`:

`[root@node01 ~]# visudo` :
```
(...)
## Read drop-in files from /etc/sudoers.d (the # here does not mean a comment)
#includedir /etc/sudoers.d
rdsm            ALL=(ALL)       NOPASSWD: ALL
```


## Disk Setup

Azure Standard D4s v3 VMs come with 30GB OS disk. I increased the OS disk size in Azure to 100GiB, and then proceeded to grow root partition to fufill empty space.

### Example from `node01.xpandit.com`

Discovered OS disk:

```
[root@sebc-node01 ~]# fdisk -l

Disk /dev/sdc: 107.4 GB, 107374182400 bytes, 209715200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 107.4 GB, 107374182400 bytes, 209715200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk label type: dos
Disk identifier: 0x000a41c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1026047      512000   83  Linux
/dev/sda2         1026048    62914559    30944256   83  Linux

```





# Preinstall

## Swappiness

Check `vm.swappiness`:
```
[root@node01 ~]# ansible -a "sysctl vm.swappiness" all
node02 | CHANGED | rc=0 >>
vm.swappiness = 30

node05 | CHANGED | rc=0 >>
vm.swappiness = 30

node01 | CHANGED | rc=0 >>
vm.swappiness = 30

node03 | CHANGED | rc=0 >>
vm.swappiness = 30

node04 | CHANGED | rc=0 >>
vm.swappiness = 30
```

Set `vm.swappiness` to `1`:

```
[root@node01 ~]# ansible -a "sysctl -w vm.swappiness=1" all
node02 | CHANGED | rc=0 >>
vm.swappiness = 1

node05 | CHANGED | rc=0 >>
vm.swappiness = 1

node03 | CHANGED | rc=0 >>
vm.swappiness = 1

node01 | CHANGED | rc=0 >>
vm.swappiness = 1

node04 | CHANGED | rc=0 >>
vm.swappiness = 1
```

Configuration set permanently by adding to `/etc/sysctl.conf`:



## Data Disks Setup

```
[root@node01 ~]# ansible -a "mkdir -p /data/01" all
```

```
[root@node01 ~]# fdisk /dev/sdc
Welcome to fdisk (util-linux 2.23.2).

Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

Device does not contain a recognized partition table
Building a new DOS disklabel with disk identifier 0x8b01d82e.

The device presents a logical sector size that is smaller than
the physical sector size. Aligning to a physical sector (or optimal
I/O) size boundary is recommended, or performance may be impacted.

Command (m for help): n
Partition type:
   p   primary (0 primary, 0 extended, 4 free)
   e   extended
Select (default p): p
Partition number (1-4, default 1): 1
First sector (2048-209715199, default 2048):
Using default value 2048
Last sector, +sectors or +size{K,M,G} (2048-209715199, default 209715199):
Using default value 209715199
Partition 1 of type Linux and of size 100 GiB is set

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
[root@node01 ~]# mkfs.xfs /dev/sdc1
meta-data=/dev/sdc1              isize=512    agcount=4, agsize=6553536 blks
         =                       sectsz=4096  attr=2, projid32bit=1
         =                       crc=1        finobt=0, sparse=0
data     =                       bsize=4096   blocks=26214144, imaxpct=25
         =                       sunit=0      swidth=0 blks
naming   =version 2              bsize=4096   ascii-ci=0 ftype=1
log      =internal log           bsize=4096   blocks=12799, version=2
         =                       sectsz=4096  sunit=1 blks, lazy-count=1
realtime =none                   extsz=4096   blocks=0, rtextents=0
[root@node01 ~]# blkid /dev/sdc1
/dev/sdc1: UUID="906fcab6-adae-4d74-a7af-67fc4804318d" TYPE="xfs"
```


Content of `/etc/fstab` (UUIDs changes on every node):
```
[root@node01 ~]# cat /etc/fstab
#
# /etc/fstab
# Created by anaconda on Mon Sep 25 21:22:22 2017
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=e0c46854-9553-4a67-a3aa-211d8a3987b0 /                       xfs     defaults        0 0
UUID=79132c44-3aa5-405f-ae02-498cba01996a /boot                   xfs     defaults        0 0
UUID=906fcab6-adae-4d74-a7af-67fc4804318d /data/01                xfs     defaults,noatime 1 2
```

Reserved SPACE:
Ran `xfs_io -c "resblks 0" /data/01` but, as mentioned, xfs does not maintain reserved space. After reboot, used space goes up again.


## Disable transparent hugepage support

Ran:

```
echo never > /sys/kernel/mm/transparent_hugepage/defrag
echo never > /sys/kernel/mm/transparent_hugepage/enabled
```

And added to `/etc/rc.local`



## Network interface

```
[root@node01 ~]# cat /etc/sysconfig/network
NETWORKING=yes
HOSTNAME=node01.xpandit.com
NETWORKING_IPV6=no
IPV6INIT=no
```


```
[root@node01 ~]# cat /etc/sysctl.conf
# sysctl settings are defined through files in
# /usr/lib/sysctl.d/, /run/sysctl.d/, and /etc/sysctl.d/.
#
# Vendors settings live in /usr/lib/sysctl.d/.
# To override a whole file, create a new file with the same in
# /etc/sysctl.d/ and put new settings there. To override
# only specific settings, add a file with a lexically later
# name in /etc/sysctl.d/ and put new settings there.
#
# For more information, see sysctl.conf(5) and sysctl.d(5).

vm.swappiness = 1
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```



```
[root@node01 ~]# cat /etc/sysconfig/network-scripts/ifcfg-eth0
DEVICE=eth0
ONBOOT=yes
BOOTPROTO=dhcp
TYPE=Ethernet
USERCTL=no
PEERDNS=yes
IPV6INIT=no
NM_CONTROLLED=no
DHCP_HOSTNAME=node01.xpandit.com
```

## Forward and Reverse Host Lookups



```
[root@node01 ~]# getent hosts node01
10.1.0.4        node01.xpandit.com node01
[root@node01 ~]# getent hosts node02
10.1.0.5        node02.xpandit.com node02
[root@node01 ~]# getent hosts node03
10.1.0.6        node03.xpandit.com node03
[root@node01 ~]# getent hosts node04
10.1.0.7        node04.xpandit.com node04
[root@node01 ~]# getent hosts node05
10.1.0.8        node05.xpandit.com node05
```


```
[root@node01 ~]# getent hosts 10.1.0.4
10.1.0.4        node01.xpandit.com node01
[root@node01 ~]# getent hosts 10.1.0.5
10.1.0.5        node02.xpandit.com node02
[root@node01 ~]# getent hosts 10.1.0.6
10.1.0.6        node03.xpandit.com node03
[root@node01 ~]# getent hosts 10.1.0.7
10.1.0.7        node04.xpandit.com node04
[root@node01 ~]# getent hosts 10.1.0.8
10.1.0.8        node05.xpandit.com node05
```



Installed `nscd` and `ntp`
```
yum install -y nscd
yum install -y ntp
```

Enabled in all hosts running `systemctl enable nscd` and `systemctl enable ntpd`.


Started in all hosts as follow:


```
[root@node01 ~]# ansible -a "systemctl start nscd" all
node02 | CHANGED | rc=0 >>


node01 | CHANGED | rc=0 >>


node03 | CHANGED | rc=0 >>


node04 | CHANGED | rc=0 >>


node05 | CHANGED | rc=0 >>


[root@node01 ~]# ansible -a "systemctl status nscd" all
node02 | CHANGED | rc=0 >>
● nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; disabled; vendor preset: disabled)
   Active: active (running) since Mon 2018-10-15 14:57:41 UTC; 6s ago
  Process: 1399 ExecStart=/usr/sbin/nscd $NSCD_OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 1400 (nscd)
   CGroup: /system.slice/nscd.service
           └─1400 /usr/sbin/nscd

Oct 15 14:57:41 node02.xpandit.com nscd[1400]: 1400 monitoring file `/etc/hosts` (4)
Oct 15 14:57:41 node02.xpandit.com nscd[1400]: 1400 monitoring directory `/etc` (2)
Oct 15 14:57:41 node02.xpandit.com nscd[1400]: 1400 monitoring file `/etc/resolv.conf` (5)
Oct 15 14:57:41 node02.xpandit.com nscd[1400]: 1400 monitoring directory `/etc` (2)
Oct 15 14:57:41 node02.xpandit.com nscd[1400]: 1400 monitoring file `/etc/services` (6)
Oct 15 14:57:41 node02.xpandit.com nscd[1400]: 1400 monitoring directory `/etc` (2)
Oct 15 14:57:41 node02.xpandit.com nscd[1400]: 1400 disabled inotify-based monitoring for file `/etc/netgroup': No such file or directory
Oct 15 14:57:41 node02.xpandit.com nscd[1400]: 1400 stat failed for file `/etc/netgroup'; will try again later: No such file or directory
Oct 15 14:57:41 node02.xpandit.com nscd[1400]: 1400 Access Vector Cache (AVC) started
Oct 15 14:57:41 node02.xpandit.com systemd[1]: Started Name Service Cache Daemon.

node05 | CHANGED | rc=0 >>
● nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; disabled; vendor preset: disabled)
   Active: active (running) since Mon 2018-10-15 14:57:42 UTC; 5s ago
  Process: 32699 ExecStart=/usr/sbin/nscd $NSCD_OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 32700 (nscd)
   CGroup: /system.slice/nscd.service
           └─32700 /usr/sbin/nscd

Oct 15 14:57:41 node05.xpandit.com nscd[32700]: 32700 monitoring file `/etc/hosts` (4)
Oct 15 14:57:41 node05.xpandit.com nscd[32700]: 32700 monitoring directory `/etc` (2)
Oct 15 14:57:41 node05.xpandit.com nscd[32700]: 32700 monitoring file `/etc/resolv.conf` (5)
Oct 15 14:57:41 node05.xpandit.com nscd[32700]: 32700 monitoring directory `/etc` (2)
Oct 15 14:57:41 node05.xpandit.com nscd[32700]: 32700 monitoring file `/etc/services` (6)
Oct 15 14:57:41 node05.xpandit.com nscd[32700]: 32700 monitoring directory `/etc` (2)
Oct 15 14:57:41 node05.xpandit.com nscd[32700]: 32700 disabled inotify-based monitoring for file `/etc/netgroup': No such file or directory
Oct 15 14:57:41 node05.xpandit.com nscd[32700]: 32700 stat failed for file `/etc/netgroup'; will try again later: No such file or directory
Oct 15 14:57:42 node05.xpandit.com nscd[32700]: 32700 Access Vector Cache (AVC) started
Oct 15 14:57:42 node05.xpandit.com systemd[1]: Started Name Service Cache Daemon.

node01 | CHANGED | rc=0 >>
● nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; disabled; vendor preset: disabled)
   Active: active (running) since Mon 2018-10-15 14:57:41 UTC; 6s ago
  Process: 3017 ExecStart=/usr/sbin/nscd $NSCD_OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 3018 (nscd)
   CGroup: /system.slice/nscd.service
           └─3018 /usr/sbin/nscd

Oct 15 14:57:41 node01.xpandit.com nscd[3018]: 3018 monitoring file `/etc/hosts` (4)
Oct 15 14:57:41 node01.xpandit.com nscd[3018]: 3018 monitoring directory `/etc` (2)
Oct 15 14:57:41 node01.xpandit.com nscd[3018]: 3018 monitoring file `/etc/resolv.conf` (5)
Oct 15 14:57:41 node01.xpandit.com nscd[3018]: 3018 monitoring directory `/etc` (2)
Oct 15 14:57:41 node01.xpandit.com nscd[3018]: 3018 monitoring file `/etc/services` (6)
Oct 15 14:57:41 node01.xpandit.com nscd[3018]: 3018 monitoring directory `/etc` (2)
Oct 15 14:57:41 node01.xpandit.com nscd[3018]: 3018 disabled inotify-based monitoring for file `/etc/netgroup': No such file or directory
Oct 15 14:57:41 node01.xpandit.com nscd[3018]: 3018 stat failed for file `/etc/netgroup'; will try again later: No such file or directory
Oct 15 14:57:41 node01.xpandit.com nscd[3018]: 3018 Access Vector Cache (AVC) started
Oct 15 14:57:41 node01.xpandit.com systemd[1]: Started Name Service Cache Daemon.

node04 | CHANGED | rc=0 >>
● nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; disabled; vendor preset: disabled)
   Active: active (running) since Mon 2018-10-15 14:57:41 UTC; 6s ago
  Process: 32737 ExecStart=/usr/sbin/nscd $NSCD_OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 32738 (nscd)
   CGroup: /system.slice/nscd.service
           └─32738 /usr/sbin/nscd

Oct 15 14:57:41 node04.xpandit.com nscd[32738]: 32738 monitoring file `/etc/hosts` (4)
Oct 15 14:57:41 node04.xpandit.com nscd[32738]: 32738 monitoring directory `/etc` (2)
Oct 15 14:57:41 node04.xpandit.com nscd[32738]: 32738 monitoring file `/etc/resolv.conf` (5)
Oct 15 14:57:41 node04.xpandit.com nscd[32738]: 32738 monitoring directory `/etc` (2)
Oct 15 14:57:41 node04.xpandit.com nscd[32738]: 32738 monitoring file `/etc/services` (6)
Oct 15 14:57:41 node04.xpandit.com nscd[32738]: 32738 monitoring directory `/etc` (2)
Oct 15 14:57:41 node04.xpandit.com nscd[32738]: 32738 disabled inotify-based monitoring for file `/etc/netgroup': No such file or directory
Oct 15 14:57:41 node04.xpandit.com nscd[32738]: 32738 stat failed for file `/etc/netgroup'; will try again later: No such file or directory
Oct 15 14:57:41 node04.xpandit.com nscd[32738]: 32738 Access Vector Cache (AVC) started
Oct 15 14:57:41 node04.xpandit.com systemd[1]: Started Name Service Cache Daemon.

node03 | CHANGED | rc=0 >>
● nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; disabled; vendor preset: disabled)
   Active: active (running) since Mon 2018-10-15 14:57:41 UTC; 6s ago
  Process: 32775 ExecStart=/usr/sbin/nscd $NSCD_OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 32776 (nscd)
   CGroup: /system.slice/nscd.service
           └─32776 /usr/sbin/nscd

Oct 15 14:57:41 node03.xpandit.com nscd[32776]: 32776 monitoring file `/etc/hosts` (4)
Oct 15 14:57:41 node03.xpandit.com nscd[32776]: 32776 monitoring directory `/etc` (2)
Oct 15 14:57:41 node03.xpandit.com nscd[32776]: 32776 monitoring file `/etc/resolv.conf` (5)
Oct 15 14:57:41 node03.xpandit.com nscd[32776]: 32776 monitoring directory `/etc` (2)
Oct 15 14:57:41 node03.xpandit.com nscd[32776]: 32776 monitoring file `/etc/services` (6)
Oct 15 14:57:41 node03.xpandit.com nscd[32776]: 32776 monitoring directory `/etc` (2)
Oct 15 14:57:41 node03.xpandit.com nscd[32776]: 32776 disabled inotify-based monitoring for file `/etc/netgroup': No such file or directory
Oct 15 14:57:41 node03.xpandit.com nscd[32776]: 32776 stat failed for file `/etc/netgroup'; will try again later: No such file or directory
Oct 15 14:57:41 node03.xpandit.com nscd[32776]: 32776 Access Vector Cache (AVC) started
Oct 15 14:57:41 node03.xpandit.com systemd[1]: Started Name Service Cache Daemon.


[root@node01 ~]# ansible -a "systemctl start ntpd" all
node05 | CHANGED | rc=0 >>


node01 | CHANGED | rc=0 >>


node02 | CHANGED | rc=0 >>


node03 | CHANGED | rc=0 >>


node04 | CHANGED | rc=0 >>


[root@node01 ~]# ansible -a "systemctl status ntpd" all
node02 | CHANGED | rc=0 >>
● ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; disabled; vendor preset: disabled)
   Active: active (running) since Mon 2018-10-15 14:58:09 UTC; 5s ago
  Process: 1609 ExecStart=/usr/sbin/ntpd -u ntp:ntp $OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 1610 (ntpd)
   CGroup: /system.slice/ntpd.service
           └─1610 /usr/sbin/ntpd -u ntp:ntp -g

Oct 15 14:58:09 node02.xpandit.com systemd[1]: Started Network Time Service.
Oct 15 14:58:09 node02.xpandit.com ntpd[1610]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Oct 15 14:58:09 node02.xpandit.com ntpd[1610]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Oct 15 14:58:09 node02.xpandit.com ntpd[1610]: Listen and drop on 1 v6wildcard :: UDP 123
Oct 15 14:58:09 node02.xpandit.com ntpd[1610]: Listen normally on 2 lo 127.0.0.1 UDP 123
Oct 15 14:58:09 node02.xpandit.com ntpd[1610]: Listen normally on 3 eth0 10.1.0.5 UDP 123
Oct 15 14:58:09 node02.xpandit.com ntpd[1610]: Listening on routing socket on fd #20 for interface updates
Oct 15 14:58:09 node02.xpandit.com ntpd[1610]: 0.0.0.0 c016 06 restart
Oct 15 14:58:09 node02.xpandit.com ntpd[1610]: 0.0.0.0 c012 02 freq_set kernel 0.000 PPM
Oct 15 14:58:09 node02.xpandit.com ntpd[1610]: 0.0.0.0 c011 01 freq_not_set

node05 | CHANGED | rc=0 >>
● ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; disabled; vendor preset: disabled)
   Active: active (running) since Mon 2018-10-15 14:58:09 UTC; 5s ago
  Process: 32904 ExecStart=/usr/sbin/ntpd -u ntp:ntp $OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 32905 (ntpd)
   CGroup: /system.slice/ntpd.service
           └─32905 /usr/sbin/ntpd -u ntp:ntp -g

Oct 15 14:58:09 node05.xpandit.com ntpd[32905]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Oct 15 14:58:09 node05.xpandit.com ntpd[32905]: Listen and drop on 1 v6wildcard :: UDP 123
Oct 15 14:58:09 node05.xpandit.com ntpd[32905]: Listen normally on 2 lo 127.0.0.1 UDP 123
Oct 15 14:58:09 node05.xpandit.com ntpd[32905]: Listen normally on 3 eth0 10.1.0.8 UDP 123
Oct 15 14:58:09 node05.xpandit.com ntpd[32905]: Listen normally on 4 lo ::1 UDP 123
Oct 15 14:58:09 node05.xpandit.com ntpd[32905]: Listen normally on 5 eth0 fe80::20d:3aff:fe19:227f UDP 123
Oct 15 14:58:09 node05.xpandit.com ntpd[32905]: Listening on routing socket on fd #22 for interface updates
Oct 15 14:58:09 node05.xpandit.com ntpd[32905]: 0.0.0.0 c016 06 restart
Oct 15 14:58:09 node05.xpandit.com ntpd[32905]: 0.0.0.0 c012 02 freq_set kernel 0.000 PPM
Oct 15 14:58:09 node05.xpandit.com ntpd[32905]: 0.0.0.0 c011 01 freq_not_set

node01 | CHANGED | rc=0 >>
● ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; disabled; vendor preset: disabled)
   Active: active (running) since Mon 2018-10-15 14:58:09 UTC; 5s ago
  Process: 3401 ExecStart=/usr/sbin/ntpd -u ntp:ntp $OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 3402 (ntpd)
   CGroup: /system.slice/ntpd.service
           └─3402 /usr/sbin/ntpd -u ntp:ntp -g

Oct 15 14:58:09 node01.xpandit.com systemd[1]: Started Network Time Service.
Oct 15 14:58:09 node01.xpandit.com ntpd[3402]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Oct 15 14:58:09 node01.xpandit.com ntpd[3402]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Oct 15 14:58:09 node01.xpandit.com ntpd[3402]: Listen and drop on 1 v6wildcard :: UDP 123
Oct 15 14:58:09 node01.xpandit.com ntpd[3402]: Listen normally on 2 lo 127.0.0.1 UDP 123
Oct 15 14:58:09 node01.xpandit.com ntpd[3402]: Listen normally on 3 eth0 10.1.0.4 UDP 123
Oct 15 14:58:09 node01.xpandit.com ntpd[3402]: Listening on routing socket on fd #20 for interface updates
Oct 15 14:58:09 node01.xpandit.com ntpd[3402]: 0.0.0.0 c016 06 restart
Oct 15 14:58:09 node01.xpandit.com ntpd[3402]: 0.0.0.0 c012 02 freq_set kernel 0.000 PPM
Oct 15 14:58:09 node01.xpandit.com ntpd[3402]: 0.0.0.0 c011 01 freq_not_set

node03 | CHANGED | rc=0 >>
● ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; disabled; vendor preset: disabled)
   Active: active (running) since Mon 2018-10-15 14:58:09 UTC; 5s ago
  Process: 32980 ExecStart=/usr/sbin/ntpd -u ntp:ntp $OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 32981 (ntpd)
   CGroup: /system.slice/ntpd.service
           └─32981 /usr/sbin/ntpd -u ntp:ntp -g

Oct 15 14:58:09 node03.xpandit.com ntpd[32981]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Oct 15 14:58:09 node03.xpandit.com ntpd[32981]: Listen and drop on 1 v6wildcard :: UDP 123
Oct 15 14:58:09 node03.xpandit.com ntpd[32981]: Listen normally on 2 lo 127.0.0.1 UDP 123
Oct 15 14:58:09 node03.xpandit.com ntpd[32981]: Listen normally on 3 eth0 10.1.0.6 UDP 123
Oct 15 14:58:09 node03.xpandit.com ntpd[32981]: Listen normally on 4 lo ::1 UDP 123
Oct 15 14:58:09 node03.xpandit.com ntpd[32981]: Listen normally on 5 eth0 fe80::20d:3aff:fe12:1f42 UDP 123
Oct 15 14:58:09 node03.xpandit.com ntpd[32981]: Listening on routing socket on fd #22 for interface updates
Oct 15 14:58:09 node03.xpandit.com ntpd[32981]: 0.0.0.0 c016 06 restart
Oct 15 14:58:09 node03.xpandit.com ntpd[32981]: 0.0.0.0 c012 02 freq_set kernel 0.000 PPM
Oct 15 14:58:09 node03.xpandit.com ntpd[32981]: 0.0.0.0 c011 01 freq_not_set

node04 | CHANGED | rc=0 >>
● ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; disabled; vendor preset: disabled)
   Active: active (running) since Mon 2018-10-15 14:58:09 UTC; 5s ago
  Process: 32947 ExecStart=/usr/sbin/ntpd -u ntp:ntp $OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 32948 (ntpd)
   CGroup: /system.slice/ntpd.service
           └─32948 /usr/sbin/ntpd -u ntp:ntp -g

Oct 15 14:58:09 node04.xpandit.com ntpd[32948]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Oct 15 14:58:09 node04.xpandit.com ntpd[32948]: Listen and drop on 1 v6wildcard :: UDP 123
Oct 15 14:58:09 node04.xpandit.com ntpd[32948]: Listen normally on 2 lo 127.0.0.1 UDP 123
Oct 15 14:58:09 node04.xpandit.com ntpd[32948]: Listen normally on 3 eth0 10.1.0.7 UDP 123
Oct 15 14:58:09 node04.xpandit.com ntpd[32948]: Listen normally on 4 lo ::1 UDP 123
Oct 15 14:58:09 node04.xpandit.com ntpd[32948]: Listen normally on 5 eth0 fe80::20d:3aff:fe10:c52b UDP 123
Oct 15 14:58:09 node04.xpandit.com ntpd[32948]: Listening on routing socket on fd #22 for interface updates
Oct 15 14:58:09 node04.xpandit.com ntpd[32948]: 0.0.0.0 c016 06 restart
Oct 15 14:58:09 node04.xpandit.com ntpd[32948]: 0.0.0.0 c012 02 freq_set kernel 0.000 PPM
Oct 15 14:58:09 node04.xpandit.com ntpd[32948]: 0.0.0.0 c011 01 freq_not_set
```


NTP synchronized:
```
[root@node01 ~]# ansible -a "ntpq -np" all
node01 | CHANGED | rc=0 >>
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*193.239.220.29  .MRS.            1 u    4   64    3   91.751   -1.968   0.591
 72.30.35.89     98.139.133.62    2 u    3   64    3   17.092    0.025   0.161
 147.231.100.5   .GPS.            1 u    -   64    3   94.254    0.263   0.192
 195.21.152.161  193.0.0.229      2 u    1   64    3   61.784    1.895   0.179

node05 | CHANGED | rc=0 >>
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*96.244.96.19    192.168.10.254   2 u    2   64    3    5.169    0.761   2.820
+198.206.133.14  25.151.162.158   3 u    1   64    3   22.368   -0.967   0.399
-204.11.201.12   216.218.254.202  2 u    2   64    3   84.204    3.390   0.349
+192.73.244.251  132.163.96.1     2 u    1   64    3   56.247   -1.656   0.384

node02 | CHANGED | rc=0 >>
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*64.113.44.55    64.113.44.54     2 u    3   64    3   23.875   -5.242   0.577
 173.255.215.209 127.67.113.92    2 u    1   64    3   72.139   -2.266   0.548
 184.105.182.7   216.218.254.202  2 u    2   64    3   66.949   -5.489   0.691
 162.220.14.253  216.218.254.202  2 u   57   64    1   56.554   -0.714   0.711

node03 | CHANGED | rc=0 >>
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*38.126.113.11   .CDMA.           1 u    2   64    3   84.706   -6.346   1.474
 91.206.8.36     131.130.251.107  2 u    -   64    3   99.381    1.219   1.569
 90.187.7.5      .DCFa.           1 u   58   64    1  105.734   -4.246   1.890
 87.233.197.123  193.79.237.14    2 u    1   64    3   80.395    0.018   1.499

node04 | CHANGED | rc=0 >>
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*38.126.113.11   .CDMA.           1 u    4   64    3   85.732   -6.452   1.516
 91.206.8.36     131.130.251.107  2 u    3   64    3   96.459   -0.072   4.044
 90.187.7.5      .DCFa.           1 u   58   64    1  105.035   -3.868   1.683
 87.233.197.123  193.79.237.14    2 u   57   64    1   80.543    0.150   0.132
```



## MariaDB

Checked yum repositories for MariaDB versions:

```
[root@node01 ~]# yum list mariadb --showduplicates
Loaded plugins: fastestmirror, langpacks
Loading mirror speeds from cached hostfile
 * epel: mirror.cogentco.com
Available Packages
mariadb.x86_64                       1:5.5.56-2.el7                          base
mariadb.x86_64                       1:5.5.60-1.el7_5                        updates
```


Installed mariadb-server on node01 and node02:
```
[root@node01 ~]# yum install -y mariadb-server

[root@node02 ~]# yum install -y mariadb-server
```


Installed mariadb-client on all hosts:
```
ansible -a "yum install -y mariadb" all
```


Installed MariaDB JDBC:
```
[root@node01 ~]# ansible -a "mkdir -p /usr/share/java/" all
[root@node01 ~]# wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.46.tar.gz
[root@node01 ~]# tar zxvf mysql-connector-java-5.1.46.tar.gz
[root@node01 ~]# cp mysql-connector-java-5.1.46/mysql-connector-java-5.1.46.jar /usr/share/java/mysql-connector-java.jar
```

Ran `scp` to send to all nodes.


Configured MariaDB with replica in `node02.xpandit.com`.


# Cloudera Manager Setup

Added CM 5.13.3 repo to `/etc/yum.repos.d/`:
```
[root@node01 ~]# cat /etc/yum.repos.d/cloudera-manager.repo
[cloudera-manager]
# Packages for Cloudera Manager, Version 5, on RedHat or CentOS 7 x86_64
name=Cloudera Manager
baseurl=https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/5.13.3
gpgkey =https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/RPM-GPG-KEY-cloudera
gpgcheck = 1
```
