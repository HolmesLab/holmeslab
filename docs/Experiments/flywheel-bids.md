---
title: Flywheel Tutorial - Raw to BIDS
parent: Running Experiments
nav_enabled: true
---
# Flywheel: Data to BIDS 
FLYWHEEL LINK: [https://cahbir-flywheel.rutgers.edu/#/projects](https://cahbir-flywheel.rutgers.edu/#/projects)

---
**Table of Contents**
1. TOC
{:toc}
---

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
3. go to Sessions tab
4. make sure you’re on “Acquisitions” tab
5. optional: Turn on “BIDS View”
    1. click on the 3 dots to the right of the “Run Gear’ button
    2. click on the on-switch for “BIDS View”
6. click on the file you want to ignore
7. in the popup, go to “Information” tab
8. scroll down to the small section which says “BIDS” and has a carrot “^”
9. Press on the carrot to expant the BIDS information
10. Scroll down to the line “ignore []” and check the box
11. Press “save” on the popup
12. Repeat steps 6-11 for any files you want to ignore

### If you need to ignore many images based on rules…

1. click on your project tab
2. Go to “Information”
3. In files find template nordic_extension_template.json
    If it's not already uploaded, upload into the project [files nordic_extension_template.json](https://rutgers.box.com/s/2m3tgn5iwi3listic0ftbq7c6esojuj9), by clicking on:
        - Project Name (in side navigation bar)
        - Information tab
        - Attachments box
        - 'Upload' button
4. Click on the 3 dots in the template row and click “Download” 
5. Open file in an editor
6. in the “initializers:” section, paste in your code

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

## BIDS process
1. click on the project you want to look at (ie ConteCenter, PCX)
2. click on ”Sessions” tab
3. Make sure you’re on “Acquisitions” tab
4. Click 'Run Gear'
5. Select 'Analysis Gear'
6. Select 'BIDS Curation'
7. Click on the project name
8. ‘Inputs’ tab: 
    1. click on “template”
    2. click on ConteCenter or your project name (in the folder path)
    3. select the [nordic_extension_template.json](https://rutgers.box.com/s/2m3tgn5iwi3listic0ftbq7c6esojuj9)
    - locates and assigns the echoes their proper echo name
    - ignores single band reference images and phase images for fieldmaps
    - If it's not already there, upload it to the project files by clicking on: 
        - Project Name (in side navigation bar)
        - Information tab
        - Attachments box
        - 'Upload' button
9. ‘Configuration’ tab:
    1. First: you need to specify the regexes in pairs, each element separated by a space.
        1. To attach all fmap to their relevant BOLD images: `fmap-.* .*bold.nii.gz`
            You have to match the fmap container to the functional images containers. 
            Our containers for Conte/PCX are (both AP and PA):
            - `fmap-epi_dir-AP_BOLD_NORDIC_run-01`
            - `fmap-fieldmap_acq-B0`
            - `fmap-phasediff_dir-AP` 

            Our functional images are
            - func-epi_task-<taskName>_BOLD_NORDIC_run-01
            
            So to map (fill intendedFor field) every fmap to the functional images, use `fmap-.* .*bold.nii.gz`
            EX: To just map epi fmaps to the functional images, use `fmap-epi_.* .*bold.nii.gz`
            

    2. **Reset: YES**
    3. Ignore Config File: YES
    4. Save idecar as Metadata: NO
        - the JSON sidecars of the data to fill in the configuration, but you can add additional stuff in the tab that isn’t in the sidecars
10. Go to jobs log tab to track usage or errors
    1. Select subject/job
    2. Select ‘log’ tab
    - Refresh to see current— not in real time

[Getting BIDS to work on Flywheel](https://www.notion.so/Getting-BIDS-to-work-on-Flywheel-1abcf00eb93680318dfbc02655ee27d5?pvs=21)
