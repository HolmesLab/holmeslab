---
title: Pipeline Outline for dFC Research
parent: Learning Resources
nav_enabled: true 
nav_order: 2
---

# Pipeline Outline for dFC Research

Date: January 31, 2024 10:05 AM

How to take a Pearson's correlated data set of brain regions, and investigate across-state network dynmics:

1. **Data Acquisition and Preprocessing**:
    - Obtain a dataset containing brain imaging data, typically functional magnetic resonance imaging (fMRI) or electroencephalography (EEG) data.
    - Preprocess the data to remove noise, artifacts, and ensure data quality. This may involve steps such as motion correction, spatial normalization, and temporal filtering.
    - See [Preprocessing Pipeline](https://www.notion.so/Pre-Processing-fMRI-Data-cd24a0ec0f6140728bd5cb290934031d?pvs=21) doc
2. **Defining Brain Regions of Interest (ROIs)**:
    - Define a set of brain regions based on anatomical or functional parcellation schemes. These regions can be defined using atlases like AAL (Automated Anatomical Labeling) or the Harvard-Oxford atlas for structural MRI, or functional networks obtained from resting-state fMRI data using techniques like independent component analysis (ICA) or clustering algorithms.
    - Extract time series data from each ROI.
3. **Calculating Pearson's Correlation**:
    - Calculate the Pearson correlation coefficient between the time series data of all pairs of ROIs. This yields a correlation matrix where each element represents the strength and direction of the linear relationship between the time series of two brain regions.
4. **Dynamic Network Analysis**:
    - Utilize dynamic network analysis techniques to investigate changes in brain network properties across different states or conditions. This may involve methods such as sliding window correlation analysis, time-varying connectivity analysis, or dynamic functional network connectivity (dFNC) analysis.
    - Apply a sliding window approach to compute correlation matrices over consecutive time windows, allowing for the examination of temporal fluctuations in network connectivity.
    - Explore changes in network properties such as modularity, connectivity strength, or network flexibility across different states or experimental conditions.
5. **State Identification**:
    - Define the states or conditions of interest based on experimental design or observed differences in brain activity.
    - Use statistical methods or clustering algorithms to identify distinct network states or transitions between states based on dynamic network properties.
6. **Statistical Analysis**:
    - Conduct statistical analysis to assess the significance of differences in network dynamics between states. This may involve techniques such as permutation testing, analysis of variance (ANOVA), or non-parametric tests.
7. **Interpretation and Visualization**:
    - Interpret the results in the context of the experimental hypotheses or research questions.
    - Visualize dynamic network properties and state transitions using techniques such as time-resolved network graphs, state space diagrams, or dynamic network metrics over time.
8. **Validation and Reproducibility**:
    - Validate findings using appropriate validation techniques such as cross-validation, bootstrapping, or independent dataset validation.
    - Ensure reproducibility by documenting data preprocessing steps, analysis pipelines, and code/scripts used for analysis.

By following these steps, researchers can investigate how brain network dynamics vary across different states or conditions using Pearson's correlated data set of brain regions, providing insights into the functional organization of the brain.