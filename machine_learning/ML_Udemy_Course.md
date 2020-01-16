* Necessary details for Course are available at https://www.superdatascience.com/pages/machine-learning
# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Data Preprocessing](#data-preprocessing)
    - [Importing Libraries](#importing-libraries)
    - [Importing Dataset](#importing-dataset)



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
data.csv file is the ![dataset](https://github.com/karthikkappagantula/my_tech_notes/blob/master/machine_learning/resources/Screenshot%202020-01-16%20at%2010.41.46%20PM.png?raw=true)


**Before importing dataset, you have to set the current working directory in Spyder/Rstudio**
* For Python
  * Use pandas to import the dataset. Pandas creates a Dataframe with imported data.
  * Create the matrix of features/independent variables.
  * Create the vector for dependent variable.
  

```
# importing the dataset
dataset = pd.read_csv('Data.csv')
```

  

