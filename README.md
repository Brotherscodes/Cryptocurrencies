# Cryptocurrencies

## Background:

Accountability Accounting, a prominent investment bank, is interested in offering a new cryptocurrency investment portfolio for its customers. The company, however, is lost in the vast universe of cryptocurrencies. So, they’ve asked you to create a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment.

## Project Overview: 

The data we are working with is not ideal so it will need to be processed to fit the machine learning models. There is no known output for what Accountability Accounting are seeking so we have decided to use unsupervised machine learning. Martha from Accountability Accounting and I have decided to use a clustering algorithm to group the currencies and many data visualizations to share our findings with the board of the company. We will complete our technical analysis following the steps outlined below:

<br>

- Pre-process the Data for PCA (Principal Component Analysis)
- Reduce data dimensions using PCA
- Cluster cryptocurrencies using K-means
- Create visualizations for our cryptocurrencies results

<br>

## Creating a 2D model using PCA:

<img src= Images/2d_model.png>

<br>

## Cryptocurrency Clustering with an Elbow Curve:

Since our output is unknown we had to identify clusters of cryptocurrencies in our data. Using K-means (1-10) we produced an Elbow Curve. The results show us that the best K-value is 4 meaning our data should be categorized into 4 clusters.




<img src= Images/elbow_curve.png>


# Creating a 3D-Scatter Plot with the PCA data and the clusters with three features:

<img src= Images/3d_scatterplot.png>


# Tradeable Cryptocurrencies:

<img src= Images/hvplot_table.png>

















<br>

## Summary:
After processing the data we were given, we determined there were 532 tradable cryptocurrencies.
## Resources:

- Software:

    - `VS Code`
    - `Pandas`
    - `Anaconda`
    - `Unsupervised Machine Learning`

<br>

- Resources:
    - `UCF-VIRT-DATA-PT-06-2022-U-B-TTH-Module 18`
    - `crypto_data.csv`
  