# --------------------------------------------------------
# Установка пакетов

Script started on Ср 08 янв 2020 15:57:12
[vagrant@centos ~]$ ls
typescript
[vagrant@centos ~]$ 
[vagrant@centos ~]$ 
[vagrant@centos ~]$ yum install -y redhat-lsb-core
Loaded plugins: fastestmirror
You need to be root to perform this command.
[vagrant@centos ~]$ sudo su
[root@centos vagrant]# yum install -y redhat-lsb-core
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.yandex.ru
 * epel: mirror.datacenter.by
 * extras: dedic.sh
 * updates: mirror.logol.ru
Resolving Dependencies
--> Running transaction check
---> Package redhat-lsb-core.x86_64 0:4.1-27.el7.centos.1 will be installed
--> Processing Dependency: redhat-lsb-submod-security(x86-64) = 4.1-27.el7.centos.1 for package: redhat-lsb-core-4.1-27.el7.centos.1.x86_64
--> Processing Dependency: spax for package: redhat-lsb-core-4.1-27.el7.centos.1.x86_64
--> Processing Dependency: /usr/sbin/fuser for package: redhat-lsb-core-4.1-27.el7.centos.1.x86_64
--> Processing Dependency: /usr/bin/time for package: redhat-lsb-core-4.1-27.el7.centos.1.x86_64
--> Processing Dependency: /usr/bin/m4 for package: redhat-lsb-core-4.1-27.el7.centos.1.x86_64
--> Processing Dependency: /usr/bin/lpr for package: redhat-lsb-core-4.1-27.el7.centos.1.x86_64
--> Processing Dependency: /usr/bin/lp for package: redhat-lsb-core-4.1-27.el7.centos.1.x86_64
--> Processing Dependency: /usr/bin/killall for package: redhat-lsb-core-4.1-27.el7.centos.1.x86_64
--> Processing Dependency: /usr/bin/batch for package: redhat-lsb-core-4.1-27.el7.centos.1.x86_64
--> Processing Dependency: /usr/bin/at for package: redhat-lsb-core-4.1-27.el7.centos.1.x86_64
--> Processing Dependency: /bin/mailx for package: redhat-lsb-core-4.1-27.el7.centos.1.x86_64
--> Processing Dependency: /bin/ed for package: redhat-lsb-core-4.1-27.el7.centos.1.x86_64
--> Running transaction check
---> Package at.x86_64 0:3.1.13-24.el7 will be installed
---> Package cups-client.x86_64 1:1.6.3-40.el7 will be installed
--> Processing Dependency: cups-libs(x86-64) = 1:1.6.3-40.el7 for package: 1:cups-client-1.6.3-40.el7.x86_64
---> Package ed.x86_64 0:1.9-4.el7 will be installed
---> Package m4.x86_64 0:1.4.16-10.el7 will be installed
---> Package mailx.x86_64 0:12.5-19.el7 will be installed
---> Package psmisc.x86_64 0:22.20-16.el7 will be installed
---> Package redhat-lsb-submod-security.x86_64 0:4.1-27.el7.centos.1 will be installed
---> Package spax.x86_64 0:1.5.2-13.el7 will be installed
---> Package time.x86_64 0:1.7-45.el7 will be installed
--> Running transaction check
---> Package cups-libs.x86_64 1:1.6.3-35.el7 will be updated
---> Package cups-libs.x86_64 1:1.6.3-40.el7 will be an update
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package                       Arch      Version                  Repository
                                                                           Size
================================================================================
Installing:
 redhat-lsb-core               x86_64    4.1-27.el7.centos.1      base     38 k
Installing for dependencies:
 at                            x86_64    3.1.13-24.el7            base     51 k
 cups-client                   x86_64    1:1.6.3-40.el7           base    151 k
 ed                            x86_64    1.9-4.el7                base     72 k
 m4                            x86_64    1.4.16-10.el7            base    256 k
 mailx                         x86_64    12.5-19.el7              base    245 k
 psmisc                        x86_64    22.20-16.el7             base    141 k
 redhat-lsb-submod-security    x86_64    4.1-27.el7.centos.1      base     15 k
 spax                          x86_64    1.5.2-13.el7             base    260 k
 time                          x86_64    1.7-45.el7               base     30 k
