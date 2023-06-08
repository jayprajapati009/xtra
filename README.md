# Codes

- Get values for a dataframe
```
df = your_dataframe
mask = (df['values_column'] >= 10000) & (df['values_column'] <= 50000)
filtered_values = df.loc[mask, 'values_column']
```

- Convert int to obj
```
data["col_name"]=data["col_name"].astype(str)
```

- To arrange the sns.countplot in order
```
https://www.statology.org/seaborn-countplot-order/
```

- function to generate the graphs
```
def generate_distplot(variable):
    sns.distplot(df[df['TARGET']==0][variable], hist=Flase, color='green', label='Good')
    sns.distplot(df[df['TARGET']==0][variable], hist=Flase, color='red', label='Bad')
    plt.legend()
    plt.show()
```

- percentage in crosstabs
```
import pandas as pd

# Create a sample dataframe
data = {
    'Target': [1, 0, 1, 0, 1, 1, 0],
}
df = pd.DataFrame(data)

# Perform crosstab
crosstab = pd.crosstab(index=df['Target'], columns='count')

# Calculate percentages
total = crosstab['count'].sum()
percentage_crosstab = crosstab.apply(lambda x: x / total * 100, axis=0)

print(percentage_crosstab)
```
