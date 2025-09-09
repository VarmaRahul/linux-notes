## File Manipulation

**`ls`** - Lists files and directories in the current working directory.
```bash
ls -l    # detailed list
ls -a    # show hidden files
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
```

**`11. find <path> -name <pattern>`** - Search files and directories.
```bash
find /home -name "*.txt"    # find all .txt files  
find . -type d -name test   # find directories named "test"
find . -type f -name test   # find files named "test"
```

**`grep <pattern> <file>`** - Search text using patterns.
```bash
grep "error" logfile.txt         # search keyword in file  
grep -r "main()" ./src           # recursive search in directory
```

**`tar`** - Archive and extract files.
```bash
tar -cvf archive.tar dir/        # create tar archive  
tar -xvf archive.tar             # extract tar archive  
tar -czvf archive.tar.gz dir/    # create compressed archive  
tar -xzvf archive.tar.gz         # extract compressed archive
```

**`df`** - Show disk space usage file system.
```bash
df -h    # human-readable format
```

**`du`** - Show file/directory space usage.
```bash
du -sh *   # summary of all files/directories in current path in human readable size  
```

**`chmod <permissions> <file>`** - Change file permissions.
```bash
chmod 755 script.sh    # owner: rwx, group: r-x, others: r-x  
chmod u+x script.sh    # add execute permission for owner
```

**`chown <user>:<group> <file>`** - Change file ownership.
```bash
chown user file.txt           # change owner  
chown user:group file.txt     # change owner and group
```

**`mount <device> <dir>`** - Mount a filesystem/device.
```bash
mount /dev/sdb1 /mnt/usb   # mount USB to /mnt/usb  
```

**`umount <dir>`** - Unmount a filesystem/device.
```bash
umount /mnt/sda   # unmount device from directory  
```

**`head <file>`** - Show the first lines of a file.
```bash
head -n 20 logfile.txt   # show first 20 lines
```

**`tail <file>`** - Show the last lines of a file.
```bash
tail -f logfile.txt      # follow logs in real-time
```

**`less <file>`** - View file content interactively (scroll/search).
```bash
less /var/log/syslog   # view large log file
```

**`wc <file>`** - Count lines, words, and characters.
```bash
wc -l file.txt     # count lines  
wc -w file.txt     # count words
```

**`sort <file>`** - Sort lines in a file.
```bash
sort users.txt               # sort alphabetically  
sort -n numbers.txt          # numeric sort  
sort -u list.txt             # unique sorted list
```

**`uniq <file>`** - Filter out duplicate lines.
```bash
uniq list.txt                # remove duplicates (must be sorted)  
sort list.txt | uniq -c      # count occurrences
```

**`cut -d <delim> -f <fields>`** - Extract specific columns from files.
```bash
cut -d',' -f1,3 data.csv   # extract 1st and 3rd column
```

**`awk '<pattern> {action}' <file>`** - Pattern scanning and text processing.
```bash
awk '{print $1, $3}' data.txt    # print 1st and 3rd columns  
awk '/error/ {print $0}' log.txt # print lines containing "error"
```

**`sed '<cmd>' <file>`** - Stream editor for search/replace.
```bash
sed 's/error/ERROR/g' logfile.txt   # replace "error" with "ERROR"  
sed -n '10,20p' file.txt            # print lines 10 to 20
```

**`xargs`** - Build and execute command lines from stdin.
```bash
find . -name "*.log" | xargs rm    # delete all .log files  
cat urls.txt | xargs -n1 curl -O   # download files from list of URLs
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

**`htop`** - Interactive process viewer (better than top).

**`kill <pid>`** - Kill a process by PID.
```bash
kill -9 1234   # force kill process
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
```

**`hostname`** - Show or set system hostname.
```bash
hostname    # display hostname  
hostnamectl set-hostname newhost
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

**`cal`** - Display a calendar.
```bash
cal 2025   # calendar for year 2025
```

**`shutdown`** - Power off/reboot system.
```bash
shutdown -h now    # shutdown immediately  
shutdown -r now    # reboot immediately
```

**`reboot`** - Restart system.

## User Management and Permission Commands
**`whoami`** - Show current logged-in user.

**`id`** - Show user/group IDs.
```bash
id username
```

**`who`*8 - Show logged-in users.

**`adduser <username>`** - Add new user.
```bash
adduser devops
```
**`passwd <username>`** - Set/change user password.
```bash
passwd devops
```

**`usermod`** - Modify user account.
```bash
usermod -aG sudo devops   # add user to sudo group
```

**`deluser <username>`** - Remove a user.
```bash
deluser devops
```

**`groups`** - Show user groups.
```bash
groups username
```

**`sudo <command>`** - Run command as superuser.
```bash
sudo apt update
```

**`chmod`** - Change file permissions.
```bash
chmod 644 file.txt
chmod ugo+x file.txt
chmod u+x file.txt
```

**`chown`** - Change file owner/group.
```bash
chown user:group file.txt
```

**`umask`** - Show or set default permissions.
```bash umask 022```

🔹 Package Management Commands

(depends on distro: Debian/Ubuntu = apt, RedHat/CentOS = yum/dnf)

apt update - Refresh package list (Debian/Ubuntu).
sudo apt update

apt install <pkg> - Install a package.
sudo apt install nginx

apt remove <pkg> - Remove a package.
sudo apt remove nginx

