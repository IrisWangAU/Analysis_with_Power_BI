
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
  - In 2017, KAT Insurance generated a total revenue of $40.65 million across all states.
  - August led the months with the highest revenue of $3.49 million, followed by October ($3.46 million) and December ($3.42 million). February, September, and April fell below the average monthly revenue, with $3.2 million, $3.26 million, and $3.33 million, respectively.
  - Among insurance types, Professional Insurance generated the most revenue at $16.54 million (41% of total revenue), followed by Auto Insurance at $7.97 million (20%). Life Insurance contributed the least, with $2.89 million (7% of total revenue)
  - New Jersey (NJ) recorded the highest sales at $1,021,569.45, while Massachusetts (MA) had the lowest at $707,795.11.
  - The average state sales were around $829K. The top 5 states were NJ, NY, DC, OH, and VA, while nine states fell below the $775K benchmark, needing immediate attention.


- 🕵️ **Contribution Margin (CM) and Contribution Margin Ratio (CMR)**
  > The Contribution Margin (CM) measures profit by subtracting variable costs from revenue (CM = Sales - Sales * Variable Cost Percent).
  > The Contribution Margin Ratio (CMR) reflects how effectively sales convert to profit (CMR = CM / Sales).
  - In 2017, the average CMR across regions and months was around 0.73, indicating healthy finances. The Northeast region led with a profit of $8.7 million.
  - Life Insurance, despite generating the least revenue, had the highest CMR at 0.89, making it the most profitable policy for KAT. Conversely, Auto Insurance, with the second-highest sales, had a lower CMR of 0.52, indicating only 52% of sales converted to profit.



- 🕵️ **Key Influencers for CM and CMR**
  - Key factors increasing CM include Insurance Type, Salesperson, and Region. For example, Professional Insurance increased CM by an average of $652, Salesperson Matt by $101.9, and the Northeast region by $87.97. The Decomposition Tree confirmed that the highest CM in 2017 was from Matt selling Professional Insurance in the Northeast.
  - Key influencers for CMR include Insurance Type and State. States like NM, IN, VA, ND, and SD, and insurance types like Life, Home, and Professional, significantly boosted CMR. The Decomposition Tree showed the most profitable sale was Life Insurance in Indiana.


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
