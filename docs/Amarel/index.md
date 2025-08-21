---
title: Amarel Computing
layout: minimal
nav_enabled: true 
---

# Amarel Compute Cluster - General
## For file system: read the [Holmes Lab File Structure and Norms](https://holmeslab.github.io/holmeslab/docs/Policies/filesystem-amarel/) page
## For how to connect to and use Amarel: read the [Using Amarel](https://holmeslab.github.io/holmeslab/docs/Amarel/connect-amarel/) page
## For Slurm Jobs instructions: read the [Slurm Jobs](https://holmeslab.github.io/holmeslab/docs/Amarel/slurm-jobs-tutorial/) page
## For transferring files: read the [Transferring Files to Amarel](https://holmeslab.github.io/holmeslab/docs/Amarel/sending-files/) page




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

### Slurm Jobs
Slurm jobs (sending jobs to be run in the compute cluster) should be used for everything EXCEPT downloads from the internet. Downloads from the internet should be run in login nodes (see below). Non-download jobs should all be packaged and run via slurm in the compute nodes

1. Save your script as a scriptname.sh file (or if it’s a python script, scriptname.py)
2. Create shell script
    1. Open a new file in text editor (BBEdit, Textedit, VSCode, etc.)
    2. paste this code:
    
    ```bash
    #!/bin/bash
    
    #SBATCH --partition=p_dz268_1
    #SBATCH --job-name=name.sh 
    #SBATCH --cpus-per-task=9
    #SBATCH --mem=1G
    #SBATCH --time=2-00:00:00
    #SBATCH --output=/path/batch_jobs/out/name_%A.out
    #SBATCH --error=/path/batch_jobs/err/name_%A.err
    
    module purge
    
    # Activate the holmesenv virtual environment to use installed packages
    eval "$(conda shell.bash hook)"  # Properly initialize Conda
    conda activate /projects/community/holmesenv #change to whatever conda env you need
    
    # Run the Python script (or bash)
    python3 /projects/f_ah1491_1/analysis_tools/script.py
    ```
    
    - Change time=48:00:00 to however much time you think you’ll need. Max to request is 2 weeks, but the more time you request the longer your slurm job will sit in the queue before running.
        - To estimate timing, try downloading 1 subject file and time how long the download takes, then multiply that by number of subjects
    - Change `python3 /projects/f_ah1491_1/analysis_tools/script.py` to whatever the script you want to run is
    - change `/projects/community/holmesenv` to whatever conda you need, or keep this as default
    - change #SBATCH --output and —err paths
        - if you have a name like ‘name.out’, that is not changing based on job, it will override each time you run this job, so the err and out file will only be from the most recent run
        - if you want to save the err and out file from each run, have the name like name_%A.out
            - %A = job ID
                - IMPORTANT if running a job array
        - other ways to name:
            - %N = node
            - %j = job allocation number
            - %a = array index
- change #SBATCH --job-name=[name.sh](http://name.sh/) to a name you want to see on the ‘Running jobs’ when you call sacct
    - make it short— sacct or watch only allows you to see the first 8 characters of this name
    - Doesn’t need to be consistent with anything else
    - can also have the % options listed above,
        - IMPORTANT if running a job array

3. Save this file as a run_scriptname.sh file, naming it something relevant to the package + shell

1. Make sure both .sh files are in the SAME folder in your home directory, or *somewhere in amarel*, not on your local computer
    
    ![Screen Shot 2024-03-21 at 10.38.41 AM.png](Lab Wiki - Shareable 44d5a7a0268f45af9b28447a0f314202/Slurm Jobs & Downloads eef0f4af183a432dafcf82ece18b7cd9/Screen_Shot_2024-03-21_at_10.38.41_AM.png)
    
2. open terminal ($ indicates terminal entry)
    1. $ `cd /home/netID/folder...` ← replace with wherever your run_scriptname.sh files are saved
    2. $ `chmod ugo+rwx filename.ext`    `chmod ugo+rwx run_filename.ext` 
    3. $ `chmod ugo+rwx dirname`
    4. $ `sbatch run_filename.sh`
3. check in terminal using `sacct` to see if your job worked
    1. Make sure state says “Running”
    2. *2 days a month is maintenance, so jobs will say “failed” during those times. Maintenance calendar:* [https://oarc.rutgers.edu/amarel-system-status/](https://oarc.rutgers.edu/amarel-system-status/) 

Helpful commands
- if anything weird comes up can do `scancel <your netID>`
- `sacct -e` shows all the variables you could pull up for existing/past jobs
- `sacct —state`=failed, running, pending, completed

From Cluster User Guide: 
![Screen Shot 2024-02-28 at 3.08.55 PM.png](Lab Wiki - Shareable 44d5a7a0268f45af9b28447a0f314202/Slurm Jobs & Downloads eef0f4af183a432dafcf82ece18b7cd9/Screen_Shot_2024-02-28_at_3.08.55_PM.png)

## Common commands


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
