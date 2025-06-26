---
title: Flywheel Tutorial
parent: Running Experiments
nav_enabled: true
---

# Flywheel Tutorial (MBME Scans)

Flywheel: [https://cahbir-flywheel.rutgers.edu/#/projects](https://cahbir-flywheel.rutgers.edu/#/projects)

**TABLE OF CONTENTS:** 
{:toc}

`fmap.*run-01*.* .**bold.nii.gz`

## How to change file names (if necessary):

Tutorial by flywheel devs: [https://docs.flywheel.io/Developer_Guides/dev_bids_curation_2_precuration/](https://docs.flywheel.io/Developer_Guides/dev_bids_curation_2_precuration/) 

1. Go to your Project tab
2. click on Subjects tab and select the subject you’d like to run
3. Go to Analysis tab
4. Click Run analysis gear 
5. Click “Bids Pre-Curation” or “relabel container” (they’re equivalent)
    1. put in no inputs, leave everything blank
6. run gear
7. Go to subjects tab
8. to go “provenance” tab in subject to see the job running
    1. refresh for new update— not live view
    2. if fails, click on the “View Log” button
    3. read the error log to figure out
        1. ask Wil if need be
9. When finished, go to “analysis” tab at the TOP (not within “Subject”)
10. click on the job Bids pre-curate
11. For the files, if you need to make edits, press on the 3 dots and then press “Download”
    
    acquisitions.csv 
    
    sessions.csv
    
    subjects.csv 
    
12. make the edits in excel
13. in flywheel, in the project tab, press “information” tab
14. press ‘upload’ 
15. upload the .csv that you made edits to
- This keeps the version history of all the prior csv versions— so if you upload a document that is wrong, you can just restore an old version

## Ignoring Files

### If you need to ignore 1-3 images into .bidsignore…

Flywheel Tutorial: [Ignoring Certain Images in Bids](https://docs.flywheel.io/user/bids/user_ignoring_certain_images_in_bids/)

1. Go to your Project tab
2. click on Subjects tab and select the subject you’d like to run
3. Go to Sessions tab
4. Make sure you’re on “Acquisitions” tab
5. Optional: Turn on “BIDS View”
    1. click on the 3 dots to the right of the “Run Gear’ button
    2. click on the on-switch for “BIDS View”
6. Click on the file you want to ignore
7. In the popup, go to “Information” tab
8. Scroll down to the small section which says “BIDS” and has a carrot “^”
9. Press on the carrot to expant the BIDS information
10. Scroll down to the line “ignore []” and check the box
11. Press “save” on the popup
12. Repeat steps 6-11 for any files you want to ignore

### If you need to ignore many images based on rules…

1. Click on your project tab
2. Go to “Information”
3. In files find template nordic_extension_template_MMDDYYYY.json
4. Click on the 3 dots in the template row and click “Download” 
5. Open file in an editor
6. In the “initializers":” section, paste in your code

for example, this skips any files which start with “fmap_” or “fmap-” and end with “SBRef” or “Pha”, and skips any files which end with “_e2” or “_e3”

```python
{
          "rule": "reproin_fieldmap_file",
          "where": {
            "acquisition.label": {
              "$regex": "fmap(-|_).*(SBRef|Pha)+$"
            }
          },
          "initialize": {
            "ignore": true
          }
        },
        {
            "rule": "reproin_fieldmap_file",
            "where": {
                "file.name": {
                    "$regex": "_e(2|3)\\.(nii(\\.gz|)|json)$"
                },
                "acquisition.label": {
                    "$regex": "fmap(-|_)"
                }
            },
            "initialize": {
                "Suffix": "echo",
                "ignore": true
            }
        },
```

## Add Additional Documents

- ‘ad-hoc’ upload
- can add any type of file to a dataset

## Flywheel Storage & Pipeline - only put active CAHBIR center data

- No restrictions for the amount of data
- but we’re charged for the data since it’s stored in google cloud
- but in general it won’t cause a problem
- Can keep all your data on flywheel
    - More likely to stay stable than stuff you take off and put on amarel
- After every session of fMRI scanning at CAHBIR the scan tech is going to automatically send data from the scanner to flywheel
    - multi-band multi-echo will go up but will go up a little later since Jeff has to do another step
    - compress-sensing MP2Rage
- Double check that the information you want in flywheel is being transferred after the data is put into flywheel
    - You should definitely do a test or two with your pipeline

## Tutorial: Flywheel MRI to BIDS process

1. click on the project you want to look at (ie ConteCenter, PCX)
2. click on ”Sessions” tab
3. make sure you’re on “Acquisitions” tab
4. run gear
5. analysis gear
6. bids curation
7. click on the project name
8. ‘inputs’ tab: 
    1. click on “template”
    2. click on ConteCenter or your project name
    3. select the nordic_extension_template.json
    - locates and assigns the echoes their proper echo name
    - ignores single band reference images and phase images for fieldmaps
9. ‘configuration’ tab:
    1. First: you need to specify the regexes in pairs, each element separated by a space.
        1. To attach all fmap to their relevant BOLD images: `fmap-.* .*bold.nii.gz`
    2. reset: YES
    3. “Ignore Config File”
    4. ‘save sidecar as metadata’ select NO
        - the JSON sidecars of the data to fill in the configuration, but you can add additional stuff in the tab that isn’t in the sidecars
10. go to jobs log tab to track usage or errors
    1. select subject/job
    2. select ‘log’ tab
    - Refresh to see current— not in real time

[Getting BIDS to work on Flywheel](https://www.notion.so/Getting-BIDS-to-work-on-Flywheel-1abcf00eb93680318dfbc02655ee27d5?pvs=21)

## Tutorial: Flywheel BIDS to fMRIPrep process

1. ‘Run gear’
2. ‘run analysis gear’
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

## Misc

### Data-Viewer

- little picture icon on the right of the dicom
- can also double check that your files are right

### Gear Exchange

- [flywheel.io/gear-exchange/](http://flywheel.io/gear-exchange/)
    - if there’s any there you want and aren’t currently installed on our flywheel, let Wil / CAHBIR-support know, and they’ll ask flywheel to add it
- You can also make requests for flywheel to make a gear, though we don’t know how quickly that might happen

### Other

- Wil custom python script
    - will unzip and grab specific files and put them where you want them to be

### Questions

- Flywheel has robust documentation
    - [https://docs.flywheel.io/Developer_Guides](https://docs.flywheel.io/Developer_Guides)
- or email flywheel directly with ‘give us feedback’ (opens up a ticket)