---
title: Flywheel Tutorial - BIDS to fMRIPrep
parent: Running Experiments
nav_enabled: true
---

# Flywheel fMRIPrep Tutorial 

Flywheel: [https://cahbir-flywheel.rutgers.edu/#/projects](https://cahbir-flywheel.rutgers.edu/#/projects)

**TABLE OF CONTENTS:** 
{:toc}

## Tutorial: Flywheel BIDS to fMRIPrep process

1. ‘Run gear’
2. ‘Run analysis gear’
    - NOT ‘fMRIPREP: A robust…”
    - Select “BIDS Apps: BIDS fMRIPrep” to run
3. Input
    - Add in your FreeSurfer license file freesurfer_license_jun2024.txt
        - way1: copy contents of text file > configuration > ‘gear FREESURFER LICENSE’
        - way2: Information > Attachments > Attach freesurfer license .txt
        - way3: Information > Custom Information > ‘+’ called FREESURFER_LICENSE > copy paste the .txt file into there
4. **Job Tags**: ‘extra-large’
5. Configuration - 
    - most recent is 1.5.1_24.0.0, but can choose your version
    - bids_app_command for **PCR:**
    
{: .new-title }
> bids_app_command for **PCR:** 
>
> `fmriprep bids_dir output --no-submm-recon --bold2anat-dof 6 --output-spaces T1w fsnative fsaverage MNI152NLin2009cAsym:res-native MNI152NLin2009cAsym:res-2 --cifti-output 91k --write-graph`

    

    
6. Finally, press ‘Run Gear’
    
    Wait 12-24 hours 
    

[Getting fMRIPrep to work on Flywheel](https://www.notion.so/Getting-fMRIPrep-to-work-on-Flywheel-1aecf00eb9368022a008d52a7599fc43?pvs=21)

If you need to check error log, you can download it here:

![image.png](Flywheel Tutorial (MBME Scans) 134cf00eb936804ca6a0d364fcfd7266/image.png)
