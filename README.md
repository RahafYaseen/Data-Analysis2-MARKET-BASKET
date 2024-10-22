## Online Retail Data Analysis with Association Rules
This project focuses on analyzing online retail sales data to extract patterns and association rules using Python libraries. The dataset is sourced from an Excel file containing sales information, particularly focusing on transactions made in the United Kingdom.

## Contents
- [System Requirements](#System_Requirements)
- [Libraries Used](#Libraries_Used)
- [Usage](#Usage)
- [Data Analysis Steps](#Data_Analysis_Steps)
- [Results](#Results)


# Libraries Used
1. pandas: For data manipulation and analysis.
2. matplotlib: For data visualization.
3. seaborn: For enhanced data visualization.
4. mlxtend: For extracting frequent itemsets and association rules.

## Installation
You can install the required libraries using pip:

```bash
pip install pandas matplotlib seaborn mlxtend openpyxl
```



## Usage
## 1. Load the Data:
 The program loads sales data from an Excel file named Online Retail.xlsx.

  
## 2. Data Cleaning and Preparation:
- The first five rows of the dataset are displayed to understand its structure.
- Null values are checked and removed.
- The InvoiceNo column is converted to a string type, and invoices containing "C" are filtered out.


## 3. Sales Distribution Analysis:
The distribution of transactions by country is calculated, and the top 10 countries are visualized in a pie chart.


## 4. Basket Analysis:
- A basket matrix is created for transactions in the United Kingdom, grouping data by InvoiceNo and Description.
- One-hot encoding is applied to the basket matrix.
- The data is filtered to include only invoices with two or more items.

## 5. Frequent Itemsets and Association Rules:
- The Apriori algorithm is used to generate frequent itemsets with a minimum support threshold.
- Association rules are extracted based on the "lift" metric.



## Data Analysis Steps
- 1. Load the Dataset:
```bash
df = pd.read_excel('/content/Online Retail.xlsx')
```
- 2. Data Inspection:
 



1. Display the first five rows:
 ```bash    
df.head()
```

  2. Check the structure of the DataFrame:
```bash
df.info()
```

- 3. Data Cleaning:
Remove null values:
```bash
df.dropna(inplace=True)
```

- 4. Sales Distribution Visualization:
 ```bash
plt.figure(figsize=[8,8])
plt.pie(top10, labels=top10.index, autopct='%0.0f%%', labeldistance=1.3)
plt.title("Distribution of Transactions by Country")
plt.show()
```

- 5. Frequent Itemsets Generation:
```bash
frequent_itemsets = apriori(basket_filtered, min_support=0.03, use_colnames=True)
```
## Results
 Based on the results from implementing association rules, we can see that “Roses Regency Teacup and Saucer” and “Green Regency Teacup and Saucer” have the highest “lift” value, and therefore the highest association of any two products. With a combined support of 0.0309, it means both items were purchased together in 3.09% of all transactions.

- 6. Association Rules Extraction:
```bash
assoc_rules = association_rules(frequent_itemsets, metric="lift", min_threshold=1)
```
