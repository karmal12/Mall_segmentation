Mall Customer Segmentation

Project Overview

This project performs customer segmentation using unsupervised machine
learning. The goal is to group mall customers into meaningful customer
segments based on their age, annual income, and spending score.

The project uses the Mall Customers dataset and applies K-Means
clustering to identify groups of customers with similar
characteristics.

Dataset

The dataset used is Mall_Customers.csv.

It contains 200 customer records with the following original
columns:

CustomerID -- Unique customer identifier

Gender -- Customer gender

Age -- Customer age

Annual Income (k$) -- Annual income in thousands of dollars

Spending Score (1-100) -- Spending score assigned to the customer

The notebook renames Annual Income (k$) to Annual Income for easier
use.

Technologies Used

Python

Pandas

NumPy

Matplotlib

Seaborn

Scikit-learn

Jupyter Notebook

Machine Learning Algorithm

K-Means Clustering

K-Means is an unsupervised learning algorithm that divides data
points into a specified number of clusters based on similarity.

In this project:

The clustering features are Age, Annual Income, and
Spending Score (1-100).

The features are standardized using StandardScaler.

K-Means is tested for different values of k.

The Elbow Method (WCSS) and Silhouette Score are used to
evaluate the number of clusters.

The final model uses 6 clusters.

Project Workflow

1. Import Libraries

The notebook imports Pandas, NumPy, Matplotlib, Seaborn, and required
Scikit-learn classes such as LabelEncoder, StandardScaler, KMeans,
and silhouette_score.

2. Load the Dataset

customer = pd.read_csv("Mall_Customers.csv")

3. Data Cleaning and Inspection

The notebook:

Renames the annual income column.

Checks for missing values.

Checks the dataset information and data types.

Generates descriptive statistics.

Checks for duplicate rows.

The dataset contains 200 rows and 5 original columns, with no
missing values and no duplicate rows.

4. Exploratory Data Analysis

The notebook performs:

Histograms of numerical variables.

Correlation analysis.

A scatter plot of annual income versus spending score.

5. Encode Categorical Data

The Gender column is converted from text into numeric values using
LabelEncoder.

6. Feature Engineering

Two additional features are created:

age_group -- age categories such as young_adult, adult,
middle_aged, and senior.

income_spending_ratio -- calculated as:

Annual Income / Spending Score

These features are used for analysis, while the K-Means model itself
uses Age, Annual Income, and Spending Score (1-100).

7. Feature Scaling

The three clustering features are standardized using StandardScaler:

scaler = StandardScaler()
x_scaled = scaler.fit_transform(
    customer[["Age", "Annual Income", "Spending Score (1-100)"]]
)

Scaling is important because the variables have different numerical
ranges.

8. Find the Number of Clusters

Elbow Method

WCSS (Within-Cluster Sum of Squares) is calculated for k values from 2
to 10.

The Elbow Method is used to identify a suitable number of clusters.

Silhouette Score

Silhouette scores are calculated for k values from 2 to 11.

The highest score obtained in the notebook is approximately 0.4284 for
k = 6.

Therefore, the project selects 6 clusters for the final K-Means
model.

9. Train K-Means Model

kmeans = KMeans(n_clusters=6, random_state=42, n_init=10)
labels = kmeans.fit_predict(x_scaled)

The generated cluster labels are added to the customer dataset.

10. Customer Segmentation

The six clusters are given descriptive business-oriented names:

Cluster Segment

      0 mature_mainsteram
      1 young_mainstream
      2 cautious_savers
      3 premium_customers
      4 young_impulsive_spenders
      5 budget_conscious

11. Cluster Profiles

The notebook calculates the average age, annual income, and spending
score for each cluster.

Cluster   Avg. Age   Avg. Annual Income   Avg. Spending Score

      0      56.33                54.27                 49.07
      1      26.79                57.10                 48.13
      2      41.94                88.94                 16.97
      3      32.69                86.54                 82.13
      4      25.00                25.26                 77.61
      5      45.52                26.29                 19.38

The cluster sizes in the notebook are:

Cluster   Customers

      0          45
      1          39
      2          33
      3          39
      4          23
      5          21

Segment Interpretation

1. Mature Mainstream

Older customers with moderate income and a moderate spending score.

2. Young Mainstream

Younger customers with moderate income and moderate spending behavior.

3. Cautious Savers

Customers with relatively high income but low spending scores.

4. Premium Customers

Customers with relatively high income and high spending scores. This
group can be considered an important target segment for premium products
and services.

5. Young Impulsive Spenders

Younger customers with lower income but high spending scores, indicating
strong spending activity relative to their income.

6. Budget Conscious

Customers with lower income and low spending scores.

Visualization

The project creates a K-Means cluster visualization using:

Annual Income on the X-axis

Spending Score on the Y-axis

Cluster/segment membership as the grouping variable

A final visualization is saved as:

images/final_clusters.png

Output

The final segmented customer dataset is exported to:

mall_segments.csv

The output contains the customer information along with:

cluster

segment

Project Structure

Mall-Customer-Segmentation/
│
├── mall_segmentation.ipynb
├── Mall_Customers.csv
├── mall_segments.csv
│
└── images/
    └── final_clusters.png

How to Run

Install Python.

Install the required libraries:

pip install pandas numpy matplotlib seaborn scikit-learn jupyter

Place Mall_Customers.csv in the same directory as the notebook.

Open the notebook:

jupyter notebook mall_segmentation.ipynb

Run the cells from top to bottom.

The final segmented dataset will be saved as mall_segments.csv.

Key Results

Dataset size: 200 customers

Missing values: 0

Duplicate rows: 0

Final clustering algorithm: K-Means

Final number of clusters: 6

Best silhouette score observed: 0.4284

Final output: 6 customer segments

Conclusion

The project demonstrates how unsupervised machine learning can be
used to discover meaningful customer groups without a predefined target
variable.

K-Means clustering identifies six distinct customer segments based on
age, income, and spending behavior. These segments can help a business
understand customer behavior and design more targeted marketing
strategies.
