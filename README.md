
# Finmark Customer Segmentation

## Project Overview

Finmark is a financial services company looking to better understand its customers and identify groups with different behaviors and levels of engagement.

This project uses transaction and customer feedback data to identify distinct customer segments and translate those segments into **business insights and actionable recommendations**.

The project combines **Python-based data analysis and machine learning** with an interactive **Tableau dashboard** to turn raw transaction data into an understandable customer segmentation story.

### The Business Question

> **Who are Finmark's customers, how do their behaviors differ, and how can Finmark use these differences to improve customer engagement?**

---

# Key Findings

The analysis identified **four distinct customer segments**, differentiated primarily by their **level of engagement, transaction behavior, and customer sentiment**.

The segments reveal that Finmark's customers do not behave uniformly. Some customers are highly engaged and positive toward the company, while others show lower activity and weaker sentiment.

### The four customer segments

| Customer Segment                         | General Profile                                                                                                           |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| **High-Engagement / Positive Sentiment** | Customers who interact frequently and show strong satisfaction and willingness to recommend Finmark.                      |
| **High-Engagement / Negative Sentiment** | Active customers who transact frequently but report weaker satisfaction or recommendation likelihood.                     |
| **Low-Engagement / Positive Sentiment**  | Customers who have relatively low activity but maintain positive opinions toward Finmark.                                 |
| **Low-Engagement / Negative Sentiment**  | Customers with lower activity combined with weaker customer sentiment, representing an important group for re-engagement. |

### What this means for Finmark

The segmentation suggests that **customer engagement and customer sentiment should not be treated as the same thing**.

For example, a customer may transact frequently while still being dissatisfied, while another customer may have positive opinions of Finmark despite relatively low transaction activity.

This gives Finmark an opportunity to move beyond a one-size-fits-all approach and instead consider different strategies for different customer groups.

### Recommended actions

**1. Retain high-engagement customers**

Highly engaged and positive customers represent a strong customer base. Finmark should focus on retention, loyalty initiatives, and maintaining the experience that keeps these customers engaged.

**2. Address dissatisfaction among highly active customers**

Customers who transact frequently but report negative sentiment are particularly important. Their activity indicates that they are valuable or engaged customers, but their dissatisfaction may represent a risk of future disengagement.

Finmark could investigate the causes of dissatisfaction and prioritize improvements for this group.

**3. Re-engage low-engagement customers**

Customers with low activity may benefit from targeted campaigns, personalized offers, product education, or other initiatives designed to increase usage.

**4. Monitor low-engagement / negative-sentiment customers**

Customers who are both inactive and dissatisfied represent the greatest potential disengagement risk. Finmark could prioritize this group for targeted retention or reactivation efforts.

---

# Dashboard

The final Tableau dashboard presents the segmentation in a non-technical format, allowing users to explore:

* The four customer segments
* Segment sizes
* Transaction behavior
* Average transaction amounts
* Customer satisfaction
* Likelihood to recommend
* Differences between customer groups

The dashboard is designed to answer three questions:

> **Who are our customers?**

> **How do these groups behave differently?**

> **What should Finmark do about it?**

