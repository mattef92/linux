# MySQL
## Slave Restart
```
  STOP SLAVE;
  FLUSH TABLES;

  systemctl restart mysql
```

## Create a list of MySQL Processes to kill depending on the time running
```
  select concat('KILL ',id,';') from information_schema.processlist where state = 'checking permissions' and time > 1000 into outfile '/tmp/a.txt';
```

## MySQL Dump
```
  mysqldump db_name [tbl_name] --events --single-transaction -q --routines --triggers --add-drop-table --default-character-set=utf8
```

## Analyse Binlogs
```
  # Number of used tables
  mysqlbinlog --no-defaults $BIN_FILE | grep Table_map | grep $DB | awk '{print $11}' | sort -n | uniq -c

  # Logs seperated by command
  mysqlbinlog --no-defaults $BIN_FILE -v | sed "s/### //" | grep -i -e "^update" -e "^insert" -e "^delete" -e "^replace" -e "^alter" | sed 's/$DB\.//' | cut -c1-100 | tr '[A-Z]' '[a-z]' | sed -e "s/\t/ /g;s/\`//g;s/(.*$//;s/ set .*$//;s/ as .*$//" | sed -e "s/ where .*$//" | sort | uniq -c | sort -nr | head -50
```

# Percona Toolkit
## pt-heartbeat
```
  pt-heartbeat -D percona --monitor -h $HOSTNAME
```

## pt-duplicate-keys
```
  pt-duplicate-keys -d $DATABASE
```

## pt-table-sync
```
  pt-table-sync
  pt-table-sync --execute --sync-to-master slave1
```
