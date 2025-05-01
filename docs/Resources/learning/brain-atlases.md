---
title: Brain Network Analysis (using Atlases)
parent: Learning
nav_enabled: true 
---

# Brain Network Analysis (using Atlases) Primer

Date: January 19, 2024 2:41 PM

Brain functional-connectivity network-analysis data pipeline is generally: 

voxel → region → network. 

So the voxels aren’t a network, the voxels get assigned to regions, and then network analysis is done on the 100-500 regions (which are groups of the voxels), with each of the regions being one ‘node’ in the brain network. 

*Brain Network Analysis Pipeline*

### First level of analysis: Voxels from the fMRI scan directly

- ex: cortex surface = ~60,000 vertices
    - do alignment, corrections, other preprocessing
- 2 common preprocessing pipelines:
    - Glasser 2013, aka Human Connectome Project Pipeline
    - fMRI Prep
- lots of distortion corrections to be done to find the same voxel in two different brains, if you’re trying to cross-examine voxels

### **Second level: the region-level**

- Algorithms tend to find 100-500 regions
- Finding communities, so that you can run the analysis on 100-500 nodes, instead of 60,000 nodes (which would take years)
- You can use an algorithm to find the communities/modules in your data
    - looking for voxels with similar patterns of activation (aka “coactivation”, “time-series dependencies”, “functional connectivity”)
    - Using methods like louvin communities, or machine learning methods, or clustering methods, community detection, multi-modal parcellation, clustering, physical location, historical precedent
        - this is the parcellation
        - brain regions are referred to as brain parcels
        - tho people may also say ‘brain node’
- Can also apply other researchers’ *atlases* to your fMRI data, instead of finding your own regions
    - called “partitioning” or “parcellation” or “using a hard partition”
    - list of all atlases: [https://www.lead-dbs.org/helpsupport/knowledge-base/atlasesresources/cortical-atlas-parcellations-mni-space/](https://www.lead-dbs.org/helpsupport/knowledge-base/atlasesresources/cortical-atlas-parcellations-mni-space/)
    - if you were to make a adjacency matrix of the FC of all your voxels to each other, you’d see a random array of correlations
        - partition (by an atlas) = indexing vector to sort the matrix
            - shows the communities structure
    - take the vertices/voxels from your data and then use someone else’s region parcellation (like yeo, shafer, glasser) and it indexes which vertices → which region
        - 5 total popular partitions
        - Partitions used because people kept applying community detection and found the same networks/communities/modules over and over again
        - this is called using a ‘hard partition’
        - other people have found these partitions

### Third level: brain network

- take regions and connect them into networks - based on coactivation (activity measuring -> Pearson’s correlation) for all of the regions against each other
- divide those regions into groups to find 5-20 networks
    - network = statistical dependency, pattern of coactivation
        - nodes = physical regions defined by the positions of the voxels (or verticies, if you’re using surface data) on the brain which were indexed into that region
    - edge value between two nodes = statistical dependency of time series between two regions
        - pearsons correlation of activation is a common method to calculate statistical dependency
- people may say ‘partition’ for network
- or may say ‘parcellation’ for network
- or ‘atlas’”

Common Atlases

- Yeo atlas = Yeo regions = 400 yeo/shafer regions
- Glasser atlas = mmp = multi-modal parcellation
- 5 total popular partitions
- using another researcher’s found partition is called “using a hard partition”

What is the scale of this data?

vertex

- 160,000 vertices across a brain = the mesh
- ‘vectorized topology’
- taken down to 91,000 number of usable vertices
    - cortex/cortical vertices: 60,000
    - subcortical: 31,000

functional connectivity matrices

- usually at the region level
    - region-level analysis
- since using 60,0000x60,0000 fc matrix would take forever to do a whole dataset
    - or you can choose specific regions or other ways to reduce the # of vertices
- MVPA or RSA still use voxel- or vertex-level analysis
    - what pattern of activation is most related to some function/task
- there’s also first- and second-level analyses aka task contrast
    - this is for quality control
    - to relate a specific region with a task
    - that will use voxel- or vertex-level analysis
        - statistical significance testing
        - multiple comparison testing

- Parcellation: Brain Region Level
    - 100-500 regions
        - people may also say ‘brain node’, ‘node’, ‘parcel’, ‘brain parcel’ instead of ‘region’
    - this is the ‘parcellation’

- Brain networks
    - they take regions and connect them into networks
    - 5-20 networks
    - people may say ‘partition’ for network
    - or may say ‘parcellation’ for network
    - or ‘atlas’
    
    Coding 
    
    Nilearn:
    

- self code
    - figure out how to access the access the 4D data
    - figure out how to resample the atlas to the data
    - create a dictionary nested datastructure for a single TR
    - loop for all 1200 TR
    - extract averages
    - pearson’s correlation
- nilearn:
    - use Nilearn atlas to do datastructure
    - extract averages
    - pearson’s
    
    compare self-code to nilearn package