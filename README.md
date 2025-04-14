# Percolation
### 1.Introduction
In this project, the QuickFind and WeightedQuickUnion algorithms are respectively used to conduct porous material penetration simulation experiments, and Monte Carlo simulations are used to estimate the penetration threshold. The running time of the two algorithms is used to compare their performance differences.  

-----

### 2.Percolation
Given a composite system comprised of randomly distributed insulating and metallic materials: what fraction of the materials need to be metallic so that the composite system is an electrical conductor? Given a porous landscape with water on the surface (or oil below), under what conditions will the water be able to drain through to the bottom (or the oil to gush through to the surface)? Scientists have defined an abstract process known as percolation to model such situations.

-----

### 3.Model
We model a percolation system using an N-by-N grid of sites. Each site is either open or blocked. A full site is an open site that can be connected to an open site in the top row via a chain of neighboring (left, right, up, down) open sites. We say the system percolates if there is a full site in the bottom row. In other words, a system percolates if we fill all open sites connected to the top row and that process fills some open site on the bottom row. (For the insulating/metallic materials example, the open sites correspond to metallic materials, so that a system that percolates has a metallic path from top to bottom, with full sites conducting. For the porous substance example, the open sites correspond to empty space through which water might flow, so that a system that percolates lets water fill open sites, flowing from top to bottom.)  

In a famous scientific problem, researchers are interested in the following question: if sites are independently set to be open with probability p (and therefore blocked with probability 1 − p), what is the probability that the system percolates? When p equals 0, the system does not percolate; when p equals 1, the system percolates.

When N is sufficiently large, there is a threshold value p* such that when p < p* a random N-by-N grid almost never percolates, and when p > p*, a random N-by-N grid almost always percolates. No mathematical solution for determining the percolation threshold p* has yet been derived. Our task is to write a computer program to estimate p*.  

-----

### 4.Monte Carlo Simulation  
Monte Carlo simulation is a statistical method to obtain numerical results through random sampling. In the percolation problem, we estimate the percolation threshold by the following steps:
1. **Initialization**: An N×N grid is created with all stations initially blocked.  
2. **Random penetration experiment**: Randomly pick a blocked site and open it. This process is repeated until the system is first penetrated.  
3. **Record results**: Calculate the proportion of open sites at this time:
   $x_t = \frac{\text{Number of open sites}}{N^2}$
4. **Repeat experiment**: Perform T such experiments independently

**Sample mean (threshold estimation)**  

$$
\sigma = \sqrt{\frac{1}{T-1}\sum_{t=1}^T (x_t - \mu)^2}
$$  

**Sample standard deviation**  

$$
\sigma = \sqrt{\frac{1}{T-1}\sum_{t=1}^T (x_t - \mu)^2}
$$

**95% confidence interval**  

$$
\left[\mu - \frac{1.96\sigma}{\sqrt{T}},\ \mu + \frac{1.96\sigma}{\sqrt{T}}\right]
$$

**Example output**  
`Total running time: 46.924 seconds`  
`Example values after creating PercolationStats(1600, 100)`  
`Mean() = 0.5932255156249996`  
`StdDev() = 0.0022747205279140667`  
`95% Confidence Interval: [0.5927796704015285, 0.5936713608484707]`  
