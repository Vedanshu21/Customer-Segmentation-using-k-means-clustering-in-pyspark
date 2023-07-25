# Customer-Segmentation-using-k-means-clustering-in-pyspark

This project focuses on Customer segmentation and analysis using RFM (Recency, Frequency, Monetary) model using an unsupervised machine learning model "K-means clustering" in PySpark which is a Python API for Apache Spark. It enables real-time, large-scale data processing in a distributed environment using Python.<br>

RFM analysis allows marketers to target specific clusters of customers with communications that are much more relevant for their particular behavior – and thus generate much higher rates of response, plus increased loyalty and customer lifetime value.

## Dataset:
The dataset used is an e-commerce dataset that contains transactions for a UK-based and registered non-store online retail from 2010 to 2011 and is provided freely from The UCI Machine Learning Repository. You can download the data here.<br>

The dataset contains the following relevant columns needed for our analysis:<br>
<ul>
<li>InvoiceNo. Unique id for each sale.</li>
<li>StockCode. Unique id for each product.</li>
<li>Quantity. Number of units bought.</li>
<li>InvioceDate. Date of the sale.</li>
<li>UnitPrice. Retail price of the product.</li>
<li>CustomerID. Unique id for each customer</li>
</ul>
<br>
<br>

## Stepwise explanation:

<ol>
  <li>Data-Preprocessing</li>
  <li>Creation Of RFM Table</li>
  <li>Clustering using K-means clustering</li>
  <li>Analysis</li>

</ol>



### 1. Data Pre-processing

1. First Load data in a spark data frame, it will automatically date datatypes of all columns as a string so, it is needed to be cast into proper data types. <br>
2. Two extra columns is added:<br>
   Total, which is equal to UnitPrice * Quantity. It is needed to calculate the monetary value of each customer.<br>
   RecencyDays, which is a measure that tells the difference in days between the 31st of December 2011 (which we have chosen as the day of reference) and the InvoiceDate.<br>

### 2. RFM table Creation
For each customer, we need to measure the following indicators:<br><br>

Recency. We shall consider as recency the minimum RecencyDays that we calculated in the previous step. This makes sense since the minimum RecencyDays will give us the number of days that have passed since the customer’s last purchase.<br>
Frequency. It is calculated as the number of purchases that the customer has made.<br>
Monetary. It is the total value of all purchases for each customer.<br>


### 3. Cluster formations

1. Optimal number of clusters are decided using Elbow Analysis<br>
![image](https://github.com/Vedanshu21/Customer-Segmentation-using-k-means-clustering-in-pyspark/assets/83238429/3a458134-d54e-45b3-b3f9-aad636ed8097)

2. Whuch indicated that the data can be best catagorised in 5 different clusters.

### Analysis

Following table shoes the distribution of customers in 5 different clusters
<img width="107" alt="image" src="https://github.com/Vedanshu21/Customer-Segmentation-using-k-means-clustering-in-pyspark/assets/83238429/b2c570aa-2049-41aa-b9c4-ecf42e278daa">
<img width="470" alt="image" src="https://github.com/Vedanshu21/Customer-Segmentation-using-k-means-clustering-in-pyspark/assets/83238429/d723d47a-db67-4768-8219-7ca4d03222a9">

#### Scatter plots for visualization
![image](https://github.com/Vedanshu21/Customer-Segmentation-using-k-means-clustering-in-pyspark/assets/83238429/d06721fe-0fcb-4216-ae6b-f9725f20628a)
![image](https://github.com/Vedanshu21/Customer-Segmentation-using-k-means-clustering-in-pyspark/assets/83238429/7e57c2d7-4aa8-4f21-a120-b70ed63d9c39)

Above plots indicate that as then recency of customer increases , both frequency and monetary decreases 


#### Box Plot Analysis











