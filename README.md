# Data Cleaning Project

## Overview

This project demonstrates a complete data cleaning workflow using Python and Pandas inside Jupyter Notebook. The dataset contains customer information with multiple quality issues such as duplicates, unnecessary columns, inconsistent formatting, missing values, and invalid phone numbers.

The goal of the project is to transform raw customer data into a cleaner and more usable dataset for analysis.

---

## Tools & Technologies

* Python
* Pandas
* Jupyter Notebook
* Excel Dataset

---

## Project Workflow

### 1. Import Libraries

The project starts by importing the Pandas library.

```python
import pandas as pd
```

---

### 2. Load Dataset

The Excel file is loaded into a DataFrame.

```python
df = pd.read_excel("Customer Call List.xlsx")
```

---

### 3. Remove Duplicate Records

Duplicate rows are removed to improve data quality.

```python
df = df.drop_duplicates()
```

---

### 4. Drop Unnecessary Columns

Columns that are not useful for analysis are removed.

```python
df = df.drop(columns = "Not_Useful_Column")
```

---

### 5. Clean Text Data

Special characters and unwanted values are removed from the `Last_Name` column.

```python
df["Last_Name"] = df["Last_Name"].str.strip("123._/")
```

---

### 6. Standardize Phone Numbers

Phone numbers are converted into a consistent format and invalid values are cleaned.

```python
df["Phone_Number"] = df["Phone_Number"].astype(str)
```

---

### 7. Split Address Column

The address column is separated into:

* Street Address
* State
* Zip Code

```python
df[["Street_Address","State","Zip_code"]] = df["Address"].str.split(',', n=2, expand=True)
```

---

### 8. Standardize Categorical Values

The project replaces long text values with shorter standardized values.

Examples:

* Yes → Y
* No → N

```python
df["Paying Customer"] = df["Paying Customer"].str.replace('Yes','Y')
```

---

### 9. Handle Missing Values

Blank values are replaced where necessary.

```python
df.fillna('', inplace=True)
```

---

### 10. Filter Unwanted Records

Customers who:

* Do not want to be contacted
* Do not have phone numbers

are removed from the dataset.

```python
if df.loc[x, "Do_Not_Contact"] == 'Y':
```

---

## Key Skills Demonstrated

* Data Cleaning
* Data Wrangling
* Handling Missing Values
* String Manipulation
* Data Standardization
* Working with Excel Files
* Pandas DataFrame Operations
