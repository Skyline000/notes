# Untitled

```text
[ccuser@ccoam etc]$ cat fstab

#
# /etc/fstab
# Created by anaconda on Wed Oct  8 21:08:19 2014
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=e33bc288-265a-490c-bd30-a7cbaf95c429 /                       ext4    defaults        1 1
UUID=5dd75a01-b6f1-413b-af19-31a063684cab /boot                   ext4    defaults        1 2
UUID=beb9194c-de8b-4c22-ab24-eb6bea43fa37 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

cclpapp1:/home/sftproot/home/sftp_ucr   /mnt/data_ucr   nfs     defaults        0 0

//192.168.80.150/backup    /NAS-backup              cifs    username=admin,password=ccadmin@1513,uid=ccuser,GID=ccuser 0 0
[ccuser@ccoam etc]$ df -h
Filesystem                                Size  Used Avail Use% Mounted on
/dev/sda3                                 244G  154G   79G  67% /
tmpfs                                     3.9G     0  3.9G   0% /dev/shm
/dev/sda1                                 194M   34M  151M  19% /boot
//192.168.80.150/backup                    15T  9.0T  5.5T  63% /NAS-backup
ccweb1:/home/PROJECTS/pegasus_media_web   244G  157G   75G  68% /mnt/ccweb1_media
ccweb1:/home/PROJECTS/pegasus_web/upload  244G  157G   75G  68% /mnt/ccweb1_upload
ccweb2:/home/PROJECTS/pegasus_media_web   244G   89G  143G  39% /mnt/ccweb2_media
ccweb2:/home/PROJECTS/pegasus_web/upload  244G   89G  143G  39% /mnt/ccweb2_upload
[ccuser@ccoam etc]$ ps -elf | grep httpd
1 S root     16654     1  0  80   0 - 86869 poll_s 10:29 ?        00:00:00 /usr/sbin/httpd
5 S apache   16656 16654  1  80   0 - 88463 inet_c 10:29 ?        00:05:02 /usr/sbin/httpd
5 S apache   16657 16654  1  80   0 - 89688 inet_c 10:29 ?        00:05:03 /usr/sbin/httpd
5 S apache   16658 16654  1  80   0 - 89807 inet_c 10:29 ?        00:05:07 /usr/sbin/httpd
5 S apache   16659 16654  1  80   0 - 88370 futex_ 10:29 ?        00:05:00 /usr/sbin/httpd
5 S apache   16660 16654  0  80   0 - 89805 inet_c 10:29 ?        00:00:04 /usr/sbin/httpd
5 S apache   16661 16654  1  80   0 - 89564 inet_c 10:29 ?        00:05:03 /usr/sbin/httpd
5 S apache   16662 16654  0  80   0 - 89423 inet_c 10:29 ?        00:00:03 /usr/sbin/httpd
5 S apache   16663 16654  1  80   0 - 88111 inet_c 10:29 ?        00:05:01 /usr/sbin/httpd
5 S apache   17019 16654  0  80   0 - 89116 inet_c 10:39 ?        00:00:02 /usr/sbin/httpd
5 S apache   17020 16654  0  80   0 - 89432 inet_c 10:39 ?        00:00:10 /usr/sbin/httpd
5 S apache   17021 16654  0  80   0 - 89464 inet_c 10:39 ?        00:00:01 /usr/sbin/httpd
5 S apache   17022 16654  0  80   0 - 89464 inet_c 10:39 ?        00:00:02 /usr/sbin/httpd
5 S apache   17023 16654  0  80   0 - 88468 inet_c 10:39 ?        00:00:03 /usr/sbin/httpd
5 S apache   17024 16654  3  80   0 - 88575 inet_c 10:39 ?        00:10:05 /usr/sbin/httpd
5 S apache   17025 16654  0  80   0 - 89722 inet_c 10:39 ?        00:00:02 /usr/sbin/httpd
5 S apache   20705 16654  0  80   0 - 89807 inet_c 12:08 ?        00:00:03 /usr/sbin/httpd
0 S ccuser   27511 27398  0  80   0 - 25813 pipe_w 14:53 pts/0    00:00:00 grep httpd
[ccuser@ccoam etc]$ cd /var/log/httpd/
[ccuser@ccoam httpd]$ ls
access_log  access_log-20181216  access_log-20181223  access_log-20181230  access_log-20190106  error_log  error_log-20181216  error_log-20181223  error_log-20181230  error_log-20190106
[ccuser@ccoam httpd]$ ll
total 55373468
-rw-r--r-- 1 root root     9182487 Jan 11 14:54 access_log
-rw-r--r-- 1 root root    12247260 Dec 16 03:17 access_log-20181216
-rw-r--r-- 1 root root    15529929 Dec 23 03:07 access_log-20181223
-rw-r--r-- 1 root root    16653952 Dec 30 03:11 access_log-20181230
-rw-r--r-- 1 root root    15142260 Jan  6 03:37 access_log-20190106
-rw-r--r-- 1 root root 56603232595 Jan 11 14:54 error_log
-rw-r--r-- 1 root root     5930596 Dec 16 03:19 error_log-20181216
-rw-r--r-- 1 root root     8229274 Dec 23 03:28 error_log-20181223
-rw-r--r-- 1 root root     8835066 Dec 30 03:13 error_log-20181230
-rw-r--r-- 1 root root     7387215 Jan  6 03:50 error_log-20190106
[ccuser@ccoam httpd]$ tail -f error_log
[Fri Jan 11 14:48:43 2019] [error] [client 203.186.115.134] PHP Warning:  mssql_result() expects parameter 1 to be resource, boolean given in /home/PROJECTS/ticketingadmin/pages/internetEnquiry/dataTableHandler.php on line 97, referer: http://210.184.155.70/ticketingadmin/pages/internetEnquiry/dailySuccessTrans.php
[Fri Jan 11 14:48:43 2019] [error] [client 203.186.115.134] PHP Warning:  mssql_result() expects parameter 1 to be resource, boolean given in /home/PROJECTS/ticketingadmin/pages/internetEnquiry/dataTableHandler.php on line 98, referer: http://210.184.155.70/ticketingadmin/pages/internetEnquiry/dailySuccessTrans.php
[Fri Jan 11 14:48:43 2019] [error] [client 203.186.115.134] PHP Warning:  mssql_result() expects parameter 1 to be resource, boolean given in /home/PROJECTS/ticketingadmin/pages/internetEnquiry/dataTableHandler.php on line 99, referer: http://210.184.155.70/ticketingadmin/pages/internetEnquiry/dailySuccessTrans.php
[Fri Jan 11 14:48:43 2019] [error] [client 203.186.115.134] PHP Warning:  mssql_query(): message: Incorrect syntax near the keyword 'AND'. (severity 15) in /home/PROJECTS/ticketingadmin/pages/internetEnquiry/dataTableHandler.php on line 120, referer: http://210.184.155.70/ticketingadmin/pages/internetEnquiry/dailySuccessTrans.php
[Fri Jan 11 14:48:43 2019] [error] [client 203.186.115.134] PHP Warning:  mssql_query(): General SQL Server error: Check messages from the SQL Server (severity 15) in /home/PROJECTS/ticketingadmin/pages/internetEnquiry/dataTableHandler.php on line 120, referer: http://210.184.155.70/ticketingadmin/pages/internetEnquiry/dailySuccessTrans.php
[Fri Jan 11 14:48:43 2019] [error] [client 203.186.115.134] PHP Warning:  mssql_query(): message: Invalid usage of the option NEXT in the FETCH statement. (severity 15) in /home/PROJECTS/ticketingadmin/pages/internetEnquiry/dataTableHandler.php on line 120, referer: http://210.184.155.70/ticketingadmin/pages/internetEnquiry/dailySuccessTrans.php
[Fri Jan 11 14:48:43 2019] [error] [client 203.186.115.134] PHP Warning:  mssql_query(): General SQL Server error: Check messages from the SQL Server (severity 15) in /home/PROJECTS/ticketingadmin/pages/internetEnquiry/dataTableHandler.php on line 120, referer: http://210.184.155.70/ticketingadmin/pages/internetEnquiry/dailySuccessTrans.php
[Fri Jan 11 14:48:43 2019] [error] [client 203.186.115.134] PHP Warning:  mssql_query(): Query failed in /home/PROJECTS/ticketingadmin/pages/internetEnquiry/dataTableHandler.php on line 120, referer: http://210.184.155.70/ticketingadmin/pages/internetEnquiry/dailySuccessTrans.php
[Fri Jan 11 14:48:43 2019] [error] [client 203.186.115.134] PHP Warning:  mssql_num_rows() expects parameter 1 to be resource, boolean given in /home/PROJECTS/ticketingadmin/pages/internetEnquiry/dataTableHandler.php on line 121, referer: http://210.184.155.70/ticketingadmin/pages/internetEnquiry/dailySuccessTrans.php
[Fri Jan 11 14:54:21 2019] [error] [client 203.186.115.134] PHP Warning:  mssql_connect(): Unable to connect to server: cccpdb:8000 in /home/PROJECTS/ticketingadmin/pages/internetEnquiry/class/TransactionWorker.php on line 45, referer: http://210.184.155.70/ticketingadmin/pages/internetEnquiry/dailySuccessTrans.php
^C
[ccuser@ccoam httpd]$ cat /etc/hosts
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4 ccoam
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6

192.168.80.121  ccoam
192.168.80.101  ccweb1
192.168.80.102  ccweb2

210.184.155.70  ccoam

#192.168.90.19  cclpapp1
192.168.90.29   cclpapp1
192.168.90.20   cclpdb1

192.168.80.111  ccdb1
192.168.80.112  ccdb2
192.168.80.131  CCMYSQL1
192.168.80.131  ccmysql1
192.168.80.132  ccmysql2

192.168.80.70   ccnagios

192.168.80.101  www.cinemacity.com.hk

10.51.1.40  cccwdb
10.51.1.21  cccwdb1
10.51.1.11  cccwapp1
10.51.1.12  cccwapp2

10.52.1.40  ccjpdb
10.52.1.21  ccjpdb1
10.52.1.22  ccjpdb2
10.52.1.11  ccjpapp1
10.52.1.12  ccjpapp2

10.53.1.20  ccsgdb
10.53.1.21  ccsgdb1
10.53.1.22  ccsgdb2
10.53.1.11  ccsgapp1
10.53.1.12  ccsgapp2

10.54.1.20  cccpdb
10.54.1.21  cccpdb1
10.54.1.22  cccpdb2
10.54.1.11  cccpapp1
10.54.1.12  cccpapp2

[ccuser@ccoam httpd]$ ping cccpdb
PING cccpdb (10.54.1.20) 56(84) bytes of data.
64 bytes from cccpdb (10.54.1.20): icmp_seq=1 ttl=123 time=4.60 ms
64 bytes from cccpdb (10.54.1.20): icmp_seq=2 ttl=123 time=4.39 ms
64 bytes from cccpdb (10.54.1.20): icmp_seq=3 ttl=123 time=4.75 ms
64 bytes from cccpdb (10.54.1.20): icmp_seq=4 ttl=123 time=4.65 ms
^C
--- cccpdb ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3096ms
rtt min/avg/max/mdev = 4.393/4.601/4.755/0.155 ms
[ccuser@ccoam httpd]$ telnet cccpdb 8000
Trying 10.54.1.20...
Connected to cccpdb.
Escape character is '^]'.
^]
telnet> quit
Connection closed.
[ccuser@ccoam httpd]$

```

