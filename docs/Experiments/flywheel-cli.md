---
title: Flywheel Command Line
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

**OPTION 1: Reference flywheel from the full path**

 This is already set up. You can call the full path to the shared copy of the file (`/projects/f_ah1491_1/analysis_tools/flywheel/linux_amd64/fw`) each time you want to run a command 

```bash
/projects/f_ah1491_1/analysis_tools/flywheel/linux_amd64/fw --help
```

**OPTION 2: Move a copy of the fw file to your /home/netID/bin folder so you only have to say `fw` to reference the package**
Run these: 
```bash
$ cp /projects/f_ah1491_1/analysis_tools/flywheel/linux_amd64/fw ~/bin/
$ chmod +x ~/bin/fw
$ fw --help
```
If that returns the flywheel help menu, it's set up correctly. 

**OPTION 3: Add the path to the flywheel executable to your bashrc file**

Run these: 
```bash
$ export PATH="/projects/f_ah1491_1/analysis_tools/flywheel/linux_amd64:$PATH"
$ source ~/.bashrc
$ fw --help
```
If that returns the flywheel help menu, it's set up correctly. 

If you get a conda error, try running `conda deactivate` and then again `conda deactivate` until you’re fully out of all condas and then try this again


### Flywheel Help Menu:
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
3. enter `alias fwlogin='/path/to/fw login cahbir-flywheel.rutgers.edu:<your_API_key>'`
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



### Usage

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

# Beta Command Line Interface (CLI)
⚙ Prerequisites: The install script requires `bash`, `curl`, `grep`, `tar`, and `shasum` (or `sha256sum`) in order to download, extract, and verify the CLI.

### 1 -- SSH into Amarel command line

```bash
ssh netID@amarel.rutgers.edu
```

### 2 -- Download prerequisites 

```bash
# latest stable version
curl https://storage.googleapis.com/flywheel-dist/fw-cli/stable/install.sh | sh
```

By default, `fw-beta` will be extracted under `~/.fw` with all of its dependencies. The installation folder can be customized using the envvar `FW_CLI_INSTALL_DIR`.

Shell profiles are automatically updated to include `fw-beta` on the `PATH` for bash and zsh using `~/.bash_profile` and `~/.zshenv` respectively.

### 3 — Activate new bash profile

```bash
source ~/.bash_profile
```

### 4 — Use CLI `export`


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