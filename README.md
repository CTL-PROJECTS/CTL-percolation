General information about the CTL course available at https://ctl.polyphys.mat.ethz.ch/

# :wave: PROJECT Percolation 

Consider a binary *N* x *N* grid with *N*<sup>2</sup> sites and periodic boundary conditions. 
A fraction $\phi=n/N^2$ of sites is black (value 1), the remaining sites are white (value 0). Two examples for *N*=8 and $n=23$, i.e., $\phi=0.359$ are shown below. 

<img src="http://www.complexfluids.ethz.ch/images/PROJECT-percolation.png" width="70%">

Sites are denoted as 'bonded' if they share an edge of the grid.  Due to periodic boundary conditions, sites can also be bonded over the boundary (such as the outermost left and right sites in the 2nd panel). A different example for *N=5* highlighting the effect of periodic boundaries is given here. This time we show not only the grid, but also its four periodic images. 

<img src="http://www.complexfluids.ethz.ch/images/PROJECT-percolation-periodic.png" width="30%">

Within the central box, 16 sites are white, the other 9 are black or pink. There are exactly two connected clusters of sites (black and pink). Without periodic boundaries, the central box would carry three clusters for this example.

Sites belong to the same cluster if they are bonded. If there is at least one cluster that connects to itself over one of the periodic boundaries, the system is called 'percolated', otherwise not. The following figure shows the bonds, in addition to the sites. 

<img src="http://www.complexfluids.ethz.ch/images/PROJECT-percolation-bonds.png" width="70%">

## Task I
1. Write a function which reads one of the sample files provided in the DATA folder and returns the grid it contains. Each grid in the DATA folder carries just a single connected cluster. The name of the file should be the argumment of your code.   
3. write a routine **percolated_cluster** that takes *grid* as argument, and determines if the cluster connects to itsself over at least one of the boundaries (this is called an infinite cluster). The routine returns True for an infinite cluster, and False otherwise. 


## Task II
1. Write a routine **create_system** that takes *N* and *n* as arguments, and returns a binary N x N *grid* with *n* occupied sites, as well as the volume fraction. Occupied sites have value 1, unoccupied sites have value 0.
2. Write a routine **is_single_cluster** that takes *N* and *grid* as arguments, and returns True if all nodes belong to the same cluster, otherwise return False.
3. Fix *N=10* and vary *n* from 1 to *N*<sup>2</sup>. For each *n*, call **create_system** and **is_single_cluster** until you (eventually) obtain a system with a single cluster. If you cannot create a system with a single cluster within a reasonable time, skip this *n*.
4. For each generated system containing a single cluster, check if it is an infinite cluster, and display the result: (*n*,0/1), where 1 stands for 'Percolated'. 


## Task III

Write a routine **load_bearing_bonds** that takes *grid* as arguments. If the *grid* does not carry a single cluster, **load_bearing_bonds** returns -1. If **percolated_cluster** gives False, the **load_bearing_bonds** routine returns 0. If **percolated_cluster** gives True, the cluster is percolated, and this routine **load_bearing_bonds** attempts to return the smallest number of bonds that need to be cut to turn the percolated cluster into an unpercolated cluster. Such so-called load-bearing bonds are those that may fail first, if the system is subjected to strain, and the number of load-bearing bonds may be related to the mechanical strength of a percolated cluster. 

<img src="http://www.complexfluids.ethz.ch/images/PROJECT-percolation-lbb.png" width="70%">

This last figure shows a possible location of the single load-bearing bond. 
