# MySQL Installation
## Adding the MySQL Yum Repository
### Download `platform-and-version-specific-package-name.rpm`
Yum Repository download link is [here](http://dev.mysql.com/downloads/repo/yum/)
### Install
```sh
$sudo rpm -Uvh platform-and-version-specific-package-name.rpm
```

Example

```sh
$ rpm -Uvh mysql57-community-release-el6-11.noarch.rpm
warning: mysql57-community-release-el6-11.noarch.rpm: Header V3 DSA/SHA1 Signature, key ID 5072e1f5: NOKEY
Preparing...                ########################################### [100%]
   1:mysql57-community-relea########################################### [100%]
$
```

## Selecting a release Series
### Retrieve `mysql` packages

```sh
$ yum repolist all | grep mysql
```

Result

```sh
$ yum repolist all | grep mysql
mysql-cluster-7.5-community        MySQL Cluster 7.5 Community   disabled
mysql-cluster-7.5-community-source MySQL Cluster 7.5 Community - disabled
mysql-cluster-7.6-community        MySQL Cluster 7.6 Community   disabled
mysql-cluster-7.6-community-source MySQL Cluster 7.6 Community - disabled
mysql-connectors-community         MySQL Connectors Community    enabled:     36
mysql-connectors-community-source  MySQL Connectors Community -  disabled
mysql-tools-community              MySQL Tools Community         enabled:     47
mysql-tools-community-source       MySQL Tools Community - Sourc disabled
mysql-tools-preview                MySQL Tools Preview           disabled
mysql-tools-preview-source         MySQL Tools Preview - Source  disabled
mysql55-community                  MySQL 5.5 Community Server    disabled
mysql55-community-source           MySQL 5.5 Community Server -  disabled
mysql56-community                  MySQL 5.6 Community Server    disabled
mysql56-community-source           MySQL 5.6 Community Server -  disabled
mysql57-community                  MySQL 5.7 Community Server    enabled:    183
mysql57-community-source           MySQL 5.7 Community Server -  disabled
mysql80-community                  MySQL 8.0 Community Server    disabled
mysql80-community-source           MySQL 8.0 Community Server -  disabled
```

### Enable & Disable packages

Enable 5.6 series and disable 5.7 series
```sh
$ sudo yum-config-manager --disable mysql57-community
$ sudo yum-config-manager --enable mysql56-community
```

Result
```sh
$ yum-config-manager --disable mysql57-community
Loaded plugins: fastestmirror, refresh-packagekit
============================================================================== repo: mysql57-community ==============================================================================
[mysql57-community]
bandwidth = 0
base_persistdir = /var/lib/yum/repos/x86_64/6
baseurl = http://repo.mysql.com/yum/mysql-5.7-community/el/6/x86_64/
cache = 0
cachedir = /var/cache/yum/x86_64/6/mysql57-community
cost = 1000
enabled = 0
enablegroups = True
exclude = 
failovermethod = priority
ftp_disable_epsv = False
gpgcadir = /var/lib/yum/repos/x86_64/6/mysql57-community/gpgcadir
gpgcakey = 
gpgcheck = True
gpgdir = /var/lib/yum/repos/x86_64/6/mysql57-community/gpgdir
gpgkey = file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
hdrdir = /var/cache/yum/x86_64/6/mysql57-community/headers
http_caching = all
includepkgs = 
keepalive = True
mdpolicy = group:primary
mediaid = 
metadata_expire = 21600
metalink = 
mirrorlist = 
mirrorlist_expire = 86400
name = MySQL 5.7 Community Server
old_base_cache_dir = 
password = 
persistdir = /var/lib/yum/repos/x86_64/6/mysql57-community
pkgdir = /var/cache/yum/x86_64/6/mysql57-community/packages
proxy = False
proxy_dict = 
proxy_password = 
proxy_username = 
repo_gpgcheck = False
retries = 10
skip_if_unavailable = False
ssl_check_cert_permissions = True
sslcacert = 
sslclientcert = 
sslclientkey = 
sslverify = True
throttle = 0
timeout = 30.0
username = 

$ yum-config-manager --enable mysql56-community
Loaded plugins: fastestmirror, refresh-packagekit
============================================================================== repo: mysql56-community ==============================================================================
[mysql56-community]
bandwidth = 0
base_persistdir = /var/lib/yum/repos/x86_64/6
baseurl = http://repo.mysql.com/yum/mysql-5.6-community/el/6/x86_64/
cache = 0
cachedir = /var/cache/yum/x86_64/6/mysql56-community
cost = 1000
enabled = 1
enablegroups = True
exclude = 
failovermethod = priority
ftp_disable_epsv = False
gpgcadir = /var/lib/yum/repos/x86_64/6/mysql56-community/gpgcadir
gpgcakey = 
gpgcheck = True
gpgdir = /var/lib/yum/repos/x86_64/6/mysql56-community/gpgdir
gpgkey = file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
hdrdir = /var/cache/yum/x86_64/6/mysql56-community/headers
http_caching = all
includepkgs = 
keepalive = True
mdpolicy = group:primary
mediaid = 
metadata_expire = 21600
metalink = 
mirrorlist = 
mirrorlist_expire = 86400
name = MySQL 5.6 Community Server
old_base_cache_dir = 
password = 
persistdir = /var/lib/yum/repos/x86_64/6/mysql56-community
pkgdir = /var/cache/yum/x86_64/6/mysql56-community/packages
proxy = False
proxy_dict = 
proxy_password = 
proxy_username = 
repo_gpgcheck = False
retries = 10
skip_if_unavailable = False
ssl_check_cert_permissions = True
sslcacert = 
sslclientcert = 
sslclientkey = 
sslverify = True
throttle = 0
timeout = 30.0
username = 
$
```

## Installing MySQL

```sh
$ yum install mysql-community-server
```

## Starting MySQL Server
```sh
$ service mysqld start
```

Status
```sh
$ service mysqld status
```
