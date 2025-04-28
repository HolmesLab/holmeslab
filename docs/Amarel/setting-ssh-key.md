---
title: SSH Keys
nav_order: 3
nav_enabled: true 
parent: Amarel Computing
---


# SSH Key

Date: March 31, 2025 2:57 PM

You need to set up SSH key-based authentication on your Mac. Follow these steps:

### **1. Generate an SSH Key (if you don’t have one)**

Open the terminal and run:

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

```

- When prompted for a file to save the key, press **Enter** to accept the default (`~/.ssh/id_rsa`).
- If you want to avoid entering a passphrase, just press **Enter** when prompted.

### **2. Copy the Public Key to the Remote Server**

Run:

```bash
ssh-copy-id user@remote_host

```

- Replace `user` with your remote username and `remote_host` with the remote machine’s address.
- If `ssh-copy-id` is not available, use:

```bash
cat ~/.ssh/id_rsa.pub | ssh user@remote_host "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"

```

### **3. Set Correct Permissions**

Ensure the correct permissions on the remote machine:

```bash
ssh user@remote_host
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
exit

```

### **4. Test Passwordless SSH**

Try logging in without a password:

```bash
ssh user@remote_host

```

If it logs you in without asking for a password, you're all set! 🚀