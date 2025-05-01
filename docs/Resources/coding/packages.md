---
title: Packages for fMRI Analysis
parent: Coding
nav_enabled: true 
---

# Packages for fMRI Analysis
Date: December 8, 2023 11:50 AM
---
### Table of Contents
1. TOC
{:toc}
---

[Table of Tools for fMRI Analysis](https://sidchop.shinyapps.io/braincode_selector/) (by Sid Chopra, 2023)

Table by Kaley:

## **Preprocessing:**

- Reasons for distortion
    - motion artifacts
    - dropout (magnetic field not-consistent)
        - can somewhat correct using a *field map*
    - ghosting / electrical signal distortion
- **Slice Timing Correction:** Correct for differences in acquisition time between slices.
    - Data are collected 1 slice at a time
        - can make diff areas collected many seconds apart
        
- **Motion Correction:** Correct for head motion during the scan.
    - methods:
        - ICA -within scan effects of head-moving etc.
- **Spatial Normalization:** Transform the images to a standardized anatomical space.
- **Spatial Smoothing:** Apply a spatial filter to improve the signal-to-noise ratio.

---

## **Functional Connectivity Analysis:**

- [**Seed Correlation Analysis](https://fcp-indi.github.io/docs/latest/user/sca) (aka contrast values or parameter estimates)**
    - A region/voxel activation weights get extracted (eg beta-weights, or other HR-adjusted activation measure) and correlated:
        - to a specific target region (between subjects)
            - diff regions activate more, lots of 3rd factor compounding variables… this isn’t enough to = connectivity
            - neg correlation might be more sig?
        - across the brain  (within subjects)
            - most correlations here will be activation induced, see below vv
- **how to take out motion-activation, hemodynamic fluctuations and other activation-induced correlations?**
    
    methods:
    
    - extract + concatenate timepoints, then remove first 6 seconds to adjust for HDF
    - nuisance model
    - beta-series correlation
        - find the size of evoked response, and then correlate all the trials — fit a model using a separate regressor for each trial.
    - PPI
        - GLM + interactions between seed region x time and seed region x time x task
    - Multivariate Decomposition:
        - decomposing matrix into separate compontents → find active networks (aka “Matrix factorization” methods)
            - will find groups even if there aren’t groups
        
        Types of MFA:
        
        - **Principal Components Analysis**
            - assumption: groups gaussian & orthogonal
            - first group: direction thru data w/ most amt variance. 2nd group = second amt variace
            - pros: simple + easy to implement
            - cons: looking for orthogonal groups & will find even if they’re not there, only sensitive to gaussian distribution signals
            - may be used for data reduction (only use first few principal components)
            - method: format data into 2 dimensional matrix (voxels in one, timepoints in other), run
        - Independent Components Analysis
        
- ROIs + Atlas

---

## **Statistical Analysis:**

- **General Linear Model (GLM):** Model the hemodynamic response function for each voxel.
- **Group Analysis:** Combine data across subjects for group-level inferences.
- **Correction for Multiple Comparisons:** Adjust p-values for multiple tests to control for false positives.

---

## **Post-processing and Visualization:**

- **Result Visualization:** Visualize activation maps, connectivity matrices, or other relevant outputs.
- **Data Interpretation:** Interpret the results in the context of your research question.

---

### Tools

[FSL](https://open.win.ox.ac.uk/pages/fslcourse/website/index.html)* (Carrisa)

[SPM](https://www.fil.ion.ucl.ac.uk/spm/)* (Carrisa)

AFNI* (Carrisa)

We generally use the HCP preprocessing pipelines, which also implements a combination of the above and the whole pipeline is implemented either via shell scripting (linux & bash seems to be the vast preference), python, or MATLAB. See here:  [https://github.com/Washington-University/HCPpipelines](https://github.com/Washington-University/HCPpipelines)

May be accessed via:

- fMRI Prep
- Nipype
- FSL/SPM/Freesurfer Directly
- Via Jupyter notebook pushing BASH to these programs
- shell scripting files (.sh)

---

Packages/methods from:

[FSL](https://open.win.ox.ac.uk/pages/fslcourse/website/index.html)*

[SPM](https://www.fil.ion.ucl.ac.uk/spm/)*

AFNI*

[ANTs](http://stnava.github.io/ANTs/)

[FreeSurfer](https://surfer.nmr.mgh.harvard.edu/fswiki/FreeSurferWiki)

[MRTrix](https://www.mrtrix.org/) 

May be accessed via:

- fMRI Prep
- Nipype
- FSL/SPM/Freesurfer Directly
- Via Jupyter notebook pushing BASH to these programs
- shell scripting files (.sh)

---

Python Data Science Packages (Sklearn, Scipy) (Carrisa)

May be accessed via:

- fMRI Prep
- Nipype
- FSL/SPM/Freesurfer Directly
- Via Jupyter notebook pushing BASH to these programs
- shell scripting files (.sh)

---

Find tools via: [https://sidchop.shinyapps.io/braincode_selector/](https://sidchop.shinyapps.io/braincode_selector/) 

HCP Workbench

FSL Eyes

Pysurfer

Nilearn

Surplt

HCPUtils

May be accessed via:

- HCP
- fMRI Prep
- Nipype
- FSL/SPM/Freesurfer Directly
- Via Jupyter notebook pushing BASH to these programs
- shell scripting files (.sh)

---

- **Shell Scripting**
    
    linux & bash (majority of lab)
    
- **GUI/IDE**
    
    Jupyter Lab (Carrisa)
    
    R (half the lab)
    
    [Nipype](https://nipype.readthedocs.io/en/latest/) & [C-PAC](https://fcp-indi.github.io/docs/latest/user/index) 
    
- **Preprocessing**
    
    [FSL](https://open.win.ox.ac.uk/pages/fslcourse/website/index.html)* (Carrisa)
    
    [SPM](https://www.fil.ion.ucl.ac.uk/spm/)* (Carrisa)
    
    AFNI* (Carrisa)
    
    We generally use the HCP preprocessing pipelines, which also implements a combination of the above and the whole pipeline is implemented either via shell scripting (linux & bash seems to be the vast preference), python, or MATLAB. See here:  [https://github.com/Washington-University/HCPpipelines](https://github.com/Washington-University/HCPpipelines)
    
- **Functional Connectivity Analysis**
    
    [ANTs](http://stnava.github.io/ANTs/)
    
    [FreeSurfer](https://surfer.nmr.mgh.harvard.edu/fswiki/FreeSurferWiki)
    
    [MRTrix](https://www.mrtrix.org/) 
    
- **Statistical Analysis**
    
    [Tracula](https://surfer.nmr.mgh.harvard.edu/fswiki/Tracula) 
    
    Python Data Science Packages (Sklearn, Scipy) (Carrisa)
    
- **Post-processing and Visualization**

- **Diffusion MRI**
    
    = measures the diffusion (movement direction & magnitude) of water molecules in the brain; primary method of studying macroscale brain activity
    
    works because axons = water barriers, so the water must flow along the axon
    
- **Voxel**
    
    A point in space and time in a 3D region
    
- **hemodynamic response (HR)**
    
    hemodynamic fluctuation in the BOLD response, need to control it out to get real measures of activation
    
- **Region of Interest (ROI)**
    
    Define specific brain regions or regions of interest for connectivity analysis.
    
- **Seed-Based Analysis** (SCA)
    
    Examine connectivity patterns from a seed region.
    
- **Independent Component Analysis (ICA)**
    
    Identify independent components representing functional networks.
    
- **nuisance model**
    
    method to remove unwanted activation-based correlation. basically fitting a model that explains the variation from the task and the activation. then control based on that model, and analyze other regions for their residuals
    
- **beta series model**
    
    response to each event estimated w/ a separate regressor for each trial
    
    correlation between these regressors shows correlations between-trials of diff regions
    
    *need 8-10secs between trials to control for HR
    
- **Psychophysiological Interaction (PPI)**
    
    models how activity in seed region is modulated by some other factor (task)
    
- **General Linear Model (GLM)**
    
    estimates the coefficient of the task interaction over the timecourse
    
- **deconvolution**
    
    most likely neuronal signal that would have given rise to that fMRI signal
    
- **principal components
analysis (PCA)**
    - *PCA is a method for reexpressing a dataset in terms of a set of components*
    *that are uncorrelated,*
- **matrix factorization analysis (MFA)**
    
    decomposing matrix into separate compontents → find active networks
    
- **orthogonal**
    
    uncorrelated
    
- **large-scale** **dynamical circuit model**:
    
    computational framework that aims to simulate and understand the complex interactions and dynamics of neural circuits on a large scale (ie many circuits and neurons)
    
- **dynamic**
    
    time dynamics, patterns of activity over time
    
- **dynamic connectivity**
    
    signal correlation between 2 regions over time 
    
- **stochastic**
    
    random
    
- **neuronal dynamics**
    
    changes in electrical and chemical activity of neurons and network as a whole
    
- **synchrony**:
    
    simultaneous action / occurrence
    
- **spontaneous brain activity aka resting state analysis**
    
    analyzing which areas are firing simultaneously/connectedly while the body is at rest in the fMRI scanner 
    
- **local circuit properties**
    
    average properties of the neural circuitry in different regions of the brain. ie synaptic strength, firing rate, and other anatomical and functional properties
    
- **index of**
    
    serve as a representative, proportional or indicative measure of another property 
    
- **principal resting-state functional connectivity (FC) gradient**
    
    the gradual change or variation in functional connectivity across the brain
    
    strength observed between different brain regions
    
- **parcellation**
    
    division of something into subsections 
    
- **temporal resolution**
    
    how accurate it is to real-time— for neuroimaging, measuring every millisecond = high temporal res (EEG is this), measuring every 2 seconds = low (fMRI is this)
    
- **Pearson correlation**
    
    Common correlation metric to measure how correlated two data series are
    
- **sliding window correlation (SWC) analysis**
    
    approach for evaluating dynamic functional connectivity
    
    computes a succession of pairwise correlation matrices using the time series from a given parcellation of brain regions
    
    method: 
    
    1. define window size (aka time points within the whole scan, aka temporal resolution)
    2. for each time point: 
        1. create correlation matrix for each brain regions to all of the others (correlation measure like Pearson correlation
        2. stack onto all other matrices
    3. → creates set of matrices = connectivity over time (aka dynamic connectivity)
    4. compute statistics for this set of matrices
- **tensor**
    
    multilayer matrix— matrices tend to have only 2 dimensions, X and Y, but a tensor can have infinite dimensions, to build more and more metadata and higher-order analysis into the nodes and links characterized by the connections matrix
    
- **functional connectivity vs diffusion MRI**
    
    Diffusion
     MRI (dMRI) and fcMRI have recently emerged as promising tools for 
    mapping the connectivity of the human brain, each with distinct 
    strengths and weaknesses. dMRI measures the diffusion of water, thus 
    allowing direct noninvasive mapping of white matter pathways ([Basser et al. 1994](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3174820/?report=printable#B12)).
     However, dMRI is presently limited to resolving major fiber tracts. By 
    contrast, fcMRI measures intrinsic functional correlations between brain
     regions ([Biswal et al. 1995](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3174820/?report=printable#B19)) and is sensitive to coupling between distributed as well as adjacent brain areas (e.g., see [Sepulcre et al. 2010](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3174820/?report=printable#B180)
     for discussion). Although not a direct measure of anatomical 
    connectivity, the functional couplings detected by fcMRI are 
    sufficiently constrained by anatomy to provide insights into properties 
    of circuit organization (for reviews, see [Fox and Raichle 2007](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3174820/?report=printable#B66); [Van Dijk et al. 2010](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3174820/?report=printable#B206)). When describing these correlations, we use the term functional connectivity as coined by Karl [Friston (1994)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3174820/?report=printable#B70) to denote “temporal correlations between remote neurophysiological events” for which the causal relation is undetermined.
    
    There
     are important limitations of fcMRI, including sensitivity to indirect 
    anatomical connectivity and functional coupling that changes in response
     to recent experience and the current task being engaged ([Buckner 2010](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3174820/?report=printable#B27)).
     For these reasons, some discussions of fcMRI have emphasized that 
    intrinsic activity measured by fcMRI reflects the prior history of 
    activity through brain systems and not simply static anatomical 
    connectivity ([Power et al. 2010](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3174820/?report=printable#B157)).
     fcMRI also does not presently provide information about whether 
    connections are feedforward (ascending) or feedback (descending). These 
    limitations constrain how analyses are conducted and results can be 
    interpreted.
    
- **FreeSurfer**
    
    [FreeSurfer](http://surfer.nmr.mgh.harvard.edu/) is software that constitutes a suite of automated algorithms for 
    reconstructing accurate surface mesh representations of the cortex from 
    individual subjects' T1 images ([Fig. 1](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3174820/figure/F1/), *B* and *C*) and the overlay of fMRI on the surfaces for group analysis
    
- **silhouette**
    
    the silhouette of a data point  measures the similarity of the data point to other data points of the same cluster compared with data points belonging to the next closest cluster
    

- **large-scale** **dynamical circuit model**:
    
    computational framework that aims to simulate and understand the complex interactions and dynamics of neural circuits on a large scale (ie many circuits and neurons)
    
- **dynamic**
    
    time dynamics, patterns of activity over time
    
- **dynamic connectivity**
    
    signal correlation between 2 regions over time 
    
- **stochastic**
    
    random
    
- **neuronal dynamics**
    
    changes in electrical and chemical activity of neurons and network as a whole
    
- **synchrony**:
    
    simultaneous action / occurrence
    
- **spontaneous brain activity aka resting state analysis**
    
    analyzing which areas are firing simultaneously/connectedly while the body is at rest in the fMRI scanner 
    
- **local circuit properties**
    
    average properties of the neural circuitry in different regions of the brain. ie synaptic strength, firing rate, and other anatomical and functional properties
    
- **index of**
    
    serve as a representative, proportional or indicative measure of another property 
    
- **principal resting-state functional connectivity (FC) gradient**
    
    the gradual change or variation in functional connectivity across the brain
    
    strength observed between different brain regions
    
- **parcellation**
    
    division of something into subsections 
    
- **temporal resolution**
    
    how accurate it is to real-time— for neuroimaging, measuring every millisecond = high temporal res (EEG is this), measuring every 2 seconds = low (fMRI is this)
    
- **Pearson correlation**
    
    Common correlation metric to measure how correlated two data series are
    
- **sliding window correlation (SWC) analysis**
    
    approach for evaluating dynamic functional connectivity
    
    computes a succession of pairwise correlation matrices using the time series from a given parcellation of brain regions
    
    method: 
    
    1. define window size (aka time points within the whole scan, aka temporal resolution)
    2. for each time point: 
        1. create correlation matrix for each brain regions to all of the others (correlation measure like Pearson correlation
        2. stack onto all other matrices
    3. → creates set of matrices = connectivity over time (aka dynamic connectivity)
    4. compute statistics for this set of matrices
- **tensor**
    
    multilayer matrix— matrices tend to have only 2 dimensions, X and Y, but a tensor can have infinite dimensions, to build more and more metadata and higher-order analysis into the nodes and links characterized by the connections matrix
    
- **tractography**
    
    involves defining white matter connections at
     the macroanatomical scale, which permits the measurement of 
    connectivity strengths by counting the streamlines that link each pair 
    of regions. Streamlines are constructed to pass through multiple 
    adjacent voxels in DTI data, when the principal diffusion tensor per 
    voxel aligns well with some of its direct neighbors ([*9*](https://www.science.org/doi/10.1126/sciadv.add2870#core-R9)).
     Tractography therefore produces subject-specific measures of regional 
    interconnectivity that are ideally suited for brain network-level 
    analysis.
    
- **Diffusion tensor imaging (DTI)**
    - enables in vivo noninvasive study of white matter in the brain ([*6*](https://www.science.org/doi/10.1126/sciadv.add2870#core-R6)).
     This technique characterizes the diffusion of water molecules, which 
    occurs preferentially in parallel to nerve fibers due to constraints 
    imposed by axonal membranes and myelin sheaths ([*7*](https://www.science.org/doi/10.1126/sciadv.add2870#core-R7)).
     Metrics commonly derived from DTI, such as fractional anisotropy or 
    mean diffusivity, reflect white matter microstructure and can index its 
    integrity ([*7*](https://www.science.org/doi/10.1126/sciadv.add2870#core-R7), [*8*](https://www.science.org/doi/10.1126/sciadv.add2870#core-R8)).
- **MNI Space**
    
    defines the boundaries around the brain, expressed in millimeters, from a set origin
    
- **White Matter**
    
    White matter structures are largely composed of axonal fibres and myelin sheaths. Communication of neurons with far-away other neurons
    
- **Grey Matter (Gray)**
    
    Pyramidal and other types of neuronal cell bodies, and their dendrites. Communication of neurons and close-by neighbors
    
- **Diffusion tensor imaging (DTI)**
    
    = model for parsing diffusion MRI data, the measurements acquired for the different directions are put into a 3x3 matrix called a **tensor**, which can then be defined by eigenvectors and eigenvalues.
    
- **a priori approach**
    
    have them do a task, that area that lights up = the area related to that task 
    
    - not always translatable to differrent modalities
- **field map**
    
    uses a image at two separate echo times to compute the difference in the magnetic field, and tehn apply that to the area with dropout, to estimate what the og reading should have looked like 
    

- **independent component analysis (ICA)**
    
    “*finds a set of components*
    *that are independent of one another”* ex: boundaries identified in the brain through the analysis of functionally specialized areas
    

- **validated parcellation scheme**
    
    research-based mapping of functional sections of the brain