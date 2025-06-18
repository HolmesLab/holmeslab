---
title: Filesystem in Amarel
parent: Lab Policies
nav_enabled: true
nav_order: 2
---
# Filesystem Amarel Holmes Lab

Date: April 1, 2025 4:09 PM

## Overview

This is a tutorial for norms of Holmes Lab’s file-space on Amarel 

There are 3 main priorities: security, organization and functionality.  If you have any suggestions for amendments to this structure, please contact Avram or the lab manager. 

<aside>
⚙

Notes:

- Versioning should be done by adding “_YYMMDD” to filenames
- Naming restrictions: Study folders should contain only letters, numbers, and underscores [A-Za-z0-9_]
</aside>

**Jump to section:**

# Security

Only lab members and certain approved collaborators have access to the `/f_ah1491_1` spaces. To get access to this file space, email [help@oarc.rutgers.edu](mailto:help@oarc.rutgers.edu) and request to be added to the holmes lab folder (`/projects/f_ah1491_1`) and the CAHBIR partition (`p_dz268_1`). You will also be added to the usergroup `/projectsp/f_ah1491_1`. (To get a collaborator access to Amarel, follow this tutorial.) 

New folders should be created giving only read permissions to others, unless it’s a lab-general folder. Raw data should be read-only whenever possible. 

# Functionality

The main concern of our filesystem functionality is space and filecount limits. We are always near the limit of both, and so we use the `/scratch/f_ah1491_1` for everything where weekly backups are not necessary. 

Stored on `/scratch/f_ah1491`

- open source datasets
- datasets which are backed up on flywheel (internal datasets)
- Data analysis processes should be done on scratch and then only needed outputs should be stored on the `/projects/f_ah1491_1` space.

Stored in `/projects/f_ah1491_1`

- Files in the `/projects/f_ah1491_1` space should be compressed when possible.

### General Process

1. Find the data you want to use in `/scratch`
2. Create or modify scripts you want to use in `/projects`  and have them pull from data in scratch
3. Move script to `/scratch` if it makes intermediate files
4. Run script in scratch (or `/projects` if it doesn’t create intermediate files locally and you can save outputs/intermediate files to scratch)
5. Move output files (not intermediates/unused files)  to the appropriate folder in /projects 

The general approach for using `/scratch` is to copy your job's files (input files, libraries, etc.) to `/scratch,` run your job and write output files to `/scratch`, then move the files you need to save to your `/projects` directory. 

```bash
scp my-dir-of-output-files.tar.gz [gc563@amarel.rutgers.edu](mailto:gc563@amarel.rutgers.edu):/home/gc563
```

- `scp` – Securely copies files back to your /home directory.
- `my-dir-of-output-files.tar.gz` – The output archive.
- `/home/gc563` – The destination folder.

---
# Locations

### /scratch/f_ah1491_1/
- 100 TB storage
- Unlimited file count
- Not backed up
- Never deleted
- Lab general

## /projects/f_ah1491_1/

- 100 TB storage
- 5 million file count limit
- Backed up frequently
- Never deleted
- Lab general

---

# File Structures

The lab follows BIDS file structuring as much as possible for the organization of data files (see “BIDS” section below for details). Documentation, scripts and user folders are choices made by Holmes Lab. 

## Structure of /scratch/f_ah1491_1/
```
/scratch/f_ah1491_1
│── open_data/
│── internal_data/
│── users/

```

