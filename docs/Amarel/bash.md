---
title: Helpful Bash Commands
nav_order: 10
nav_enabled: true 
parent: Amarel Computing
---

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