Updating for dependencies:
 cups-libs                     x86_64    1:1.6.3-40.el7           base    358 k

Transaction Summary
================================================================================
Install  1 Package  (+9 Dependent packages)
Upgrade             ( 1 Dependent package)

Total download size: 1.6 M
Downloading packages:
No Presto metadata available for base
(1/11): at-3.1.13-24.el7.x86_64.rpm                        |  51 kB   00:00     
(2/11): cups-client-1.6.3-40.el7.x86_64.rpm                | 151 kB   00:00     
(3/11): ed-1.9-4.el7.x86_64.rpm                            |  72 kB   00:00     
(4/11): cups-libs-1.6.3-40.el7.x86_64.rpm                  | 358 kB   00:00     
(5/11): m4-1.4.16-10.el7.x86_64.rpm                        | 256 kB   00:00     
(6/11): mailx-12.5-19.el7.x86_64.rpm                       | 245 kB   00:00     
(7/11): redhat-lsb-core-4.1-27.el7.centos.1.x86_64.rpm     |  38 kB   00:00     
(8/11): redhat-lsb-submod-security-4.1-27.el7.centos.1.x86 |  15 kB   00:00     
(9/11): psmisc-22.20-16.el7.x86_64.rpm                     | 141 kB   00:00     
(10/11): time-1.7-45.el7.x86_64.rpm                        |  30 kB   00:00     
(11/11): spax-1.5.2-13.el7.x86_64.rpm                      | 260 kB   00:00     
--------------------------------------------------------------------------------
Total                                              1.4 MB/s | 1.6 MB  00:01     
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : psmisc-22.20-16.el7.x86_64                                  1/12 
  Installing : m4-1.4.16-10.el7.x86_64                                     2/12 
  Installing : ed-1.9-4.el7.x86_64                                         3/12 
  Installing : mailx-12.5-19.el7.x86_64                                    4/12 
  Installing : spax-1.5.2-13.el7.x86_64                                    5/12 
  Updating   : 1:cups-libs-1.6.3-40.el7.x86_64                             6/12 
  Installing : 1:cups-client-1.6.3-40.el7.x86_64                           7/12 
  Installing : at-3.1.13-24.el7.x86_64                                     8/12 
  Installing : time-1.7-45.el7.x86_64                                      9/12 
  Installing : redhat-lsb-submod-security-4.1-27.el7.centos.1.x86_64      10/12 
  Installing : redhat-lsb-core-4.1-27.el7.centos.1.x86_64                 11/12 
  Cleanup    : 1:cups-libs-1.6.3-35.el7.x86_64                            12/12 
  Verifying  : redhat-lsb-submod-security-4.1-27.el7.centos.1.x86_64       1/12 
  Verifying  : time-1.7-45.el7.x86_64                                      2/12 
  Verifying  : at-3.1.13-24.el7.x86_64                                     3/12 
  Verifying  : 1:cups-libs-1.6.3-40.el7.x86_64                             4/12 
  Verifying  : spax-1.5.2-13.el7.x86_64                                    5/12 
  Verifying  : mailx-12.5-19.el7.x86_64                                    6/12 
  Verifying  : ed-1.9-4.el7.x86_64                                         7/12 
  Verifying  : redhat-lsb-core-4.1-27.el7.centos.1.x86_64                  8/12 
  Verifying  : m4-1.4.16-10.el7.x86_64                                     9/12 
  Verifying  : 1:cups-client-1.6.3-40.el7.x86_64                          10/12 
  Verifying  : psmisc-22.20-16.el7.x86_64                                 11/12 
  Verifying  : 1:cups-libs-1.6.3-35.el7.x86_64                            12/12 

Installed:
  redhat-lsb-core.x86_64 0:4.1-27.el7.centos.1                                  

