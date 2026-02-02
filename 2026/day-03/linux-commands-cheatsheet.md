1]Process Management
top – shows all running processes and system usage in real time
ps – shows currently running processes
ps -ef – shows all processes with full details
htop – interactive process viewer (if installed)
free – shows free and used memory
free -h – shows memory in human readable format
uptime – shows system running time and load average
kill – stops a process using PID

2]File System
df -h – shows all mounted filesystems with disk usage
lsblk – shows block devices and mount points
/etc/fstab – used to mount filesystems permanently
mount – mounts a filesystem
umount – unmounts a filesystem
mount -a – mounts all filesystems defined in /etc/fstab without rebooting
fsck – used to check and repair a filesystem
chown – changes owner and group of a file
chmod – changes file permissions
du -sh – shows disk usage of a directory
ls -l – shows file permissions and ownership

3]Networking Troubleshooting
ping – checks connectivity to a host
curl ifconfig.me – shows public IP address
hostname -i – shows private IP
ifconfig – shows network interface details (older command)
ip addr / ip a – shows IP addresses
ip route / ip r – shows routing table
dig – checks DNS records and IP of a domain
nslookup – shows IP address of a domain
netstat -tulnp – shows ports and services using them (older)
ss -tulnp – shows active ports and listening services
traceroute – shows network path to a destination  
