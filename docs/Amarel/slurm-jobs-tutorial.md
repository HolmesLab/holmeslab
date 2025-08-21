---
title: Slurm Jobs Tutorial
nav_order: 4
nav_enabled: true 
parent: Amarel Computing
---

# Slurm Jobs Tutorial - Rutgers
Job scheduler (batch system)

The job scheduler used on OARC-managed clusters is SchedMD's SLURM Workload Manager.

Any memory-intensive or compute-intensive process should be run using scheduled resources and not simply run on one of our shared login nodes. In short, do not run applications on the login nodes.


## Basic Slurm Job Example:

1. Create a script named <NAME>.sh (make sure to add #!/bin/bash  at top)
2. Fill in this with your specs

```bash
#! /bin/bash
#SBATCH --partition=p_dz268_1
#SBATCH --job-name=<some job name>.sh 
#SBATCH --requeue
#SBATCH --nodes=1 
#SBATCH --ntasks=1
#SBATCH --cpus-per-task=1
#SBATCH --mem=2000
#SBATCH --time=*48:00:00*
#SBATCH --output=/path/to/folder/<some job name>.out 
#SBATCH --error=/path/to/folder/<some job name>.err

module purge

# Activate the holmesenv virtual environment to use installed packages
# if you need additional packages for your script, install them into /holmesenv/bin/activate
source ~/projects/community/holmesenv/bin/activate

eval "$(conda shell.bash hook)"  # Properly initialize Conda
conda activate /projects/community/holmesenv

bash /path/to/your/file/<filename>.sh    
#OR 
python3 /path/to/your/file/<filename>.py
```

1. then save that whole script as run_NAME.sh (even if the file running is python)
2. then do this to make both files executable
    
    ```bash
    chmod +x NAME.py
    chmod +x run_NAME.sh
    ```
    
3. then run

```bash
sbatch run_NAME.sh
```

### Slurm Jobs Tutorial - In Depth
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
    
![Screen Shot 2024-03-21 at 10.38.41 AM.png](Slurm Jobs Tutorial - Rutgers f8f32e7fadf34f62a258fdd5c1080ed7/Screen_Shot_2024-03-21_at_10.38.41_AM.png)
    
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
![Screen Shot 2024-02-28 at 3.08.55 PM.png](Slurm Jobs Tutorial - Rutgers f8f32e7fadf34f62a258fdd5c1080ed7/Screen_Shot_2024-03-21_at_10.42.55_AM.png)

**Troubleshooting:**
- open error files via:
    ```bash
    cd /dir/where error file is/
    vi slurm.most.recent.err
    ```
    the top line will be the reasoning
- check permissions
- check everything is in the right folders

**Tips:**
- if anything weird comes up can do `scancel <job number>`
- `sacct -e` shows all the variables you could pull up for existing/past jobs
    - —state=failed, running, pending, completed
- try it with one subject, see time, multiply by subjects = time estimate


### OARC Tutorials
- [Job partitions (job submission queues)](https://sites.google.com/view/cluster-user-guide#h.oeejy9yf80e4)
- [Job scheduler (batch system)](https://sites.google.com/view/cluster-user-guide#h.p4379j6lgjuh)
- [Current configuration](https://sites.google.com/view/cluster-user-guide#h.uf94ou58xx4)
- [Serial job example](https://sites.google.com/view/cluster-user-guide#h.dbi0w5juf4x)
- [Parallel (multicore MPI) job example](https://sites.google.com/view/cluster-user-guide#h.sb7j0wpf9irf)
- [Interactive job example](https://sites.google.com/view/cluster-user-guide#h.26x9sbburvsg)
- [Parallel interactive job example](https://sites.google.com/view/cluster-user-guide#h.8m11azm33quv)
- [Job array example](https://sites.google.com/view/cluster-user-guide#h.ge8wh4qyffca)
- [Some helpful tips](https://sites.google.com/view/cluster-user-guide#h.571s1axqevdj)
- [Monitoring job status](https://sites.google.com/view/cluster-user-guide#h.4bsndqufii8p)
- [Actively running jobs](https://sites.google.com/view/cluster-user-guide#h.q2jwsgupcfav)
- [Completed or terminated jobs](https://sites.google.com/view/cluster-user-guide#h.w7jwa95gq7yy)
- [Cancelling jobs](https://sites.google.com/view/cluster-user-guide#h.5weq73pbxbk0)
- [Rutgers Slurm Job / Batch User Guide](https://sites.google.com/view/cluster-user-guide#h.p4379j6lgjuh)


