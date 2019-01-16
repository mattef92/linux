# MySQL
## Slave Restart

  STOP SLAVE;
  FLUSH TABLES;

  /etc/init.d/mysql restart
  systemctl restart mysql

## Create a list of MySQL Processes to kill
  select concat('KILL ',id,';') from information_schema.processlist where state = 'checking permissions' and time > 1000 into outfile '/tmp/a.txt';

## Create a list of MySQL Processes to kill
  select concat('KILL ',id,';') from information_schema.processlist where state = 'checking permissions' and time > 1000 into outfile '/tmp/a.txt';

## MySQL Dump
  mysqldump db_name [tbl_name] --events --single-transaction -q --routines --triggers --add-drop-table --default-character-set=utf8

## Analyse Binlogs
  mysqlbinlog --no-defaults  mysql-bin.031848 | grep Table_map | grep $DATABASE | awk '{print $11}' | sort -n | uniq -c


# Percona Toolkit
## pt-heartbeat
  pt-heartbeat -D percona --monitor -h $HOSTNAME

## pt-duplicate-keys
  pt-duplicate-keys -d $DATABASE

## pt-table-sync
  pt-table-sync
  pt-table-sync --execute --sync-to-master slave1
