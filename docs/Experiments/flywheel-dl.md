---
title: Download Data from Flywheel
parent: Running Experiments
nav_enabled: true
---
# Downloading Data from Flywheel 

---
**Table of Contents**
1. TOC
{:toc}
---

# Downloading fMRIPrep Data
1. Log into Amarel
2. Make sure your profile is set up to automatically activate the Holmes Lab Conda environment. 
  - Go to your terminal, and run:
```bash
$ nano ~/.bashrc
```
  - Add the following lines to your bashrc-- this will mean that every time you sign into Amarel, your account will automatically activate the Holmes Lab Conda. Thus, any slurm scripts will also use the Holmes Lab Conda
  
```bash
# Set up for conda
. /projects/community/py-data-science-stack/5.1.0/kp807/etc/profile.d/conda.sh

# Activate conda
source /projects/community/py-machine-learning/intel18/cuda12/pgarias/etc/profi$
conda activate /projects/community/holmesenv
```
3. In terminal or the Amarel OnDemand GUI ()

# Downloading Specific Data: The `fw download` Command

Sessions, acquisitions, and files can be downloaded individually using the `fw download` command.

### Usage

```bash
fw download [-h] [--config-file CONFIG_FILE | --no-config] [-y] 
[--ca-certs CA_CERTS] [--timezone TIMEZONE] [--debug | --quiet][-o [OUTPUT]] [-p PREFIX] [-i INCLUDE] [-e EXCLUDE] <source-path>
```

### Arguments

| Argument | Description |
| --- | --- |
| `source-path` | REQUIRED: The location of the file on your Flywheel instance. For example [fw://group/project/subject/acquisition/attachments] |
| `-i FILE_TYPE`, `--include FILE_TYPE` | Download only files with the specified types.* |
| `-e FILE_TYPE`, `--exclude FILE_TYPE` | Ignore files with the specified types.* |
| `-o`, `--output file name` | Name of the folder where the data is downloaded |
| `-p PREFIX`, `--prefix PREFIX` | Prefix for downloaded directory structure |


For a full, up-to-date list of options, run the following from your command line:

`fw download --help`

- [Learn more about file types in Flywheel](https://docs.flywheel.io/user/upload/user_file_types_in_flywheel/)


### Example: Downloading Acquisition Files

Below is an example of how to download a particular subject:

### Find the files
1. Find which group you need files from. You can return all the "groups" you're a part of (and your permissions) by running run `fw ls`. The Holmes Lab "group" in flywheel is `022`, so it may say:

  $ `fw ls`
  Output: `rw   022`
    
2. Next, figure out what "project" they're in. Running `fw ls 022` will return all the projects in the Holmes Lab group
```bash
[netID@amarel ~]$ fw ls 022
rw   Napls       
rw   PCX         
rw   ConteCenter 
```
3. See what data is availabe in the project you're interested in. For example
```bash
[kj537@amarel2 ~]$ fw ls 022/Napls
rw                          analyses/bids-pre-curate 05/03/2025 17:41:29 
rw                          analyses/curate-bids 05/03/2025 17:47:15     
rw     5B May 03 2025 22:47 files/README.txt                             
rw   200B May 03 2025 22:47 files/dataset_description.json               
rw  1.1KB May 03 2025 22:47 files/participants.txt                       
rw                          sub-NDARZN877YYQ                             
rw                          sub-NDARZP892XY9                             
rw                          sub-NDARZW884MZC          
```
4. You can investigate the contents of subjects (acquisition files) or specific analyses. For example

```bash
[kj537@amarel2 ~]$ fw ls "022/ConteCenter/PCR2Pilot/001/analyses/bids-fmriprep 03/14/2025 11:22:35"
files/bids_tree.html
files/bids-fmriprep_001_67d449d202be158786fab2d3.zip
files/fmriprep_log.txt
files/sub-PCR2Pilot.html.zip
```


### Download the files

To download files, run `fw download /path/to/files`. 

```bash
[kj537@amarel2 ~]:~ AvaAnderson$ fw download "022/ConteCenter/PCR2Pilot/001/analyses/bids-fmriprep 03/14/2025 11:22:35"
This download will be about 218 KB comprising 4 files.
Continue? (yes/no): yes
Wrote 218 MB to 2025 11:22:35.tar
```

# Downloading BIDS Files: The `fw export bids` Command

To download the BIDS versions of files (ie the output of the BIDS Curation gear), you don't use the `fw download` on the BIDS Curation analysis. That will just download the acquisitions.tsv and other tsvs which were the outputs of that gear. To download the files in BIDS format, use the `fw export bids` command.

The formula is:
`fw export bids -p "<project>" -g "<group>" /path/to/destination/folder`

For the Holmes Lab: 
group = 022
project = ConteCenter, PCX, Napls, ...

So a download command may look like: 
```bash
fw export bids -p "ConteCenter" -g "022" ~/flywheel_download
```
You can also download specific subjects, using the --subject flag. For example:
```bash
fw export bids -p "ConteCenter" --subject PCR2Pilot -g "022" ~/flywheel_download

```
