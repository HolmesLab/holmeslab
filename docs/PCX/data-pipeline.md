---
title: Full Data Pipeline
parent: Psychiatric Connectomics
nav_enabled: true
nav_order: 6
---

# Overview of Data Pipeline

[https://www.canva.com/design/DAGzzTQp35k/3GgZoToVdE6ngsTJr_o5VA/edit](https://www.canva.com/design/DAGzzTQp35k/3GgZoToVdE6ngsTJr_o5VA/edit)

### Locations/Processes

| ID | Action | Process | Test for completion | Time it takes | Frequency |  |
| --- | --- | --- | --- | --- | --- | --- |
| 1 |  | Manually download from qualtrics |  |  |  |  |
| 2 |  | **Qualtrics Data**
Download qualtrics data to amarel using the Qualtrics API
1. Log into amarel
2. Navigate to `~/Library/CloudStorage/Box-Box/Holmes_Lab_Wiki/PCX_Round2/Data_processing/download_qualtrics.ipynb`
3. Run the notebook | Check the datasheets have  appeared for today’s date in `~/Library/CloudStorage/Box-Box/(Restricted)_PCR/PCX/behavioral` | >1min | Weekly |  |
| 3 |  | TBD - do we need this? Brien would have to maybe upload to PCX Box? |  |  |  |  |
| 4.1 |  | Lochness (run every 12 hours on MGB server. Maintained by Habib) |  | None | Daily (auto) |  |
| 4.2 |  | Lochness (run every 12 hours on MGB server. Maintained by Habib) |  | None | Daily |  |
| 5 |  | **MindLAMP Data**
1. Be on a computer at Rutgers so it’s on Rutgers wifi
2. VPN into Eris (MGB HPC)
3. Run (replace ‘kj110’ with your MGB netID)
`rsync -avz kj110@eristwo.partners.org:'/data/sbdp/PHOENIX/GENERAL/PCX/PC*' '/Users/demo/Library/CloudStorage/Box-Box/(Restricted)_PCR/PCX/mindlamp_mri_data/data'` |  | >1min | Weekly |  |
| 6 |  | 1. Create nifti files with this command
`sh ~/Library/CloudStorage/Box-Box/Holmes_Lab_Wiki/PCX_Round2/Data_processing/create_nii.sh 1> ~/Library/CloudStorage/Box-Box/Holmes_Lab_Wiki/PCX_Round2/Data_processing/create_nii.out 2> ~/Library/CloudStorage/Box-Box/Holmes_Lab_Wiki/PCX_Round2/Data_processing/create_nii.err &`

2. Script to import data from HIPAA-box to Flywheel | Check `create_nii.out` & `create_nii.err` | 10min per subject |  |  |
| 7 |  | 1. Connect to Rutgers VPN (to access HPC Amarel)
2. Run
`rsync -avz '/Users/demo/Library/CloudStorage/Box-Box/(Restricted)_PCR/PCX/mindlamp_mri_data/data' kj537@amarel.rutgers.edu:'/scratch/f_ah1491_1/internal_data/PCX'` |  |  |  |  |
| 8 |  | 1. Log into amarel
2. Navigate to `/projects/f_ah1491_1/analysis_tools/qualtrics/download_qualtrics.ipynb`
3. Run the notebook
4. Check the data has appeared in `/scratch/f_ah1491_1/internal_data/PCX/behavioral` |  |  |  |  |
| 9 |  | **Task Data**
When you run tasks from files in Box (through Psychopy), the data saves to the same Box location in the /data folder. Send task data from Box to Amarel in BIDS format using this script: `~/Library/CloudStorage/Box-Box/Holmes_Lab_Wiki/PCX_Round2/Data_processing/create_bids_files.ipynb` |  | >1min | Weekly |  |
| 10 |  | TBD - Kaley needs to write script |  |  |  |  |
| 11 |  | Download fMRIPrep data using this tutorial:
[https://holmeslab.github.io/holmeslab/docs/PCX/download-mri/](https://holmeslab.github.io/holmeslab/docs/PCX/download-mri/) |  |  |  |  |
| 12 |  | Move BIDS and fMRIPrep data to Amarel using this tutorial:
[https://holmeslab.github.io/holmeslab/docs/PCX/download-mri/](https://holmeslab.github.io/holmeslab/docs/PCX/download-mri/) |  |  |  |  |
| 13 |  | Finish + Publish Page: CAHBIR Scans to Flywheel |  | 1hr per subject | Daily (auto) |  |
| 14 |  | Process data from Raw to BIDS using this tutorial:
[https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-bids/](https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-bids/) |  | 5min per subject | Weekly |  |
| 15 |  | Process BIDS data to fMRIPrep using this tutorial: [https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-fmriprep/](https://holmeslab.github.io/holmeslab/docs/Experiments/flywheel-fmriprep/)
 |  | 12-24hr per subject |  |  |
| 16 |  | Process on [https://holmeslab.github.io/holmeslab/docs/PCX/eris-xnat/](https://holmeslab.github.io/holmeslab/docs/PCX/eris-xnat/)  |  | 1 min per subject | Weekly |  |
| 17 |  | Manually download from flywheel into '~/Library/CloudStorage/Box-Box/(Restricted)_PCR/PCX/fmriprep_reports’ |  | 1 min per subject | Daily |  |

CHECKING:

---