Dependency Installed:
  at.x86_64 0:3.1.13-24.el7                                                     
  cups-client.x86_64 1:1.6.3-40.el7                                             
  ed.x86_64 0:1.9-4.el7                                                         
  m4.x86_64 0:1.4.16-10.el7                                                     
  mailx.x86_64 0:12.5-19.el7                                                    
  psmisc.x86_64 0:22.20-16.el7                                                  
  redhat-lsb-submod-security.x86_64 0:4.1-27.el7.centos.1                       
  spax.x86_64 0:1.5.2-13.el7                                                    
  time.x86_64 0:1.7-45.el7                                                      

Dependency Updated:
  cups-libs.x86_64 1:1.6.3-40.el7                                               

Complete!
[root@centos vagrant]# exit
exit
[vagrant@centos ~]$ sudo yum install -y wget
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.yandex.ru
 * epel: fedora-mirror02.rbc.ru
 * extras: dedic.sh
 * updates: mirror.logol.ru
Package wget-1.14-18.el7_6.1.x86_64 already installed and latest version
Nothing to do
[vagrant@centos ~]$ sudo yum install -y rpmdevtools
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.yandex.ru
 * epel: mirror.datacenter.by
 * extras: dedic.sh
 * updates: mirror.logol.ru
Package rpmdevtools-8.3-5.el7.noarch already installed and latest version
Nothing to do
[vagrant@centos ~]$ 
[vagrant@centos ~]$ 
[vagrant@centos ~]$ sudo yum install -y rpm-build
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.yandex.ru
 * epel: fedora-mirror02.rbc.ru
 * extras: dedic.sh
 * updates: mirror.logol.ru
Package rpm-build-4.11.3-40.el7.x86_64 already installed and latest version
Nothing to do
[vagrant@centos ~]$ sudo yum install -y createrepo
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.yandex.ru
 * epel: fedora-mirror02.rbc.ru
 * extras: dedic.sh
 * updates: mirror.logol.ru
Package createrepo-0.9.9-28.el7.noarch already installed and latest version
Nothing to do
[vagrant@centos ~]$ sudo yum install -y yum-utils
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.yandex.ru
 * epel: fedora-mirror02.rbc.ru
 * extras: dedic.sh
 * updates: mirror.logol.ru
Package yum-utils-1.1.31-52.el7.noarch already installed and latest version
Nothing to do
[vagrant@centos ~]$ exit
exit

Script done on Ср 08 янв 2020 16:00:57
[vagrant@centos ~]$ 


# --------------------------------------------------------
[vagrant@centos ~]$ wget https://nginx.org/packages/centos/7/SRPMS/nginx-1.14.1-1.el7_4.ngx.src.rpm
--2020-01-09 16:53:54--  https://nginx.org/packages/centos/7/SRPMS/nginx-1.14.1-1.el7_4.ngx.src.rpm
Resolving nginx.org (nginx.org)... 95.211.80.227, 62.210.92.35, 2001:1af8:4060:a004:21::e3
Connecting to nginx.org (nginx.org)|95.211.80.227|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1033399 (1009K) [application/x-redhat-package-manager]
Saving to: ‘nginx-1.14.1-1.el7_4.ngx.src.rpm’

100%[======================================>] 1 033 399    232KB/s   in 4,4s   

2020-01-09 16:53:59 (232 KB/s) - ‘nginx-1.14.1-1.el7_4.ngx.src.rpm’ saved [1033399/1033399]

