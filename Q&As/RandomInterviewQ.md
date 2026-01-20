# Questions and answers  

Here are some questions that I have stumbled upon or asked myself during lectures, interviews, readings, and YouTube videos. I’ll try to keep this list updated and well organized, with quick answers for reference.


### Difference between Supervised and Unsupervised Learning ?

- **Supervised Learning**
  - Uses **labeled data**
  - Learns from known answers
  - Used for **prediction**

- **Unsupervised Learning**
  - Uses **unlabeled data**
  - Finds **patterns or groups**
  - Used for **exploration**

**Resume**
``Supervised`` = learns with answers (training dataset)
``Unsupervised`` = learns without answers


### Difference between Logistic Regression and classic regression ? 

- **Linear Regression**
  - Predicts **continuous values**
  - Output is a **quantitativ feature** (e.g., price, temperature)
  - Uses a **linear function**

- **Logistic Regression**
  - Predicts **probabilities**
  - Output is between **0 and 1**
  - Used for **classification**
  - Uses the **sigmoid (logistic) function**

**Short version :**  
Linear regression predicts numbers  
Logistic regression predicts class probabilities


---

## SQL 

### Difference Between `DELETE`, `TRUNCATE` and `DROP`

- **`DELETE`**
  - Removes **specific rows** (can use `WHERE`)
  - Can be **rolled back** (if inside a sub-request)
  - Slower for large tables

- **`TRUNCATE`**
  - Removes **all rows** only
  - **Cannot** use `WHERE`
  - Faster than `DELETE`

- **`DROP`**
  - Removes the **entire table**
  - Deletes **data + table structure**

**Resume**  
`DELETE` = remove rows  
`TRUNCATE` = empty table  
`DROP` = delete table completely


### Difference between and `INNER` and a `LEFT` JOIN ?

- **`INNER JOIN`**
  - Returns **only matching rows** from both tables
  - Rows without a match are **excluded** (no null values)

- **`LEFT JOIN`**
  - Returns **all rows from the left table**
  - Includes matching rows from the right table
  - Non-matching rows from the right table return **NULL**

**Short version:**  
`INNER JOIN` = only matches  
`LEFT JOIN` = all left rows + matches



---
