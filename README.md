
<div align="center">
  
  <div id="user-content-toc">
    <ul>
      <summary><h1 style="display: inline-block;"> Financial Analysis for KAT Insurance </h1></summary>
    </ul>
  </div>
  
  <p> Analysis for financial health based on Contribution Margin Ratio across various regions and states in USA </p>
    
  <a href="#">
    <img src="https://github.com/IrisWangAU/Retail_Data_Pipeline/blob/main/asset/walmartecomm.jpg" alt="Banner" width="720">
  </a>
</div>
<br>


## 📝 Table of Contents
1. [Introduction](#introduction)
2. [Key Insights](#key-insights)
3. [Project Architecture](#project-architecture)  
  3.1. [Data Cleaning](#data-extraction)  
  3.2. [Data Transformation](#data-transformation)  
  3.3. [Data Analysis](#data-loading)  
5. [Technology used](#technology)
6. [Contact](#contact)

<br>

<a name="introduction"></a>
## 🔬 Project Overview 

In 2017, KAT Insurance marked a significant achievement by exceeding a total sales figure of 40 million. To offer a comprehensive perspective of the company's financial health, the project analyzed these sales numbers in greater detail, categorizing them by region, state and insurance type. Alongside total sales, this report also delves into the company's profitability and financial ratios (Contribution Margin Ratio), thereby providing a holistic overview of the business's financial wellbeing.

Furthermore, the project also provided an analysis of the key influences for KAT's Contribution Margin and Contribution Margin Ratio to further reveal the sales performance.


<br>

### 💾 Dataset

The original dataset comprises 64,544 insurance policy sales records from 2017, spanning 6 regions, 49 states within the USA, and includes five types of insurance: Professional, Auto, Home, Disability, and Life.  In response to these queries, the total sales is classified by region, state and insurance type, thereafter delving into their patterns and rankings for insights. The primary data is saved in an Excel file, including 2 tables.

The `2017sales` table have the following features:

<br>

#### **`2017sales`**
- `"Invoice No"` - an unique Invoice Number for the sale
- `"Date of Sale"` - date of the sale
- `"Month of Sale"` - the month number of the year
- `"Region"` - the Region of the insurance policy sale
- `"State"` - the State of the insurance policy sale
- `"Salesperson"` - the Salesperson of the insurance policy sale
- `"Insurance Type"` - the Insurance type of the insurance policy sale
- `"State Type"` - combination of the state and the insurance type of the sale

The `VariableCostPct` table contains variable cost percentage figures for each combination of state and insurance type:

#### **`VariableCostPct`**
- `"State Type"` - combination of the state and the insurance type
- `"Variable Cost Percent"` - the variable cost percentage for each state and insurance type


The two tables are merged and manipulated. The transformed Dataset are stored as the `SalesMerged` table containing the following columns:
- `"Invoice No"` 
- `"Date of Sale"` 
- `"Month of Sale"` 
- `"Region"` 
- `"State"` 
- `"Salesperson"` 
- `"Insurance Type"` 
- `"State Type"`
- `"Variable Cost Percent"`
- `"Variable Cost"`
- `"Contribution Margin"`
- `"Contribution Margin Ratio"`

<br>

### 🎯 Project Goals

- analyse the total sales, profit and cost in 2017 by region, state and Insurance type to provide insights for revenue distribution
- analysis for the key influencers for contribution margin and contribution margin ratio to provide insghts for financial performance

<br>

<a name="key-insights"></a>
## 🕵️ Key Insights

- 💸 **Total Sales**
  - The total revenue for KAT Insurance across all states amounts to 40.65 million in 2017.
  - Among all the months, KAT has the highest revenue in August (3.49 million), followed by October (3.46 million) and December (3.42 million). There are three months fall behind the average monthly revenue (Feb:3.2 million, Sep: 3.26m and Apr: 3.33m)
  - Among all the insurance type, the professional insurance reached the highest revenue (16.54m) which is 41% of the total revenue of KAT, followed by Auto Insurance (7.97m and 20%). The Life Insurance makes the least revenue in 2017 with only 2.89m, contributed to 7% of total revenue.
  - After organizing the sales data across the 49 states in the USA, it emerged that New Jersey (NJ) topped the list, recording sales totaling $1,021,569.45. In contrast, Massachusetts (MA) logged the lowest sales for 2017, aggregating to $707,795.11.
  - The average state sales is around 829K, with the top 5 states being NJ, NY, DC, OH and VA. In contrast, nine states falling short of the $775K benchmark, warranting immediate attention.
  - 
 
- 🕵️ **Contribution Margin (CM) and Contribution Margin Ratio (CMR)**
  > The Contribution Margin shows the profit of sale by excluding variable cost from the revenu (Contribution Margin = Sales - Sales * Variable Cost Percent)
  > The Contribution Margin Ratio shows the ability of the sale to convert investment to profit (CMR = CM / Sales)
  - In 2017, the average CMR for each region and month is quite similar around 0.73, which indicates a healthy finance in terms of regions. The Northeast makes the most profit of 8.7 million.
  - when looking at Insurance type, things are getting more interesting. Previously, we have Life Insurance making the least revuene during the year. However, it has reached the highest CMR of 0.89, showing that it is the most profitable insurance policy for KAT. Similarly, although Auto Insurance has reached the 2nd place in total sales, its low CMR of 0.52 indicating that only 52% of the sales are converted into profit.
<br>

<a name="project-architecture"></a>
## 📝 Project Architecture

<br>

<a name="data-extraction"></a>
### 📤 Data Ingestion
- Extract Data from source file

![extract](https://github.com/IrisWangAU/Retail_Data_Pipeline/blob/main/asset/Extract.PNG)

<br>

<a name="data-transformation"></a>
### ⚙️ Data Transformation

- Fill NAs in Date, CPI, Unemployment with the last non-null values.
- Drop any rows with missing values in weekly sales and keep only rows with sales revenue above 10K.
- Create a new column for Month from the Date Column.
- Create a new Data Frame for Average Weekly Sales by Month using aggregation.

![Transform](https://github.com/IrisWangAU/Retail_Data_Pipeline/blob/main/asset/Transform.PNG)

<br>

<a name="data-loading"></a>

### 📥 Data Loading

- Save the Cleaned and Aggregated Data into CSV files

![SaveData](https://github.com/IrisWangAU/Retail_Data_Pipeline/blob/main/asset/savedata.PNG)

<br>

<a name="pipeline-validate"></a>

### ⚙️ Pipeline Testing

- Create a function to validate the existence of cleaned data and aggregated data files in the path
- Use Try-Except to run pipeline

![validate](https://github.com/IrisWangAU/Retail_Data_Pipeline/blob/main/asset/validate.PNG)
![pipelinerun](https://github.com/IrisWangAU/Retail_Data_Pipeline/blob/main/asset/pipelinerun.PNG)

<br>

<a name="data-reporting"></a>
### 📊 Data Reporting
- Connect PowerBI with cleaned and aggregated data to perform analysis

![salesreport](https://github.com/IrisWangAU/Retail_Data_Pipeline/blob/main/asset/WalmartSalesReport.PNG)


<br>

<a name="technology"></a>

### 🛠️ Technologies Used

- **Data Source**: csv and parquet files
- **Data Extraction**: Python Pandas Package
- **Data Transformation**: Pandas DataFrame, Python programming
- **Data Loading**: Python Pandas
- **Data Visualization**: PowerBI
- **Pipeline Testing**: Python Logging package

<br>

<a name="contact"></a>

## 📨 Contact Me

[LinkedIn](https://www.linkedin.com/in/iriswangau/) •
[Gmail](iriswang.mel@gmail.com)
