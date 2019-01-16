# Bash

## Possibility to read in of CLI options

```
POSITIONAL=()
while [[ $# -gt 0 ]]
do
  key="$1"

  case $key in
      -v1|--var1)
      VAR1="$2"
      shift # past argument
      shift # past value
      ;;
      -v2|--var2)
      VAR2="$2"
      shift
      shift
      ;;
      *)
      POSITIONAL+=("$1") # save it in an array for later
      shift # past argument
      ;;
  esac
done
set -- "${POSITIONAL[@]}" # restore positional parameters
```
