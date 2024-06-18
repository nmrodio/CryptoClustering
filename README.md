# **CryptoClustering** #

------------------------------
------------------------------

## **Project Goal:** ##
* This project aims to leverage K-means clustering to group cryptocurrencies based on their price change characteristics. By analyzing historical data and employing dimensionality reduction techniques, the project seeks to identify meaningful clusters that can potentially enhance market understanding and inform investment strategies using both the original scaled dataset and then applying PCA to reduce the dimensions of the original scaled dataset to compare the two models and the clusters that were produced from each technique.

## **Key Steps:** ##

### **Model 1: K-Means Clustering with Original Scaled Data** ###
**1.1) Instantiate the model:** Creating a specific instance of the K-Means algorithm with defined parameters (4 clusters => `n_clusters=4`) => 4 clusters was determined by using the elbow curve method

**1.2) Fit the model:** Using the original scaled data `StandardScaler()` to fit/train the model with `market_data_scaled_df`

**1.3) Use the model / Predict:** Using the original scaled data (`market_data_scaled_df`) with the function `model.predict(market_data_scaled_df)` to have the K-Means clustering model create 4 clusters after being trained

**1.4) Create Scatter Plot to show cluster results:** Plotting the predicted clusters into a scatter plot and coloring the data points based on cluster labels (0,1,2,3)

### **Model 2: K-Means Clustering with PCA Scaled Data** ###
**2.1) Instantiate the model:** Creating a specific instance of the K-Means algorithm with defined parameters (4 clusters => `n_clusters=4`) => 4 clusters was determined by using the elbow curve method

**2.2) Fit the model:** Using the `PCA(n_components=3)` function on the original scaled data to fit/train the model with `crypto_pca_df` which minimizes the dimesions => 89.5% of the variance/'information' was kept after applying PCA

**2.3) Use the model / Predict:** Using the PCA data (`crypto_pca_df`) with the function `pca_model.predict(crypto_pca_df)` to have the K-Means clustering model create 4 clusters after being trained

**2.4) Create Scatter Plot to show cluster results:** Plotting the predicted clusters into a scatter plot and coloring the data points based on cluster labels (0,1,2,3)

------------------------------
------------------------------

## **Elbow Curve - Original Scaled Data** ##

![Screenshot 2024-06-18 124140](https://github.com/nmrodio/CryptoClustering/assets/157527614/b277b50f-628b-487a-a375-faa82632dfc2)

## **Elbow Curve - PCA Data** ##

![Screenshot 2024-06-18 124201](https://github.com/nmrodio/CryptoClustering/assets/157527614/be0fa3de-fcbb-4522-a834-0baa53149969)

## **Clustering Results - Original Scaled Data** ##

![Screenshot 2024-06-18 124118](https://github.com/nmrodio/CryptoClustering/assets/157527614/d7993665-0ef3-4d63-87bc-ecf05bb24d04)

## **Clustering Results - PCA Data** ##

![Screenshot 2024-06-18 124212](https://github.com/nmrodio/CryptoClustering/assets/157527614/e3a5610e-0135-4778-9807-e3bc41a22121)

------------------------------
------------------------------

## **How does the code work?** ##

### **Model 1: K-Means Clustering with Original Scaled Data**

* **Data Preprocessing:**

**1)** Import and prepare cryptocurrency data from a CSV file.

**2)** Normalize the data using scikit-learn's StandardScaler for improved clustering performance.

* **Finding the Optimal K with Elbow Method (Original Data):**

**1)** Implement the elbow curve method to determine the ideal number of clusters (k) for K-means clustering. This involves iteratively calculating inertia for different k values and visually identifying the "elbow" in the resulting line chart (4 clusters seems to be the most opitmal for the model).

* **K-Means Clustering with Original Data:**

**1)** Apply the K-means algorithm using the optimal k value obtained from the elbow curve method `n_clusters=4`.

**2)** Group cryptocurrencies into distinct clusters based on their price change behavior.

**3)** Visualize the clusters using hvPlot, highlighting data points with their corresponding cryptocurrency IDs for easy identification.

### **Model 2: K-Means Clustering with PCA Scaled Data**

* **Dimensionality Reduction with Principal Component Analysis (PCA):**

**1)** Perform PCA on the scaled data to reduce its dimensionality and potentially improve clustering results.

**2)** Analyze the explained variance of each principal component to assess the information retained after dimensionality reduction.

* **Finding the Optimal K with Elbow Method (PCA Data):**

**1)** Repeat the elbow curve method analysis using the PCA-transformed data to identify the best k value for this reduced dimensionality space `n_clusters=4`.

**2)** Compare the optimal k obtained from the PCA data to the one found with the original data.

* **K-Means Clustering with PCA Data:**

**1)** Conduct K-means clustering again, using the optimal k identified based on the PCA data.

**2)** Group cryptocurrencies based on their principal components and visualize the resulting clusters using hvPlot.

------------------------------
------------------------------

## **Analysis of PCA/Dimensionality Reduction Impact:** ##

After analyzing the cluster results for the original scaled data vs the PCA data, the impact of using fewer features to cluster the data using K-Means seems to be a little bit better after applying PCA and using the PCA data. Although the original scaled data scatter plot shows clusters that seem to be more seperated, the PCA data scatter plot did a great job of seperating the two outliers into seperate groups while still keeping the two "like" groups together while keeping 89.5% of the variance/'information' from the original dataset. Its still important to keep in mind that the model became less accurate using the PCA data compared to the entire original scaled dataset because we lost around 10.5% of the variance/"information" to cut down on features/dimensions and create more "appealing" clusters.
