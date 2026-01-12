# 📊 Part 2 – Data Manipulation (Pandas)

This section covers **data loading, cleaning, transformation, and visual exploration**
Using **pandas**, one of the core library for data manipulation in Python

---

# **1. Pandas Fundamentals**


`pandas` is the core Python library for **data manipulation and analysis**.
It provides two main data structures: **Series** and **DataFrame**.


## 1.1 Importing Pandas & Basic Objects  

Standard convention:

```python
import pandas as pd
```

### Core `pandas` objects 

| Object      | Description                       |
| ----------- | --------------------------------- |
| `Series`    | 1D labeled array                  |
| `DataFrame` | 2D labeled table (rows & columns) |


### Creating a `Serie` and a `Dataframe`

#### ``Serie``

```python
s = pd.Series([10, 20, 30])  # from a list

s = pd.Series([10, 20, 30], index=["a", "b", "c"])  # With index

s = pd.Series({"a": 10, "b": 20})   # from a dict
```


#### ``Dataframe``

```python
data = {
    "name": ["Alice", "Bob"],
    "age": [25, 30]
}

df = pd.DataFrame(data)
```

## 1.2 Series vs DataFrame  

### Pandas Series

A `Series` is a **one-dimensional labeled array**.
It behaves similarly to a NumPy array but with an index.

```python
import pandas as pd

s = pd.Series([10, 20, 30], index=["a", "b", "c"])
```


#### Key properties 

```python
s.values # [10, 20, 30]
s.index  # ["a", "b", "c"]
s.dtype  # int64
```

### Pandas DataFrame

A ``DataFrame`` is a **two-dimensional table** where :

- columns are ``Series``
- each column can have a different data type

#### Key properties 

```python
df.head()  # First lines of the df
df.tail()  # Last lines of the df
df.shape   # (rows, columns)
df.columns # Column names
df.index   # Index information 
```

### Conversion 

**``Series`` → ``DataFrame`` :**
```python
df = s.to_frame(name="values")
```

**``DataFrame column`` → ``Series`` :**
```python
age_series = df["age"]
```

## 1.3 Inspecting Data  

### Statistical Information

Quick Summary of the dataframe metadata

```python
df.dtypes  # Data types
df.info()  # Information about the dataset

df.describe() # Statistical Summary
```

### Missing Values

When you need to normalize data or train a model you need to make sure they are no missing information in your dataset. 

```python
df.isna().sum()
df.isnull().sum()   # alias
```

### Duplicates

```python
df.duplicated().sum()
```

### Sampling

If you need to check something with a sample from the dataframe 
``Random state`` to assure reproductibility 

```python
df.sample(5, random_state=42) # 42 value is chatgpt classic answer 
```


### **Practical Examples**
This function can give you quick inside of the dataset you are working with 

```python
def inspect(df):
    print("Shape:", df.shape)
    print("Missing values:\n", df.isna().sum())
    print("Data types:\n", df.dtypes)
```

---

# **2. Loading & Saving Data**

This section covers the most common ways to **load datasets into pandas** and **export results**.

## 2.1 Reading CSV / Excel / JSON  


### CSV

```python
import pandas as pd

df = pd.read_csv("data.csv")
```

Options 

```python
df = pd.read_csv(
    "data.csv",
    sep=",",            # separator -> use ; if the values seems really strange it might help fix ! 
    encoding="utf-8",
    header=0,           # row number for column names
    index_col=None,     # set an index column
)
```


### Excel

```python
df = pd.read_excel("data.xlsx")
```

#### Specific sheet:

```python
df = pd.read_excel("data.xlsx", sheet_name="Sheet1")
```

#### Multiple sheets (returns dict of DataFrames) :

```python
sheets = pd.read_excel("data.xlsx", sheet_name=None)
```

### JSON 

```python
df = pd.read_json("data.json")
```

If JSON is nested / records-like:
```python
df = pd.read_json("data.json", orient="records")
```


## 2.2 Writing Data  

### Write CSV
```python
df.to_csv("output.csv", index=False)
```

### Write Excel
```python
df.to_excel("output.xlsx", index=False)
```

Multiple sheets:

```python
with pd.ExcelWriter("report.xlsx") as writer:
    df.to_excel(writer, sheet_name="data", index=False)
```

