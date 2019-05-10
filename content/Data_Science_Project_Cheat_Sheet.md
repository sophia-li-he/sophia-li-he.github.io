Title: Data Science Project Cheat Sheet
Date: 2019-05-07 10:20
Category: Python


## Pre-processing
- Drop na in one column: drop all the rows if columns 'Salary' is null.

```python
drop_sal_df = num_vars.dropna(subset = ['Salary'])
```

- Fill all missing values with the mean of the column

```python
fill_mean = lambda col: col.fillna(col.mean())
fill_df = drop_sal_df.apply(fill_mean, axis = 0)
```

### Categorical
- Create a dummy variable with na as a new column

```python
dummy_cols_df = pd.get_dummies(dummy_var_df['col1'], dummy_na = True)
```

INPUT:
    df - pandas dataframe with categorical variables you want to dummy
    cat_cols - list of strings that are associated with names of the categorical columns
    dummy_na - Bool holding whether you want to dummy NA vals of categorical columns or not
    
OUTPUT:
    df - a new dataframe that has the following characteristics:
            1. contains all columns that were not specified as categorical
            2. removes all the original columns in cat_cols
            3. dummy columns for each of the categorical columns in cat_cols
            4. if dummy_na is True - it also contains dummy columns for the NaN values
            5. Use a prefix of the column name with an underscore (_) for separating 
```python
cat_df = df.select_dtypes(include=['object']).copy()
#Create a copy of the dataframe
cat_df_copy = cat_df.copy()
#Pull a list of the column names of the categorical variables
cat_cols_lst = cat_df.columns

def create_dummy_df(df, cat_cols, dummy_na):
    cat_df = pd.get_dummies(df[cat_cols], prefix = cat_cols, prefix_sep='_', dummy_na = dummy_na, drop_first=True)
    df_copy = df.drop(cat_cols, axis = 1)
    df_copy = df_copy.merge(cat_df, how = 'inner', left_index = True, right_index = True)

    return df_copy
```

## Linear Regression
- Numeric variables

```python
X = fill_df[['CareerSatisfaction', 'HoursPerWeek', 'JobSatisfaction', 'StackOverflowSatisfaction']]
y = fill_df['Salary']

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = .30, random_state=42) 

lm_model = LinearRegression(normalize=True) # Instantiate
lm_model.fit(X_train, y_train) #Fit

y_test_preds = lm_model.predict(X_test) 

rsquared_score = r2_score(y_test, y_test_preds) #r2_score
length_y_test = len(y_test) #num in y_test

"The r-squared score for your model was {} on {} values.".format(rsquared_score, length_y_test)
```

