# Day 04 – Linux Practice: Processes and Services

**Environment:** Ubuntu Linux
**Service Inspected:** ssh

Today I practiced Linux fundamentals by checking running processes, inspecting system services, and reviewing logs.

---

## 1. Process Checks

### Check all running processes

Command:

```
ps aux | head
```

Sample Output:

```
USER       PID %CPU %MEM COMMAND
root         1  0.0  systemd
root       620  0.0  sshd
ubuntu    1020  0.1  bash
```

**Observation:**

* `systemd` is running as PID 1
* SSH daemon (`sshd`) is active

---

### Find SSH process

Command:

```
pgrep -a sshd
```

Output:

```
620 /usr/sbin/sshd -D
```

**Observation:**

* SSH process is running with PID 620

---

## 2. Service Checks (systemd)

### Check SSH service status

Command:

```
systemctl status ssh
```

Important Output:

```
Loaded: loaded (/lib/systemd/system/ssh.service)
Active: active (running)
```

**Observation:**

* SSH service is loaded and running properly

---

### List running services

Command:

```
systemctl list-units --type=service --state=running
```

Sample Output:

```
ssh.service
cron.service
systemd-journald.service
networking.service
```

**Observation:**

* Shows all active system services

---

## 3. Log Checks

### View SSH logs

Command:

```
journalctl -u ssh --no-pager | tail -n 10
```

Sample Output:

```
Accepted password for ubuntu from 172.31.x.x
Session opened for user ubuntu
```

**Observation:**

* Shows recent SSH login activity

---

### View system logs

Command:

```
tail -n 20 /var/log/syslog
```

**Observation:**

* Displays recent system events and warnings

---

## 4. Mini Troubleshooting Flow (If SSH is not working)

Step 1: Check process

```
pgrep sshd
```

Step 2: Check service status

```
systemctl status ssh
```

Step 3: Restart service if needed

```
sudo systemctl restart ssh
```

Step 4: Check logs

```
journalctl -u ssh
```

---

## Summary

Today I practiced:

* Checking running processes using `ps` and `pgrep`
* Inspecting services using `systemctl`
* Reading logs using `journalctl` and `tail`
* Basic troubleshooting for a system service

These are essential commands for real-world DevOps troubleshooting and incident handling.

