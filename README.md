
# Student Performance Data Analysis 📚📊

## 📌 Dataset Description

The dataset file is **`student_data.csv`** and is used to analyze **student performance and related factors** using exploratory data analysis (EDA). The dataset contains student-related attributes such as scores, demographics, and academic details.

---

## 📊 Columns Information

*(Column names may vary slightly based on dataset)*

* **Student_ID (int)**: Unique identifier for each student
* **Gender (object)**: Male / Female
* **Age (int)**: Age of the student
* **Subject (object)**: Subject name
* **Score (float)**: Marks obtained by the student
* **Attendance (float)**: Attendance percentage

---

## 🔍 Data Exploration Steps

### 1️⃣ Loading the Dataset

```python
import pandas as pd

df = pd.read_csv("/content/student_data.csv")
```

---

### 2️⃣ Initial Data Exploration

```python
df.head()      # Shows first 5 rows
df.info()      # Column info, data types, non-null counts
df.shape       # Dataset dimensions
df.describe()  # Summary statistics
df.index       # Index details
df.columns     # Column names
df.dtypes      # Data types
```

---

### 3️⃣ Uniqueness and Counts

```python
df['Column'].unique()   # Unique values in a column
df.nunique()           # Unique value count per column
df.count()             # Non-null values
```

#### Example: Gender Count

```python
df['Gender'].value_counts()
```

---

### 4️⃣ Query Examples

#### Students scoring more than 80

```python
df[df['Score'] > 80]
```

#### Average score by gender

```python
df.groupby('Gender')['Score'].mean()
```

#### Check null values

```python
df.isnull().sum()
```

➡️ Dataset contains **no missing values**.

#### Rename a column

```python
df.rename(columns={'Attendance': 'attendance_percent'})
```

📌 *Use `inplace=True` to update the original DataFrame.*

---

### 5️⃣ Basic Statistics

#### Mean Student Score

```python
df['Score'].mean()
```

#### Standard Deviation of Scores

```python
df['Score'].std()
```

---

## 🛠️ Requirements

* **Python 3.x**
* **pandas**
* **numpy**

---

## 🎯 Skills Demonstrated

* Data Cleaning & Inspection
* Exploratory Data Analysis (EDA)
* GroupBy Operations
* Statistical Analysis

---

## 👩‍💻 Author

**Namrata Gupta**
Aspiring Data Analyst

---

⭐ *This project is suitable for GitHub portfolio and resume showcase.*

