# Day 05 – Linux Troubleshooting Runbook

**Target Service:** ssh
**Environment:** Ubuntu Linux

This runbook captures a quick health snapshot of the system and basic troubleshooting steps for the SSH service.

---

## 1. Environment Basics

### Check kernel and system info

Command:

```
uname -a
```

Observation:

* System is running Linux kernel successfully.

### Check OS version

Command:

```
cat /etc/os-release
```

Observation:

* Confirmed Ubuntu environment and version.

---

## 2. Filesystem Sanity Check

### Create test directory and copy file

Command:

```
mkdir -p /tmp/runbook-demo
cp /etc/hosts /tmp/runbook-demo/hosts-copy
ls -l /tmp/runbook-demo
```

Observation:

* Directory and file created successfully.
* Filesystem is writable and healthy.

---

## 3. CPU & Memory Snapshot

### Check system resource usage

Command:

```
top
```

Observation:

* CPU usage low (<10%)
* No abnormal high CPU processes.

### Check memory usage

Command:

```
free -h
```

Observation:

* Memory usage within normal range.
* No memory pressure or swap usage.

---

## 4. Disk & IO Snapshot

### Check disk usage

Command:

```
df -h
```

Observation:

* Root disk usage below 70%.
* No immediate disk space issue.

### Check log directory size

Command:

```
du -sh /var/log
```

Observation:

* Log size is manageable.
* No excessive log growth.

---

## 5. Network Snapshot

### Check listening ports

Command:

```
ss -tulpn | grep ssh
```

Observation:

* SSH service is listening on port 22.

### Test local connectivity

Command:

```
curl -I http://localhost
```

Observation:

* System responding to network requests.

---

## 6. Process Check

### Verify SSH process

Command:

```
pgrep -a sshd
```

Observation:

* SSH daemon running normally.

---

## 7. Logs Reviewed

### Check SSH service logs

Command:

```
journalctl -u ssh -n 50
```

Observation:

* Recent login entries.
* No errors or failures.

### Check system logs

Command:

```
tail -n 50 /var/log/syslog
```

Observation:

* No critical system errors found.

---

## 8. Quick Findings

* System CPU and memory usage are normal.
* Disk space is sufficient.
* SSH service is active and listening.
* No recent errors in SSH or system logs.
* System health is stable.

---

## 9. If This Worsens (Next Steps)

1. Restart SSH service:

```
sudo systemctl restart ssh
```

2. Check for high resource usage:

```
ps aux --sort=-%cpu | head
ps aux --sort=-%mem | head
```

3. Collect deeper diagnostics:

* Increase SSH log level
* Capture process activity using `strace`
* Check firewall or network security group rules

---

## Summary

This runbook provides a quick troubleshooting checklist to:

* Capture system health
* Verify service status
* Review logs before taking action

Following this approach helps reduce downtime and avoids guesswork during production incidents.

