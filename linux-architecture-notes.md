# Day 02 – Linux Architecture, Processes, and systemd

## 1. Core Components of Linux

### Kernel
- The core of the Linux OS.
- Manages:
  - CPU scheduling
  - Memory management
  - Device drivers
  - File systems
  - Networking
- Acts as a bridge between hardware and user applications.

### User Space
- Where users and applications run.
- Examples:
  - Shell (bash)
  - System utilities (ls, cp, ps)
  - Applications (nginx, docker)
- User programs cannot access hardware directly; they communicate via the kernel.

### Init / systemd
- First process started by the kernel.
- Has **PID 1**.
- Responsible for starting and managing system services.

---

## 2. How Processes Work in Linux

### Process Creation
- Every process has a unique **PID**.
- Created using:
  - `fork()` → creates a child process
  - `exec()` → loads a new program
- Parent → Child relationship exists.

### Common Process States

| State | Meaning |
|------|---------|
| Running (R) | Currently using CPU |
| Sleeping (S) | Waiting for an event (most common state) |
| Stopped (T) | Paused by user or system |
| Zombie (Z) | Process finished but parent didn’t clean it |
| Dead | Terminated and removed |

### Useful Commands to Monitor Processes
- `ps aux` → list running processes
- `top` / `htop` → real-time CPU & memory usage
- `kill <PID>` → stop a process
- `kill -9 <PID>` → force kill
- `pgrep <name>` → find process by name

---

## 3. What is systemd and Why It Matters

**systemd** is the service manager used by most modern Linux distributions.

### Responsibilities
- Starts system services during boot
- Manages background services (nginx, docker, ssh)
- Handles service restarts if they crash
- Maintains system logs (journal)
- Supports parallel service startup (faster boot)

### Important systemctl Commands
- `systemctl status nginx`
- `systemctl start nginx`
- `systemctl stop nginx`
- `systemctl restart nginx`
- `systemctl enable nginx` (start at boot)
- `journalctl -u nginx` (view logs)

---

## 4. 5 Daily Linux Commands for DevOps

1. `ps aux` – Check running processes  
2. `top` – Monitor system resources  
3. `systemctl status <service>` – Check service health  
4. `journalctl -xe` – View system logs  
5. `df -h` – Check disk usage  

---

## Summary
Linux works through the kernel, user space, and systemd. Understanding process states and service management helps in debugging high CPU usage, crashed applications, and system failures—core skills for a DevOps engineer.
