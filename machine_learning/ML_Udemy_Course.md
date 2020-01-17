* Necessary details for Course are available at https://www.superdatascience.com/pages/machine-learning
# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Data Preprocessing](#data-preprocessing)
    - [Importing Libraries](#importing-libraries)
    - [Importing Dataset](#importing-dataset)
    - [Handling missing data](#handling-missing-data)



## Data Preprocessing

### Importing Libraries

* For Python - import below libraries.
  ```
  # importing the libraries
  import numpy as np
  import matplotlib.pyplot as plt
  import pandas as pd
  ```
* For R - Does not need any special libraries.

### Importing Dataset
data.csv file is the as below - 
![dataset](https://github.com/karthikkappagantula/my_tech_notes/blob/master/machine_learning/resources/Screenshot%202020-01-16%20at%2010.41.46%20PM.png?raw=true)


**Before importing dataset, you have to set the current working directory in Spyder/Rstudio**
* For Python
  * Use pandas to import the dataset. Pandas creates a Dataframe with imported data.
  * Create the matrix of features/independent variables.
  * Create the vector for dependent variable.
  
```
# importing the dataset
dataset = pd.read_csv('Data.csv')
X = dataset.iloc[:, :-1].values     #Object for Country, Age, Salary - independent variables or features
y = dataset.iloc[:, 3].values       #Object for Purshed - dependent variable
```

*dataset.iloc[:, :-1].values extracts data from all rows, and all columns except the last column* <br>
*dataset.iloc[:, 3].values extracts data from all rows, and from last column* <br>
*In python index starts from 0* <br>

* For R
  * Use read.csv to import dataset (10 observations of 4 variables)

```
# Importing the dataset
dataset = read.csv("Data.csv")
```
*In R index starts from 1*

### Handling missing data
  
* In the input dataset, there are few missing values (Age value for Spain, and Salary value for Germany). 
* This should be handled without removing the observation.
* We will use the mean value of all the values for the feature for the missing data.

* For Python
  * Use **Imputer** from **sklearn.preprocessing** library (scikit-learn)

```
#taking care of missing data
from sklearn.impute import SimpleImputer
imputer = SimpleImputer(missing_values = np.nan, strategy = "mean")
imputer = imputer.fit(X[:, 1:3])
X[:, 1:3] = imputer.transform(X[:, 1:3])
print(X)
```
*In spyder use command+i to bring up object inspector*

  * SimpleImputer definition
  
  ```
  Definition : SimpleImputer(missing_values=np.nan, strategy="mean", fill_value=None, verbose=0, copy=True, add_indicator=False)
  Type : Present in sklearn.impute._base module
  ```

* For R
  
```
# Taking care of missing values
dataset$Age = ifelse(is.na(dataset$Age), 
                     ave(dataset$Age, FUN = function(x) mean(x, na.rm = TRUE)),
                     dataset$Age)
dataset$Salary = ifelse(is.na(dataset$Salary),
                        ave(dataset$Salary, FUN = function(x) mean(x, na.rm = TRUE)),
                        dataset$Salary)
```