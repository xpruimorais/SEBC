### Cloud Provider
- Azure (Region: East US 2)

### Linux Release
```
[root@node01 ~]# cat /etc/centos-release
CentOS Linux release 7.3.1611 (Core)
```

### Disk Space

```
[root@node01 ~]# ansible -a "df -h" all
node01 | CHANGED | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       100G  1.4G   99G   2% /
devtmpfs        7.9G     0  7.9G   0% /dev
tmpfs           7.9G  124K  7.9G   1% /dev/shm
tmpfs           7.9G  8.4M  7.9G   1% /run
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sda1       497M   62M  436M  13% /boot
/dev/sdb1       100G   33M  100G   1% /data/01
/dev/sdc1        32G   49M   30G   1% /mnt/resource
tmpfs           1.6G     0  1.6G   0% /run/user/0
tmpfs           1.6G     0  1.6G   0% /run/user/1000

node04 | CHANGED | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       100G  1.2G   99G   2% /
devtmpfs        7.9G     0  7.9G   0% /dev
tmpfs           7.9G     0  7.9G   0% /dev/shm
tmpfs           7.9G  8.4M  7.9G   1% /run
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sda1       497M   62M  436M  13% /boot
/dev/sdc1       100G   33M  100G   1% /data/01
/dev/sdb1        32G   49M   30G   1% /mnt/resource
tmpfs           1.6G     0  1.6G   0% /run/user/0

node03 | CHANGED | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       100G  1.2G   99G   2% /
devtmpfs        7.9G     0  7.9G   0% /dev
tmpfs           7.9G     0  7.9G   0% /dev/shm
tmpfs           7.9G  8.4M  7.9G   1% /run
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sda1       497M   62M  436M  13% /boot
/dev/sdc1       100G   33M  100G   1% /data/01
/dev/sdb1        32G   49M   30G   1% /mnt/resource
tmpfs           1.6G     0  1.6G   0% /run/user/0

node02 | CHANGED | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       100G  1.2G   99G   2% /
devtmpfs        7.9G     0  7.9G   0% /dev
tmpfs           7.9G     0  7.9G   0% /dev/shm
tmpfs           7.9G  8.4M  7.9G   1% /run
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sda1       497M   62M  436M  13% /boot
/dev/sdc1       100G   33M  100G   1% /data/01
/dev/sdb1        32G   49M   30G   1% /mnt/resource
tmpfs           1.6G     0  1.6G   0% /run/user/0

node05 | CHANGED | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       100G  1.2G   99G   2% /
devtmpfs        7.9G     0  7.9G   0% /dev
tmpfs           7.9G     0  7.9G   0% /dev/shm
tmpfs           7.9G  8.4M  7.9G   1% /run
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sda1       497M   62M  436M  13% /boot
/dev/sdc1       100G   33M  100G   1% /data/01
/dev/sdb1        32G   49M   30G   1% /mnt/resource
tmpfs           1.6G     0  1.6G   0% /run/user/0
```


### Repolist Enabled
```
[root@node01 ~]# ansible -a "yum repolist enabled" all
node02 | CHANGED | rc=0 >>
Loaded plugins: fastestmirror, langpacks
Loading mirror speeds from cached hostfile
repo id                   repo name                                       status
base/7/x86_64             CentOS-7 - Base                                 9,911
extras/7/x86_64           CentOS-7 - Extras                                 432
openlogic/7/x86_64        CentOS-7 - openlogic packages for x86_64          115
updates/7/x86_64          CentOS-7 - Updates                              1,561
repolist: 12,019

node04 | CHANGED | rc=0 >>
Loaded plugins: fastestmirror, langpacks
Loading mirror speeds from cached hostfile
repo id                   repo name                                       status
base/7/x86_64             CentOS-7 - Base                                 9,911
extras/7/x86_64           CentOS-7 - Extras                                 432
openlogic/7/x86_64        CentOS-7 - openlogic packages for x86_64          115
updates/7/x86_64          CentOS-7 - Updates                              1,561
repolist: 12,019

node03 | CHANGED | rc=0 >>
Loaded plugins: fastestmirror, langpacks
Loading mirror speeds from cached hostfile
repo id                   repo name                                       status
base/7/x86_64             CentOS-7 - Base                                 9,911
extras/7/x86_64           CentOS-7 - Extras                                 432
openlogic/7/x86_64        CentOS-7 - openlogic packages for x86_64          115
updates/7/x86_64          CentOS-7 - Updates                              1,561
repolist: 12,019

node05 | CHANGED | rc=0 >>
Loaded plugins: fastestmirror, langpacks
Loading mirror speeds from cached hostfile
repo id                   repo name                                       status
base/7/x86_64             CentOS-7 - Base                                 9,911
extras/7/x86_64           CentOS-7 - Extras                                 432
openlogic/7/x86_64        CentOS-7 - openlogic packages for x86_64          115
updates/7/x86_64          CentOS-7 - Updates                              1,561
repolist: 12,019

node01 | CHANGED | rc=0 >>
Loaded plugins: fastestmirror, langpacks
Loading mirror speeds from cached hostfile
 * epel: mirror.cogentco.com
repo id                repo name                                          status
base/7/x86_64          CentOS-7 - Base                                     9,911
epel/x86_64            Extra Packages for Enterprise Linux 7 - x86_64     12,741
extras/7/x86_64        CentOS-7 - Extras                                     432
openlogic/7/x86_64     CentOS-7 - openlogic packages for x86_64              115
updates/7/x86_64       CentOS-7 - Updates                                  1,561
repolist: 24,760
```


