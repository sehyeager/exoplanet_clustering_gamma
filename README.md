# Using Machine Learning to categorize exoplanets.
## Executive Summary:

Problem Statement:  Can I use unsupervised machine learning to categorize exoplanets in novel and meaningful ways?
In this project, I am setting out to take openly available exoplanet data, and apply unsupervised machine learning to discover previously unknown classifications and relationships that may be useful to astronomers in the future.

1. Background
I have been fascinated by astronomy and outer space since I was a child.  I am by no means an expert in the field, but one of the most exciting parts of modern life is how many new worlds are being discovered all the time. These exoplanets hold so much potential for learning more about the universe around us, and so I hoped to learn a little more myself through this project.
 - What is an exoplanet?  Any planet found outside of our own solar system is counted as an exoplanet.  Some of these are the only planet in their system, some orbit binary star pairs, and even some are rogue planets without a star of their own.

2. Notebook Structure
  - https://github.com/sehyeager/exoplanet_clustering_gamma/blob/main/notebooks/cleaning-notebook.ipynb Initial read-in of data and imputation of null values
  - https://github.com/sehyeager/exoplanet_clustering_gamma/blob/main/notebooks/EDA.ipynb Exploratory data analysis, outlier examinations, summary statistics
  - https://github.com/sehyeager/exoplanet_clustering_gamma/blob/main/notebooks/Clustering.ipynb Clustering with BIRCH, DBScan, and KMeans models of planetary data.  

3. Data Collection
All data was taken from https://exoplanetarchive.ipac.caltech.edu/cgi-bin/TblView/nph-tblView?app=ExoTbls&config=PSCompPars, through their built-in CSV exporting features.  
Data Dictionary:
| Key             | Description                                                            |
|-----------------|------------------------------------------------------------------------|
| pl_name         | Name of the exoplanet                                                  |
| hostname        | Name of host star                                                      |
| disc_facility   | Name of facility credited with discovery of the exoplanet              |
| pl_orbper       | Orbital period of exoplanet, in Earth day units                        |
| pl_orbsmax      | Orbit Semi-Major Axis: the longest radius of an elliptic orbit         |
| pl_rade         | Length of exoplanet's radius, in units equal to Earth's radius         |
| pl_bmasse       | Mass of exoplanet, in units equal to Earth's mass                      |
| pl_orbeccen     | Eccentricity: amount by which the orbit deviates from a perfect circle |
| pl_insol        | Insolation flux: one way to measure equilibrium temperature            |
| pl_eqt          | Equilibrium temperature as modeled by a body only heated by its stars  |


4. EDA
Outliers are extremely frequent for every one of these features.  I debated culling all the outliers to only limit myself to exoplanets within a distribution spread, but I figured that would not be representative of reality.   I did, however, remove planets that were orders of magnitude beyond their nearest neighbor in each feature.  One planet, for example, has an orbital period of almost 20,000 Earth years.  I left that planet out.

5. Clustering
The first model I attempted to run was a BIRCH (Balanced Iterative Reducing and Clustering using Hierarchies) model, which operates by first clustering a small sample of the dataset and then applying that model to the whole dataset.  However, it resulted in almost the entire dataset being put into one cluster.  This is not helpful to my problem, at all!  The next model I attempted, DBSCAN, wound up with a similarly useless result.
I only found a measure of successful clustering after finding an optimal value for K in a KMeans model through the Elbow method.  With a KMeans model with a K value of 8, I ended up with a very imbalanced clusters.  Over half the dataset sits in one cluster, while 5 of the other clusters ranged from 100 to 700 exoplanets apiece.  Two clusters had less than ten exoplanets each.  
I examined these clusters through a Seaborn pair-plot, to see if I could find meaningful distinctions between these 8 clusters.  Disappointingly, though, I could not find any truth in the categories.  To my eyes, it seemed random, and I cannot make sense of how these planets were categorized by my model.  I tried searching for individual and well-known exoplanets in the dataset, but their categorizations offered no insight into the differences between the clusters.  

6. Conclusion and Futures
Due to my failure to find any meaningful insights in these clusters, I fail to reject my null hypothesis:  I cannot, given my current domain knowledge and resources, use unsupervised machine learning to categorize exoplanets in a meaningful way. In the future, if I had access to atmospheric data for these planets (gained from spectroscopy), I could maybe use that data to create more meaningful categories, and could thus reject my null hypothesis.  

Presentation Slide-deck: https://drive.google.com/file/d/1G-miUGp3QbGXchoKkpAFo4xX3YEL6seb/view?usp=sharing