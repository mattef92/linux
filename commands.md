# Code Samples

# MySQL Slave Restart
Mysql Restart on Slave

STOP SLAVE;
FLUSH TABLES;

/etc/init.d/mysql restart


# Check if deletes files after update are still used
lsof | awk '$5 == "DEL" { print }'


# Run a local salt Test
salt-call state.highstate test=True

# Run upgrades from Salt Master on Minions 
salt -C 'pillar.grain' pkg.list_upgrades dist_upgrade=false
salt -C 'pillar.grain' pkg.upgrade


# Create a list of MySQL Processes to kill
select concat('KILL ',id,';') from information_schema.processlist where state = 'checking permissions' and time > 1000 into outfile '/tmp/a.txt';


# MegaCLI Commands 
# Controller Status and Configuration
megacli -AdpAllInfo -aAll
# Status of a logical drive
megacli -LDInfo -L0 -a0
# Output of the hard drive information on a controller
megacli -PDList -a0


# Usage Percona Toolkit commands
pt-heartbeat -D percona --monitor -h $HOSTNAME
pt-duplicate-keys -d $DATABASE 

pt-table-sync
pt-table-sync --execute --sync-to-master slave1


# TCP Connections sorted by state
netstat -nat | awk '{print $6}' | sort | uniq -c | sort -n


# Sample of MySQL Dump Usage
mysqldump db_name [tbl_name] --events --single-transaction -q --routines --triggers --add-drop-table --default-character-set=utf8 


# Number of used Tables in a binlog:
mysqlbinlog --no-defaults  mysql-bin.031848 | grep Table_map | grep $DATABASE | awk '{print $11}' | sort -n | uniq -c


# Swap usage per process
for file in /proc/*/status ; do awk '/VmSwap|Name/{printf $2 " " $3}END{ print ""}' $file; done | sort -k 2 -n -r | less

# Delete lots of files
perl -e 'for(<*>){((stat)[9]<(unlink))}'