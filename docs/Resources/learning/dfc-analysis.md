---
title: Dynamic FC Patterns
parent: Neuroscience Learning Resources
nav_enabled: true 
nav_order: 9
---

# Dynamic Functional Connectivity Patterns Analysis Methods

1. **Sliding Window Correlation Analysis**:
    - One of the most common approaches, where the time series data is segmented into overlapping or non-overlapping windows.
    - Functional connectivity is calculated separately for each window using measures like Pearson correlation or partial correlation.
    - Provides insights into the temporal dynamics of connectivity patterns.
2. **Dynamic Conditional Correlation Models**:
    - Extends traditional correlation analysis by allowing the correlation coefficient to vary over time.
    - Models the temporal evolution of connectivity using dynamic linear models or time-varying autoregressive models.
    - Captures changes in connectivity strength and directionality across different time points.
3. **Dynamic Graphical Models**:
    - Represent brain networks as graphs where nodes correspond to brain regions and edges represent functional connections.
    - Employ dynamic graphical models such as dynamic Bayesian networks or dynamic graphical LASSO to estimate time-varying connectivity patterns.
    - Allows for the identification of evolving network structures and connectivity dynamics.
4. **Hidden Markov Models (HMM)**:
    - Model the brain's dynamic connectivity states as a sequence of hidden states governed by transition probabilities.
    - Estimate the most likely sequence of hidden states given the observed fMRI data using the Viterbi algorithm or forward-backward algorithm.
    - Provides a framework for characterizing discrete brain states and transitions between them.
5. **Dynamic Connectivity Regression**:
    - Incorporates external variables or experimental conditions as regressors to investigate how they modulate dynamic connectivity patterns.
    - Fit a regression model to estimate the relationship between covariates and time-varying connectivity metrics.
    - Allows for the investigation of task-evoked or stimulus-dependent changes in functional connectivity.
6. **Time-Frequency Analysis**:
    - Decompose the fMRI time series data into different frequency bands using techniques like wavelet transform or Hilbert-Huang transform.
    - Estimate dynamic connectivity within each frequency band to capture oscillatory dynamics of brain networks.
    - Reveals frequency-specific changes in connectivity patterns over time.
7. **Functional Network Dynamics Analysis**:
    - Characterize the dynamics of functional brain networks using graph-theoretical measures such as modularity, network flexibility, or resilience.
    - Investigate how network properties evolve over time and their relationship to cognitive or behavioral states.
    - Provides insights into the reconfiguration of functional brain networks during different tasks or mental states.
8. **Deep Learning Approaches**:
    - Utilize deep learning architectures such as recurrent neural networks (RNNs) or convolutional neural networks (CNNs) to model the temporal dynamics of functional connectivity directly from fMRI data.
    - Train neural networks to predict future connectivity patterns based on past observations, enabling the capture of complex temporal dependencies.