[vagrant@centos ~]$ ls
nginx-1.14.1-1.el7_4.ngx.src.rpm
[vagrant@centos ~]$ rpm -i nginx-1.14.1-1.el7_4.ngx.src.rpm
warning: nginx-1.14.1-1.el7_4.ngx.src.rpm: Header V4 RSA/SHA1 Signature, key ID 7bd9bf62: NOKEY
warning: user builder does not exist - using root
warning: group builder does not exist - using root
warning: user builder does not exist - using root
warning: group builder does not exist - using root
warning: user builder does not exist - using root
warning: group builder does not exist - using root
warning: user builder does not exist - using root
warning: group builder does not exist - using root
warning: user builder does not exist - using root
warning: group builder does not exist - using root
warning: user builder does not exist - using root
warning: group builder does not exist - using root
warning: user builder does not exist - using root
warning: group builder does not exist - using root
warning: user builder does not exist - using root
warning: group builder does not exist - using root
warning: user builder does not exist - using root
warning: group builder does not exist - using root
warning: user builder does not exist - using root
warning: group builder does not exist - using root
warning: user builder does not exist - using root
warning: group builder does not exist - using root
warning: user builder does not exist - using root
warning: group builder does not exist - using root
warning: user builder does not exist - using root
warning: group builder does not exist - using root
warning: user builder does not exist - using root
warning: group builder does not exist - using root
[vagrant@centos ~]$ 
[vagrant@centos ~]$ 
[vagrant@centos ~]$ ls
nginx-1.14.1-1.el7_4.ngx.src.rpm  rpmbuild
[vagrant@centos ~]$ ll rpmbuild
total 4
drwxr-xr-x. 2 vagrant vagrant 4096 янв  9 16:54 SOURCES
drwxr-xr-x. 2 vagrant vagrant   24 янв  9 16:54 SPECS
[vagrant@centos ~]$ mkdir rpmbuild/BUILD
[vagrant@centos ~]$ ll rpmbuild
total 4
drwxrwxr-x. 2 vagrant vagrant    6 янв  9 16:55 BUILD
drwxr-xr-x. 2 vagrant vagrant 4096 янв  9 16:54 SOURCES
drwxr-xr-x. 2 vagrant vagrant   24 янв  9 16:54 SPECS
[vagrant@centos ~]$ mkdir rpmbuild/BUILDROOT
[vagrant@centos ~]$ mkdir rpmbuild/RPMS
[vagrant@centos ~]$ mkdir rpmbuild/SRPMS
[vagrant@centos ~]$ ll rpmbuild
total 4
drwxrwxr-x. 2 vagrant vagrant    6 янв  9 16:55 BUILD
drwxrwxr-x. 2 vagrant vagrant    6 янв  9 16:56 BUILDROOT
drwxrwxr-x. 2 vagrant vagrant    6 янв  9 16:56 RPMS
drwxr-xr-x. 2 vagrant vagrant 4096 янв  9 16:54 SOURCES
drwxr-xr-x. 2 vagrant vagrant   24 янв  9 16:54 SPECS
drwxrwxr-x. 2 vagrant vagrant    6 янв  9 16:56 SRPMS
[vagrant@centos ~]$ 



[vagrant@centos ~]$ wget https://www.openssl.org/source/latest.tar.gz
--2020-01-09 17:33:47--  https://www.openssl.org/source/latest.tar.gz
Resolving www.openssl.org (www.openssl.org)... 104.92.90.148, 2a02:26f0:e2:19b::c1e, 2a02:26f0:e2:190::c1e
Connecting to www.openssl.org (www.openssl.org)|104.92.90.148|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://www.openssl.org/source/openssl-1.1.1d.tar.gz [following]
--2020-01-09 17:33:48--  https://www.openssl.org/source/openssl-1.1.1d.tar.gz
Reusing existing connection to www.openssl.org:443.
HTTP request sent, awaiting response... 200 OK
Length: 8845861 (8,4M) [application/x-gzip]
Saving to: ‘latest.tar.gz’

100%[======================================>] 8 845 861   5,12MB/s   in 1,6s   

2020-01-09 17:33:50 (5,12 MB/s) - ‘latest.tar.gz’ saved [8845861/8845861]

[vagrant@centos ~]$ ls
latest.tar.gz  nginx-1.14.1-1.el7_4.ngx.src.rpm  rpmbuild
[vagrant@centos ~]$ 