### Users

## Create Users
```
[root@node01 ~]# ansible -a "useradd -u 2000 raffles" all
node01 | CHANGED | rc=0 >>


node04 | CHANGED | rc=0 >>


node03 | CHANGED | rc=0 >>


node02 | CHANGED | rc=0 >>


node05 | CHANGED | rc=0 >>


```

```
[root@node01 ~]# ansible -a "useradd -u 3000 fullerton" all
node04 | CHANGED | rc=0 >>


node01 | CHANGED | rc=0 >>


node02 | CHANGED | rc=0 >>


node05 | CHANGED | rc=0 >>


node03 | CHANGED | rc=0 >>


```

## Create Groups

```
[root@node01 ~]# ansible -a "groupadd hotels" all
node03 | CHANGED | rc=0 >>


node04 | CHANGED | rc=0 >>


node02 | CHANGED | rc=0 >>


node01 | CHANGED | rc=0 >>


node05 | CHANGED | rc=0 >>



```


```
ansible -a "groupadd shops" all
node01 | CHANGED | rc=0 >>


node04 | CHANGED | rc=0 >>


node02 | CHANGED | rc=0 >>


node03 | CHANGED | rc=0 >>


node05 | CHANGED | rc=0 >>



```

## Add Users to Groups

```
[root@node01 ~]# ansible -a "usermod -aG hotels fullerton" all
node01 | CHANGED | rc=0 >>


node04 | CHANGED | rc=0 >>


node02 | CHANGED | rc=0 >>


node05 | CHANGED | rc=0 >>


node03 | CHANGED | rc=0 >>



```


```
[root@node01 ~]# ansible -a "usermod -aG shops raffles" all
node04 | CHANGED | rc=0 >>


node01 | CHANGED | rc=0 >>


node05 | CHANGED | rc=0 >>


node02 | CHANGED | rc=0 >>


node03 | CHANGED | rc=0 >>



```


### List Users and Groups

```
[root@node01 ~]# ansible -a "getent passwd raffles" all
node03 | CHANGED | rc=0 >>
raffles:x:2000:2000::/home/raffles:/bin/bash

node02 | CHANGED | rc=0 >>
raffles:x:2000:2000::/home/raffles:/bin/bash

node01 | CHANGED | rc=0 >>
raffles:x:2000:2000::/home/raffles:/bin/bash

node04 | CHANGED | rc=0 >>
raffles:x:2000:2000::/home/raffles:/bin/bash

node05 | CHANGED | rc=0 >>
raffles:x:2000:2000::/home/raffles:/bin/bash
```

```
[root@node01 ~]# ansible -a "getent passwd fullerton" all
node01 | CHANGED | rc=0 >>
fullerton:x:3000:3000::/home/fullerton:/bin/bash

node03 | CHANGED | rc=0 >>
fullerton:x:3000:3000::/home/fullerton:/bin/bash

node04 | CHANGED | rc=0 >>
fullerton:x:3000:3000::/home/fullerton:/bin/bash

node05 | CHANGED | rc=0 >>
fullerton:x:3000:3000::/home/fullerton:/bin/bash

node02 | CHANGED | rc=0 >>
fullerton:x:3000:3000::/home/fullerton:/bin/bash
```


```
[root@node01 ~]# ansible -a "getent group hotels" all
node03 | CHANGED | rc=0 >>
hotels:x:3001:fullerton

node01 | CHANGED | rc=0 >>
hotels:x:3001:fullerton

node02 | CHANGED | rc=0 >>
hotels:x:3001:fullerton

node05 | CHANGED | rc=0 >>
hotels:x:3001:fullerton

node04 | CHANGED | rc=0 >>
hotels:x:3001:fullerton
```


```
[root@node01 ~]# ansible -a "getent group shops" all
node02 | CHANGED | rc=0 >>
shops:x:3002:raffles

node01 | CHANGED | rc=0 >>
shops:x:3002:raffles

node03 | CHANGED | rc=0 >>
shops:x:3002:raffles

node04 | CHANGED | rc=0 >>
shops:x:3002:raffles

node05 | CHANGED | rc=0 >>
shops:x:3002:raffles
```
