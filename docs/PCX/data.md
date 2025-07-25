---
title: Data Pipeline
parent: Psychiatric Connectomics
nav_enabled: true
nav_order: 4

---

# Data Pipeline


Full Data Processing + Compilation in Amarel for PCX Data 

---

## Qualtrics Data

Download qualtrics data to amarel using the Qualtrics API 

1. Log into amarel
2. Navigate to `/projects/f_ah1491_1/analysis_tools/qualtrics/download_qualtrics.ipynb`
3. Run the notebook
4. Check the data has appeared in `/scratch/f_ah1491_1/internal_data/PCX/behavioral`

---

## MindLAMP Data

1. Be on a computer at Rutgers so it’s on Rutgers wifi

1. VPN into Eris (MGB HPC)

3.  Run 

```python
scp  /scratch/f_ah1491_1/internal_data/PCX/behavioral/smartphone [KJ110@eristwo.partners.org](mailto:KJ110@eristwo.partners.org):/data/sbdp/PHOENIX/PCX/PROTECTED .
```

---

## MRI Data

1. Log into flywheel using this tutorial: [https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-tutorial/](https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-tutorial/) 
2. Process data from Raw to BIDS using this tutorial:
    
    [https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-bids/](https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-bids/) 
    
3. Process BIDS data to fMRIPrep using this tutorial: [https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-fmriprep/](https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-fmriprep/) 
4. Download BIDS and fMRIPrep data using this tutorial:
    
    [https://holmeslab.github.io/holmeslab/docs/PCX/download-mri/](https://holmeslab.github.io/holmeslab/docs/PCX/download-mri/) 
    

---

## Task Data

When you run tasks from files in Bo in psychopy, the data saves to the same sSend task data from Box to Amarel in BIDS format using this script: [create_bids_files.ipynb](https://rutgers.box.com/s/2ko0vive5aegeplaqabd8go4ug0e0g6h)

---