
# **Born2beRoot: Setting Up Your First Virtual Server**

## **Project Description**
The goal of this project is to introduce you to virtualization and system administration by setting up your first virtual server using **VirtualBox** (or **UTM** if VirtualBox is unavailable). You will implement strict security and system configuration policies while learning about user management, services, and firewalls.

---

## **Mandatory Part**

### **System Requirements**

1. **Virtualization Tool**:
   - Use **VirtualBox** (or **UTM** if VirtualBox does not work on your system).

2. **Operating System**:
   - Debian (latest stable) **OR** Rocky Linux (latest stable).  
     **Debian** is strongly recommended for beginners.

3. **Server Configuration**:
   - **No Graphical Interface**: Do not install X.org or any other graphical server.
   - **Encrypted Partitions**: Create at least 2 LVM-encrypted partitions.

4. **SSH Configuration**:
   - SSH service must run on **port 4242**.
   - **Root login over SSH must be disabled**.

5. **Firewall**:
   - Use **UFW** (Debian) or **firewalld** (Rocky) to allow **only port 4242**.

6. **Hostname**:
   - Set your machine's hostname to `<your_login>42` (e.g., `john42`).

7. **User Management**:
   - Create a user with your login.  
   - This user must belong to the groups `user42` and `sudo`.

8. **Password Policies**:
   Enforce the following password rules:
   - Password expires every **30 days**.  
   - Minimum of **2 days** before a password can be changed.  
   - User receives a warning **7 days** before password expiration.  
   - Password must be **at least 10 characters** (including uppercase, lowercase, and numbers).  
   - No more than **3 identical consecutive characters**.  
   - Root passwords must also follow this policy.

9. **Sudo Configuration**:
   - Limit sudo password attempts to **3**.  
   - Display a custom error message for incorrect passwords.  
   - Log all sudo commands (inputs/outputs) to `/var/log/sudo/`.  
   - Enable TTY mode for sudo.  
   - Restrict paths available to sudo:
     ```
     /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin
     ```

---

## **Monitoring Script**

Create a **bash script** called `monitoring.sh` that runs every 10 minutes. It should display system information on all terminals using the `wall` command.

### **Required Information**:
- OS architecture and kernel version.  
- Number of physical and virtual CPUs.  
- RAM and disk usage (percentage).  
- Current CPU load (percentage).  
- Last reboot date and time.  
- LVM usage status.  
- Number of active connections and logged-in users.  
- IPv4 address and MAC address.  
- Number of commands executed with `sudo`.

### **Example Output**:
```
Broadcast message from root@john42 (tty1) (Sun Apr 25 15:45:00 2021):

#Architecture: Linux john42 4.19.0-16-amd64 #1 SMP Debian 4.19.181-1 (2021-03-19) x86_64 GNU/Linux
#CPU physical : 1
#vCPU : 1
#Memory Usage: 74/987MB (7.50%)
#Disk Usage: 1009/2Gb (49%)
#CPU load: 6.7%
#Last boot: 2021-04-25 14:45
#LVM use: yes
#Connexions TCP : 1 ESTABLISHED
#User log: 1
#Network: IP 10.0.2.15 (08:00:27:51:9b:a5)
#Sudo : 42 cmd
```

---

## **Bonus Part**

If the mandatory part is completed perfectly, implement the following bonuses:

 **Partition Structure**:  
   Optimize your partitions for an advanced layout.

---
