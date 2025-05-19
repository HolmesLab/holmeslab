---
title: Connecting to Amarel
parent: Amarel Computing
nav_enabled: true 
nav_order: 1
---

## Connecting to Amarel in Terminal
1. **Connect to VPN on Cisco Anyconnect App** [Tutorial](https://holmeslab.github.io/holmeslab/docs/Amarel/rutgers-vpn/)

    1. fill in on Cisco Anyconnect app:
        1. [vpn.rutgers.edu](http://vpn1.rutgers.edu) 
        2. NetID password 
        3. DUO mobile password
    2. or webpage: [https://vpn1.rutgers.edu/+CSCOE+/logon.html#form_title_text](https://vpn1.rutgers.edu/+CSCOE+/logon.html#form_title_text) 


2. **Now, in your terminal...**
    1. On terminal or shell scripting application, Enter `ssh netID@amarel.rutgers.edu` (replace with your NetID)
    2. prompts for password- Enter NetID password

3. **Activate Environment**
    1.  `conda activate /projects/community/holmesenv`


### Connecting to Amarel Online Jupyter Notebook
1. Connect to VPN
2. Start a jupyter notebook etc. session  [https://ondemand.hpc.rutgers.edu](https://ondemand.hpc.rutgers.edu/)
    1. Go to [https://ondemand.hpc.rutgers.edu](https://ondemand.hpc.rutgers.edu/) for the GUI
    2. Go to dashboard → interactive apps → Personal Jupyter
        
        **Recommended Settings**
        Partition: p_dz268_1 (CAHBIR Partition)
        Hours: 72 (max is 8064)
        Conda Path: projects/community/holmesenv 
        Conda Environment: holmesenv
5. Launch session
6. In Jupyter Notebook, if necessary, make sure you’re in the holmesenv conda
    1. Select in toolbar *Kernel>Change kernel>holmesenv*
    