### Structure of **/internal_data or /open_data**
More information abot BIDS compliant datasets can be found at [bids-specification.readthedocs.io](https://bids-specification.readthedocs.io/en/stable/) 
More information about fMRIPrep (+ FreeSurfer) outputs can be found at [fmriprep.org](https://fmriprep.org/en/stable/outputs.html) 

```
/project_name/
├── bids/                     # BIDS-compliant raw dataset
	├── sub-01/
	├── sub-02/
├── dataset_description.json
├── participants.tsv


├── derivatives/                  # BIDS derivatives (preprocessed data)
	├── fmriprep/                 # fMRIPrep outputs, structured by fMRIPrep 
		├── sub-01/
		├── sub-02/
		├── logs/
		├── figures/
		├── reports/
		├── dataset_description.json   
	├── sourcedata/             # FreeSurfer outputs, structured by FreeSurfer (processed anatomical volumes)
		├── freesurfer/
		├── fsaverage{,5,6}/
			├── mri/
			├── surf/
				...
		├── sub-<label>/
			├── mri/
			├── surf/
				...
			...
	├── desc-aparc_dseg.tsv      # Precomputed anatomical volume numbers in text files
	├── desc-aparcaseg_dseg.tsv
  


```

### Structure of **/users**

```
/projects/f_ah1491_1/users/
│── <user_name>/
│── <user_name>/
│── <user_name>/
```

---

## Structure of /projects/f_ah1491_1/

```
/projects/f_ah1491_1
│── open_data/
│── internal_data/
│── analysis_tools/
│── documentation/
│── users/

```

### **/internal_data or /open_data**

structure:

```
/project_name/
│
├── behavioral/                     
│   ├── mindlamp/
│   ├── qualtrics/
│   ├── testmybrain/
│   ├── dataset_description.json
│   └── ...
├── processed_data/    
│   ├── timeseries/
│   └── ...
├── results/              
│   ├── connectivity/
│   ├── GLM_analysis/
│   ├── ICA_components , nmf , loadings, /
│   ├── dataset_description.json
│   ├── carrisa
	│   ├── ICA_components , nmf , loadings, /
│   └── ...
│   
├── results/                  # Processed results (stats, figures)
│   ├── group_level/
│   ├── individual_subjects/
│   ├── figures/
│   ├── tables/
│   ├── dataset_description.json
│   └── ...
│
├── scripts/                         # Scripts and notebooks
│   ├── preprocessing/            # fMRIPrep/FreeSurfer prep scripts
│   ├── analysis/                 # GLM, connectivity, clustering scripts
│   ├── visualization/            # Scripts for visualizing results
│   ├── utils/                    # Helper functions
│   ├── README.md                ## github explanation ssh 
│   └── ...
│
├── docs/                         # Documentation for project
│   ├── README.md
│   ├── methods.md
│   ├── references/
│   └── ...
│
└── logs/                         # Log files for pipeline runs
    ├── preprocessing_logs/
    ├── analysis_logs/
    ├── errors/
    ├── dataset_description.json
    └── ...

```

### /analysis_tools

structure:

```
/projects/f_ah1491_1/analysis_tools/
│── preprocessing/      # fMRIprep, Freesurfer, DWI processing
│── analysis/           # Statistical analysis, GLMs, MVPA
│── visualization/      # Brain plots, ROI maps
│── utilities/          # Helper scripts (e.g., BIDS conversion, file renaming)
│── README.md          # Script usage guidelines

```

### /documentation

structure:

```
/projects/f_ah1491_1/documentation/
│── guidelines.md      # Data management policies
│── tutorials/         # Pipeline guides, usage instructions
│── changelog.md       # Updates and notes on processing

```

### /users

structure:

```
/projects/f_ah1491_1/users/
│── <user_name>/
```

---

## BIDS Structure

The Brain Imaging Data Structure is a consistent file structure for neuroimaging. The specification can be browsed online in the [BIDS specification](https://bids-specification.readthedocs.io/). Below is an overview based on file types used in Holmes Lab studies. 

BIDS compliance can be checked on [https://bids-standard.github.io/bids-validator/](https://bids-standard.github.io/bids-validator/) 

Naming specifications:

- Subject IDs are “sub-” + the full ID. (ie  ID “PCR200” → “sub-PCR200”)
- Session labels are 2 digits, so the first session is “ses-01”
- All naming conventions can be found in the [BIDS specification](https://bids-specification.readthedocs.io/)

```jsx
sub-001		
└── ses-10
		├── anat
		│   ├── sub-101_ses-10_T1w.json
		│   ├── sub-101_ses-10_T1w.nii.gz
		│   ├── sub-101_ses-10_T2w.json
		│   └── sub-101_ses-10_T2w.nii.gz
		├── fmap
		│   ├── sub-101_ses-10_dir-AP_epi.json
		│   ├── sub-101_ses-10_dir-AP_epi.nii.gz
		│   ├── sub-101_ses-10_dir-PA_epi.json
		│   └── sub-101_ses-10_dir-PA_epi.nii.gz
		├── func
		│   ├── sub-101_ses-10_task-language_run-01_bold.json
		│   ├── sub-101_ses-10_task-language_run-01_bold.nii.gz
		│   ├── sub-101_ses-10_task-language_run-01_events.tsv
		│   ├── sub-101_ses-10_task-language_run-01_sbref.json
		│   ├── sub-101_ses-10_task-language_run-01_sbref.nii.gz
		│   ├── sub-101_ses-10_task-rest_run-01_bold.json
		│   ├── sub-101_ses-10_task-rest_run-01_bold.nii.gz
		│   ├── sub-101_ses-10_task-rest_run-01_events.tsv
		│   ├── sub-101_ses-10_task-rest_run-01_sbref.json
		│   ├── sub-101_ses-10_task-rest_run-01_sbref.nii.gz
		│   ├── sub-101_ses-10_task-rest_run-02_bold.json
		│   ├── sub-101_ses-10_task-rest_run-02_bold.nii.gz
		│   ├── sub-101_ses-10_task-rest_run-02_events.tsv
		│   ├── sub-101_ses-10_task-rest_run-02_sbref.json
		│   └── sub-101_ses-10_task-rest_run-02_sbref.nii.gz
		├── sub-101_ses-10_scans.json
		└── sub-101_ses-10_scans.tsv
dataset_description.json
participants.tsv
task-rest_bold.json
task-flanker_bold.json
task-language_bold.json
task-elevator_bold.json
task-momentous_bold.json
```