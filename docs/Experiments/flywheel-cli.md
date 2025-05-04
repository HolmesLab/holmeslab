---
title: Download Data from Flywheel
parent: Running Experiments
nav_enabled: true
---
# Flywheel in Command Line
Date: April 3, 2025 1:14 PM

---
**Table of Contents**
1. TOC
{:toc}
---

# Install Legacy Command Line Interface (CLI)

### Step 1: Download flywheel command line interface
The flywheel CLI is not able to be downloaded off a package manager like pip. Instead, you download it manually into your computer.

There is an existing instance in the Holmes Lab project space at `/projects/f_ah1491_1/analysis_tools/flywheel/linux_amd64/fw`

OR, you can download it somewhere locally by following the instructions on this tutorial: [Installing the Flywheel CLI](https://docs.flywheel.io/CLI/start/install/) Then, copy the filepath to where the flywheel .exe was downloaded into. The 

Now try linking to that flywheel instance in your terminal, like:
```
/projects/f_ah1491_1/analysis_tools/flywheel/linux_amd64/fw --version
```

If that returns a version number, you have it set up correctly. 

To use fw commands, you can either:

OPTION 1: This is already set up. You can call the full path to the shared copy of the file (`/projects/f_ah1491_1/analysis_tools/flywheel/linux_amd64/fw`) each time you want to run a command 

```bash
/projects/f_ah1491_1/analysis_tools/flywheel/linux_amd64/fw [COMMAND]
```

OPTION 2: move a copy of the fw file to your /home/netID/bin folder so you only have to say `fw` to reference the package

```bash
fw [COMMAND]
```

**How to set up Option 2:** 

Run this command in your terminal, replacing <netID> with your netID

```bash
export PATH="/projects/f_ah1491_1/analysis_tools/flywheel/linux_amd64:$PATH"
source ~/.bashrc
```

If you get a conda error, try running `conda deactivate` and then again `conda deactivate` until you’re fully out of all condas and then try this again

You should be able to run

```bash
fw --help
```

If it returns this, you’ve got it setup!

```bash
usage: fw [-h]  ...

Flywheel command-line interface

options:
  -h, --help  show this help message and exit

Available commands:
  
    login     Login to a Flywheel instance
    logout    Delete your saved API key
    status    See your current login status
    version   Print CLI version
    cp        Copy a local file to a remote location, or vice-a-versa
    ls        Show remote files
    download  Download a remote file or container
    upload    Upload a local file to a Flywheel container
    export    Export data from Flywheel
    job       [DEPRECATED] Start or manage server jobs
    sync      Sync files from Flywheel to storage
    ingest    Ingest data
    deid      Test your de-identification template or generate a sample template

```

### Step 2: Generate an API key on Flywheel

1. Go to [https://cahbir-flywheel.rutgers.edu/#/projects](https://cahbir-flywheel.rutgers.edu/#/projects)
2. Click on your profile picture in the top right > ‘Profile’
3. Scroll down to ‘Flywheel Access’ and click ‘+ Generate API Key’
4. Copy API key and save in safe space

### Step 3: Add your API key to your .bash_aliases file

1. Log into Amarel on the terminal with ssh
2. enter `nano ~/.bash_aliases`
3. enter ``alias fwlogin='/path/to/fw login cahbir-flywheel.rutgers.edu:<your_API_key>'` 
  For example, if using the Holmes Lab fw instance: `alias fwlogin='/projects/f_ah1491_1/analysis_tools/flywheel/linux_amd64/fw login cahbir-flywheel.rutgers.edu:<your_API_key>`
4. press control+X → ‘Y’ → ‘Enter’ to save and exit 
5. enter `source ~/.bashrc`` to update

🚨 Note: when your API key expires, make a new one and update it in your bash_aliases through this process


### Step 4: login to CLI with API Key on Flywheel:

1. If you did step 3, type `fwlogin'`
  -> This should return `You are now logged in as <Your Name>!`

2. If you did not do step 3, copy and paste this formula into your command line
```bash
#Formula: <filepath to fw> login <yourAPIKey>
#ex: 
/path/to/fw  login cahbir-flywheel.rutgers.edu:<your_API_key> 
```

-> When it logs in, it will say `You are now logged in as: <Your Name>!`



## Usage

To view the available list of commands, run `fw -h` (^^pasted above). More information about each command can found in the *Command References* documentation folder.

*Getting Help*

With any command, you can add -h or --help to get more information. For example, with the `ls` command we'll see in the following section:

```bash
usage: fw ls [-h] [--config-file CONFIG_FILE | --no-config] [-y] [--ca-certs CA_CERTS] [--timezone TIMEZONE] [--debug | --quiet]
             [--ids] [-a]
             [path]
positional arguments:
  path                  The path to list subfolders and files
options:
  -h, --help            show this help message and exit
  --config-file CONFIG_FILE, -C CONFIG_FILE
                        Specify configuration options via config file
  --no-config           Do NOT load the default configuration file
  -y, --yes             Assume the answer is yes to all prompts
  --ca-certs CA_CERTS   The file to use for SSL Certificate Validation
  --timezone TIMEZONE   Set the effective local timezone for imports
  --debug               Turn on debug logging
  --quiet               Squelch log messages to the console
  --ids                 Display database identifiers
  -a, --all             Show all

```

# Downloading Data: The `fw download` Command

Sessions, acquisitions, and files can be downloaded individually using the `fw download` command.

## Usage

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


## Example: Downloading Acquisition Files

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
project = Conte, PCX, Napls, ...

So a download command may look like: 
`fw export bids -p "Conte" -g "022" ~/flywheel_download`

You can also download specific subjects, using the --subject flag. For example:
`fw export bids -p "Conte" --subject PCR2Pilot -g "022" ~/flywheel_download`



# Beta Command Line Interface (CLI)

<aside>
⚙

Prerequisites: The install script requires `bash`, `curl`, `grep`, `tar`, and `shasum` (or `sha256sum`) in order to download, extract, and verify the CLI.

</aside>

# 1 -- SSH into Amarel command line

```bash
ssh netID@amarel.rutgers.edu
```

# 2 -- Download prerequisites 

```bash
# latest stable version
curl https://storage.googleapis.com/flywheel-dist/fw-cli/stable/install.sh | sh
```

By default, `fw-beta` will be extracted under `~/.fw` with all of its dependencies. The installation folder can be customized using the envvar `FW_CLI_INSTALL_DIR`.

Shell profiles are automatically updated to include `fw-beta` on the `PATH` for bash and zsh using `~/.bash_profile` and `~/.zshenv` respectively.

# 3 — Activate new bash profile

```bash
source ~/.bash_profile
```

# 4 — Use CLI `export`

### `export`

Export data from a Flywheel project to an external storage.

```bash
USAGE
  fw-beta export [OPTIONS] COMMAND [ARGS]...

  Export data from FW to a storage.

COMMANDS
  run       Export data from a project via the connector service
  get       Get export by ID
  list      List exports
  cancel    Cancel an export by ID
  rerun     Rerun an export by ID
  schedule  Schedule exports to run later or repeatedly

OPTIONS--docs  Show HTML docs for command
  --help  Show this message and exit

```