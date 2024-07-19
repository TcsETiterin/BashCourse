Most Linux distributions come with a core set of tools pre-installed by default. Here is a breakdown of the common commands and utilities that are typically available out of the box on most Linux distributions:

### Basic Unix/Linux Commands
- **Navigation and File Operations**
  - `ls`, `cd`, `pwd`, `cp`, `mv`, `rm`, `mkdir`, `rmdir`, `touch`, `find`, `locate`, `grep`

- **File Content Viewing**
  - `cat`, `tac`, `more`, `less`, `head`, `tail`
  - **Note:** Editors like `nano` and `vim` are often but not always installed by default. `nano` is common in more user-friendly distributions, while `vim` or `vi` is almost always available.

### System Information and Management
- **Process Management**
  - `ps`, `top`
  - **Note:** `htop` is often not installed by default but is available in repositories.

- **System Monitoring**
  - `df`, `du`, `free`, `uptime`, `uname`, `dmesg`

### User and Group Management
- `who`, `w`, `id`
- Basic tools like `adduser`, `useradd`, `deluser`, `userdel`, `passwd`
- `groupadd`, `groupdel`, `groupmod`

### Network Utilities
- **Connection and Listening**
  - `ifconfig` (being replaced by `ip` in many distributions), `ip`, `ping`, `netstat` (being replaced by `ss` in newer versions), `traceroute`, `tracepath`
  - **Some distributions may have:** `route`, `arp`, `dig` (often part of `dnsutils` or `bind-utils`)
  - `wget` is usually installed, while `curl` might or might not be.
  - `scp` and `sftp` when OpenSSH is installed (`ssh` is common).
  - **Note:** Tools like `nmap` and `netcat` are not typically installed by default but are available in repositories.

### Security Tools
- **Network Scanning and Reconnaissance**
  - **Note:** Tools like `nmap`, `nikto`, `sqlmap`, `theHarvester`, and `recon-ng` are generally not installed by default.

- **Vulnerability Analysis and Exploitation**
  - **Note:** `metasploit`, ` - **Note:** `metasploit`, `exploitdb`, `msfconsole`, and `searchsploit` are specialized tools that are not included by default in typical Linux distributions. They must be installed separately from official repositories or through external sources.

- **Password Cracking**
  - **Note:** Tools like `john` (John the Ripper), `hashcat`, and `hydra` are not installed by default.

- **Packet Analysis**
  - `tcpdump` is often included by default or available in repositories.
  - **Note:** `wireshark` (with its CLI counterpart `tshark`) is generally not installed by default and must usually be installed separately.

### File and Data Manipulation
- **Archiving and Compression**
  - `tar`, `gzip`, `bzip2`, and `xz` are typically available by default.
  - Core tools like `zip` and `unzip` might not always be included but are commonly available in repositories.

- **Data Modification**
  - `sed`, `awk`, `cut`, `sort`, `uniq`, `tr` are generally included.
  - `jq` is not typically installed by default but can be easily added from repositories.

### Scripting and Automation
- Basic shell scripting (`bash`) is integral to the system.
- **Note:** `tmux` and `screen` are usually available in repositories but not installed by default.

### Advanced System Interaction
- **Permissions and Ownership**
  - `chmod`, `chown`, `chgrp` are standard commands available by default.

- **Remote System Interaction**
  - `ssh`, `scp`, and `rsync` are typically included when OpenSSH is installed.

### Specific Security Tools for Unix/Linux
- **Intrusion Detection and Defense**
  - **Note:** `fail2ban` and `iptables` (`ufw` as a front-end) are generally available in repositories but not always installed by default.

- **File Integrity Monitoring**
  - **Note:** `tripwire` and `aide` are specialized tools and are not included by default.

- **Log Analysis**
  - **Note:** `logwatch` and `auditd` are available in repositories but need to be installed and configured.

### Version Control
- **Git**: While not always pre-installed, `git` is usually available in the default repositories and can be quickly installed.

### Learning More About Default Tools
To find out what is installed on yourcurrent Linux distribution, you can use several commands to explore the available tools:

1. **List All Installed Packages:**
   - For Debian-based systems (e.g., Ubuntu):
     ```sh
     dpkg --list
     ```
   - For Red Hat-based systems (e.g., Fedora, CentOS):
     ```sh
     rpm -qa
     ```

2. **Check if a Specific Command is Available:**
   ```sh
   which command_name
   # or
   command -v command_name
   ```

3. **Explore Packages in the Default Repositories:**
   - For Debian-based systems:
     ```sh
     apt-cache search package_name
     ```
   - For Red Hat-based systems:
     ```sh
     yum search package_name
     # or for newer systems
     dnf search package_name
     ```

By using these commands, you can get a comprehensive overview of the tools and utilities available on your Linux system. Remember that while many tools come pre-installed, others can be easily added from the distribution's package repositories.
