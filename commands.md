# Code Samples

## Basics
```
# Where is the file belonging to this command
whereis $CMD
# Short description of the command
whatis $CMD
# Search command by description
apropos $DESC
```

## TCP Connections sorted by state
```
  netstat -nat | awk '{print $6}' | sort | uniq -c | sort -n
```

## Swap usage per process
```
  for file in /proc/*/status ; do awk '/VmSwap|Name/{printf $2 " " $3}END{ print ""}' $file; done | sort -k 2 -n -r | less
```

## Delete lots of files
```
  perl -e 'for(<*>){((stat)[9]<(unlink))}'
```

## Get rid of failed apt-get install process

```
  dpkg --get-selections > install_list
  # -> adjust the package from install to deinstall or remove it completely out of the list
  dpkg --clear-selections
  dpkg --set-selections < install_list
  apt-get -u dselect-upgrade
```

## Full unattended upgrade via apt
```
  apt update && apt -o Dpkg::Options::="--force-confdef" -o Dpkg::Options::="--force-confold" full-upgrade
```

## NFT show ruleset
```
  nft list ruleset
```

## Get information about a ssl certificate
```
  # Hash value of the certificate
  openssl x509 -in $CERT -noout -hash
  # Fingerprint of certificate
  openssl x509 -in $CERT  -noout  -fingerprint
  # All information about the certificate
  openssl x509 -in $CERT -issuer -noout -subject -dates -text
```
