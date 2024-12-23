# Shell Scripting Explained

## 1. What is Shebang (`#!/bin/bash` or `#!/bin/dash` or `#!/bin/sh`)?

### **Definition**
- The **shebang** (`#!`) is the first line in a script file that tells the system which interpreter to use to execute the script.
- It is followed by the path to the interpreter (e.g., `/bin/bash`, `/bin/sh`, `/bin/dash`, etc.).
- Without the shebang, the script might not execute correctly, or it might run using the default shell of the environment.

### **How It Works**
- When you execute a script, the operating system reads the shebang line and invokes the specified interpreter to execute the script.

### **Example of Shebang Usage**
```bash
#!/bin/bash
echo "Hello, World!"
```
When this script is executed, the system uses the **Bash** shell (`/bin/bash`) to interpret it.

---

## **2. What is `/bin`, `/bash`, `/sh`, and `/dash`?**

### **`/bin`:**
- The **`/bin` directory** (short for "binary") contains essential system binaries and executables required for the system to function.
- These executables are used by all users and scripts, including core shell interpreters like `bash`, `sh`, and `dash`.

### **`bash`:**
- **Bash** (Bourne Again Shell) is a widely used shell and command language interpreter.
- It supports advanced scripting features like arrays, functions, and arithmetic operations.
- Most Linux distributions use Bash as the default shell.

**Example Bash Script:**

```bash
#!/bin/bash
name="Alice" echo "Hello, $name"
```

### **`sh`:**
- **`sh`** (Bourne Shell) is the original Unix shell developed by Stephen Bourne.
- It is simpler and has fewer features compared to Bash.
- On modern systems, `/bin/sh` is often a symbolic link to another shell like `dash` or `bash`.

**Example `sh` Script:**
```bash
#!/bin/sh
for i in 1 2 3;
do echo "Number $i" done
```

### **`dash`:**
- **`dash`** (Debian Almquist Shell) is a modern POSIX-compliant shell known for its speed and minimalism.
- It is often used for system scripts like those in `/etc/init.d` because it is lightweight.

**Example `dash` Script:**
```bash
#!/bin/dash 
echo "This script runs using dash."
```

---

## **3. Differences Between `/bin/bash`, `/bin/sh`, and `/bin/dash`:**

| Feature/Aspect       | `/bin/bash`                            | `/bin/sh`                        | `/bin/dash`                     |
|----------------------|----------------------------------------|----------------------------------|---------------------------------|
| **Features**         | Rich scripting features like arrays, arithmetic, and functions. | Basic scripting with minimal features. | Lightweight and minimal, POSIX-compliant. |
| **Performance**      | Slower due to its additional features. | Moderate speed.                 | Faster due to simplicity.      |
| **POSIX Compliance** | Extends POSIX, includes non-standard features. | Generally POSIX-compliant.      | Strictly POSIX-compliant.      |
| **Use Case**         | Interactive shells, complex scripts.  | Legacy or minimal scripts.      | System scripts, speed-critical tasks. |

---

## **Why Use Different Shebangs?**

- Use **`#!/bin/bash`** for scripts that require advanced Bash features like arrays and string manipulation.
- Use **`#!/bin/sh`** for portable scripts that need to work across different Unix-like systems.
- Use **`#!/bin/dash`** for system scripts where speed and POSIX compliance are critical.

---

### **Example to Highlight Differences:**

#### **Script with Advanced Features:**

```bash
#!/bin/bash
# This script uses arrays (supported only in Bash)
arr=(apple orange banana)
for fruit in "${arr[@]}"; do
  echo "I like $fruit"
done
```
- If run with /bin/sh or /bin/dash, this script will fail because they do not support arrays.

#### **Simple POSIX Script:**

```bash
#!/bin/sh
# This script works with any POSIX-compliant shell
for i in 1 2 3; do
  echo "Number $i"
done
```
- This script works with /bin/bash, /bin/sh, and /bin/dash.

