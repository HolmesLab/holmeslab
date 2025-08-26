---
title: Amarel Storage and File Structure
parent: Amarel Computing
nav_enabled: true 
nav_order: 5
---

# Storage and File Structure
## Holmes Lab Storage
Holmes lab storage and user group is located in Amarel at `/projects/f_ah1491_1` 


To be added to the user group to acces this storage, email [help#oarc.rutgers.edu](mailto:help@oarc.rutgers.edu) with your NetID and CC Avram, avram.holmes@rutgers.edu. If no response, email [pgarias#oarc.rutgers.edu](mailto:pgarias@oarc.rutgers.edu) 


### NOTE: 
To access the Holmes Lab files from Jupyter Notebook in Amarel, you must create symlinks to the project and scratch directories. 

The formula for creating a symlink is:
`ln -s /path/to/original /path/to/symlink`. For example: 

```bash
ln -s /projects/f_ah1491_1 ~/projects_f_ah1491_
```

This will create a folder in your home directory called `projects_f_ah1491_1` that links to the Holmes Lab project directory. **You can call the link any name**. You can do the same for the scratch directory:
```bash
ln -s /scratch/f_ah1491_1 ~/scratch_f_ah1491_
```

Again, you can name it 'scratch_f_ah1491_' or any name you want.


# Read the [Holmes Lab File Structure and Norms](https://holmeslab.github.io/holmeslab/docs/Policies/filesystem-amarel/) page

## Holmes Lab Storage
- **/projects/f_ah1491_1** > 100TB of storage, backed up -- 5 million files
- **/scratch/f_ah1491_1** > 100TB of storage, NOT backed up, no filecount limit
For more information see the [Holmes Lab File Structure and Norms](https://holmeslab.github.io/holmeslab/docs/Policies/filesystem-amarel/) page.

## Personal Storage
Each NetID Gets personal storage of:
- **/home/NetID** > 100GB of storage, not fastest, backed up
- **/scratch/NetID** > 1TB of storage, fast, up to 2TB before purging, not backed up



### Storage Info from OARC
- [Storage file sets and how to use them](https://sites.google.com/view/cluster-user-guide#h.28elrlg2ux9g)
- [/home](https://sites.google.com/view/cluster-user-guide#h.d15j83outs5z)
- [/scratch](https://sites.google.com/view/cluster-user-guide#h.t618y9lhk7u9)
- [/projects](https://sites.google.com/view/cluster-user-guide#h.ljrl328mzer9)
- [/mnt/scratch](https://sites.google.com/view/cluster-user-guide#h.63fiubi0rljz)
- [Home and Projects Snapshots](https://sites.google.com/view/cluster-user-guide#h.fx1d4cvdwed3)
- [Checking storage utilization](https://sites.google.com/view/cluster-user-guide#h.kc5vkty50xan)
- [Snapshots of /home and /projects data](https://sites.google.com/view/cluster-user-guide#h.6iwoh91v5af6)



### Storage Best practices
- Move files to your /scratch directory and run your job from that location.
- Don't leave files sitting unused (unaccessed) for a long time because you may lose them to the 90 day purge process.
- Frequently check the utilization or quota for your /home and /scratch directories
to ensure that they don't become unusable due to over-filling with
files.
- The general approach for using /scratch is to copy your job's files (input files, libraries, etc.) to /scratch, run your job and write output files to /scratch, then move the files you need to save to your /home or /projects directory.

- Helpful Code Snippets:
You can stage needed files in /scratch from within a job (either within your job script for a batch job or on the command line during an interactive job)
    ```bash
    mkdir /scratch/$USER/$SLURM_JOB_NAME-$SLURM_JOB_ID
    
    scp my-dir-of-input-files.tar.gz /scratch/$USER/$SLURM_JOB_NAME-$SLURM_JOB_ID
    
    tar -zxf /scratch/$USER/$SLURM_JOB_NAME-$SLURM_JOB_ID/my-dir-of-input-files.tar.gz
    ```