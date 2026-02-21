# Day 03 – Linux Commands Cheat Sheet

This cheat sheet includes commonly used Linux commands for **Process Management**, **File System**, and **Networking Troubleshooting**. These commands are useful for daily DevOps operations.

---

## 1. Process Management

| Command | Usage |
|--------|------|
| ps aux | Show all running processes |
| top | Real-time CPU and memory usage |
| htop | Interactive process viewer (if installed) |
| pgrep <name> | Find process by name |
| kill <PID> | Stop a process |
| kill -9 <PID> | Force kill a process |
| nice -n 10 <command> | Start process with lower priority |
| renice <priority> -p <PID> | Change priority of running process |

---

## 2. File System & Disk

| Command | Usage |
|--------|------|
| ls -la | List files with details |
| cd <dir> | Change directory |
| pwd | Show current directory |
| mkdir <dir> | Create directory |
| rm -rf <dir/file> | Remove file or directory |
| cp <src> <dest> | Copy files |
| mv <src> <dest> | Move or rename files |
| find /path -name file.txt | Search for a file |
| df -h | Check disk space |
| du -sh * | Check folder size |
| chmod 755 file | Change file permissions |
| chown user:group file | Change file ownership |
| tail -f /var/log/syslog | Monitor logs in real time |
| head file | View first lines of a file |

---

## 3. Networking Troubleshooting

| Command | Usage |
|--------|------|
| ping google.com | Check network connectivity |
| ip addr | Show IP address details |
| ss -tuln | Show listening ports |
| netstat -tuln | Check open ports (older systems) |
| curl http://example.com | Test HTTP response |
| wget <url> | Download a file from internet |
| dig google.com | DNS lookup |
| traceroute google.com | Check network path |

---

## 4. System Information

| Command | Usage |
|--------|------|
| uptime | Show system uptime and load |
| free -h | Check memory usage |
| uname -a | System information |
| whoami | Current user |

---

## Summary
These commands help in quickly checking system health, analyzing logs, managing processes, and troubleshooting network issues — essential skills for real-world DevOps work.
