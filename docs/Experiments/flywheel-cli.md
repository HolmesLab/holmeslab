---
title: Flywheel in Command Line
parent: Running Experiments
nav_enabled: true
---
# Flywheel in Command Line

Date: April 3, 2025 1:14 PM

# Command Line Interface (CLI)

### Step 1: Download flywheel command line interface
The flywheel CLI is not able to be downloaded off a package manager like pip. Instead, you download it manually into your computer.

There is an existing instance in the Holmes Lab project space at `/projects/f_ah1491_1/analysis_tools/flywheel/linux_amd64/fw`

OR, you can download it somewhere locally by following the instructions on this tutorial: [Installing the Flywheel CLI](https://docs.flywheel.io/CLI/start/install/) Then, copy the filepath to where the flywheel .exe was downloaded into. The 

Now try linking to that flywheel instance in your terminal, like:
```
/projects/f_ah1491_1/analysis_tools/flywheel/linux_amd64/fw --version
```

If that returns a version number, you have it set up correctly. 


### Step 2: Generate an API key on Flywheel

1. Go to [https://cahbir-flywheel.rutgers.edu/#/projects](https://cahbir-flywheel.rutgers.edu/#/projects)
2. Click on your profile picture in the top right > ‘Profile’
3. Scroll down to ‘Flywheel Access’ and click ‘+ Generate API Key’
4. Copy API key and save in safe space

### Step 3: Add your API key to your .bash_aliases file

1. Log into Amarel on the terminal with ssh
2. enter `nano ~/.bash_aliases`
3. enter ``alias fwlogin='fw login [cahbir-flywheel.rutgers.edu](http://cahbir-flywheel.rutgers.edu/):<your_API_key>'` 
4. press control+X → ‘Y’ → ‘Enter’ to save and exit 
5. enter `source ~/.bashrc`` to update

🚨 Note: when your API key expires, make a new one and update it in your bash_aliases through this process


### Step 4: login to CLI with API Key on Flywheel:

1. type `alias fwlogin`
2. copy and paste the string into your command line

```bash
#Formula: <filepath to fw> login <yourAPIKey>
#ex: 
/projects/f_ah1491_1/analysis_tools/flywheel/linux_amd64/fw  login [cahbir-flywheel.rutgers.edu](http://cahbir-flywheel.rutgers.edu/):<your_API_key> 
```

Then it will say `You are now logged in as: Kaley Joss!`

### Step 4: Move the fw executable to your home/netID/bin folder

The fw executable is something downloaded from online, not from pip/package manager, so it doesn’t automatically get downloaded to the files your command line searches through. 

To use fw, you can either:

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

## Usage

To view the available list of commands, run `fw -h` (^^pasted above). More information about each command can found in the *Command References* documentation folder.

## Getting Help

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

# The `fw download` Command

Sessions, acquisitions, and files can be downloaded individually using the `fw download` command.

## Usage

`fw download [-h] [--config-file CONFIG_FILE | --no-config] [-y] 
[--ca-certs CA_CERTS] [--timezone TIMEZONE] [--debug | --quiet][-o [OUTPUT]] [-p PREFIX] [-i INCLUDE] [-e EXCLUDE] <source-path>`

### Required Arguments

| Required Argument | Description |
| --- | --- |
| `source-path` | The location of the file on your Flywheel instance. For example [fw://group/project/subject/acquisition/attachments] |

### Optional Arguments

### Download

For a full, up-to-date list of options, run the following from your command line:

`fw download --help`

Below is a list of commonly used options.

| Optional Argument | Description |
| --- | --- |
| `-i FILE_TYPE`, `--include FILE_TYPE` | Download only files with the specified types.* |
| `-e FILE_TYPE`, `--exclude FILE_TYPE` | Ignore files with the specified types.* |
| `-o`, `--output file name` | Name of the folder where the data is downloaded |
| `-p PREFIX`, `--prefix PREFIX` | Prefix for downloaded directory structure |
- [Learn more about file types in Flywheel](https://docs.flywheel.io/user/upload/user_file_types_in_flywheel/)

### General

| Optional Argument | Description |
| --- | --- |
| `-h`, `--help` | Show help message and exit. |
| `-C PATH`, `--config-file` | Specify configuration options via config file.* |
| `--no-config` | Do NOT load the default configuration file. |
| `-y`, `--yes` | Assume the answer is yes to all prompts. |
| `--ca-certs CA_CERTS` | Path
 to a local Certificate Authority certificate bundle file. This option 
may be required when using a private Certificate Authority. |
| `--timezone TIMEZONE` | Set the effective local timezone to use when uploading data. |
| `-q`, `--quiet` | Squelch log messages to the console. |
| `-d`, `--debug` | Turn on debug logging. |
| `-v`, `--verbose` | Get more detailed output. |
- [Learn more about how to create this file](https://docs.flywheel.io/CLI/start/config_file/).

## Example

Below is an example of how to download a particular subject:

1. 
    
    [Download the Flywheel CLI](https://docs.flywheel.io/CLI/start/install/), and sign in using your API key. Once signed in, the following message should appear:
    
- `C02W39YBHTD6:~ AvaAnderson$ fw login staging2.dev.flywheel.io:Ja0ib***********pf
You are now logged in as Ava Anderson!`
    
    ---
    
- 
    
    Now you can navigate to the files you wish to download. In this example, we're navigating to the subjects in the ConteCenter project:
    
- `fw ls 022/ConteCenter`
outputs:

```bash
files/README.txt                               
files/dataset_description.json                 
files/freesurfer_license_jun2024.txt           
files/nordic_extension_template.json           
files/nordic_extension_template_archived.json  
files/nordic_extension_template_archived2.json 
PCR2Pilot     # Subject folder                            
PCR2Pilot2    # Subject folder  
```

- `fw ls 022/ConteCenter/PCR2Pilot`
    
    outputs:
    
    ```bash
    001     # Session folder
    ```
    
- `fw ls 022/ConteCenter/PCR2Pilot/001`
    
    outputs:
    
    - All analyses/gears run
    - ALL acquisition folder in RAW acquisition format
    
    ```bash
    #example:
    analyses/bids-pre-curate 02/28/2025 14:18:16           
    analyses/curate-bids 02/28/2025 16:48:13               
    analyses/bids-fmriprep 03/14/2025 11:22:35   
    AAHead_Scout
    AAHead_Scout_MPR_sag
    AAHead_Scout_MPR_cor
    ```
    
- `fw ls "022/ConteCenter/PCR2Pilot/001/analyses/bids-fmriprep 03/14/2025 11:22:35"`

```bash
files/bids_tree.html
files/bids-fmriprep_001_67d449d202be158786fab2d3.zip
files/fmriprep_log.txt
files/sub-PCR2Pilot.html.zip
```

---

Tip

If a project or subject's name includes spaces, use quotes around the name. For example: `Psychology/"An example study"`

- 
    
    To download one of those subjects:
    
1. `C02W39YBHTD6:~ AvaAnderson$ fw download Psychology/AnxietyStudy/s3
This download will be about 218 MB comprising 39 files.
Continue? (yes/no): yes
Wrote 218 MB to s3.tar`

    
    ---



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