# Essential Shell Scripts for Cloud and DevOps

## 1. Script to Monitor Node Health

Monitoring the health of a node is crucial in ensuring smooth operations in a cloud or DevOps environment. Below is a shell script that consolidates various Linux commands to provide insights into node health.

### Shell Script to Output Node Health
Save the following script in a file named `node_health.sh` and give it execute permissions using `chmod +x node_health.sh`:

```bash
#!/bin/bash

# Node Health Script

# Display Disk Usage
echo "Disk Usage:"
df -h

echo "----------------------"

# Display Memory Usage
echo "Memory Usage:"
free -h

echo "----------------------"

# Display CPU Cores
echo "CPU Cores:"
nproc

echo "----------------------"

# Display Top Resource-Consuming Processes
echo "Top Resource-Consuming Processes:"
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head

echo "----------------------"

# Display Load Average
echo "Load Average:"
cat /proc/loadavg

echo "----------------------"

# Display System Uptime
echo "System Uptime:"
uptime

echo "----------------------"

# Display Network Connections
echo "Active Network Connections:"
netstat -tuln

echo "----------------------"
```

### How to Use the Script
1. Save the script to a file named `node_health.sh`.
2. Grant execute permissions: `chmod +x node_health.sh`.
3. Run the script: `./node_health.sh`.

The script outputs a comprehensive overview of the node's health, including disk usage, memory usage, CPU information, top processes, load averages, uptime, and network connections.

---

## 2. Explanation of Shell Features and Commands

### `set -x`
The `set -x` command is used for debugging shell scripts. When enabled, it prints each command and its arguments to the terminal before executing it, allowing you to trace script execution step-by-step. Use it to identify issues in scripts.

#### Example
```bash
#!/bin/bash
set -x
# Commands to debug
echo "Debugging with set -x"
```
Disable it using `set +x` once debugging is complete.

### `ps -ef`
The `ps -ef` command lists all running processes on a system in a full-format listing. It displays details such as process ID (PID), parent process ID (PPID), the command that started the process, and more.

#### Key Fields:
- **UID:** User ID of the process owner.
- **PID:** Process ID.
- **PPID:** Parent Process ID.
- **C:** CPU utilization.
- **STIME:** Start time of the process.
- **CMD:** Command that started the process.

### `grep`
The `grep` command is used to search for specific patterns in files or output. It is a powerful text search tool that supports regular expressions.

#### Example
```bash
# Find processes related to "nginx":
ps -ef | grep nginx
```

### Pipe (`|`)
The pipe operator (`|`) is used to direct the output of one command as input to another. This enables chaining commands together for complex operations.

#### Example
```bash
# List all running processes and filter by keyword "java":
ps -ef | grep java
```

### `awk`
The `awk` command is a text processing tool used to manipulate and analyze text. It is particularly useful for extracting specific fields from structured text.

#### Example
```bash
# Extract the process ID (PID) and CPU usage of all running processes:
ps -ef | awk '{print $2, $3}'
```

---

This article provides an overview of essential shell scripting commands and techniques for cloud and DevOps professionals. Understanding and using these scripts effectively can help in automating tasks, monitoring resources, and ensuring system stability.

