---
layout: default
title: sh
parent: Cheatsheet
nav_order: 2
---

# sh

## [Find duplicate lines in a file and count how many time each line was duplicated](https://stackoverflow.com/questions/6712437/find-duplicate-lines-in-a-file-and-count-how-many-time-each-line-was-duplicated)

```bash
sort files.list | uniq -c
```

## [Count number of files within a directory](https://stackoverflow.com/questions/20895290/count-number-of-files-within-a-directory-in-linux)

```bash
ls ./images/*.jpg | wc -l
# or
find ./images -name "*.jpg" -type f | wc -l
```

## [Disk Space](https://stackoverflow.com/questions/16054112/disk-space-in-linux-server)

```bash
df -h
```

## [GPU memory usage (CUDA)](https://unix.stackexchange.com/questions/38560/gpu-usage-monitoring-cuda)

```bash
watch -n 0.5 nvidia-smi
```

## [Invoke function whose name is stored in a variable](https://stackoverflow.com/questions/33387263/invoke-function-whose-name-is-stored-in-a-variable-in-bash)

```bash
a=ls
$a
```

## [How to prevent command from reporting](https://stackoverflow.com/questions/10247472/how-to-prevent-rm-from-reporting-that-a-file-was-not-found)

```bash
rm file.txt 2> /dev/null
```

## [How to count lines in a document](https://stackoverflow.com/questions/3137094/how-to-count-lines-in-a-document)

```bash
wc -l < file.txt
```

## [How to rename the downloaded file with wget](https://stackoverflow.com/questions/14306382/how-to-rename-the-downloaded-file-with-wget)

```bash
wget http://www.kernel.org/pub/linux/kernel/README -O foo
```

## [Progress indicator for git clone](https://stackoverflow.com/questions/4640020/progress-indicator-for-git-clone)

```bash
# in cloned folder
watch du -ksh
```

## [Looping over arrays, printing both index and value](https://stackoverflow.com/questions/6723426/looping-over-arrays-printing-both-index-and-value)

```bash
for i in "${!foo[@]}"; do 
  printf "%s\t%s\n" "$i" "${foo[$i]}"
done
```

## [How to add arithmetic variables in a script](https://unix.stackexchange.com/questions/55069/how-to-add-arithmetic-variables-in-a-script)

```bash
a=`expr "$a" + "$num"`

a=$(($a+$num))
```

## [How to count the length of an array](https://unix.stackexchange.com/questions/193039/how-to-count-the-length-of-an-array-defined-in-bash)

```bash
length=${#array[@]}
```

## [Check if passed argument is file or directory](https://stackoverflow.com/questions/4665051/check-if-passed-argument-is-file-or-directory-in-bash)

```bash
if [[ -d $PASSED ]]; then
    echo "$PASSED is a directory"
elif [[ -f $PASSED ]]; then
    echo "$PASSED is a file"
else
    echo "$PASSED is not valid"
    exit 1
fi
```

## [How to make "if not true condition"](https://stackoverflow.com/questions/10552711/how-to-make-if-not-true-condition)

```bash
if [[ !  $(cat /etc/passwd | grep "sysa") ]]; then
  echo " something"
  exit 2
fi
```

## [How to check if an environment variable exists and get its value](https://stackoverflow.com/questions/39296472/how-to-check-if-an-environment-variable-exists-and-get-its-value)

```bash
if [[ -z "${DEPLOY_ENV}" ]]; then
  MY_SCRIPT_VARIABLE="Some default value because DEPLOY_ENV is undefined"
else
  MY_SCRIPT_VARIABLE="${DEPLOY_ENV}"
fi

# or

var=${DEPLOY_ENV:-default_value}
```

## [How do I parse command line arguments in Bash?](https://stackoverflow.com/questions/192249/how-do-i-parse-command-line-arguments-in-bash)

```bash
POSITIONAL_ARGS=()

while [[ $# -gt 0 ]]; do
  case $1 in
    -e|--extension)
      EXTENSION="$2"
      shift # past argument
      shift # past value
      ;;
    -s|--searchpath)
      SEARCHPATH="$2"
      shift # past argument
      shift # past value
      ;;
    --default)
      DEFAULT=YES
      shift # past argument
      ;;
    -*|--*)
      echo "Unknown option $1"
      exit 1
      ;;
    *)
      POSITIONAL_ARGS+=("$1") # save positional arg
      shift # past argument
      ;;
  esac
done

set -- "${POSITIONAL_ARGS[@]}" # restore positional parameters

echo "FILE EXTENSION  = ${EXTENSION}"
echo "SEARCH PATH     = ${SEARCHPATH}"
echo "DEFAULT         = ${DEFAULT}"
echo "Number files in SEARCH PATH with EXTENSION:" $(ls -1 "${SEARCHPATH}"/*."${EXTENSION}" | wc -l)

if [[ -n $1 ]]; then
    echo "Last line of file specified as non-opt/last argument:"
    tail -1 "$1"
fi
```

## [How to trim whitespace from a Bash variable](https://stackoverflow.com/questions/369758/how-to-trim-whitespace-from-a-bash-variable)

```bash
echo -e "   lol  "
```

## [renaming files to creation time](https://stackoverflow.com/questions/25152995/linux-shell-renaming-files-to-creation-time)

```bash
for f in *.jpg
do
    mv -n "$f" "$(date -r "$f" +"%Y%m%d_%H%M%S").jpg"
done
```

## [How do I remount a filesystem as read/write?](https://askubuntu.com/questions/175739/how-do-i-remount-a-filesystem-as-read-write)

```bash
mount -o remount, rw /
```