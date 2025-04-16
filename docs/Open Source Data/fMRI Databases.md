---
title: fMRI Databases
parent: Open Source Data
nav_enabled: true 
---
# fMRI Databases

Date: January 26, 2024 12:52 PM

### Databases - Steps to get access

- [Human Connectome Project](https://db.humanconnectome.org/)
    
    Access via: NDA (below)
    
- [UK Bio Bank](https://www.ukbiobank.ac.uk/)
    
    Steps to get access: 
    
    1. Sign up for an account and file 
    2. Fill out your profile information and institutional affiliation
    3. Wait for your registration to be activated
    4. Ask PI to add you to the “Ethics” ie the IRB for the site-access for your institution
- [National Data Archive](https://nda.nih.gov/) at the United States National Institute of Health
    
    Steps to get access:
    
    1. Go to the NDA website: [https://nda.nih.gov/](https://nda.nih.gov/). To create an account, click the “log in” button in the top right which will prompt a few “create account” options. Any of the ways they list to create your account will work fine. 
    2. Once you have your account, request access to the “NIMH Data Archive” 
        1. Put in name of the project- doesn’t have to match everyone else
        2. You can add collaborators here, or you can each do it separately
        3. Description of use can be like this
            
            “We are applying for access to the NDA dataset [Enter dataset name] for the purposes of scientific investigation. The data will be stored on a secure server, in a password protected file on the Rutgers University Amarel computing cluster. The folder will only be accessible by those listed in this DUA. All raw data will be deleted after the conclusion of the project.”
            
        4. For “Signing Official”, select **Gregory Werhner** [gw266@ored.rutgers.edu](mailto:gw266@research.rutgers.edu) 
    3. Download the DUC file that they create & E-sign it
    4. Email the signed file to **Gregory Werhner** [gw266@ored.rutgers.edu](mailto:gw266@research.rutgers.edu) 
    5. Once you receive it back signed, upload the DUC (signed by both of you) to the “Upload Supporting Documentation” under “active requests”
        
        ![Screen Shot 2024-01-26 at 3.40.04 PM.png](fMRI%20Databases%20143ba69c58654779880017db71871c86/Screen_Shot_2024-01-26_at_3.40.04_PM.png)
        
    6. Wait to get granted access

### Tutorials

Tutorial on Using HCP Data: [https://www.humanconnectome.org/storage/app/media/documentation/tutorials/Connectome_WB_Tutorial_v1.5.pdf](https://www.humanconnectome.org/storage/app/media/documentation/tutorials/Connectome_WB_Tutorial_v1.5.pdf) 

### Practice Data

Practice data: [https://balsa.wustl.edu/study/kN3mg](https://balsa.wustl.edu/study/kN3mg) 

### Pipelines:

VPN → Compute Cluster Registration & Login → Create a job in compute node (using GUI or Slurm) → Activate Conda Environment → Open Jupyter Lab or RStudio → Access data on compute node → Write code in Python or R using the applications/installed tools → Use BASH script to run the code using the data from the compute node → download outputs to compute node

Applications:

FreeSurfer

FSL

SPM

ConnectomeWorkbench

Libraries, packages and modules:

[holmes-spec.txt](fMRI%20Databases%20143ba69c58654779880017db71871c86/holmes-spec.txt)