apt upgrade - Upgrade installed packages.
sudo apt upgrade

yum install <pkg> - Install package (RHEL/CentOS).
sudo yum install httpd

yum remove <pkg> - Remove package.
sudo yum remove httpd

dnf update - Update packages (newer RHEL).
sudo dnf update

rpm -qa - List installed RPM packages.
rpm -qa | grep nginx

🔹 Networking Commands
ifconfig - Show network interfaces. (deprecated → use ip)
ifconfig -a

ip addr - Show IP addresses.
ip addr show

ping <host> - Check network connectivity.
ping google.com

curl <url> - Fetch content from URL.
curl -I https://example.com   # fetch headers only

wget <url> - Download files from the web.
wget https://example.com/file.tar.gz

netstat -tulnp - Show network connections/ports. (deprecated → ss)
netstat -an | grep 80

ss -tulnp - Show listening ports and sockets.
ss -tulnp

traceroute <host> - Trace route to host.
traceroute google.com

nslookup <domain> - DNS query.
nslookup openai.com

dig <domain> - Detailed DNS query.
dig google.com +short

scp <src> <user@host>:<dest> - Secure copy files between hosts.
scp file.txt user@server:/tmp/

rsync -avz <src> <dest> - Sync files between servers.
rsync -avz /src/ user@server:/dest/

🔹 Text Processing & Manipulation Commands
cat <file> - View file content.
cat file.txt

less <file> - View large files interactively.
less /var/log/syslog

head -n <num> <file> - Show first N lines.
head -n 20 file.txt

tail -f <file> - Show last lines (follow mode).
tail -f logfile.log

wc <file> - Count lines, words, characters.
wc -l file.txt

sort <file> - Sort lines.
sort names.txt

uniq <file> - Remove duplicate lines.
sort names.txt | uniq -c

cut -d <delim> -f <fields> - Extract columns.
cut -d',' -f2 users.csv

awk - Pattern-based text processing.
awk '{print $1,$3}' data.txt

sed - Stream editor for search/replace.
sed 's/error/ERROR/g' logfile.txt

tr - Translate or delete characters.
cat file.txt | tr 'a-z' 'A-Z'   # convert lowercase to uppercase

xargs - Build commands from input.
find . -name "*.log" | xargs rm

🔹 Disk and Filesystem Management
lsblk - List block devices.
lsblk    # show disks and partitions

blkid - Show block device attributes.
blkid /dev/sda1

fdisk - Partition a disk (interactive).
fdisk /dev/sdb

parted - Partition tool (modern).
parted /dev/sdb print

mkfs - Create a filesystem.
mkfs.ext4 /dev/sdb1

mount - Mount filesystem.
mount /dev/sdb1 /mnt/data

umount - Unmount filesystem.
umount /mnt/data

fsck - Check/repair filesystem.
fsck /dev/sdb1

🔹 Archive and Compression
tar - Archive files.
tar -czvf archive.tar.gz dir/

gzip - Compress a file.
gzip file.txt

gunzip - Decompress a file.
gunzip file.txt.gz

zip - Create zip archive.
zip -r archive.zip dir/

unzip - Extract zip archive.
unzip archive.zip

🔹 Log Management
journalctl - View systemd logs.
journalctl -xe   # view recent errors  
journalctl -u nginx   # logs for nginx service

tail -f - Follow log files.
tail -f /var/log/syslog

less - Browse log files.
less +F /var/log/auth.log

🔹 Service Management (systemd)
systemctl status <service> - Check service status.
systemctl status nginx

systemctl start <service> - Start a service.
systemctl start nginx

systemctl stop <service> - Stop a service.
systemctl stop nginx

systemctl restart <service> - Restart a service.
systemctl restart nginx

systemctl enable <service> - Enable on boot.
systemctl enable nginx

systemctl disable <service> - Disable on boot.
systemctl disable nginx

🔹 Security and SSH
ssh user@host - Connect to remote server.
ssh user@192.168.1.10

ssh-copy-id user@host - Copy SSH key to server.
ssh-copy-id user@server

scp file user@host:/path/ - Copy file via SSH.
scp file.txt user@server:/tmp/

rsync - Sync files between hosts.
rsync -avz /src/ user@server:/dest/

ufw - Simple firewall management.
ufw enable  
ufw allow 22/tcp  
ufw status

iptables - Firewall rule management.
iptables -L -n -v

🔹 Performance Troubleshooting
uptime - Show load averages.
uptime

free -h - Show memory usage.
free -h

vmstat 1 - System performance stats.
vmstat 1

iostat - CPU and I/O usage.
iostat -xz 1

dstat - General system performance tool.
dstat

lsof - List open files & ports.
lsof -i :80   # processes using port 80

strace - Trace system calls.
strace -p <pid>

tcpdump - Capture network packets.
tcpdump -i eth0 port 80

🔹 Cron and Scheduling
crontab -e - Edit user’s cron jobs.
crontab -e

crontab -l - List cron jobs.
crontab -l

Example: Run script every day at midnight
0 0 * * * /path/to/script.sh

at <time> - Run a command once at a given time.
echo "shutdown -h now" | at 23:00

🔹 Disk Usage & Cleanup
du - Disk usage of files/directories.
du -sh *   # summary in current directory

df -h - Disk space usage.
df -h

ncdu - Interactive disk usage (requires install).
ncdu /var/log
