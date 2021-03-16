# Using Machine Learning to categorize exoplanets.
## Executive Summary:
Problem Statement:  Can I use unsupervised machine learning to categorize exoplanets in novel and meaningful ways?
In this project, I am setting out to take openly available exoplanet data (from https://exoplanetarchive.ipac.caltech.edu/cgi-bin/TblView/nph-tblView?app=ExoTbls&config=PSCompPars), and apply unsupervised machine learning to discover previously unknown classifications and relationships that may be useful to astronomers in the future.

The metrics I relied upon were the silhouette score and the Elbow method, and through these I discovered the most impactful clustering method was a K Means model, with 7 clusters.  My model resulted in one cluster of about 2900 exoplanets, which is over half the dataset.  4 of the other clusters ranged in size from 100-800, and the last two clusters only had 4 and 1 exoplanet.  Despite this, to my eyes, many of these clusters seemed rather similar to each other, and so I cannot find any meaningful differences in these exoplanet clusters. I tried looking up specific planets that are used by NASA's exoplanet website (https://exoplanets.nasa.gov/what-is-an-exoplanet/planet-types/overview/) as examples of their normal categories, but 3 of them fell into the largest '1' cluster.  These planets are vastly different, but according to my model they belong to the same group.   Additionally, I tried examining a pair-plot of the data, using the labels as the hue for the points.  I could not discern any meaningful separations in the clusters.


As such, I fail to reject my null hypothesis:  I cannot, given my current domain knowledge and resources, use unsupervised machine learning to categorize exoplanets in a meaningful way. In the future, if I had access to atmospheric data for these planets (gained from spectroscopy), I could maybe use that data to create more meaningful categories, and could thus reject my null hypothesis.

Data Dictionary: https://exoplanetarchive.ipac.caltech.edu/docs/API_PS_columns.html

Presentation: https://drive.google.com/file/d/1G-miUGp3QbGXchoKkpAFo4xX3YEL6seb/view?usp=sharing