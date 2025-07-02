---
title: Download MRI Data from Flywheel
parent: Psychiatric Connectomics
nav_enabled: true
---
# Downloading PCX from Flywheel 

# Downloading BIDS Data
1. 

# Downloading fMRIPrep Data
1. Log into Amarel
2. In terminal or the Amarel OnDemand GUI, navigate to this file: 
`/projects/f_ah1491_1/analysis_tools/flywheel/fmriprep_download/download_fmriprep_PCX_Joss.py`
3. Make a copy to modify for your needs (ie specifying which data types, which data files, which subjects, which sessions, etc. you would like to download). If you run this script, it will download all data. 
4. Make a copy of `/projects/f_ah1491_1/analysis_tools/flywheel/fmriprep_download/slurm_download_fmriprep.sh` and change `download_fmriprep_PCX_Joss.py` to your new, modified .py file
5. Go to terminal and run $`sbatch /projects/f_ah1491_1/analysis_tools/flywheel/fmriprep_download/<your slurm file>` 


