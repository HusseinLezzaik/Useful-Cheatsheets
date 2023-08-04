## Topics
- Works well for most traditional dataframe manipulation, but doesn't work on GPUs

## Imports
```
$ import pandas
$ from pandas import read_csv
```

## Read from csv file
```
$ pd.read_csv('link')
```

## To find columns of data with missing or corrupted data and drop those values
```
$ isnull()
$ dropna()
$ fillna() # to fill the invalid values with a placeholder value (for example 0) you could use the fillna() method
```

##  Complexity Optimization
- Don't use `pd.iterrows`! Use `apply` or `pd.itertuples` if you must, > 2 orders of magnitude of a speedup

## Data plot hack
```
$ from skimpy import skim, generate_test_data
$ df = generate_test_data()
$ skim(df)
```
