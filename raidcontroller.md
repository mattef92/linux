# MegaCLI Commands
## Controller Status and Configuration
```
  megacli -AdpAllInfo -aAll
```

## Status of a logical drive
```
  megacli -LDInfo -L0 -a0
```

## Output of the hard drive information on a controller
```
  megacli -PDList -a0
```

# Storcli Commands

## Informationen zum Controller und Konfiguration
```
  storcli /c0 show all
```

## Informationen zu den vorhandenen Festplatten und deren Status (IDs,...)
```
  storcli /c0 /eall /sall show all
```
