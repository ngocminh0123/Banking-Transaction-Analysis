# Banking Transaction Analysis

## 📊 Project Overview

This project analyzes banking transactional data to identify patterns, detect fraud, and derive actionable insights for risk management and customer behavior analysis. Using PySpark and machine learning techniques, the analysis processes over 13 million transaction records to understand customer spending behavior, transaction patterns, and fraud detection.

**Source**: [Kaggle - Financial Transactions Dataset](https://www.kaggle.com/datasets/computingvictor/transactions-fraud-datasets?select=transactions_data.csv)

---

## 🎯 Project Objectives

* **Fraud Detection**: Identify abnormal transaction patterns and suspicious financial activities
* **Customer Behavior Analysis**: Understand customer financial behavior across demographic and income segments
* **Product Usage Analysis**: Analyze the most frequently used banking products and services
* **Risk Management**: Detect transaction anomalies and assess fraud risks using machine learning
* **Business Intelligence**: Generate actionable insights for banking operations and strategic decision-making

---

## 📁 Dataset Description

The dataset contains comprehensive banking transaction records from the 2010s decade, including:

### 1. **transactions_data.csv** (~13.3M records)
| Feature | Description |
|---------|-------------|
| `id` | Unique transaction identifier |
| `date` | Transaction timestamp |
| `client_id` | Customer identifier |
| `card_id` | Payment card identifier |
| `amount` | Transaction monetary value |
| `use_chip` | Chip authentication indicator |
| `merchant_id` | Merchant identifier |
| `merchant_city` | Merchant location (city) |
| `merchant_state` | Merchant location (state) |
| `zip` | Merchant postal code |
| `mcc` | Merchant Category Code |
| `errors` | Transaction error information |

### 2. **cards_data.csv**
Card information including brand, type, credit limits, and chip capabilities.

### 3. **users_data.csv** (~2,000 customers)
Customer demographics: age, gender, location (latitude/longitude), retirement age, and address.

### 4. **train_fraud_labels.json**
Ground-truth fraud labels for supervised learning (1 = fraudulent, 0 = legitimate).

---

## 🛠️ Technologies & Tools

* **Big Data Processing**: PySpark (ML, MLlib)
* **Data Analysis**: Pandas, NumPy
* **Visualization**: Matplotlib, Seaborn
* **Statistical Analysis**: SciPy, Statsmodels
* **Machine Learning**: 
  * Logistic Regression
  * Random Forest Classifier
  * Gradient Boosted Trees (GBT)
* **Platform**: Databricks (Apache Spark)
* **Visualization**: Power BI (`Banking_Transactions_Analysis.pbix`)

---

## 📂 Project Structure

```
Banking-Transaction-Analysis/
│
├── README.md                                    # Project documentation
├── requirements.txt                             # Python dependencies
├── Banking Transactions Analysis.ipynb          # Main analysis notebook
├── Banking_Transactions_Analysis.pbix           # Power BI dashboard
└── Final Project Proposal.pdf                   # Project proposal document
```

---

## 🔍 Analysis Workflow

### **I. Data Import & Setup**
* Import libraries (PySpark, Pandas, Scikit-learn, Matplotlib)
* Load data from Unity Catalog (`cybersoftda-google-bigquery-catalog`)

### **II. Data Preprocessing**

#### **2.1. Transaction Data**
* **Data Type Conversion**: Cast `amount` from string to double, handle negative values
* **Handle Missing Values**:
  * `merchant_state`: Fill nulls with 'ONLINE' for online transactions
  * `zip`: Map missing zip codes for international cities
  * `errors`: Fill nulls with 'no error'
* **Remove Duplicates**: Drop duplicate transaction IDs
* **Descriptive Statistics**: Analyze distribution of amounts, transaction counts, merchant patterns

#### **2.2. Users Data**
* Validate customer demographics (age, gender, location)
* Check for missing values and duplicates
* Analyze age distribution and geographic patterns

#### **2.3. Cards Data**
* Analyze card brands, types, and credit limits
* Validate chip-enabled card usage
* Examine cards issued per customer

### **III. Exploratory Data Analysis (EDA)**
* Transaction volume analysis by time period
* Customer spending patterns and segmentation
* Merchant category analysis (MCC codes)
* Geographic transaction distribution
* Payment method analysis (chip vs. swipe)

### **IV. Feature Engineering**
* Time-based features (hour, day, month, year)
* Customer aggregation features (transaction frequency, avg amount)
* Geographic features
* Card usage patterns
* Merchant risk indicators

### **V. Fraud Detection Modeling**
* **Data Preparation**: Merge transaction, user, card, and fraud label datasets
* **Feature Selection**: Identify key fraud indicators
* **Model Training**:
  * Logistic Regression
  * Random Forest Classifier
  * Gradient Boosted Trees (GBT)
* **Model Evaluation**: Accuracy, Precision, Recall, F1-Score, AUC-ROC
* **Insights**: Identify high-risk transaction patterns

### **VI. Business Insights & Recommendations**
* High-risk customer segments
* Fraud prevention strategies
* Product recommendations for upselling/cross-selling
* Operational efficiency improvements

---

## 🚀 Getting Started

### **Prerequisites**
* Databricks workspace with Spark compute
* Unity Catalog access to dataset: `cybersoftda-google-bigquery-catalog.financial_transactions_dataset`
* Python 3.8+

### **Installing Dependencies**

For Databricks environment, most libraries are pre-installed. To install additional packages:

```python
# In a Databricks notebook cell
%pip install -r requirements.txt
```

Or install packages individually:
```python
%pip install pandas numpy matplotlib seaborn scipy statsmodels scikit-learn
```

### **Running the Analysis**

1. **Open the Notebook**:
   ```
   Banking Transactions Analysis.ipynb
   ```

2. **Attach Compute**: Select a Databricks cluster (Serverless or All-Purpose)

3. **Install Dependencies** (if needed):
   ```python
   %pip install -r requirements.txt
   ```

4. **Run All Cells**: Execute cells sequentially to perform the complete analysis

5. **View Results**: Examine outputs, visualizations, and model performance metrics

---

## 📈 Key Findings

* **Transaction Volume**: 13.3M transactions across 2,000 customers (avg ~6,650 transactions per customer)
* **Average Transaction Amount**: $42.98 (range: -$500 to $6,820)
* **Fraud Rate**: Calculated through model evaluation on labeled dataset
* **High-Risk Patterns**: Identified through machine learning classification models
* **Geographic Insights**: Transaction patterns vary by merchant location and customer region
* **Payment Methods**: Analysis of chip vs. swipe transactions for security assessment

---

## 📊 Visualizations

Interactive dashboards available in:
* **Power BI**: `Banking_Transactions_Analysis.pbix`
* **Notebook**: Matplotlib and Seaborn charts throughout the analysis

---

## 👥 Use Cases

* **Financial Institutions**: Fraud detection and prevention
* **Risk Management Teams**: Transaction monitoring and anomaly detection
* **Marketing Teams**: Customer segmentation and targeting
* **Operations Teams**: Process optimization and efficiency improvements
* **Compliance Teams**: Regulatory reporting and audit support

---

## 📝 Future Enhancements

* Real-time fraud detection pipeline
* Deep learning models (Neural Networks, LSTM)
* Customer lifetime value prediction
* Recommendation engine for financial products
* Integration with streaming transaction data

---

## 🙏 Acknowledgments

* Dataset: [Kaggle - Financial Transactions Dataset](https://www.kaggle.com/datasets/computingvictor/transactions-fraud-datasets)
* Platform: Databricks Community Edition / AWS Databricks
* Tools: Apache Spark, PySpark, Scikit-learn, Power BI
