# Linux

```
[Ctrl] + [a] => move to beginning
[Ctrl] + [l] => clear terminal
```

## Commands

### General

```Bash
# Search
find /usr/share/doc -name '*.pdf'

# Error output Redirect
ls /etcw 2> err

# Ignore
ls /etcw 2> /dev/null

# STDERR AND STDOUT
ls /etcw &> err.txt

# STDIN
mail -s "ddd" tux < diskfree

# piping
ls | wc -l
head -n1 /etc/passwd
cut -f7 -d: /etc/passwd | sort | unique

# named pipes
ls -l /dev/sda

# last argument
ls -l !$

# tee - send data to files and stdin like broadcast
ls | tee f89
```

### File management

```Bash
# current folder
pwd

# change path
cd ..

# copy file
cp source dest

# create folder
mkdir -p directory_name

# create link
ln source link

# symbolic link seperate file which is pointing through
ln -s source link

# get top
head -n 1 f1

# get bottom
tail -n 1 f1

# find lines in input
cat data | grep ^kernel
```

### Archiving



```Bash
# size of specifid directory
du -sh .
echo $HOME
# backup to tarball
sudo tar -cvf /tmp/$USER.tar.gz $HOME/Dokumente

# test tar to see what is in it
tar -tf /tmp/adnan.tar

# expand / extract with -x
tar -xvf test.tar

# compress
gzip adnan.tar
# adnan.tar.gz is created

# to unzip use gunzip
gunzip adnan.tar.gz
# which can further be untared

# with file type can be checked
file adnan.tar

# eveon more zipping
bzip2 adnan.tar
bunzip2 adnan.tar.bz2
```

### Help

```Bash
# append --help
cp --help

# manual pages search with / n for next uppercase n for backwards... ? for searching backwards
# press q to jump out
man cp

# go to section with number
man 5 crontab
```

### File permissions

```Bash
# set mask to create files / folders
umask 0002
# file rw rw rw => 666
# directory rwx rwx rwx => 777

chmod rwxrwxrwx file
chmod a+x file, chmod a-x file
chmod o+x file, chmod o-x file
chmod g+r file, chmod g-w file
chmod 555 file
```

### Managing Ownership

```Bash
# user id
id -u
# username
id -un
# primary groups (creating)
id -gn
# secondary groups (accessing file resources this groups are used)
id -Gn

# changing group ownership
chgrp adm
# change group
newgroup adm
# exit returns from group
# change user
chown user file
```

```
# su changes user
su

# copying without chaning ownership (as root)
cp -a file2 /root/file2a
```