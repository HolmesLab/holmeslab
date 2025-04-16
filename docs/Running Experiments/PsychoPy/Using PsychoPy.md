---
title: Using PsychoPy
parent: Running Experiments
nav_enabled: true 
---
# Using PsychoPy

Date: January 7, 2025 5:04 PM

Tutorial

1. Download psychopy from [https://www.psychopy.org/download.html](https://www.psychopy.org/download.html) 
2. Open psychopy 
    1. if immediately crashing, try searching for your hidden folders in /Users/yourusername and delete folders called .psychopy3 .psychopy2
3. Open ‘coder’
4. Load in your file
5. press the green ‘run’ button
    1. if giving problems, try the following things:
    
    1. If on a mac, go to System Preferences → Security & Privacy → Privacy tab, then for ‘Accessibility’ and ‘Input Monitoring’, add Psychopy as an app who can access
    
    ![Screen Shot 2025-01-07 at 5.09.33 PM.png](Using%20PsychoPy%20174cf00eb936801fa53bddd32723eba2/Screen_Shot_2025-01-07_at_5.09.33_PM.png)
    
    1. Install `brew install portaudio`, `brew install libsndfile`, `brew install portmidi`, `brew install liblo` and then `brew install —cask psychopy` and then `brew install pipx`
        
        `pipx install psychopy-sounddevice`, `pipx install psychopy-ptb`, `pipx install  psychopy-pyo`
        
        ended up also having to install git, gitpython, libsndfile, curl, pipx, and then trying to install psychopy from the command line instead of from the standalone since i was still getting dependency issues
        
    2. if needed to change  preferences, go to builder and click the grey ‘gear’ icon to alter settings. cannot alter settings of already-built scripts via this— this is just how you alter stuff for building scripts. 
    
    JUSt KIDDING all of that is for nothing i have to redo it all in a virtual environemnt pythonenv
    
    AND THEN redo it in psychopy-env becuase i ended up needing to use python3.11 for some reason? we’ll see if this works
    
    ```python
    brew install python@3.11
    python3.11 -m venv ~/venvs/psychopy-env
    brew link --overwrite python@3.11 --dry-run
    brew link --overwrite python@3.11
    source ~/venvs/psychopy-env/bin/activate
    (psychopy-env) pip install --upgrade pip setuptools wheel
    (psychopy-env) pip install psychopy
    
    ```
    
    okay psychopy STILL won’t download because it needs the X Coder tools which are not available on this mac os.
    

```python
(psychopy-env) HolmesLab05sMBP:bin holmeslab05$ brew install qt
==> Downloading https://formulae.brew.sh/api/formula.jws.json

==> Downloading https://formulae.brew.sh/api/cask.jws.json
########################################################################################################### 100.0%
Warning: You are using macOS 10.13.
We (and Apple) do not provide support for this old version.
It is expected behaviour that some formulae will fail to build in this old version.
It is expected behaviour that Homebrew will be buggy and slow.
Do not create any issues about this on Homebrew's GitHub repositories.
Do not create any issues even if you think this message is unrelated.
Any opened issues will be immediately closed without response.
Do not ask for help from Homebrew or its maintainers on social media.
You may ask for help in Homebrew's discussions but are unlikely to receive a response.
Try to figure out the problem yourself and submit a fix as a pull request.
We will review it but may or may not accept it.

qt: A full installation of Xcode.app is required to compile
this software. Installing just the Command Line Tools is not sufficient.

Xcode can be installed from the App Store.
molten-vk: A full installation of Xcode.app 11.7 is required to compile
this software. Installing just the Command Line Tools is not sufficient.

Xcode 11.7 cannot be installed on macOS 10.13.
You must upgrade your version of macOS.
Error: qt: Unsatisfied requirements failed this build.

```