[vagrant@centos ~]$ tar -xvf latest.tar.gz
openssl-1.1.1d/
openssl-1.1.1d/ACKNOWLEDGEMENTS
openssl-1.1.1d/AUTHORS
openssl-1.1.1d/CHANGES
...
openssl-1.1.1d/util/process_docs.pl
openssl-1.1.1d/util/shlib_wrap.sh.in
openssl-1.1.1d/util/su-filter.pl
openssl-1.1.1d/util/unlocal_shlib.com.in
[vagrant@centos ~]$ ls




# --------------------------------------------------------
[vagrant@centos ~]$ sudo yum-builddep rpmbuild/SPECS/nginx.spec
Loaded plugins: fastestmirror
Enabling base-source repository
Enabling docker-ce-stable-source repository
Enabling epel-source repository
Enabling extras-source repository
Enabling updates-source repository
Loading mirror speeds from cached hostfile
epel/x86_64/metalink                                     |  25 kB     00:00     
epel-source/x86_64/metalink                              |  24 kB     00:00     
 * base: dedic.sh
 * epel: ftp.lysator.liu.se
 * epel-source: ftp.lysator.liu.se
 * extras: dedic.sh
 * updates: dedic.sh
base                                                     | 3.6 kB     00:00     
base-source                                              | 2.9 kB     00:00     
docker-ce-stable                                         | 3.5 kB     00:00     
docker-ce-stable-source                                  | 3.5 kB     00:00     
epel                                                     | 5.3 kB     00:00     
epel-source                                              | 4.1 kB     00:00     
extras                                                   | 2.9 kB     00:00     
extras-source                                            | 2.9 kB     00:00     
updates                                                  | 2.9 kB     00:00     
updates-source                                           | 2.9 kB     00:00     
(1/4): epel-source/x86_64/updateinfo                       | 1.0 MB   00:01     
(2/4): epel/x86_64/updateinfo                              | 1.0 MB   00:01     
(3/4): epel-source/x86_64/primary_db                       | 2.4 MB   00:02     
(4/4): epel/x86_64/primary_db                              | 6.9 MB   00:05     
Checking for new repos for mirrors
Getting requirements for rpmbuild/SPECS/nginx.spec
 --> Already installed : redhat-lsb-core-4.1-27.el7.centos.1.x86_64
 --> Already installed : systemd-219-62.el7_6.6.x86_64
 --> Already installed : 1:openssl-devel-1.0.2k-19.el7.x86_64
 --> Already installed : zlib-devel-1.2.7-18.el7.x86_64
 --> Already installed : pcre-devel-8.32-17.el7.x86_64
No uninstalled build requires
[vagrant@centos ~]$ 

# --------------------------------------------------------
[vagrant@centos ~]$ vi rpmbuild/SPECS/nginx.spec

./configure %{BASE_CONFIGURE_ARGS} \
    --with-cc-opt="%{WITH_CC_OPT}" \
    --with-ld-opt="%{WITH_LD_OPT}" \
    --with-openssl=/home/vagrant/openssl-1.1.1d

# --------------------------------------------------------

[vagrant@centos ~]$ rpmbuild -bb rpmbuild/SPECS/nginx.spec
...
Executing(%clean): /bin/sh -e /var/tmp/rpm-tmp.JAg1Bm
+ umask 022
+ cd /home/vagrant/rpmbuild/BUILD
+ cd nginx-1.14.1
+ /usr/bin/rm -rf /home/vagrant/rpmbuild/BUILDROOT/nginx-1.14.1-1.el7_4.ngx.x86_64
+ exit 0


[vagrant@centos ~]$ ll rpmbuild/RPMS/x86_64/
total 4736
-rw-rw-r--. 1 vagrant vagrant 2315012 янв  9 18:10 nginx-1.14.1-1.el7_4.ngx.x86_64.rpm
-rw-rw-r--. 1 vagrant vagrant 2529284 янв  9 18:10 nginx-debuginfo-1.14.1-1.el7_4.ngx.x86_64.rpm
[vagrant@centos ~]$ 

# --------------------------------------------------------
# --------------------------------------------------------
# --------------------------------------------------------
# --------------------------------------------------------
# --------------------------------------------------------

