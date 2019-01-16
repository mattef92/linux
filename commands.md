# Code Samples

# TCP Connections sorted by state
  netstat -nat | awk '{print $6}' | sort | uniq -c | sort -n

# Swap usage per process
  for file in /proc/*/status ; do awk '/VmSwap|Name/{printf $2 " " $3}END{ print ""}' $file; done | sort -k 2 -n -r | less

# Delete lots of files
  perl -e 'for(<*>){((stat)[9]<(unlink))}'

# Get rid of failed apt-get install process

  dpkg --get-selections > install_list
  -> adjust the package from install to deinstall or remove it completely out of the list
  dpkg --clear-selections
  dpkg --set-selections < install_list
  apt-get -u dselect-upgrade
