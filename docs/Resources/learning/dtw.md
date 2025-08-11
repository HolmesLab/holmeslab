---
title: Dynamic Time Warping (DTW)
parent: Neuroscience Learning Resources
nav_enabled: true 
---

# Dynamic Time Warping (DTW)

Date: February 24, 2025 3:57 PM

*Created by Kaley Joss, 08.15.2024*

*Sources: [https://www.cs.unm.edu/~mueen/DTW.pdf](https://www.cs.unm.edu/%7Emueen/DTW.pdf)* 

**Contents**

---

# Dynamic Time Warping (DTW)

***How to write it accurately, and efficiently.*** 

## Why use DTW?

- Almost always wins on extracting features vs. attempting to create feature vectors to characterize something
    
    ![Screenshot 2024-08-15 at 9.46.18 AM.png](Dynamic Time Warping (DTW) 1a4cf00eb9368056bcd1ece535ed58f5/Screenshot_2024-08-15_at_9.46.18_AM.png)
    

### Why efficiency?

- Efficiency: You can use DTW to search one billion
subsequences in under two minutes, using all the “tricks”
shown in this tutorial. However a naïve off-the-shelf recursion-
based DTW implementation would take six years.
- Effectiveness: While DTW is quite robust, there are some
“silly” things you could do to cripple its effectiveness; not z-
normalizing, set the wrong warping window, enforcing the
endpoint constraint in certain datasets…

## How is DTW Calculated?

1. For 2 1D timeseries, Q and c, length len(Q) and len(c), it creates a matrix size len(Q) by len(c) and fills the matrix with the euclidian (or some other distance measure) between every pair of points (not just those at the same time).

![Screenshot 2024-08-15 at 9.49.18 AM.png](Dynamic Time Warping (DTW) 1a4cf00eb9368056bcd1ece535ed58f5/Screenshot_2024-08-15_at_9.49.18_AM.png)

1. Then, a path touching each timepoint of both timeseries is calculated, with the distance matrix, to sub to the least total distance. (k=1):

![Screenshot 2024-08-15 at 9.57.31 AM.png](Dynamic Time Warping (DTW) 1a4cf00eb9368056bcd1ece535ed58f5/Screenshot_2024-08-15_at_9.57.31_AM.png)

$$
DTW(Q,c) = min\lbrace\sqrt{\mathstrut a}\textstyle\sum_k^Kw_k / K

$$

***Visualization:***

![Screenshot 2024-08-15 at 10.11.20 AM.png](Dynamic Time Warping (DTW) 1a4cf00eb9368056bcd1ece535ed58f5/Screenshot_2024-08-15_at_10.11.20_AM.png)

 

### Functions to achieve this:

**Recursive Function**

“Starting at $i,j = (0,0)$, search all possible ‘steps’ at the adjoining cells of the matrix (1,1) (1,0) (0,1) and take the one with the least distance.”

- Using warping constraint *w, can* weight it towards the diagonal step (1,1) to discourage ‘warping’ away from time-locked movement
    - In data mining, ‘seems to make little difference’?

**Iterative Function**

- Equivalent to recursive function, no logical difference
- Orders of magnitude faster

<aside>
🛠 ****Important note: Defaults to Boundary Condition**

Constraint that DTW must match the pairs of beginning and end points, even though they may be a poor match.

</aside>

## Choices to Consider when Running DTW

### DTW: Time and Space Complexity

- The “off-the-shelf” DTW has
    - a time complexity of  $O(n^2)$ (with a large constant factor)
    - a space complexity of $O(n^2)$
- Efficient DTW version can have
    - a space complexity of $O(n)$
    - an amortized time complexity of $O(n)$

### The Warping Constraint $*w*$

- The value of w is the maximum amount the warping path is allowed to deviate from the diagonal.
- It is normally expressed as the ratio $w = r/n$  (or as a percentage)

**Impact of *w*:**

- The value chosen for w greatly affects accuracy and speed
- The value also is important for clustering
    - No warping = timelocked series, no non-time-equal clusters
    - Unlimited warping = clusters found by shape, time-independent
    - Optimal warping = clusters by time and shape. Time ranges

**How to choose $w$?** 

- Can test every value of w from $w=0$ to $w=20$, and measure accuracy
    - Different datasets have different optimal values or ranges of $w$
- The size of the dataset— more data = the error rate should decrease and the optimal size of *w* should get smaller
    - as the dataset gets bigger, DTW = euclidian distance
    - though DTW would probably still be faster
- Best value for classification (shortest distance between neighbor and exemplar) may not be the best value for clustering (mutual distance of group)

### Endpoints and Unequal Lengths

**Possibilities for using DTW on unequal lengths:**

1. Can compare them at unequal lengths
2. Can cut off the longer one so they have equal lengths
3. Could resample/interpolate them to have the same length

<aside>
🛠 ****Remember: defaults to Boundary Condition**

Constraint that DTW must match the pairs of beginning and end points, even though they may be a poor match.

</aside>

![Screenshot 2024-08-15 at 10.36.26 AM.png](Dynamic Time Warping (DTW) 1a4cf00eb9368056bcd1ece535ed58f5/Screenshot_2024-08-15_at_10.36.26_AM.png)

**Possible Fixes for Differently-Patterned Start/End**

1. Use a better extraction so that subsequences are more similar in their start/end point
2. Change the boundary condition

## Z-Normalization

<aside>
⚠️ 1. Always normalize
2. Normalizing entire sequence is *not* sufficient— you must normalize *each subsequence*

</aside>

# Multi-Dimensional DTW (MD DTW)

### How to Compute MD DTW: 2 Ways

- **Independent**: compute the DTW score for each dimension independently, and sum up each score
    - Best for times where the coupled variables are related but with time-lags or non-simultaneous impact
- **Dependent**: Create a single distance matrix that reflects the distance between each corresponding pair of time series, then find the single warping path and distance as per normal
    - Best for times where the coupled variables are impacted simultaneously by environmental/3rd factors
- If you’re not sure, you can always try both and compare the error rate

### How Many Dimensions?

- Could generalize to 1,000+ dimensions, but unlikely that >3 is useful— more dimensions = less accuracy
- Example: dataset of inertial movement from 36 different places on someone’s body while they perform