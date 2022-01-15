Useful Bash commands:

*Note: all commands written or found from various locations which I found useful*

**How to use find to locate all files types & copy into a new directory.**

```bash
$ find -iname '*.mp3' -exec cp {} /home/sk/test2/ \;
```

- **find** - It's the command to find files and folders in Unix-like systems.
- **-iname '\*.mp3'** - Search for files matching with extension .mp3.
- **-exec cp** - Tells you to execute the 'cp' command to copy files from source to destination directory.
- **{}** - is automatically replaced with the file name of the files found by 'find' command.
- **/home/sk/test2/** - Target directory to save the matching files.
- **\;** - Indicates it that the commands to be executed are now complete, and to carry out the command again on the next match

**Change permission recursively for a directory**

#Full permission user/group, none to others
chmod -R 770 my_di

#FUll perimission all
chmod -R a=rwx my_dir

**File sorting in ls**

# time
ls -lt

# extension
ls -lx

**Find & Sort files via file extension**

find . -iname "*.md" | sort -r

**Find files & sort by type**

find -name "snap*" -type d

**Find files via properties of the file**

find -name "snap*" -printf "%a %p \n"

find \( -name "*.html" -type f \) -or -name "*.json" -printf "%u %g %p \n"

    %a – Returns the last time a file was accessed.
    %b – Returns the amount of disk space used for a file in 512-byte blocks.
    %d – Returns a file’s depth in the directory tree.
    %g – Returns a file’s group name or numeric group ID if the group has no name.
    %k – Returns the amount of disk space used for a file in 1K blocks.
    %m – Returns permission bits of a file (in octal).
    %p – Returns a file’s exact filename.
    %s – Returns a file’s size in bytes.
    %t – Returns a file’s last modification time in the format returned by the -ctime option.
    %u – Returns a file owner’s user name or numeric user ID if the user has no name.

# Find files and directories one step down from the working directory
find . -maxdepth 1 -name "chart*"

# Find files and directories two steps down from the ~/chart directory
find ~/chart -maxdepth 2 -name "chart"

**Find a MAC addr**

```bash
$ ifconfig | grep HWaddr
```

**How to rsync**

```bash
$ rsync /home/user/dir1/file1.txt /home/user/dir2/text_file.txt
```

**Find an IP addr**

'''bash
$ ifconfig | grep broadcast | awk '{print $2}'
'''
#More IP addr info

'''bash
$ netstat -rn
'''

**Public IP information**

'''bash
$ dig +short myip.opendns.com @resolver1.opendns.com
'''

**List all rules for IP Tables**

# IPv4
sudo iptables -S
# IPv6
sudo ip6tables -S

