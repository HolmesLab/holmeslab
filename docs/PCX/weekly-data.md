---
title: Weekly Data Processing
parent: Psychiatric Connectomics
nav_enabled: true
nav_order: 4
---
# Weekly Data Processing

---
## Qualtrics Data

Download qualtrics data to amarel using the Qualtrics API 

1. Log into amarel
2. Navigate to `/projects/f_ah1491_1/analysis_tools/qualtrics/download_qualtrics.ipynb`
3. Run the notebook
4. Check the data has appeared in `/scratch/f_ah1491_1/internal_data/PCX/behavioral`

Download qualtrics data to Box using the Qualtrics API 

1. Navigate to `/Users/demo/Library/CloudStorage/Box-Box/Holmes_Lab_Wiki/PCX_Round2/Data_processing/download_qualtrics.ipynb`
2. Run the notebook
3. Check the data has appeared in ~`/Library/CloudStorage/Box-Box/(Restricted)_PCR/PCX/behavioral`

---

## MindLAMP Data

1. Connect to MGB VPN (to access HPC Eris)
2. Run 

```python
rsync -avz kj110@eristwo.partners.org:'/data/sbdp/PHOENIX/GENERAL/PCX/PC*' '/Users/demo/Library/CloudStorage/Box-Box/(Restricted)_PCR/PCX/mindlamp_mri_data/data'
```

1. Connect to Rutgers VPN (to access HPC Amarel)
2. Run

```python
rsync -avz '/Users/demo/Library/CloudStorage/Box-Box/(Restricted)_PCR/PCX/mindlamp_mri_data/data' kj537@amarel.rutgers.edu:'/scratch/f_ah1491_1/internal_data/PCX'
```

---

## MRI Data

1. Log into flywheel using this tutorial: [https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-tutorial/](https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-tutorial/)
2. Check each recent person has 
    - All relevant scans
    - Echos are in the appropriate scan container if the scan was repeated
3. Process data from Raw to BIDS using this tutorial:[https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-bids/](https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-bids/) 
4. Process BIDS data to fMRIPrep using this tutorial: [https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-fmriprep/](https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-bids/) 
5. Download BIDS and fMRIPrep data using this tutorial: [https://holmeslab.github.io/holmeslab/docs/PCX/download-mri/](https://holmeslab.github.io/holmeslab/docs/PCX/download-mri/) 
    

---

## Task Data

When you run tasks from files in Box (through Psychopy), the data saves to the same Box location in the /data folder. Send task data from Box to Amarel in BIDS format by running this script: 

`~/Library/CloudStorage/Box-Box/Holmes_Lab_Wiki/PCX_Round2/Data_processing/create_bids_files.ipynb`

[Overview of Data Pipeline](https://www.notion.so/Overview-of-Data-Pipeline-25ecf00eb93680c09f1ac3f54ed16e75?pvs=21)
---

# Bi-weekly Data Processing

- Check mindlamp 
- Check scans pulled from McLean are all there
- Check over fmriprep outputs
- Check task data