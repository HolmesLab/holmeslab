---
title: Download MRI Data from Flywheel
parent: Psychiatric Connectomics
nav_enabled: true
nav_order: 9
---
# Downloading PCX MRI Data from Flywheel 

# Exporting BIDS Data
1. Log into Amarel
Note-- to do this you must have flywheel setup in your command line. Follow these instructions to setup the legacy command line: [https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-cli/](https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-cli/)
First time: need to copy the `fw` file into your home directory:
- `cp /projectsp/f_dz268_1/wr178/forAlex/fw /home/ad2434/bin/`
- if /bin/ doesnt exist, create the directory
- this only needs to be done ONCE

3. In terminal or the Amarel OnDemand GUI, navigate to this location:
- this is where the data will be copied to: 
`cd /projects/f_ah1491_1/internal_data/PCX/bids/`
3. Log into flywheel: `fw login cahbir-flywheel.rutgers.edu:blahblahblah_numb3r5_l3tt3r5`
- you must have a flywheel API key for this login
4. Modify parameters to specify which subjects you would like to download from
`w export bids -g '022' -p 'PCX' --data-type anat --data-type dwi --data-type fmap --data-type func .`
- add `--subject __`after `-p 'PCX'` if you are doing it for one person
- the period after func is important.
- for multiple participants just reuse the subject flag in a row
- `fw export bids -g '022' -p 'PCX' --subject PCRXXX --subject PCRXXX --data-type anat --data-type dwi --data-type fmap --data-type func .`

# Downloading fMRIPrep Data
1. Log into Amarel
2. In terminal or the Amarel OnDemand GUI, navigate to this file: 
`/projects/f_ah1491_1/analysis_tools/flywheel/fmriprep_download/download_fmriprep_PCX.ipynb`
3. Make a copy to modify for your needs (ie specifying which data types, which data files, which subjects, which sessions, etc. you would like to download). If you run this script, it will submit a slurm job to download all subjects. 
4. Check the download succeeded by looking for your files in `/scratch/f_ah1491_1/internal_data/PCX/derivatives/fmriprep`




