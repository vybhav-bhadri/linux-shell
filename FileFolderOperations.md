# How to Open, Write, Save, and Execute a Shell File

## **Opening a Shell File**

To create and open a shell file:

1. **Create an empty file:**
   ```plaintext
   touch myscript.sh
   ```
2. **Open the file with a text editor:**
  ```bash
  vi or nano or vin filename.sh
  ```
--- 
### **Writing to the File**

Add a script inside the editor:

```bash
#!/bin/bash
echo "Hello, $(whoami)! Welcome to Shell Scripting."
```

---

### **Saving the File**

- **In `nano`:**
  - Press `Ctrl + O`, then press `Enter` to save.
  - Press `Ctrl + X` to exit.

- **In `vim`:**
  - Press `Esc`, then type `:wq` and press `Enter` to save and exit.

---

### **Granting Execution Permissions**

Check file permissions:
- ls -l filename.sh
make the script executable
- chmod +x filename.sh
Verify permission
- ls 0l filename.sh

---
### **Executing the File**

- Run the script:
```bash
./filename.sh
```
- or use the interpreter directly
```bash
bash filename.sh
```
# Understanding `chmod`

The `chmod` command in Linux and Unix systems is used to change the permissions of files and directories. Permissions dictate who can read, write, or execute a file or directory.

## **File Permissions**

Each file has three sets of permissions:

| Permission | Symbol | Binary Value | Description                     |
|------------|--------|--------------|---------------------------------|
| Read       | `r`    | `4`          | Allows viewing the file's contents. |
| Write      | `w`    | `2`          | Allows modifying the file's contents. |
| Execute    | `x`    | `1`          | Allows running the file as a program/script. |

Permissions are divided into **three groups**:

| Group       | Symbol | Applies To                              |
|-------------|--------|-----------------------------------------|
| Owner/User  | `u`    | The user who owns the file.             |
| Group       | `g`    | The group associated with the file.     |
| Others      | `o`    | All other users on the system.          |

---

## **How `chmod` Works**

### **Symbolic Mode**

Modify permissions using symbols (`r`, `w`, `x`) with operators (`+`, `-`, `=`).

#### Examples:

- Add execute permission for the owner:
  `chmod u+x file.txt`

- Remove write permission for the group:
  `chmod g-w file.txt`

- Set read-only permission for everyone:
  `chmod ugo=r file.txt`

---

### **Numeric Mode**

Permissions are represented by a 3-digit octal number (base 8). Each digit corresponds to the permission for the owner, group, and others.

#### Octal Values:
- `4` = read
- `2` = write
- `1` = execute

Combine values to set multiple permissions:
- `7` = `4` (read) + `2` (write) + `1` (execute)
- `6` = `4` (read) + `2` (write)
- `5` = `4` (read) + `1` (execute)
- `0` = No permissions

#### Examples:

- `chmod 755 file.txt` sets:
  - Owner: `7` (read, write, execute)
  - Group: `5` (read, execute)
  - Others: `5` (read, execute)

---

## **Numeric Mode Breakdown**

To calculate the permission number:

1. Assign permissions for each group (Owner, Group, Others).
2. Add the values for `r`, `w`, `x`.

#### Example: `chmod 764 file.txt`

- **Owner (7):**
  - Read (`4`) + Write (`2`) + Execute (`1`) = `7`
- **Group (6):**
  - Read (`4`) + Write (`2`) = `6`
- **Others (4):**
  - Read (`4`) = `4`

Resulting permissions:
- Owner: `rwx` (`7`)
- Group: `rw-` (`6`)
- Others: `r--` (`4`)

---

## **Permission for Admin, Groups, and Users**

### **Admin (Superuser/Root)**

The root user has unrestricted access to all files regardless of permissions. Use `sudo chmod` to change permissions as root:
`sudo chmod 700 file.txt`

---

### **Groups**

If a file is associated with a group, users in that group can access it based on group permissions.

#### Example:
`chmod 750 file.txt`

- Owner: Full access (`7`)
- Group: Read and execute (`5`)
- Others: No access (`0`)

---

### **Users (Others)**

Permissions for all users not covered by the owner or group.

#### Example:
`chmod 644 file.txt`

- Owner: Read and write (`6`)
- Group: Read-only (`4`)
- Others: Read-only (`4`)

---

## **Practical Examples**

1. **Set Full Access for Owner, Read-Only for Others:**
   `chmod 744 script.sh`

   - Owner: Read, write, execute (`7`)
   - Group: Read-only (`4`)
   - Others: Read-only (`4`)

2. **Remove Execute Permission for All:**
   `chmod a-x file.txt`

   - `a`: All users (Owner, Group, Others).
   - `-x`: Remove execute permission.

3. **Grant Write Permission to Group Only:**
   `chmod g+w file.txt`

---

## **View File Permissions**

Use the `ls -l` command to view file permissions:
`ls -l file.txt`

#### Example Output:
`-rwxr-xr-- 1 user group 1234 Dec 23 10:00 file.txt`

**Breakdown:**
- `-rwxr-xr--`: File permissions.
  - `rwx`: Owner can read, write, and execute.
  - `r-x`: Group can read and execute.
  - `r--`: Others can read only.

---

## **Summary of Common `chmod` Arguments**

| Argument         | Meaning                | Example Command        |
|------------------|------------------------|------------------------|
| `+`             | Add a permission.      | `chmod u+x file.txt`   |
| `-`             | Remove a permission.   | `chmod g-w file.txt`   |
| `=`             | Set exact permissions. | `chmod o=r file.txt`   |
| Numeric Octals  | Set permissions numerically. | `chmod 755 file.txt`  |

By combining symbolic or numeric modes, you can precisely control access to files and directories!

