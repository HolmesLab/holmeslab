---
title: Download MRI Data from Flywheel
parent: Psychiatric Connectomics
nav_enabled: true
nav_order: 9
---
# Downloading PCX MRI Data from Flywheel 

# Downloading BIDS Data
1. Log into Amarel
Note-- to do this you must have flywheel setup in your command line. Follow these instructions to setup the legacy command line: [https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-cli/](https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-cli/)
2. In terminal or the Amarel OnDemand GUI, navigate to this file: 
`/projects/f_ah1491_1/analysis_tools/flywheel/bids_download/download_bids_PCX_Joss.ipynb`
3. Modify parameters to specify which subjects you would like to download from
4. Run the notebook, which will do these things:
    1. Create a new slurm shell script for each subject, with the slurm header and the bash command to download that subject's bids file
        - Specifying subject-specific .err and .out files
    2. Send the script to slurm as a job
5. Check 

# Downloading fMRIPrep Data
1. Log into Amarel
2. In terminal or the Amarel OnDemand GUI, navigate to this file: 
`/projects/f_ah1491_1/analysis_tools/flywheel/fmriprep_download/download_fmriprep_PCX_Joss.py`
3. Make a copy to modify for your needs (ie specifying which data types, which data files, which subjects, which sessions, etc. you would like to download). If you run this script, it will download all data. 
4. Make a copy of `/projects/f_ah1491_1/analysis_tools/flywheel/fmriprep_download/slurm_download_fmriprep.sh` and change `download_fmriprep_PCX_Joss.py` to your new, modified .py file
5. Go to terminal and run $`sbatch /projects/f_ah1491_1/analysis_tools/flywheel/fmriprep_download/<your slurm file>` 
6. Check the download succeeded by looking for your files in `/scratch/f_ah1491_1/internal_data/PCX/derivatives/fmriprep`




