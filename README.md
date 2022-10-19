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

Please reference the code to follow along [crypto_clustering.ipynb](https://github.com/Brotherscodes/Cryptocurrencies/blob/main/crypto_clustering.ipynb)

## Reducing Data Dimensions and Creating a 2D model using PCA:

A scatter plot was created to show cryptocurrencies grouped in their respective class. In a graph with total coins mined and total supplied as the axis we see two outliers, `BitTorrent` and `TurtleCoin`.

    # Create a hvplot.scatter plot using x="TotalCoinsMined" and y="TotalCoinSupply".
    plot_df.hvplot.scatter(
            x='TotalCoinsMined',
            y='TotalCoinSupply',
            hover_cols=['CoinName'],
            by='class'
    )
    


<img src= Images/2d_model.png>

<br>

## Cryptocurrency Clustering with an Elbow Curve:

Since our output is unknown we had to identify clusters of cryptocurrencies in our data. In the code below we produced an Elbow Curve to determine the value of K. The results show us that K=4 meaning our data should be categorized into 4 clusters.

    # Create an elbow curve to find the best value for K.
    # Find the best value for K
    inertia = []
    k = list(range(1, 11))

    # Calculate the inertia for the range of K values
    for i in k:
        km = KMeans(n_clusters=i, random_state=0)
        km.fit(X_pca_df)
        inertia.append(km.inertia_)

    # Create the elbow curve
    elbow_data = {"k": k, "inertia": inertia}
    df_elbow = pd.DataFrame(elbow_data)
    df_elbow.hvplot.line(x="k", y="inertia", xticks=k, title="Elbow Curve")




<img src= Images/elbow_curve.png>


# Creating a 3D-Scatter Plot with the PCA data and the clusters with three features:

This 3D model was created with the code below:

    fig = px.scatter_3d(clustered_df, 
                        x="PC 1", 
                        y="PC 2", 
                        z="PC 3", 
                        color="class", 
                        symbol="class",
                        width=800)

    fig.update_layout(legend=dict(x=0,y=1))
    fig.show()

<img src= Images/3d_scatterplot.png>


# Tradeable Cryptocurrencies:

A table was formed with the `hvplot.table()` function holding all 532 tradable currencies.

    # create an hv plot table:
    table = clustered_df[
    [
        "CoinName",
        "Algorithm",
        "ProofType",
        "TotalCoinSupply",
        "TotalCoinsMined",
        "class",
    ]
    ].hvplot.table()

    table

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
  