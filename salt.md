# Salt

## Run a local salt Test (pull)
Pull all salt changes from local pillar files
```
  salt-call state.highstate test=True
```

## Push state changes

Examples for pushing changes from the master to minions

```
  salt [-C] '$TARGET' state.highstate [test=true] [--state-verbose=false]
  salt [-C] '$TARGET' state.sls $STATE [test=true] [--state-verbose=false]
```


## Run modules from Salt Master on Minions (push)

Example for installing package upgrades on a server:

```
  salt -C '$TARGET' pkg.list_upgrades dist_upgrade=false
  salt -C '$TARGET' pkg.upgrade
```
