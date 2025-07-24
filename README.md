# Exploratory Data Analysis & Machine Learning Projects 

This repository demonstrates end-to-end Exploratory Data Analysis (EDA) and Machine Learning workflows, focusing on data cleaning, visualization, preprocessing, and model building using Python libraries like **Pandas**, **NumPy**, **Seaborn**, and **Scikit-learn**.

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

- 🐍 Python 3 – Core programming language used for data analysis and machine learning

- 📊 Pandas – Data manipulation and analysis (DataFrames, cleaning, exploration)

- ➕ NumPy – Numerical operations and array processing

- 📈 Matplotlib & Seaborn – Data visualization and statistical plotting

- 📓 Jupyter Notebook – Interactive coding environment for exploratory workflows

- 🧠 Scikit-learn – Machine learning algorithms and model evaluation tools

---

### 🧼 Steps for Data Cleaning

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

 ### ❇️ Data Visualization 
**NOTE**: Before Plotting to the data visualization we have to known which one is output column, to identify we have see dataset from UCI learning website and find a word called **target** written in **Role** column...

**⭐ Some Rules To be Followed before plotting...**
<li>If the output is string or object or Integer like Eg - Male/Female, 0/1, 0/1/2, Yes/No then the output is of <b>Categorical</b> type </li>
<li>If the output is float values or continuous type values like 2.4,2.6,2.9,3.5,3.8.... then the output is <b>Continuous</b> type </li>
<li>After deciding the output is of which type now compare the remaing input values is of which types.. Let say if input datatype is int and output datatype is object then it will be Categorical and Categorical.. </li>

**✅ Use These Plots:**

**1️⃣ Continuous vs Categorical**

| Plot Type    | Description                                     | Code Example                                                |
| ------------ | ----------------------------------------------- | ----------------------------------------------------------- |
| `boxplot`    | Box and whiskers plot to show spread & outliers | `sns.boxplot(x='category', y='value', data=df)`             |
| `violinplot` | Adds KDE distribution to boxplot                | `sns.violinplot(x='category', y='value', data=df)`          |
| `stripplot`  | All data points with some jitter                | `sns.stripplot(x='category', y='value', data=df)`           |
| `swarmplot`  | Spread points non-overlapping                   | `sns.swarmplot(x='category', y='value', data=df)`           |
| `barplot`    | Shows mean and confidence intervals             | `sns.barplot(x='category', y='value', data=df)`             |
| `pointplot`  | Similar to barplot, but with points             | `sns.pointplot(x='category', y='value', data=df)`           |
| `catplot`    | General interface for categorical plots         | `sns.catplot(x='category', y='value', kind='box', data=df)` |
| `boxenplot`  | Better for large datasets with many outliers    | `sns.boxenplot(x='category', y='value', data=df)`           |

**2️⃣ Continuous vs Continuous**

| Plot Type     | Description                                   | Code Example                                              |
| ------------- | --------------------------------------------- | --------------------------------------------------------- |
| `scatterplot` | Standard 2D plot showing relationship         | `sns.scatterplot(x='age', y='income', data=df)`           |
| `jointplot`   | Combines scatterplot with marginal histograms | `sns.jointplot(x='age', y='income', data=df, kind='reg')` |
| `heatmap`     | Shows correlation matrix                      | `sns.heatmap(df.corr(), annot=True, cmap='coolwarm')`     |

**3️⃣ Categorical vs Categorical**

| Plot Type   | Description                                              | Code Example                                                           |
| ----------- | -------------------------------------------------------- | ---------------------------------------------------------------------- |
| `countplot` | Number of occurrences per category                       | `sns.countplot(x='education', hue='gender', data=df)`                  |
| `barplot`   | Mean of a numerical target across categories (works too) | `sns.barplot(x='occupation', y='target_value', hue='gender', data=df)` |

**4️⃣ Univariate Distributions**

| Variable Type | Plot Type   | Code Example                         |
| ------------- | ----------- | ------------------------------------ |
| Numerical     | `histplot`  | `sns.histplot(df['age'], kde=True)`  |
| Numerical     | `kdeplot`   | `sns.kdeplot(df['salary'])`          |
| Categorical   | `countplot` | `sns.countplot(x='gender', data=df)` |
| Any           | `displot`   | `sns.displot(df['age'], kde=True)`   |

**5️⃣ All-in-One Plots**

| Plot Type  | Description                                 | Code Example                                                 |
| ---------- | ------------------------------------------- | ------------------------------------------------------------ |
| `pairplot` | Automatically plots pairwise relationships  | `sns.pairplot(df, hue='target')`                             |
| `catplot`  | Versatile wrapper around multiple cat plots | `sns.catplot(x='workclass', y='hours', kind='box', data=df)` |







The following common steps were applied across datasets using **Matplotlib** and **Seaborn**:





