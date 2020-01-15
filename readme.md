# Установка пакетов

1. Доустановим необходимые для работы пакеты  (redhat-lsb-core, wget, rpmdevtools, rpm-build, createrepo, yum-utils)
	```bash	
	[vagrant@centos ~]$ sudo su  
	[root@centos vagrant]# yum install -y redhat-lsb-core  
	...
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
	```
2. Как оказалось остальные пакеты уже предустановлены при развертывании вагранта  
	```bash	
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
	```
3. Не мудрствуя лукаво будем собирать пакет NGINX с поддержкой openssl, предложенный заданием. Для этого скачаем SRPM пакет NGINX  
	```bash	
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
	```

4. Действия ниже нужно выполнять от обычного пользователя, не от root, это очень важный момент! Создадим командой rpmdev-setuptree каталог rpmbuild со следующими подкаталогами:  
	```bash	
	+ rpmbuild
		-BUILD  
		-RPMS  
		-SOURCES  
		-SPECS  
		-SRPMS
	
	[vagrant@centos ~]$ rpmdev-setuptree
	[vagrant@centos ~]$ ll rpmbuild
	total 0
	drwxrwxr-x. 2 vagrant vagrant 6 янв 15 15:43 BUILD
	drwxrwxr-x. 2 vagrant vagrant 6 янв 15 15:43 RPMS
	drwxrwxr-x. 2 vagrant vagrant 6 янв 15 15:43 SOURCES
	drwxrwxr-x. 2 vagrant vagrant 6 янв 15 15:43 SPECS
	drwxrwxr-x. 2 vagrant vagrant 6 янв 15 15:43 SRPMS
	```

5. Скачаем и разархивируем последние исходники для openssl, которые потребуеются нам при сборке  
	```bash	
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
	latest.tar.gz  nginx-1.14.1-1.el7_4.ngx.src.rpm  openssl-1.1.1d  rpmbuild
	```
6. Установим необходимые зависимости, чтобы в процессе сборки RPM пакета не было ошибок  
	```bash	
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
	```
7. Изменим nginx.spec, добавив в него опцию поддержки openssl с указанием полного пути до каталога  
	```bash	
	[vagrant@centos ~]$ vi rpmbuild/SPECS/nginx.spec

	./configure %{BASE_CONFIGURE_ARGS} \
	    --with-cc-opt="%{WITH_CC_OPT}" \
	    --with-ld-opt="%{WITH_LD_OPT}" \
	    --with-openssl=/home/vagrant/openssl-1.1.1d
	```
8. Теперь запустим сборку RPM пакета, после чего убедимся, что пакеты создались  
	```bash	
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
	```

9. Теперь установим созданный пакет (Примечание - оказалось, что при развертывании вагранта автоматически устанавливался nginx, поэтому предварительно пришлось его удалить)  
	```bash	
	[vagrant@centos ~]$ sudo yum localinstall -y rpmbuild/RPMS/x86_64/nginx-1.14.1-1.el7_4.ngx.x86_64.rpm
	Loaded plugins: fastestmirror
	Examining rpmbuild/RPMS/x86_64/nginx-1.14.1-1.el7_4.ngx.x86_64.rpm: 1:nginx-1.14.1-1.el7_4.ngx.x86_64
	Marking rpmbuild/RPMS/x86_64/nginx-1.14.1-1.el7_4.ngx.x86_64.rpm to be installed
	Resolving Dependencies
	--> Running transaction check
	---> Package nginx.x86_64 1:1.14.1-1.el7_4.ngx will be installed
	--> Finished Dependency Resolution

	Dependencies Resolved

	================================================================================
	 Package
		Arch    Version                 Repository                         Size
	================================================================================
	Installing:
	 nginx  x86_64  1:1.14.1-1.el7_4.ngx    /nginx-1.14.1-1.el7_4.ngx.x86_64  8.8 M

	Transaction Summary
	================================================================================
	Install  1 Package

	Total size: 8.8 M
	Installed size: 8.8 M
	Downloading packages:
	Running transaction check
	Running transaction test
	Transaction test succeeded
	Running transaction
	  Installing : 1:nginx-1.14.1-1.el7_4.ngx.x86_64                            1/1 
	----------------------------------------------------------------------

	Thanks for using nginx!

	Please find the official documentation for nginx here:
	* http://nginx.org/en/docs/

	Please subscribe to nginx-announce mailing list to get
	the most important news about nginx:
	* http://nginx.org/en/support.html

	Commercial subscriptions for nginx are available on:
	* http://nginx.com/products/

	----------------------------------------------------------------------
	  Verifying  : 1:nginx-1.14.1-1.el7_4.ngx.x86_64                            1/1 

	Installed:
	  nginx.x86_64 1:1.14.1-1.el7_4.ngx                                             

	Complete!
	```
10. Запустим nginx и проверим, что он работает
	```bash	
	[vagrant@centos ~]$ sudo systemctl start nginx
	[vagrant@centos ~]$ sudo systemctl status nginx
	● nginx.service - The nginx HTTP and reverse proxy server
	   Loaded: loaded (/usr/lib/systemd/system/nginx.service; disabled; vendor preset: disabled)
	   Active: active (running) since Сб 2020-01-11 16:42:53 UTC; 10s ago
	  Process: 29493 ExecStart=/usr/sbin/nginx (code=exited, status=0/SUCCESS)
	  Process: 29491 ExecStartPre=/usr/sbin/nginx -t (code=exited, status=0/SUCCESS)
	  Process: 29489 ExecStartPre=/usr/bin/rm -f /run/nginx.pid (code=exited, status=0/SUCCESS)
	 Main PID: 29495 (nginx)
	   CGroup: /system.slice/nginx.service
		   ├─29495 nginx: master process /usr/sbin/nginx
		   └─29496 nginx: worker process

	янв 11 16:42:53 centos systemd[1]: Starting The nginx HTTP and reverse p.....
	янв 11 16:42:53 centos nginx[29491]: nginx: the configuration file /etc/n...k
	янв 11 16:42:53 centos nginx[29491]: nginx: configuration file /etc/nginx...l
	янв 11 16:42:53 centos systemd[1]: Failed to read PID from file /run/ngi...nt
	янв 11 16:42:53 centos systemd[1]: Started The nginx HTTP and reverse pr...r.
	Hint: Some lines were ellipsized, use -l to show in full.
	```

# --------------------------------------------------------
[vagrant@centos ~]$ ls /usr/share/nginx/html
404.html  en-US  img         nginx-logo.png
50x.html  icons  index.html  poweredby.png
[vagrant@centos ~]$ mkdir /usr/share/nginx/html/repo
mkdir: cannot create directory ‘/usr/share/nginx/html/repo’: Permission denied
[vagrant@centos ~]$ sudo mkdir /usr/share/nginx/html/repo
[vagrant@centos ~]$ ls /usr/share/nginx/html
404.html  en-US  img         nginx-logo.png  repo
50x.html  icons  index.html  poweredby.png
[vagrant@centos ~]$ 
[vagrant@centos ~]$ 
[vagrant@centos ~]$ cp rpmbuild/RPMS/x86_64/nginx-1.14.1-1.el7_4.ngx.x86_64.rpm /usr/share/nginx/html/repo/
cp: cannot create regular file ‘/usr/share/nginx/html/repo/nginx-1.14.1-1.el7_4.ngx.x86_64.rpm’: Permission denied
[vagrant@centos ~]$ sudo cp rpmbuild/RPMS/x86_64/nginx-1.14.1-1.el7_4.ngx.x86_64.rpm /usr/share/nginx/html/repo/
[vagrant@centos ~]$ sudo wget http://www.percona.com/downloads/percona-release/redhat/0.1-6/percona-release-0.1-6.noarch.rpm -O /usr/share/nginx/html/repo/percona-release-0.1-6.noarch.rpm
--2020-01-11 16:45:16--  http://www.percona.com/downloads/percona-release/redhat/0.1-6/percona-release-0.1-6.noarch.rpm
Resolving www.percona.com (www.percona.com)... 74.121.199.234
Connecting to www.percona.com (www.percona.com)|74.121.199.234|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://www.percona.com/downloads/percona-release/redhat/0.1-6/percona-release-0.1-6.noarch.rpm [following]
--2020-01-11 16:45:17--  https://www.percona.com/downloads/percona-release/redhat/0.1-6/percona-release-0.1-6.noarch.rpm
Connecting to www.percona.com (www.percona.com)|74.121.199.234|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14520 (14K) [application/x-redhat-package-manager]
Saving to: ‘/usr/share/nginx/html/repo/percona-release-0.1-6.noarch.rpm’

100%[======================================>] 14 520      --.-K/s   in 0,1s    

2020-01-11 16:45:18 (97,7 KB/s) - ‘/usr/share/nginx/html/repo/percona-release-0.1-6.noarch.rpm’ saved [14520/14520]

[vagrant@centos ~]$ ls /usr/share/nginx/html/repo
nginx-1.14.1-1.el7_4.ngx.x86_64.rpm  percona-release-0.1-6.noarch.rpm
[vagrant@centos ~]$ 

# --------------------------------------------------------
[vagrant@centos ~]$ sudo createrepo /usr/share/nginx/html/repo/
Spawning worker 0 with 2 pkgs
Workers Finished
Saving Primary metadata
Saving file lists metadata
Saving other metadata
Generating sqlite DBs
Sqlite DBs complete
[vagrant@centos ~]$ 
# --------------------------------------------------------

[vagrant@centos ~]$ curl -a http://localhost/repo/
<html>
<head><title>403 Forbidden</title></head>
<body>
<center><h1>403 Forbidden</h1></center>
<hr><center>nginx/1.16.1</center>
</body>
</html>

[vagrant@centos ~]$ sudo vi /etc/nginx/conf.d/default.conf 
[vagrant@centos ~]$ cat /etc/nginx/conf.d/default.conf 
server {
    listen       80;
    server_name  localhost;

    #charset koi8-r;
    #access_log  /var/log/nginx/host.access.log  main;

    location / {
        root   /usr/share/nginx/html;
        index  index.html index.htm;
	autoindex on;
    }

    #error_page  404              /404.html;

    # redirect server error pages to the static page /50x.html
    #
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }

    # proxy the PHP scripts to Apache listening on 127.0.0.1:80
    #
    #location ~ \.php$ {
    #    proxy_pass   http://127.0.0.1;
    #}

    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    #location ~ \.php$ {
    #    root           html;
    #    fastcgi_pass   127.0.0.1:9000;
    #    fastcgi_index  index.php;
    #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
    #    include        fastcgi_params;
    #}

    # deny access to .htaccess files, if Apache's document root
    # concurs with nginx's one
    #
    #location ~ /\.ht {
    #    deny  all;
    #}
}

[vagrant@centos ~]$ sudo nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful


[vagrant@centos ~]$ sudo nginx -s reload

[vagrant@centos ~]$ curl -a http://localhost/repo/
<html>
<head><title>Index of /repo/</title></head>
<body>
<h1>Index of /repo/</h1><hr><pre><a href="../">../</a>
<a href="repodata/">repodata/</a>                                          11-Jan-2020 16:46                   -
<a href="nginx-1.14.1-1.el7_4.ngx.x86_64.rpm">nginx-1.14.1-1.el7_4.ngx.x86_64.rpm</a>                11-Jan-2020 16:44             3598432
<a href="percona-release-0.1-6.noarch.rpm">percona-release-0.1-6.noarch.rpm</a>                   13-Jun-2018 06:34               14520
</pre><hr></body>
</html>

# --------------------------------------------------------
[vagrant@centos ~]$ sudo touch /etc/yum.repos.d/otus.repo
[vagrant@centos ~]$ sudo vi /etc/yum.repos.d/otus.repo
[vagrant@centos ~]$ cat /etc/yum.repos.d/otus.repo
[otus]
name=otus-linux
baseurl=http://localhost/repo
gpgcheck=0
enabled=1

[vagrant@centos ~]$ yum repolist enabled | grep otus
otus                     otus-linux                                            2

[vagrant@centos ~]$ yum list | grep otus
percona-release.noarch                   0.1-6                         otus     

# --------------------------------------------------------
# --------------------------------------------------------
# --------------------------------------------------------
# --------------------------------------------------------