**[View the Tableau Dashboard](#)**

---

# Project Workflow

The project followed an end-to-end data analytics workflow:

```text
Raw Transaction Data
        ↓
Data Cleaning
        ↓
Customer-Level Feature Engineering
        ↓
Feature Preparation & Encoding
        ↓
Standardization
        ↓
Principal Component Analysis (PCA)
        ↓
K-Means Clustering
        ↓
Customer Segment Interpretation
        ↓
Tableau Dataset
        ↓
Interactive Dashboard
        ↓
Business Recommendations
```

---

# Dataset

The original dataset contained approximately **5,000 transaction records**.

Because the objective was to segment **customers rather than individual transactions**, the data was transformed into a customer-level dataset.

After aggregation and feature engineering, the final analytical dataset contained **993 customers**.

### Customer-level features

| Feature                           | Description                                       |
| --------------------------------- | ------------------------------------------------- |
| `Customer_ID`                     | Unique customer identifier                        |
| `Total_Transactions`              | Total number of transactions made by the customer |
| `Avg_Transaction_Amount`          | Average transaction amount                        |
| `Avg_Satisfaction_Score`          | Average customer satisfaction score               |
| `Avg_Likelihood_to_Recommend`     | Average likelihood-to-recommend score             |
| `Mode_Transaction_Type`           | Most frequently used transaction type             |
| `Mode_Transaction_Amount_Segment` | Most common transaction amount category           |

---

# Technical Methodology

## 1. Data Cleaning

Python and Pandas were used to prepare the raw transaction data for analysis.

The process included:

* Inspecting the dataset structure
* Checking data types
* Checking for missing values
* Converting variables into appropriate analytical formats
* Preparing categorical and numerical variables for modeling

---

## 2. Customer-Level Feature Engineering

The transaction-level data was aggregated by customer.

Instead of treating each transaction independently, customer behavior was summarized using metrics such as:

* Total transaction count
* Average transaction amount
* Average satisfaction
* Average likelihood to recommend
* Most common transaction type
* Most common transaction amount segment

This transformed the original transaction dataset into a dataset where **each row represented one customer**.

---

## 3. Feature Preparation

The clustering model required the variables to be represented numerically.

Numerical variables were standardized using `StandardScaler`.

Categorical transaction-type information was transformed using one-hot encoding.

This ensured that variables measured on different scales could contribute appropriately to the clustering process.

---

## 4. Principal Component Analysis

**Principal Component Analysis (PCA)** was applied to reduce the dimensionality of the prepared feature set.

Two principal components were retained for visualization:

* **PC1**
* **PC2**

The PCA results also helped interpret the characteristics that differentiated customers.

PC1 was strongly influenced by **transaction activity and transaction amount segment**, while PC2 was more strongly associated with **customer satisfaction and likelihood to recommend**.

The resulting PCA coordinates were retained in the final dataset so that the customer clusters could be visualized in Tableau.

---

## 5. Choosing the Number of Clusters

The **Elbow Method** was used to evaluate different values of K for the K-Means algorithm.

The analysis indicated that **four clusters** provided an appropriate balance between capturing meaningful differences in customer behavior and avoiding unnecessary fragmentation of the customer base.

---

## 6. K-Means Clustering

K-Means clustering was then applied with **K = 4**.

The resulting cluster distribution was:

| Cluster   | Customers |
| --------- | --------: |
| Cluster 0 |       239 |
| Cluster 1 |       255 |
| Cluster 2 |       224 |
| Cluster 3 |       275 |
| **Total** |   **993** |

The numerical cluster labels were subsequently translated into business-friendly segment names based on the behavioral characteristics of each group.

---

# PCA & Cluster Interpretation

The PCA visualization provides a way to see how the customers are distributed across the main dimensions of variation in the dataset.

Each point represents a customer, while the color represents their assigned segment.

The purpose of this visualization is not simply to show the machine-learning output, but to demonstrate that the identified customer groups represent **observable differences in customer behavior**.

The clustering analysis identified four broad behavioral profiles:

### High Engagement / Positive Sentiment

These customers combine relatively high activity with positive customer sentiment.

They represent a strong customer group that Finmark should aim to retain.

### High Engagement / Negative Sentiment

These customers remain active but show weaker satisfaction or recommendation scores.

This group may represent an important business opportunity because their engagement indicates continued usage, while their sentiment suggests areas of potential dissatisfaction.

### Low Engagement / Positive Sentiment

These customers have relatively low transaction activity but maintain positive sentiment.

They may represent an opportunity for Finmark to increase engagement without needing to address major dissatisfaction issues.

### Low Engagement / Negative Sentiment

These customers combine lower activity with negative sentiment.

They represent a potentially vulnerable customer group and may benefit from targeted re-engagement or retention strategies.

---

# Tools & Technologies

### Data Analysis

* **Python**
* **Pandas**
* **NumPy**
* **Scikit-learn**
* **Jupyter Notebook**

### Machine Learning

* StandardScaler
* One-Hot Encoding
* Principal Component Analysis (PCA)
* K-Means Clustering
* Elbow Method

### Data Visualization & BI

* **Tableau**

### Version Control

* **Git / GitHub**

---

# Project Structure

```text
finmark-customer-segmentation/
│
├── data/
│   └── ...
│
├── notebooks/
│   └── customer_segmentation.ipynb
│
├── tableau/
│   └── ...
│
├── outputs/
│   └── tableau_dataset.csv
│
├── README.md
└── ...
```

---

# Deliverables

This project contains:

* **Python analysis notebook** — data cleaning, feature engineering, PCA, and K-Means clustering
* **Processed customer-level dataset**
* **Tableau-ready dataset**
* **Interactive Tableau dashboard**
* **Business findings and recommendations**
* **Project documentation**

---

# Limitations

The segmentation should be interpreted as a **descriptive customer analysis**, rather than a prediction of future customer behavior.

The clusters are based on the variables available in the dataset. Additional information such as customer demographics, account tenure, product usage, profitability, or historical changes in behavior could potentially produce more detailed segmentation.

The recommendations therefore serve as **data-informed strategic directions** that would benefit from further validation with additional business and customer data.

---

# Conclusion

This project demonstrates an end-to-end approach to customer segmentation, starting with raw transaction data and ending with business-oriented insights.

Rather than presenting clustering as a purely technical machine-learning exercise, the project focuses on translating the results into a form that can support business decision-making.

The analysis shows that Finmark's customers can be grouped into four distinct behavioral profiles based largely on **engagement and sentiment**.

These segments provide a framework for Finmark to think differently about customer retention, re-engagement, and customer experience rather than applying the same strategy to every customer.

---

## Author

**Zach Malonjao**

IT Student | Data Analytics & Business Intelligence

**Skills demonstrated:** Python · Pandas · SQL · Machine Learning · Data Visualization · Tableau · Customer Segmentation · Data Storytelling

