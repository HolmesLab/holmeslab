---
title: Accessing Eris (MGB Server)
parent: Psychiatric Connectomics
nav_enabled: true
nav_order: 99
---
# How to get into Eris (MGB Server)
        
## Sign into Eris each time by:
1. Connect to Mclean VPN:  **pvc.partners.org/saml**
2. In terminal, type `ssh -Y netID@eristwo.partners.org` or `ssh -Y netID@dna006.research.partners.org`
NOTE: netID must be all LOWERCASE. 
3. Type your password
Connected!

### Data is in…
    /data/sbdp/PCM

## Tutorial to Get Access to Eris: 

1. If you don't have an MGB NetID, first ask Justin/Avram if you need one. You will need one if you need to access Eris. If so, fill out these forms from and send them to Justin. 
Forms:
- [Attestation of Outside Employment McLean](mclean-id-forms/attestation.pdf)
- [POI Form 2024.pdf](mclean-id-forms/poi.pdf)
- [McLean Intellectual Property Acknowledgment](mclean-id-forms/ip.pdf)

- The start of your employment is the start of your employment with Rutgers, not with MGB
- The "Institutional Official Signature" is for someone at Rutgers, David Zald (director of CAHBIR) signed it for Kaley in 2025. 
- **Make sure to fill in your own name on the second page of the POI Form 2024** 


2. If you don’t have an account on Eris, apply for an account by signing in with your MGB login and filling out the form here: [registration link](https://rc.partners.org/node/3687) — [https://rc.partners.org/scic-cluster-account-request](https://rc.partners.org/scic-cluster-account-request) 
    - **Form field answers:**
        
    - ERISOne Linux Cluster Account Request Form
    - Submitted by user: <netID>
    - MGB Username: <netID>
    - Full Name: <Your name>
    - Position: Research Collaborator EW
    - Department: RSCH Imaging Center-Baker
    - Institution: The McLean Hospital Corporation
    - Email: <netID>@mgb.org
    - Phone: <enter your phone number>
    - Office Location: REMOTE
    - Principal Investigator: Justin Baker
    - Principal Investigator's Email: <justin's email>
    - Principal Investigator's Mass General Brigham ID: jtbaker
    - Grant or Project ID?: Blank
    - Access Methods: Linux command line using SSH
    - Briefcase Group (PAS): sbdp, MCL-ITP_ERIS1-G, mcl-sbdp-eris1-g
    - Data Classification: de-identified human subjects data
    - Lab or storage group: None
    - Purpose: Research
    - Storage Required: Up to 50GB
    - Area of Study: Other (describe in comments section)
    - Applications: python3, pandas, numpy, rclone
    - Comment: 
    - "Please add to group sbdp. Area of study: Digital phenotyping. I am the research assistant for Dr Avram Holmes at Rutgers University, and we're collaborating with Dr Justin Baker at McLean. We are doing a joint data collection, and I will be using the Eris servers to rclone the de-identified and some identifiable data from Dr Baker's data collection into the Rutgers servers to compile the full dataset of the joint data collection. Dr Baker's lab members will be putting data for me in a specific folder and I'll be syncing that specific folder to the Rutgers cluster. My access to this data and the joint sharing of PHI data is all approved in a McLean IRB and Rutgers IRB."
3. If you don’t have “Windows App” setup follow this tutorial: →  [How To: Intune - Enroll Your Personal Mac](https://partnershealthcare.service-now.com/kb_view.do?sysparm_article=KB0041620)

→ following this tutorial: [HOWTO: Configure and Connect to VPN on a Mac](https://partnershealthcare.service-now.com/isservicehub?id=kb_article_view&sysparm_article=KB0033989&sys_kb_id=83f8cb2edb3e8b48dcc93a90ad96197f&spa=1)  



4. Access the MGB VPN by opening Cisco AnyConnect
    1. enter domain: **pvc.partners.org/saml**
    2. enter MGB ID and password

5. Follow instructions in "Sign into Eris each time"

---

ERIS Information: [https://rc.partners.org/it-services/computational-resources#erisone-linux-cluster](https://rc.partners.org/it-services/computational-resources#erisone-linux-cluster) 

The ERIS Linux Cluster is an ecosystem of scientific 
computing resources centered around a cluster of remote-desktop 
and compute nodes connected to very high speed storage. A large 
selection of popular scientific applications are installed and you can 
request additional software packages to be added.  The cluster runs a 
Linux operating system and requires some familiarity with Linux for 
efficient use.

This platform is ideal for workflows that run many jobs in parallel, 
and for those that read and write many files or require very high speed 
access to data files.  A job scheduling system queues jobs for dispatch 
to the compute nodes, allowing submission of many jobs at once.  Linux 
remote-desktop nodes allow graphical applications for data visualization
 to interacting with data stored on the cluster, as well as software 
development and application testing.  Some research groups also dispatch
 analysis pipeline jobs to the cluster through custom web-portals.

### Typical Uses

- Medical image processing
- Genome sequencing
- Monte-carlo modeling
- MPI parallel workloads
- Very large memory jobs
- AI/ML and Deep Learning using NVIDIA GPUs

### Supported methods of connecting to the cluster

- SSH command line terminal for job submission
- NoMachine Linux remote desktops for graphical applications
- Network file share (SMB/CIFS) for data transfer
- Web portals and applications (R Studio, Jupyter, etc)

Getting an account?

- Use the [registration link](https://rc.partners.org/node/3687) — [https://rc.partners.org/scic-cluster-account-request](https://rc.partners.org/scic-cluster-account-request)