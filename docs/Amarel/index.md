---
title: Amarel Computing
layout: minimal
nav_enabled: true 
---

# Amarel Compute Cluster - General
- ### [Holmes Lab File Structure and Norms](https://holmeslab.github.io/holmeslab/docs/Policies/filesystem-amarel/) 
- ### [How to connect to and use Amarel](https://holmeslab.github.io/holmeslab/docs/Amarel/connect-amarel/) 
- ### [Slurm Jobs Overview and Tutorials](https://holmeslab.github.io/holmeslab/docs/Amarel/slurm-jobs-tutorial/) 
- ### [Holmes Lab Conda environment instructions](https://holmeslab.github.io/holmeslab/docs/Amarel/holmes-conda/) 
- ### [Transferring Files to Amarel](https://holmeslab.github.io/holmeslab/docs/Amarel/sending-files/) 



---
**Table of Contents**
1. TOC
{:toc}
---


Notes:
- When making files, sure the 'group owner' is the Holmes Lab group, g_ah1491_1. To change the group owner, run in the terminal $ `chgrp g_ah1491_1 /path/to/file.ext` (or for a folder, $`chgrp -R g_ah1491_1 /path/to/folder`)
    - To see who the group owner is, run $`ls -l`. The file/folder will be listed as `rwxrwxrwx author group ...` 
- 1-2 days a month Amarel does maintenance- you can’t connect to the compute nodes, see or edit your files, and any running jobs will be paused (though they won’t be stopped). You can see when maintenance days are scheduled here: [https://oarc.rutgers.edu/amarel-system-status](https://oarc.rutgers.edu/amarel-system-status/)


### Permissions
Example: Using `getfacl` to view the current permissions for ‘examplescript’. 
Using `setfacl` to provide user ‘netID’ read, write, and execute (`rwx`) permissions to ‘examplescript’.

```bash
getfacl examplescript
setfacl -m u:netID:rwx examplescript
```

To see what permissions you have in a directory, you can do
```bash
ls -ld /home/netID
```
OARC Resources:
- [Granting access to files and folders for other users](https://sites.google.com/view/cluster-user-guide#h.wz5eolaevxv9)

### Help desk: email [help@oarc.rutgers.edu](mailto:help@oarc.rutgers.edu)

## Amarel Info:
Amarel OS: CentOS Linux release 7.9.2009 (Core) 


## Resources from OARC:
### How to use Amarel:
- [Applications](https://sites.google.com/view/cluster-user-guide#h.hokil5r3nnq4) (Conda, Singularity, Python, R)
- [User Guide](https://sites.google.com/view/cluster-user-guide/) (Policies, Storage, Slurm, File transferring)
- [Beginner Information Hub](https://resources.cs.rutgers.edu/docs/new-users/beginners-info/) - Linux, Bash, Code Editors, etc
- [Getting access (requesting an account)](https://sites.google.com/view/cluster-user-guide#h.17klxqb62i99)
- [User environment](https://sites.google.com/view/cluster-user-guide#h.17qhrejyd98m)

### Using Compute Notes
- [Connecting to the cluster](https://sites.google.com/view/cluster-user-guide#h.6bb8ylmm9bzz)
- [Login nodes (proper use)](https://sites.google.com/view/cluster-user-guide#h.6ruev1yb6cb)
- [Available compute hardware](https://sites.google.com/view/cluster-user-guide#h.kyrykrouyxxz)


### Using Software
- [Installing your own software](https://sites.google.com/view/cluster-user-guide#h.3wg2loo92bhn)
- [Connecting your lab's systems to Amarel](https://sites.google.com/view/cluster-user-guide#h.sc8js9m67xet)


[FAQ](https://sites.google.com/view/cluster-user-guide#h.7wm69kjuc9z5)
