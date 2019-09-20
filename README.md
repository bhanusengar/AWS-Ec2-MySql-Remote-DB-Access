# AWS-EC2-MySql-Remote-DB-Access
Access remote db (MySql) hosted over AWS EC2


## Getting Started

```
1.Make an entry in the aws security group to allow remote access 
 1.1 EC2 Instance
 1.2 Edit inbound rule
 1.3 Add new rule
 1.4 Choose MySQL/Aurora and source to Anywhere
```
```
2.Login to your putty as root user
```
```
3.Add either set it to 0.0.0.0, or to be more secure add your IP address to your /etc/mysql/mysql.conf.d/mysqld.cnf file.
bind-address		= 127.0.0.1
bind-address    = 0.0.0.0 or your_public_ip
```
```
4.Login to mysql of your server
```
```
5.create dbuser and dbpassword for remote access

CREATE USER 'remoteuser'@'localhost' IDENTIFIED BY 'remotePassword';
CREATE USER 'remoteuser'@'%' IDENTIFIED BY 'remotePassword';

GRANT ALL ON *.* TO 'remoteuser'@'localhost';
GRANT ALL ON *.* TO 'remoteuser'@'%';
```
```
6.Now try to access mysql
DB_CONNECTION=mysql
DB_HOST=YOUR_EC2_IP
DB_PORT=3306
DB_DATABASE=DB_NAME
DB_USERNAME=remoteuser
DB_PASSWORD=remotePassword
```

## Authors

* **Bhanu Pratap Singh** - *Initial work* - [Usefull resource](https://github.com/bpss2010)
