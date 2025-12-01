# Linux-Handbook
Here are **short, crisp, interview-level important Linux notes** — exactly how a **4-year DevOps engineer** should answer.
(Straight to the point, no theory overload — perfect for revision or recording.)

---

# 🔥 **LINUX IMPORTANT NOTES (DevOps Cheat Sheet)**

---

## 🟢 **1. File System Basics**

* Everything in Linux is a **file** (including devices).
* Important directories:

  * `/etc` → Config files
  * `/var/log` → Logs
  * `/usr/bin` → User-level binaries
  * `/opt` → Optional apps
  * `/home` → User home directories
  * `/root` → Root user
  * `/boot` → Bootloader files
  * `/dev` → Devices (disks, USB, partitions)

---

## 🟡 **2. User & Permission Management**

### User creation

```
useradd -m dev1
passwd dev1
```

### Groups

```
groupadd devteam
usermod -aG devteam dev1
```

### Permissions

* Read = 4
* Write = 2
* Execute = 1
* Example:

```
chmod 750 file
chown dev1:devteam file
```

### SUDO control

```
visudo
dev1 ALL=(ALL) NOPASSWD:ALL
```

---

## 🔵 **3. System Monitoring**

### Commands

```
top                 → Live process monitor
htop                → Better top (manual install)
free -h             → RAM usage
df -h               → Disk
du -sh *            → Folder size
uptime              → Load average
vmstat 1            → CPU/IO stats
iostat              → Disk I/O
ps -ef              → List all processes
```

### Load average meaning:

* 1 min, 5 min, 15 min load
* Load > CPU cores = high load

---

## 🟣 **4. Systemctl & Services**

### Start / stop / check service:

```
systemctl start nginx
systemctl stop nginx
systemctl status nginx
```

### Enable at boot:

```
systemctl enable nginx
```

### Check logs of a service:

```
journalctl -u nginx -f
```

### Custom systemd service:

```
/etc/systemd/system/myapp.service
```

---

## 🔴 **5. Networking**

### Check IP:

```
ip a
```

### Check open ports:

```
ss -tulnp
```

### DNS troubleshoot:

```
nslookup google.com
dig google.com
```

### Connectivity:

```
ping
curl -I http://server
traceroute google.com
```

### Firewall (UFW):

```
ufw allow 22
ufw allow 80
ufw status
```

---

## 🟤 **6. Disk & Storage**

### List disks:

```
lsblk
fdisk -l
```

### Mount disk:

```
mount /dev/xvdf1 /data
```

### Check filesystem:

```
df -Th
```

### LVM (important):

```
pvcreate /dev/xvdf
vgcreate appvg /dev/xvdf
lvcreate -L 5G -n applv appvg
mkfs.ext4 /dev/appvg/applv
mount /dev/appvg/applv /mnt/app
```

---

## 🟠 **7. Logs (VERY important for DevOps)**

### Logs location:

```
/var/log
/var/log/messages
/var/log/syslog
/var/log/nginx/access.log
/var/log/nginx/error.log
```

### Follow logs:

```
tail -f file.log
```

### Journal logs:

```
journalctl -xe
```

---

## 🟢 **8. Cron Jobs**

```
crontab -e
```

### Example daily backup at 2 AM:

```
0 2 * * * tar -czf /backup/app.tar.gz /opt/app
```

### List cron jobs:

```
crontab -l
```

---

## 🔵 **9. Shell Scripting Essentials**

### Basic script:

```
#!/bin/bash
echo "Hello"
```

Make executable:

```
chmod +x script.sh
```

### Useful scripts:

* Log cleanup
* Service restart
* Health check
* Disk alert

### Variables:

```
name="rukhs"
echo $name
```

### Loops:

```
for i in {1..5}; do echo $i; done
```

---

## 🟣 **10. Package Management**

### Debian/Ubuntu:

```
apt update
apt install nginx
apt remove nginx
```

### RHEL/Amazon:

```
yum install nginx
systemctl restart nginx
```

---

## 🔴 **11. SSH & Security**

### Key-based auth:

```
ssh-keygen
ssh-copy-id user@IP
```

### SSH hardening:

* Disable root login
* Disable password login
* Allow only specific users

Config:

```
/etc/ssh/sshd_config
```

---

## 🟤 **12. File Search & Management**

```
find / -name "*.log"
grep "error" file.log
grep -iR "fail" /var/log
```

Copy & move:

```
cp file /tmp/
mv file /opt/
```

Archives:

```
tar -czf backup.tar.gz /opt/app
tar -xzf backup.tar.gz
```

---

# ⭐ **If you want, I can convert this into a 2-page CLEAN PDF-style note for you.**
