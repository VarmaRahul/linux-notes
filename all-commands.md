## File Manipulation

#### 1. `ls` - Lists files and directories in the current working directory.
```bash
ls -l    # detailed list
ls -a    # show hidden files
ll       # alias for ls -l
```
#### 2. `pwd` - It allows you to print the current working directory.
#### 3. `cd <path>` - Change current working directory.
#### 4. `mkdir <new_dir>` - Create new directory.
```bash
mkdir -p <dir_name>  # create recursive directory
```
#### 5. `rmdir <dir>` - Remove empty directory.
#### 6. `rm <file>` - Remove empty file.
```bash
rm -rf <dir_name>  # recursive delete all files in directory
```
#### 7. touch <file> - Create an empty file or update file timestamp.
```bash
touch file1 file2   # create multiple files
```
#### 8. cp <src> <dest> - Copy files or directories.
```bash
cp file1 file2.txt         # copy file  
cp -r dir1 dir2            # copy directory recursively
```
#### 9. mv <src> <dest> - Move or rename files/directories.
```bash
mv old.txt new.txt         # rename file  
mv file.txt /path/to/dir   # move file
```
#### 10. cat <file> - Display file content or concatenate files.
```bash
cat file.txt                   # show file content  
cat file1 file2 > merged.txt   # concatenate files
```
#### 11. find <path> -name <pattern> - Search files and directories.
```bash
find /home -name "*.txt"    # find all .txt files  
find . -type d -name test   # find directories named "test"
```
#### 12. grep <pattern> <file> - Search text using patterns.
```bash
grep "error" logfile.txt         # search keyword in file  
grep -r "main()" ./src           # recursive search in directory
```
#### 13. tar - Archive and extract files.
```bash
tar -cvf archive.tar dir/        # create tar archive  
tar -xvf archive.tar             # extract tar archive  
tar -czvf archive.tar.gz dir/    # create compressed archive  
tar -xzvf archive.tar.gz         # extract compressed archive
```
#### 14. df - Show disk space usage file system.
```bash
df -h    # human-readable format
```
#### 15. du - Show file/directory space usage.
```bash
du -sh *   # summary of all files/directories in current path in human readable size  
```
#### 16. chmod <permissions> <file> - Change file permissions.
```bash
chmod 755 script.sh    # owner: rwx, group: r-x, others: r-x  
chmod u+x script.sh    # add execute permission for owner
```
#### 17. chown <user>:<group> <file> - Change file ownership.
```bash
chown user file.txt           # change owner  
chown user:group file.txt     # change owner and group
```
#### 18. mount <device> <dir> - Mount a filesystem/device.
```bash
mount /dev/sdb1 /mnt/usb   # mount USB to /mnt/usb  
```
#### 19. umount <dir> - Unmount a filesystem/device.
```bash
umount /mnt/sda   # unmount device from directory  
```

head <file> - Show the first lines of a file.
head -n 20 logfile.txt   # show first 20 lines

tail <file> - Show the last lines of a file.
tail -f logfile.txt      # follow logs in real-time

less <file> - View file content interactively (scroll/search).
less /var/log/syslog   # view large log file

wc <file> - Count lines, words, and characters.
wc -l file.txt     # count lines  
wc -w file.txt     # count words

sort <file> - Sort lines in a file.
sort users.txt               # sort alphabetically  
sort -n numbers.txt          # numeric sort  
sort -u list.txt             # unique sorted list

uniq <file> - Filter out duplicate lines.
uniq list.txt                # remove duplicates (must be sorted)  
sort list.txt | uniq -c      # count occurrences

cut -d <delim> -f <fields> - Extract specific columns from files.
cut -d',' -f1,3 data.csv   # extract 1st and 3rd column

awk '<pattern> {action}' <file> - Pattern scanning and text processing.
awk '{print $1, $3}' data.txt    # print 1st and 3rd columns  
awk '/error/ {print $0}' log.txt # print lines containing "error"

sed '<cmd>' <file> - Stream editor for search/replace.
sed 's/error/ERROR/g' logfile.txt   # replace "error" with "ERROR"  
sed -n '10,20p' file.txt            # print lines 10 to 20

xargs - Build and execute command lines from stdin.
find . -name "*.log" | xargs rm    # delete all .log files  
cat urls.txt | xargs -n1 curl -O   # download files from list of URLs

stat <file> - Show detailed file information.
stat file.txt   # show inode, size, permissions, timestamps

file <file> - Determine file type.
file script.sh   # check if it’s ASCII, binary, etc.

strings <binary> - Extract readable text from binaries.
strings /bin/ls | grep "usage"   # find readable strings in binary