### Write JSON
```python
df.to_json("output.json", orient="records", indent=2)
```

## 2.3 Common Parameters  

**When reading (read_*)**
| Parameter           | Description                       |
| ------------------- | --------------------------------- |
| `sep` / `delimiter` | CSV separator                     |
| `header`            | Row used as column names          |
| `names`             | Provide column names manually     |
| `index_col`         | Set a column as index             |
| `usecols`           | Load only specific columns        |
| `dtype`             | Enforce data types at read time   |
| `parse_dates`       | Parse date columns                |
| `na_values`         | Define missing-value markers      |
| `nrows`             | Load the first *N* rows           |
| `skiprows`          | Skip rows (e.g. metadata headers) |
| `chunksize`         | Stream large files in chunks      |


**When reading (write_*)**
| Parameter     | Description                               |
| ------------- | ----------------------------------------- |
| `index`       | Include index column or not               |
| `columns`     | Write only a subset of columns            |
| `sep`         | CSV separator                             |
| `encoding`    | Specify file encoding (useful on Windows) |
| `mode`        | Append vs overwrite file (CSV)            |
| `compression` | Apply compression (`gzip`, `zip`, etc.)   |


---

# **3. Indexing & Selection**

Selecting the right rows and columns is one of the most important skills in data .

## 3.1 Column Selection  

### Select a Single Column 

A dataframe single column is a pandas `Series`

```python
df["sepal length (cm)"]
```

### Select a Multi Column 

```python
df[["sepal length (cm)", "sepal width (cm"]]
```

### Select a Column w/ pattern

```python
df.filter(like="sepal length (cm)")
```

## 3.2 Row Selection (`loc`, `iloc`)  

Really important part, the difference between `loc` and `iloc` method 

#### ``loc`` – Label-based indexing

```python
df.loc[0]                 # row with index label 0
df.loc[0, "sepal length (cm)"] # first row, sepal length column         # single value
df.loc[:, ["age"]]        # all rows, selected columns
```

Range (inclusive):

```python
df.loc[0:5]
```
#### ``iloc`` – Position-based indexing

```python
df.iloc[0]                # first row
df.iloc[0, 1]             # row 0, column 1
df.iloc[:, 0:2]           # all rows, first two columns
```

## 3.3 Boolean Masking  

### Filter rows using conditions.

```python
df[df["sepal length (cm)"] > 5]
```

Multiple conditions :

```python
df[(df["sepal length (cm)"] > 5) & (df["petal length (cm)"] > 1)]
```

``OR`` condition :

```python
df[(df["sepal length (cm)"] < 5) | (df["petal length (cm)"] > 1)]
```

``isin``

```python
df[df["city"].isin(["Paris", "London"])]
```

``query`` (clean syntax)
```python
df.query("sepal length (cm) > 30 and petal length (cm) > 1")
```

## 3.4 Sorting

```python
df.sort_values("sepal length (cm)")
df.sort_values(["sepal length (cm) ", "petal length (cm)"], ascending=[True, False])
```

---

# **4. Data Cleaning**
## 4.1 Missing Values  
## 4.2 Duplicates  
## 4.3 Type Conversion  
## 4.4 String Operations  

---

# **5. Data Transformation**
## 5.1 Applying Functions  
## 5.2 `apply`, `map`, `applymap`  
## 5.3 Creating New Features  

---

# **6. Grouping & Aggregation**
## 6.1 `groupby` Basics  
## 6.2 Aggregation Functions  
## 6.3 Multiple Aggregations  

---

# **7. Merging & Joining**
## 7.1 `merge`  
## 7.2 `concat`  
## 7.3 Join Types  

---

# **8. Time Series Basics**
## 8.1 Datetime Conversion  
## 8.2 Resampling  
## 8.3 Rolling Windows  

---

# **9. Exploratory Data Analysis (EDA)**
## 9.1 Descriptive Statistics  
## 9.2 Correlations  
## 9.3 Value Counts  

---

# **10. Performance & Best Practices**
## 10.1 Vectorization  
## 10.2 Memory Optimization  
## 10.3 Chaining & Readability  

---

# **11. To-Do / Advanced Topics**
- Categorical data  
- MultiIndex  
- Large datasets (chunks)  
- Integration with NumPy / SQL  

---
