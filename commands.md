# 📑 Index

- [File Manipulation](#file-manipulation)
- [Process and System Monitoring Commands](#process-and-system-monitoring-commands)
- [System Commands](#system-commands)
- [User Management and Permission Commands](#user-management-and-permission-commands)
- [Package Management Commands](#package-management-commands)
- [Networking Commands](#networking-commands)
- [Text Processing & Manipulation Commands](#text-processing--manipulation-commands)
- [Disk and Filesystem Management](#disk-and-filesystem-management)
- [Archive and Compression](#archive-and-compression)
- [Log Management](#log-management)
- [Service Management (systemd)](#service-management-systemd)
- [Security and SSH](#security-and-ssh)
- [Performance Troubleshooting](#performance-troubleshooting)
- [Cron and Scheduling](#cron-and-scheduling)
- [Disk Usage & Cleanup](#disk-usage--cleanup)


## File Manipulation

**`ls`** - Lists files and directories in the current working directory.
```bash
ls -l    # detailed list
ls -a    # show hidden files
ls -r    # reverse order
ls -h    # human readable
ls -t    # sort by modified time
ll       # alias for ls -l
```
**`pwd`** - It allows you to print the current working directory.

**`cd <path>`** - Change current working directory.

**`mkdir <new_dir>`** - Create new directory.
```bash
mkdir -p <dir_name>  # create recursive directory
```

**`rmdir <dir>`** - Remove empty directory.

**`rm <file>`** - Remove empty file.
```bash
rm -rf <dir_name>  # recursive delete all files in directory
```

**`touch <file>`** - Create an empty file or update file timestamp.
```bash
touch file1 file2   # create multiple files
```

**`cp <src> <dest>`** - Copy files or directories.
```bash
cp file1 file2.txt         # copy file  
cp -r dir1 dir2            # copy directory recursively
```

**`mv <src> <dest>`** - Move or rename files/directories.
```bash
mv old.txt new.txt         # rename file  
mv file.txt /path/to/dir   # move file
```

**`cat <file>`** - Display file content or concatenate files.
```bash
cat file.txt                   # show file content  
cat file1 file2 > merged.txt   # concatenate files
cat file1 >> file2             # add all content from file1 to file 2
cat >> file                    # add text to file and ctrl+d to exit
```

**`find <path> -name <pattern>`** - Search files and directories.
```bash
find /home -name "*.txt"    # find all .txt files  
find . -type d -name test   # find directories named "test"
find . -type f -name test   # find files named "test"
```

**`grep <pattern> <file>`** - Search text using patterns.
```bash
grep "error" logfile.txt         # search keyword in file, -i for ignore case  
grep -r "main()" ./src           # recursive search in directory
grep -c 'Failed' messages.log    # count occurance word "Failed" appears in file.
```

**`stat <file>`**- Show detailed file information.
```bash
stat file.txt   # show inode, size, permissions, timestamps
```

**`file <file>`** - Determine file type.
```bash
file script.sh   # check if it’s ASCII, binary, etc.
```

**`strings <binary>`** - Extract readable text from binaries.
```bash
strings /bin/ls | grep "usage"   # find readable strings in binary
```

## Process and System Monitoring Commands
**`ps`** - Show running processes.
```bash
ps aux          # detailed process info  
ps -ef | grep nginx   # find process by name
```

**`top`** - Real-time process and resource monitor.
```bash
P # Sorts by CPU usage
M # Sorts by memory usage
T # Sorts by running time
```

**`htop`** - Interactive process viewer

**`kill [signal] [PID]`** - Kill a process by PID.
```bash
15 (SIGTERM) # default and common
9 (SIGKILL)  # forcefull kill
1 (SIGHUP)   # hang up signal
```

**`jobs`** - Show background jobs in current shell.

**`bg / fg`** - Resume jobs in background/foreground.
```bash
fg %1   # bring job 1 to foreground  
bg %1   # run job 1 in background
```

**`free -h`** - Show memory usage.

**`vmstat`** - Show CPU, memory, I/O statistics.
```bash
vmstat 2 5   # sample every 2s, 5 times
```

**`iostat`** - Show CPU and disk I/O statistics.
```bash
iostat -x 2   # extended stats every 2s
```

**`sar`** - System activity reporter (CPU, memory, network).
```bash
sar -u 1 3   # CPU usage every 1s, 3 times
```

## System Commands

**`uname -a`** - Show system information.
```bash
uname -r    # kernel version  
uname -m    # machine architecture
uname -s    # kernal name
uname -n    # node name/ hostname of system
uname -p    # processor type
uname -o    # operating system
```

**`hostname`** - Show or set system hostname.
```bash
hostname    # display hostname  
hostnamectl set-hostname newhost  # set new name of host
```

**`dmesg`** - Show kernel ring buffer logs.
```bash
dmesg | grep usb   # check USB logs
```

**`uptime`** - Show system load averages and uptime.

**`date`** - Show or set system date/time.
```bash
date "+%Y-%m-%d %H:%M:%S"   # formatted date
```

**`cal`** - Display calendar for current month.
```bash
cal 9 2025   # calendar for sept in year 2025
cal 2025   # calendar for year 2025
```

**`shutdown`** - Power off/reboot system.
```bash
shutdown -h now    # shutdown immediately, h for halt
shutdown -r now    # reboot immediately, r for reboot
shutdown +5        # Shuts down the system in 5 minutes.
shutdown 22:00     # Shuts down the system at 10:00 PM.
```

**`reboot`** - Restart system.
```bash
reboot -f  # force reboot
```

## User Management and Permission Commands

**`whoami`** - Show current logged-in user.

**`id`** - Show user/group IDs.
```bash
id username
```

**`who`** - Show logged-in users.

**`adduser <username>`** - Add new user.
```bash
adduser devuser
```
**`passwd <username>`** - Set/change user password.
```bash
passwd devuser
```

**`usermod`** - Modify user account.
```bash
usermod -aG sudo devuser   # add user to sudo group
usermod -g developers devuser  # This changes the primary group of devuser to developers
usermod -l newname oldname     # change login name
usermod -d /home/newhome <username>  # change user home directory
```

**`deluser <username>`** - Remove a user.
```bash
deluser devuser
```

**`groups`** - Show user groups.
```bash
groups username
```

**`sudo <command>`** - Run command as superuser.
```bash
sudo su  # change to superuser
```

**`chmod`** - Change file permissions.
```bash
chmod 644 file.txt
chmod ugo+x file.txt
chmod u+x file.txt
```

**`chown <user>:<group> <file>`** - Change file ownership.
```bash
chown user file.txt           # change owner  
chown user:group file.txt     # change owner and group
```

**`umask`** - Show or set default permissions.
```bash
umask 022
```

## Package Management Commands
(depends on distro: Debian/Ubuntu = apt, RedHat/CentOS/Amazon Linux = yum/dnf)

**`apt update`** - Refresh package list (Debian/Ubuntu).
```bash
sudo apt update
```

**`apt install <pkg>`** - Install a package.
```bash
sudo apt install nginx
```

**`apt remove <pkg>`** - Remove a package.
```bash
sudo apt remove nginx
```

**`apt upgrade`** - Upgrade installed packages.
```bash
sudo apt upgrade
```

**`yum install <pkg>`** - Install package (RHEL/CentOS).
```bash
sudo yum install httpd
```

**`yum remove <pkg>`** - Remove package.
```bash
sudo yum remove httpd
```

**`dnf update`** - Update packages (newer RHEL).
```bash
sudo dnf update
```

```bash
dpkg -s nginx  # check a package's installation status
dpkg -l nginx  # lists all packages that match a given pattern
apt list --installed nginx  #  check installed packages
yum list installed nginx  #  check packages if currently installed on the system
rpm -q nginx  #  query the database for a specific package
rpm -qa | grep nginx  #  lists all installed RPM packages 
```

## Networking Commands

**`ip addr`** - Show IP addresses.
```bash
ip addr show
```

**`ip link set <interface_name> up`** - Use this command to manually bring a network interface up if it's down

**`ping <host>`** - Check network connectivity.
```bash
ping google.com
```

**`curl <url>`** - Fetch content from URL.
```bash
curl -I https://example.com   # fetch headers only
```

**`wget <url>`** - Download files from the web.
```bash
wget https://example.com/file.tar.gz
```

**`netstat -tulnp`** - Show network connections/ports. (deprecated use ss)
```bash
netstat -an | grep 80
```

**`ss -lutnp`** - Show listening ports and sockets.
```bash
-t	Show TCP sockets
-u	Show UDP sockets
-l	Show listening sockets
-n	Don't resolve names/ports
-p	Show processes using sockets
```

**`traceroute <host or IP>`** - Trace route to host.
```bash
traceroute google.com
```

**`nslookup <domain>`** - DNS query.
```bash
nslookup openai.com
nslookup -type=AAAA google.com
nslookup -type=CNAME www.google.com
nslookup -type=NS google.com
```

**`dig <domain>`** - Detailed DNS query.
```bash
dig google.com +short # minimal output
dig google.com AAAA
dig google.com NS
dig google.com CNAME
```

**`scp <src> <user@host>:<dest>`** - Secure copy files between hosts.
```bash
scp file.txt user@server:/tmp/
```

**`rsync -avz <src> <dest>`** - Sync files between servers.
```bash
rsync -avh /home/user/documents/ /mnt/backup/documents/  #  local backup
rsync -avz /home/user/myproject/ user@remote-server:/var/www/html/  # remote server push with compression
rsync -avz user@remote-server:/var/www/html/ /home/user/backups/  #  remote server pull with compression
rsync -avz --delete /home/user/myproject/ user@remote-server:/var/www/html/  #  Exact mirror copy with deletion on destination
```

## Text Processing & Manipulation Commands

**`cat <file>`** - View file content.
```bash
cat file.txt
```

**`more <file>`** - Can only move forward in file

**`less <file>`** - Can move both forward and backward

**`head -n <num> <file>`** - Show first 10 lines by default
```bash
head -n 20 file.txt  # show first n lines
```

**`tail <file>`** - Show last 10 lines by default
```bash
tail -f logfile.log  #  follow live data in file
tail -n file.txt  #  # show last n lines
```

**`wc <file>`** - Count lines, words, characters.
```bash
wc -l file.txt  # count lines
wc -w file.txt  # count words
wc -c file.txt  # count characters
```

**`sort <file>`** - Sort lines.
```bash
sort -r names.txt  # reverse
sort -n names.txt  # numeric
sort -r <fieldname> names.txt  # based on field/column
```

**`uniq <file>`** - Remove duplicate lines.
```bash
sort names.txt | uniq -u  #  only the unique lines from file
sort names.txt | uniq -c  #  counts the occurrences of each unique line and prints the count next to the line
sort names.txt | uniq -d  #  outputs only the lines that are duplicated and appear at least twice
```

**`cut -d <delim> -f <fields>`** - Extract columns.
```bash
cut -d',' -f2 users.csv
```

**`awk`** - Pattern-based text processing.
```bash
awk '{print $1,$3}' data.txt
```

**`sed`** - Stream editor for search/replace.
```bash
sed 's/old/new/' file.txt  #  Only the first instance of "old" on the second line is replaced
sed 's/old/new/g' file.txt  #  replace every occurrence of a pattern on a line
sed -i 's/old/new/g' file.txt  #  In-place editing, permanently modifies the file
sed '/pattern/d' file.txt  #  to delete lines that match a certain pattern
```

**`tr`** - Translate or delete characters.
```bash
cat file.txt | tr 'a-z' 'A-Z'   # convert lowercase to uppercase
```

**`xargs`** - Build commands from input.
```bash
find . -name "*.log" | xargs rm
```

## Disk and Filesystem Management

**`lsblk`** - List block devices.
```bash
lsblk    # show disks and partitions
```

**`blkid`** - Show block device attributes.
```bash
blkid /dev/sda1
```

**`fdisk`** - Partition a disk (interactive).
```bash
fdisk /dev/sdb
```

**`parted`** - Partition tool (modern).
```bash
parted /dev/sdb print
```

**`mkfs`** - Create a filesystem.
```bash
mkfs.ext4 /dev/sdb1
```

**`mount <device> <dir>`** - Mount a filesystem/device.
```bash
mount /dev/sdb1 /mnt/usb   # mount USB to /mnt/usb  
umount /mnt/sdb1          # unmount device from directory  
```

**`fsck`** - Check/repair filesystem.
```bash
fsck /dev/sdb1
```

**`ulimit [options] [limit]`** - It is used to view or set the resource limits for a user's session or a running process. These limits control how many system resources, such as open files, memory, and CPU time, a process can use.
```bash
-a: This is the most common option. It displays all current resource limits.
-n: Sets or displays the maximum number of open file descriptors (files).
-c: Sets or displays the maximum size of a core file.
-f: Sets or displays the maximum file size a user can create.
-s: Sets or displays the maximum stack size.
-u: Sets or displays the maximum number of user processes.
-v: Sets or displays the maximum virtual memory size.
```

**`Format file system on linux`** - find the file system type of the disk, like EXT4, NTFS, or XFS. Then run one of the following commands according to the file system type
```bash
mkfs.ext4 <partition>
mkfs.xfs <partition>
mkfs.ntfs <partition>
```

## Archive and Compression

**`tar`** - Archive and extract files.
```bash
tar -cvf archive.tar dir/        # create tar archive  
tar -xvf archive.tar             # extract tar archive
tar -tvf archive.tar             # check content of tar archive  
tar -czvf archive.tar.gz dir/    # create compressed archive  
tar -xzvf archive.tar.gz         # extract compressed archive
tar -tzvf archive.tar            # check content of compressed tar archive  
```

**`gzip`** - Compress a file.
```bash
gzip file.txt  #  compress
gunzip file.txt.gz  #  decompress
```

**`zip`** - Create zip archive.
```bash
zip -r archive.zip dir/  # zip archive
unzip archive.zip  #  Extract zip archive
```

## Log Management

**`journalctl`** - View systemd logs.
```bash
journalctl -xe   # view recent errors with explanatory
journalctl -u nginx   # logs for nginx service unit
```

**`cat /var/log/syslog`**  # check central log file for a Linux system

**`cat /var/log/dmesg`**  # Contains kernel ring buffer messages, to look for information about hardware detection, device drivers, and kernel-level errors that occur during system boot. 

**`cat /var/log/boot.log`** # system startup sequence

**`/var/log/auth.log`**  # authentication related events

**`sudo logrotate -f /etc/logrotate.conf`** # force rotation of all logs

## Service Management (systemd)

**`systemctl status <service>`** - Check service status.

**`systemctl start <service>`** - Start a service.

**`systemctl stop <service>`** - Stop a service.

**`systemctl restart <service>`** - Restart a service.

**`systemctl enable <service>`** - Enable on boot.

**`systemctl disable <service>`** - Disable on boot.

**`systemctl mask <service>`** - prevents a service from being started under any circumstances, even as a dependency of another service

**`systemctl unmask <service>`** - reverses mask action, allowing the service to be started again.

## Security and SSH

**`ssh user@host`** - Connect to remote server.

**`ssh-copy-id user@host`** - Copy SSH key to server.

**`ufw`** - Simple firewall management.
```bash
ufw enable  
ufw allow 22/tcp  
ufw status
```

**`iptables`** - Firewall rule management.
```bash
iptables -L -n -v # list numeric and verbose
```

## Performance Troubleshooting

**`dstat`** - General system performance tool.

**`lsof`** - List open files & ports.
```bash
lsof -i :80   # processes using port 80
```

**`strace`** - Trace system calls.
```bash
strace -p <pid> # traces the system calls made by a process with the specified process ID
```

**`tcpdump`** - Capture network packets.
```bash
tcpdump -i eth0 port 80 # captures and displays all network packets passing through the eth0 interface that are destined for or originating from port 80
```

## Cron and Scheduling

**`crontab -e`** - Edit user’s cron jobs.
```bash
crontab -l # List cron jobs
Example: Run script every day at midnight
0 0 * * * /path/to/script.sh
```

**`at <time>`** - Run a command once at a given time.
```bash
echo "shutdown -h now" | at 23:00
```

## Disk Usage & Cleanup

**`df`** - Show disk space usage file system.
```bash
df -h    # human-readable format
```

**`du`** - Show file/directory space usage.
```bash
du -sh *   # summary of all files/directories in current path in human readable size  
```
