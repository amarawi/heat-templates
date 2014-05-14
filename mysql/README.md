## Backup/restore a MySQL database

Here are just two simple methods gathered from Internet. The scripts are just for demonstrating the methods. 

### Use [mysqlhotcopy](http://dev.mysql.com/doc/refman/5.5/en/mysqlhotcopy.html)

This backup is done on file system level. mysqlhotcopy works only for backing up MyISAM and ARCHIVE tables. It runs on Unix. 

```shell
# to backup
mysqlhotcopy db-to-be-backedup /dir/to/save
tar -zcvf db_backed_up.tar.gz /dir/to/save

# to restore:
tar -xzvf db_backed_up.tar.gz -C /some_working_dir
# check, if OK, copy to MysQL's database location. Reference distro and version for exact location.
service mysqld stop
sudo -u mysql cp -rp /some_working_dir/restored_db /var/lib/mysql/restored_db
service mysqld start
```

### Use [mysqldump](http://dev.mysql.com/doc/refman/5.5/en/mysqldump.html)

This backup method use SQL statements to backup and restore.

```shell
# to backup 
mysqldump db_name | gzip > db_name.gz

# to restore:
mysqladmin create -uroot -ppass db_name
gunzip < db_name.gz | mysql -uroot -ppass db_name
```

### Manage database through web interface

[mysql_phpMyAdmin.yaml](mysql_phpMyAdmin.yaml) creates a MySQL database server with root account's password set when a VM is created.
The configuration of phpMyAdmin is very simple and with convenience in mind. It allows the access from permitted IP or range. It uses
root and password to connect the database server. `['auth_type'] = 'config'`. Read the [documentation](http://docs.phpmyadmin.net/en/latest/index.html) for detail.
