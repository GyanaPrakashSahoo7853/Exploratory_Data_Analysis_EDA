# 🧹 Dataset Cleaning with NumPy and Pandas 🐼

This repository showcases practical examples of **Data Cleaning and Preprocessing** using Python libraries — **NumPy** and **Pandas** — on real-world datasets.

---

## 📂 Datasets Used

| Dataset               | Source                      | Description                                                                                     | Target Variable        |
|-----------------------|-----------------------------|-------------------------------------------------------------------------------------------------|------------------------|
| **Adult Income**      | UCI ML Repository           | Predict whether income exceeds \$50K/year using demographic and work-related attributes.        | `income`               |
| **Wine Quality**      | UCI ML Repository           | Predict wine quality based on physicochemical tests like acidity, alcohol, sulphates, and pH.   | `quality`              |
| **Titanic**           | Kaggle                      | Predict passenger survival based on features like age, sex, class, fare, and siblings aboard.   | `Survived`             |
| **Iris**              | UCI ML Repository           | Classify iris flowers into species using petal and sepal measurements.                          | `species`              |
| **Auto MPG**          | UCI ML Repository           | Predict car fuel efficiency (MPG) based on engine, weight, horsepower, and model details.       | `mpg`                  |

---

## 🛠️ Technologies Used

- 🐍 Python 3
- 📊 Pandas
- ➕ NumPy
- 📓 Jupyter Notebook

---

## 🧼 Steps for Data Cleaning

The following common steps were applied across datasets using **NumPy** and **Pandas**:


![Data_Clean_Steps](https://github.com/user-attachments/assets/e4bf6d2e-db36-426e-b12a-13d514ff6225)


---

### 🔍 Detailed Steps (Explained)

### 1️⃣ Data Reading
- Load datasets using `pd.read_csv()` or other methods.
- Ensure proper encoding and separators.

### 📌 Common Parameters in `read_csv()`

| Parameter              | Use Case                                                                 |
|------------------------|--------------------------------------------------------------------------|
| `sep=','`              | Default. Use this for standard comma-separated CSV files.                |
| `sep='\s+'`            | Use this for whitespace-separated data (including irregular spacing).    |
| `delim_whitespace=True`| Same as `sep='\s+'`, a shorthand for separating on whitespace.           |
| `delimiter=':'`        | For files with custom delimiters like `:`, `;`, `|`, etc.                |


### 2️⃣ Renaming Columns
- Assign meaningful column names if not present in the original dataset.
- Useful for better readability and processing.
- Example:
  ```python
  auto.columns = ['MPG','Cylinders','Displacements','Horsepower','Weight','Acceleration','ModelYear','Origin','Car Name']

### 3️⃣ Checking for Missing Values or Null values
- Use `df.isnull().sum()` or check for symbols like `?` or `NAN`.
- Replace or drop missing values based on context (mode/median/mean/drop).
- Example:
  ```python
  df.isnull().sum()
  
### 4️⃣ Check Data Types
- Use `df.dtypes` to inspect data types.
- Fix incorrect types (e.g., converting object to numeric).

### 5️⃣Check Unique Values in Each Column
- Use `for i in df.columns:
    print(i,':','\n',df[i].unique(),'\n')`
  to explore categorical columns.
- Identify typos or inconsistent labels.

### 6️⃣ Descriptive Statistics
- Use `df.describe()` to get a statistical overview of numeric columns.
- Helps detect anomalies like negative ages, wrong units, or outliers.

### 7️⃣ Value Replacement and Cleaning
- Use:
  - `df.replace()`
  - `df.fillna()`
- Example:
  ```python
  df['age'].fillna(df['age'].median(), inplace=True)
  auto.Horsepower.replace('?',d['Horsepower'][2],inplace = True)

### 8️⃣ Change Data Types After Replacing (if Required)
- After cleaning, recheck and convert data types to optimize memory and performance.
- Example:
  ```python
  auto.Horsepower=auto.Horsepower.astype(float)
