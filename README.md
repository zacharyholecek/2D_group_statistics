# 2D_group_statistics
Statistics and visualization of individual based simulations in 2D. 

# Purpose
Fast collection of group data and visualization of directed individuals in 2D plane. Useful for quickly quanitifying and visualizing group behavior. Easy to modify by adding more statistics or making the visualization better for your purposes.

# How to use
Download .ipynb file and add it to your working directory. To input use "import import_ipynb" and then import functions as necessary.

All methods take either a 4 column (no cluster data column) or 5 column pandas dataframe as input. 

If you want to add clusters to your data using DB scan call:

add_clusters(your_data_frame,episilon [see https://github.com/alitouka/spark_dbscan/wiki/Choosing-parameters-of-DBSCAN-algorithm], minimum sample amount, metric type (either built in to DBScan or "periodic", 2D boundary (as a 2-tuple, only needed for periodic metric type)). 

To get the summary statistics for all points your data call:

summary_statistics(your_df, precision, periodic). periodic is a 3-tuple [Bool, float, float]. periodic[0] is True or False depending on if you are using periodic boundaries. If true, then input periodic[1] and [2] as the 2D boundary lengths in the x and y direction. This assumes that the boundary runs from [0, periodic[1]] in the x direction and [0,periodic[2]] in the y direction. This method returns a dictionary with keys:

 'centroid' 
 'average_distance'
 'average_dir'
 'polarization'
 'angular_momentum'
 'number'
 'density'
 'elongation'
 'tilt'

To visualize clusters call:

visualize_clusters(your_df_with_clusters, window_length_x, window_length_y,periodic). Current implementation assumes that position values are small enough to be drawn without scaling. 

# Periodic Boundaries
Periodic boundaries are often an annoying to deal with when looking at clusters in a 2D plane. This implementation supports periodic boundary conditions for clustering and gathering statisitcs. 


# Biology
For biologists studying collective behavior in swarms, flocks, schools, etc. DBSCAN has natural parameters. Set epsilon equal to the median of the organism's "zone of interaction" range, and set min sample number to smallest natural group size.

