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


`./` = current directory

`..` = parent directory

**`pwd`=** print working dir

**`cd /'dir'` =** change wd to specified dir

**`cd ..`** = change wd to parent directory

**`cd -`** = will go back to the directory you were last in 

**`ls`** = prints all the files in current dir

**`echo`** = returns whatever is after echo (or in quotes for stuff w spaces in it)

**`cat`** = display contents of files, concatenate (if multiple listed)

**`vim`** or `vi` = displays contents, like cat, but with additional features (scrolling, etc.)

`:q` gets you out of the vim viewer

**`cat ‘file’` =** prints the contents of a file

**`xdg-open** ‘file’` = 

**`~`** = home directory

**`<fn> -l`** = will give you more info on that function

**`ls -l`** = returns the permissions you have on the working directory
**`chmod +x <script.sh`>** = gives execute permissions to script.sh 

**`chmod ugo+rwx <script.sh`>** = change your permissions in a folder to read-write-execute 

**`mv /dir` =** moves a file

**`mkdir`** = make a new directory

**`rm`** = remove file (theres no undo)

**`cp`** 
`rsync [options] <source_file> <destination_directory>` = copy files; [options]: These are optional flags that modify the behavior of `rsync`. Some common options include `-a` (archive mode, preserves permissions and other attributes), `-v` (verbose output), `-r` (recursively copy directories), and `-u` (update only, skip files that are newer in the destination).

- rsync is recommended for larger files

**`>`** = specifies where you want the output of that command to be saved/to go

**`x | y`** = makes the *output* of x the *input* of 

**`sudo`** = runs the next command as the Root / Super User (can’t run multiple commands w/o shell) 

- `sudo su` = run root as shell
- dangerous

**`tee`** = takes its input, and writes it to a (specific?) file, and prints it out

**`tail`** = print __ of the last output

**`tail -n1`** = print the last 1 line of the last output

**`./script.sh`** = will run script.sh in current directory

**`python script.py`** = run script.py in python