---
title: Amarel Computing
layout: minimal
nav_enabled: true 
---

# Amarel Compute Cluster - General
Date: February 6, 2024 11:31 AM
---
**Table of Contents**
1. TOC
{:toc}
---

Notes:
- When making files, sure the 'group owner' is the Holmes Lab group, g_ah1491_1. To change the group owner, run in the terminal $ `chgrp g_ah1491_1 /path/to/file.ext` (or for a folder, $`chgrp -R g_ah1491_1 /path/to/folder`)
    - To see who the group owner is, run $`ls -l`. The file/folder will be listed as `rwxrwxrwx author group ...` 
- 1-2 days a month Amarel does maintenance- you can’t connect to the compute nodes, see or edit your files, and any running jobs will be paused (though they won’t be stopped). You can see when maintenance days are scheduled here: [https://oarc.rutgers.edu/amarel-system-status](https://oarc.rutgers.edu/amarel-system-status/)


## Personal Storage

Each NetID Gets personal storage of:
- **/home/NetID** > 100GB of storage, not fastest, backed up
- **/scratch/NetID** > 1TB of storage, fast, up to 2TB before purging, not backed up

### Best practices

- Move files to your /scratch directory and run your job from that location.
- Don't leave files sitting unused (unaccessed) for a long time because you may lose them to the 90 day purge process.
- Frequently check the utilization or quota for your /home and /scratch directories
to ensure that they don't become unusable due to over-filling with
files.
- The general approach for using /scratch is to copy your job's files (input files, libraries, etc.) to /scratch, run your job and write output files to /scratch, then move the files you need to save to your /home or /projects directory.

- Helpful Code Snippets:
    
    You can stage needed files in /scratch from within a job (either within your job script for a batch job or on the command line during an interactive job):
    
    ```bash
    mkdir /scratch/$USER/$SLURM_JOB_NAME-$SLURM_JOB_ID
    
    scp my-dir-of-input-files.tar.gz /scratch/$USER/$SLURM_JOB_NAME-$SLURM_JOB_ID
    
    tar -zxf /scratch/$USER/$SLURM_JOB_NAME-$SLURM_JOB_ID/my-dir-of-input-files.tar.gz
    ```
    

## Holmes Lab Storage

Holmes lab storage and user group is located in Amarel at `/projects/f_ah1491_1` 

To be added to the user group to acces this storage, email [help#oarc.rutgers.edu](mailto:help@oarc.rutgers.edu) with your NetID and CC Avram, avram.holmes@rutgers.edu. If no response, email [pgarias#oarc.rutgers.edu](mailto:pgarias@oarc.rutgers.edu) 

Storage capacity: 100TB

For file structure and norms, see:

[Filesystem Amarel Holmes Lab  ](https://www.notion.so/Filesystem-Amarel-Holmes-Lab-1c8cf00eb93680a0ac27f2b106b1b333?pvs=21)

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

### Slurm Job

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

if anything weird comes up can do `scancel <your netID>`

`sacct -e` shows all the variables you could pull up for existing/past jobs

`sacct —state`=failed, running, pending, completed

From Cluster User Guide: 

![Screen Shot 2024-02-28 at 3.08.55 PM.png](Lab Wiki - Shareable 44d5a7a0268f45af9b28447a0f314202/Slurm Jobs & Downloads eef0f4af183a432dafcf82ece18b7cd9/Screen_Shot_2024-02-28_at_3.08.55_PM.png)

## Common commands

### Sending Files to and from Amarel

Let’s assume you’re logged-in to a local workstation or laptop and not connected to Amarel. To send files from your local system to your Amarel /home directory,

```bash
scp file-1.txt file-2.txt <NetID>@amarel.rutgers.edu:/home/<NetID>
```

To pull a file from your Amarel /home directory to your laptop (note the “.” at the end of this command),

```bash
scp <NetID>@amarel.rutgers.edu:/home/<NetID>/file-1.txt .
```

If you want to copy an entire directory and its contents using scp, you’ll need to “package” your directory into a single, compressed file before moving it:

```bash
tar -czf my-directory.tar.gz my-directory
```

After moving it, you can unpack that .tar.gz file to get your original directory and contents:

```bash
tar -xzf my-directory.tar.gz
```

A handy way to synchronize a local file or entire directory between your local workstation and the Amarel cluster is to use the rsync utility. First, let's sync a local (recently updated) directory with the same directory stored on Amarel:

```bash
rsync -trlvpz work-dir gc563@amarel.rutgers.edu:/home/gc563/work-dir
```

In this example, the rsync options I'm using are:

- t (preserve modification times)
- r (recursive, sync all subdirectories)
- l (preserve symbolic links)
- v (verbose, show all details)
- p (preserve permissions)
- z (compress transferred data)

To sync a local directory with updated data from Amarel:

```bash
rsync -trlvpz <your NetID>@amarel.rutgers.edu:/home/<your NetID>/work-dir work-dir
```

Here, we've simply reversed the order of the local and remote locations.

For added security, you can use SSH for the data transfer by adding the e option followed by the protocol name (SSH, in this case):

```bash
rsync -trlvpze ssh <your NetID>@amarel.rutgers.edu:/home/<your NetID>/work-dir work-dir
```

<aside>
🛠 [**Slurm Documentation**](https://slurm.schedmd.com/documentation.html)

</aside>

<aside>
📖 [**Amarel User Guide](https://sites.google.com/view/cluster-user-guide#h.17qhrejyd98m)**

</aside>

<aside>
<img src="https://www.notion.so/icons/preview_gray.svg" alt="https://www.notion.so/icons/preview_gray.svg" width="40px" /> [**Amarel Intro and Basics - Video Tutorial](https://rutgers.mediaspace.kaltura.com/media/Weekly+Open+Workshop+-+December+17%2C+2020/1_62thyamw/171647611) (1hr)**

</aside>

[Modules available in Amarel (2024)](https://www.notion.so/Modules-available-in-Amarel-2024-b8f06cc4f631467d9c0831bf3c7b5e44?pvs=21)

### Help desk: email [help@oarc.rutgers.edu](mailto:help@oarc.rutgers.edu)

## Amarel Info:

Amarel OS: CentOS Linux release 7.9.2009 (Core) 

holmesenv modules installed:

[Modules/pkg Installed in /projects/community/holmesenv](https://www.notion.so/Modules-pkg-Installed-in-projects-community-holmesenv-c71e338a9767430c98d73dcb38b65899?pvs=21)

BASICS (From [**Amarel User Guide](https://sites.google.com/view/cluster-user-guide#h.17qhrejyd98m))**: 

## Cluster User Guide:

[Overview](https://sites.google.com/view/cluster-user-guide#h.q5kh60n6t6zy)

[Getting access (requesting an account)](https://sites.google.com/view/cluster-user-guide#h.17klxqb62i99)

[Boilerplate for proposal development](https://sites.google.com/view/cluster-user-guide#h.bbhiax138gnp)

[Acknowledging OARC or Amarel](https://sites.google.com/view/cluster-user-guide#h.clzlpvemkoi5)

[User environment](https://sites.google.com/view/cluster-user-guide#h.17qhrejyd98m)

[Login nodes (proper use)](https://sites.google.com/view/cluster-user-guide#h.6ruev1yb6cb)

[Granting access to files and folders for other users](https://sites.google.com/view/cluster-user-guide#h.wz5eolaevxv9)

[Applications and libraries](https://sites.google.com/view/cluster-user-guide#h.hokil5r3nnq4)

[Installing your own software](https://sites.google.com/view/cluster-user-guide#h.3wg2loo92bhn)

[Available compute hardware](https://sites.google.com/view/cluster-user-guide#h.kyrykrouyxxz)

[Job partitions (job submission queues)](https://sites.google.com/view/cluster-user-guide#h.oeejy9yf80e4)

[Connecting to the cluster](https://sites.google.com/view/cluster-user-guide#h.6bb8ylmm9bzz)

[Command-line access via SSH](https://sites.google.com/view/cluster-user-guide#h.z2yzkhdnjk82)

[Using the Open OnDemand interface](https://sites.google.com/view/cluster-user-guide#h.z6biscu53ldl)

[Using the FastX interface](https://sites.google.com/view/cluster-user-guide#h.jsnqsekyy1u6)

[Storage file sets and how to use them](https://sites.google.com/view/cluster-user-guide#h.28elrlg2ux9g)

[/home](https://sites.google.com/view/cluster-user-guide#h.d15j83outs5z)

[/scratch](https://sites.google.com/view/cluster-user-guide#h.t618y9lhk7u9)

[/projects](https://sites.google.com/view/cluster-user-guide#h.ljrl328mzer9)

[/mnt/scratch](https://sites.google.com/view/cluster-user-guide#h.63fiubi0rljz)

[Home and Projects Snapshots](https://sites.google.com/view/cluster-user-guide#h.fx1d4cvdwed3)

[Best practices](https://sites.google.com/view/cluster-user-guide#h.72v51025o4ja)

[Basics of moving files to/from the cluster](https://sites.google.com/view/cluster-user-guide#h.3jyxmx35y8y2)

[Transferring files with external institute using cloud bucket](https://sites.google.com/view/cluster-user-guide#h.dbytkcny0aip)

[With GCP](https://sites.google.com/view/cluster-user-guide#h.d4yd0653roo5)

[With AWS](https://sites.google.com/view/cluster-user-guide#h.omfmnbxkx74k)

[Transferring files using Globus Personal Connect](https://sites.google.com/view/cluster-user-guide#h.sndo8v81d03c)

[Transferring files to cloud storage using rclone](https://sites.google.com/view/cluster-user-guide#h.zgtvv015l57n)

[Setting-up your rclone configuration on Amarel](https://sites.google.com/view/cluster-user-guide#h.x36410dl5ede)

[Using rclone to move files](https://sites.google.com/view/cluster-user-guide#h.7q3loifijbjs)

[Splitting large files](https://sites.google.com/view/cluster-user-guide#h.og2qx4q6913s)

[Passwordless access and file transfers using SSH keys](https://sites.google.com/view/cluster-user-guide#h.jgwrkm9e9rwg)

[Job scheduler (batch system)](https://sites.google.com/view/cluster-user-guide#h.p4379j6lgjuh)

[Current configuration](https://sites.google.com/view/cluster-user-guide#h.uf94ou58xx4)

[Serial job example](https://sites.google.com/view/cluster-user-guide#h.dbi0w5juf4x)

[Parallel (multicore MPI) job example](https://sites.google.com/view/cluster-user-guide#h.sb7j0wpf9irf)

[Interactive job example](https://sites.google.com/view/cluster-user-guide#h.26x9sbburvsg)

[Parallel interactive job example](https://sites.google.com/view/cluster-user-guide#h.8m11azm33quv)

[Job array example](https://sites.google.com/view/cluster-user-guide#h.ge8wh4qyffca)

[Some helpful tips](https://sites.google.com/view/cluster-user-guide#h.571s1axqevdj)

[Monitoring job status](https://sites.google.com/view/cluster-user-guide#h.4bsndqufii8p)

[Actively running jobs](https://sites.google.com/view/cluster-user-guide#h.q2jwsgupcfav)

[Completed or terminated jobs](https://sites.google.com/view/cluster-user-guide#h.w7jwa95gq7yy)

[Cancelling jobs](https://sites.google.com/view/cluster-user-guide#h.5weq73pbxbk0)

[Connecting your lab's systems to Amarel](https://sites.google.com/view/cluster-user-guide#h.sc8js9m67xet)

[Checking storage utilization](https://sites.google.com/view/cluster-user-guide#h.kc5vkty50xan)

[Snapshots of /home and /projects data](https://sites.google.com/view/cluster-user-guide#h.6iwoh91v5af6)

[FAQ](https://sites.google.com/view/cluster-user-guide#h.7wm69kjuc9z5)

Terminal Commands

[Helpful bash script lines](https://www.notion.so/Helpful-bash-script-lines-cfb5aa83a8104a6dafffb188fa7227ba?pvs=21)

```bash
conda activate /projects/community/holmesenv #activate holmesenv conda
cd /home/netID #change working directory
ls #contents of wd
tree #structure of files within wd 
cd .. #goes to parent dir
mkdir dirName #make directory
rm filename #remove file
mv /sourceDir /movingLocation
cat file.extension #displays file contents 
vim file.extension #like cat but with scroll
sacct #see all the jobs you're running
#optional specifications for sacct:
sacct --format=JobId,JobName%50,Partition%15,State,Elapsed,ExitCode,Start,End --starttime=2024-06-08T22:43:21
watch -n 1 squeue -u netID # View in real time all the jobs you're running
			#ctrl+C to exit

```

```bash

#Use terminal packages
module use /projects/community/modulefiles
module load FreeSurfer/7.4.1-ez82
module load fsl/6.0.0-gc563
```

Notes
