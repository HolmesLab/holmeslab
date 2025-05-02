---
title: Update to New Python in Amarel
nav_order: 5
nav_enabled: true 
parent: Amarel Computing
---


# Update to New Python in Amarel
Date: April 3, 2025 4:06 PM
---
**Table of Contents**
1. TOC
{:toc}
---


Since we don’t have sudo privileges, this is how to update Python or install a specific version in your local user space on Amarel: 

    
1. **Install a new Python version using Conda:**
Once Conda is installed, you can create a new environment with the desired Python version. For example, to create an environment with Python 3.9:
    
    ```bash
    conda create --name myenv python=3.9
    ```
    
3. **Activate the environment:**
Activate the new environment:
    
    ```bash
    conda activate myenv
    ```
    
4. **Verify the Python version:**
Check the active Python version:
    
    ```bash
    python --version
    ```
    
    This should show Python 3.9 (or whichever version you specified).
    

### **Step 2: Update `python3` to Point to the Correct Version**

Of seems like `pip3` is pointing to the correct version of Python, but `python3` is still pointing to an incorrect version, you'll need to update your shell.

### **1. Check Python Binaries**

First, verify the location of the Python binary that your shell is using:

```bash
which python3
```

This should return the path to your current `python3` binary. It may still point to the older version (e.g., `/usr/bin/python3`).

### **2. Update `python3` to Point to the Correct Version**

You can set `python3` to point to your newly installed Python (3.12.8 in this case). If the newly installed Python version is located in `/home/kj537/python3.12.8/bin/python3`, you can create a symbolic link:

```bash
ln -sf /home/kj537/python3.12.8/bin/python3 /usr/bin/python3
```

However, this requires root (sudo) privileges to modify `/usr/bin/`. Since you don’t have `sudo` privileges, you can create the symlink in your home directory:

```bash
ln -sf /home/kj537/python3.12.8/bin/python3 /home/kj537/bin/python3
```

Then, add `/home/kj537/bin` to your `PATH` in `~/.bashrc` (or the appropriate shell config file):

```bash
echo 'export PATH="/home/kj537/bin:$PATH"' >> ~/.bashrc
```

Afterward, source your `.bashrc` file:

```bash
source ~/.bashrc
```

Now, `python3` should point to the correct version. Check it by running:

```bash
python3 --version
```

It should now show `Python 3.12.8`.

### **3. Verify the Setup**

Finally, verify both Python and pip are updated:

```bash
python3 --version
pip3 --version
```

Both should point to the correct version.