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


Since we don’t have sudo privileges, this is how to update Python in your local user space on Amarel: 

### **Installing Python from Source (without `sudo` privileges)**

1. **Download the Python source code:**
Go to the [official Python website](https://www.python.org/downloads/) and find the version you want to install. Alternatively, you can use `wget` or `curl` to download it directly. For example:
    
    ```bash
    wget https://www.python.org/ftp/python/3.9.6/Python-3.9.6.tgz
    ```
    
2. **Extract the tarball:**
Once the file is downloaded, extract it using the following command:
    
    ```bash
    tar -xvzf /path/to/Python-3.9.6.tgz
    ```
    
3. **Navigate to the Python directory:**
Change to the directory of the extracted Python source code:
    
    ```bash
    cd Python-3.9.6
    ```
    
4. **Configure the installation:**
Configure the installation to install Python in your home directory (or any directory you have write access to):
    
    ```bash
    ./configure --prefix=$HOME/python3.9
    ```
    
    This will configure the build process to install Python in `~/python3.9` (you can change this to any path you prefer).
    
5. **Build and install Python:**
Compile and install Python:
    
    ```bash
    make
    make install
    ```
    
    This will take some time, depending on your system.
    
6. **Add the new Python version to your PATH:**
Once the installation is complete, add the `bin` directory of the installed Python version to your PATH. Open your `.bashrc` or `.zshrc` file and add the following line:
    
    ```bash
    export PATH=$HOME/python3.9/bin:$PATH
    ```
    
    Then, reload the shell configuration:
    
    ```bash
    source ~/.bashrc  # or source ~/.zshrc
    ```
    
7. **Verify the installation:**
Check the Python version to verify that the new version is being used:
    
    ```bash
    python3 --version
    ```
    
    If you installed Python 3.9, you should see something like:
    
    ```
    Python 3.9.6
    ```
    

### **Method 2: Using `pyenv` (Recommended)**

`pyenv` is a popular tool for managing multiple Python versions without needing `sudo` privileges.

1. **Install `pyenv`:**
If `pyenv` is not already installed, you can install it by running the following commands:
    
    ```bash
    curl https://pyenv.run | bash
    ```
    
    After the installation is complete, add the following to your `.bashrc` or `.zshrc` file to set up the `pyenv` environment:
    
    ```bash
    export PATH="$HOME/.pyenv/bin:$PATH"
    eval "$(pyenv init --path)"
    eval "$(pyenv init -)"
    ```
    
    Then, reload your shell:
    
    ```bash
    source ~/.bashrc  # or source ~/.zshrc
    ```
    
2. **Install a new Python version using `pyenv`:**
With `pyenv`, you can install any version of Python that is available. For example, to install Python 3.9.6:
    
    ```bash
    pyenv install 3.9.6
    ```
    
3. **Set the global Python version:**
After the installation, set the newly installed version as the global default:
    
    ```bash
    pyenv global 3.9.6
    ```
    
4. **Verify the new Python version:**
Check the active Python version:
    
    ```bash
    python --version
    ```
    
    This should return the Python version you installed using `pyenv`.
    

### **Method 3: Using Miniconda or Anaconda (if available)**

If you have the option to install Conda (Miniconda or Anaconda), you can manage multiple Python versions in isolated environments without requiring `sudo` privileges.

1. **Download Miniconda (for example):**
You can download Miniconda from the official website or use the following command to install it in your home directory:
    
    ```bash
    wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
    bash Miniconda3-latest-Linux-x86_64.sh
    ```
    
    Follow the installation prompts, and make sure to allow the installer to initialize Conda.
    
2. **Install a new Python version using Conda:**
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
    

---

Using `pyenv` or installing Python from source are typically the most flexible methods, but if you need an isolated environment, Miniconda or Conda is a good option too. Let me know if you need help with any of these methods!

### **Step 2: Update `python3` to Point to the Correct Version**

It seems like `pip3` is pointing to the correct version of Python, but `python3` is still pointing to the old version (3.6.4). This can happen if multiple versions of Python are installed, and the shell is using the system's default Python version instead of the one you installed manually.

Here's how to update your `python3` version:

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

### **3. Update `python3` Using `update-alternatives` (Optional)**

If you have multiple versions of Python installed and are using a system with `update-alternatives` (common on Debian-based systems), you can set the default version using:

```bash
sudo update-alternatives --install /usr/bin/python3 python3 /home/kj537/python3.12.8/bin/python3 1
```

But again, this requires `sudo` privileges, which you don't have.

### **4. Verify the Setup**

Finally, verify both Python and pip are updated:

```bash
python3 --version
pip3 --version
```

Both should point to the new version (Python 3.12.8).