# Run a local salt Test
  salt-call state.highstate test=True

# Run upgrades from Salt Master on Minions
  salt -C 'pillar.grain' pkg.list_upgrades dist_upgrade=false
  salt -C 'pillar.grain' pkg.upgrade


