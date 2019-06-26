# Change SSH port

 Check if SELinux is enabled, execute the `sestatus` command

```text
[root@localhost ssh]# sestatus
SELinux status:                 enabled
SELinuxfs mount:                /sys/fs/selinux
SELinux root directory:         /etc/selinux
Loaded policy name:             targeted
Current mode:                   enforcing
Mode from config file:          enforcing
Policy MLS status:              enabled
Policy deny_unknown status:     allowed
Max kernel policy version:      31

```

When SELinux is disabled you should be able to put the SSHD daemon on any port you like. However, when SELinux is enabled, you’ll need to do some extra work.

 To view the allowed ports for ssh you can execute the following command 

```text
semanage port -l | grep ssh
```

```text
[root@localhost ssh]# semanage port -l | grep ssh
ssh_port_t                     tcp      22
```

 If you don’t have the semanage command in your CentOS distro \(ex: the minimal distro\), you can install it using `sudo yum install policycoreutils-python`

 To allow the SSH daemon to also run on port 7387, you need to execute this \(this can take a while to return\)

```text
semanage port -a -t ssh_port_t -p tcp 7387
```

 After that, you’ll be able to run the ssh daemon on port 7387

```text
[root@localhost ssh]# semanage port -l | grep ssh
ssh_port_t                     tcp      7387, 22
```

Change SSH service config  `/etc/ssh/sshd_config`

```text
[root@localhost ~]# vi /etc/ssh/sshd_config
Port 7387
```

Restart service to activate the changes, and use `netstat` to confirm is the SSH service listening to port 7387

```text
[root@localhost ssh]# netstat -ant | grep :7387
tcp        0      0 0.0.0.0:7387            0.0.0.0:*               LISTEN
tcp6       0      0 :::7387                 :::*                    LISTEN
```

Now SSH port changed to 7387, but still do not accept port 7387 connection, because iptables only allow port 22. We need to open the port 7387.

WE can create a  Shell Script for the  iptables setting. Later we can use back the file for 

```text
[root@localhost ~]# vi ~/set_iptables.sh

TH=/sbin:/bin:/usr/sbin:/usr/bin; export PATH

iptables -F
iptables -X
iptables -Z

iptables -P   INPUT DROP
iptables -P  OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

### 允許本機和已經建立連線的封包通過 ###
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

### icmp 全部開放 ###
iptables -A INPUT -p icmp -j ACCEPT

### sshd 內網 開放 ###
iptables -A INPUT -i ens33 -p tcp -s 192.168.0.0/16   --dport 7387  -j ACCEPT

### 儲存設定檔給下次開機使用 ###
iptables-save > /etc/sysconfig/iptables
```

Then execute and check the  iptables setting.

```text
[root@localhost ~]# sh ~/set_iptables.sh
[root@localhost ~]#
[root@localhost ~]# iptables -L -n
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0
ACCEPT     tcp  --  192.168.0.0/16       0.0.0.0/0            tcp dpt:7387

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```



Reference:

[http://yenpai.idis.com.tw/archives/273-%E6%95%99%E5%AD%B8-centos-6-3-%E8%A8%AD%E5%AE%9A-1-%E5%9F%BA%E6%9C%AC%E8%AA%BF%E6%95%88%E8%88%87-ssh-%E9%80%A3%E7%B7%9A](http://yenpai.idis.com.tw/archives/273-%E6%95%99%E5%AD%B8-centos-6-3-%E8%A8%AD%E5%AE%9A-1-%E5%9F%BA%E6%9C%AC%E8%AA%BF%E6%95%88%E8%88%87-ssh-%E9%80%A3%E7%B7%9A)

[https://ddewaele.github.io/networking/ssh/changing-the-ssh-port/](https://ddewaele.github.io/networking/ssh/changing-the-ssh-port/)





