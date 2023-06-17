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

- Subplots
```
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd

# Create a sample dataframe
data = {
    'Category': ['A', 'A', 'B', 'B', 'B', 'C', 'C'],
    'Value': [1, 2, 3, 4, 5, 6, 7]
}
df = pd.DataFrame(data)

# Create subplots
fig, axes = plt.subplots(2, 2, figsize=(10, 8))

# Create displots on each subplot
sns.histplot(data=df[df['Category'] == 'A'], x='Value', kde=True, ax=axes[0, 0])
sns.histplot(data=df[df['Category'] == 'B'], x='Value', kde=True, ax=axes[0, 1])
sns.histplot(data=df[df['Category'] == 'C'], x='Value', kde=True, ax=axes[1, 0])

# Remove the last subplot (axes[1, 1])
fig.delaxes(axes[1, 1])

# Set titles for each subplot
axes[0, 0].set_title('Category A')
axes[0, 1].set_title('Category B')
axes[1, 0].set_title('Category C')

# Adjust spacing between subplots
plt.tight_layout()

# Display the plot
plt.show()

```

```
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd

# Create a sample dataframe
data = {
    'Category': ['A', 'A', 'B', 'B', 'B', 'C', 'C'],
    'Value': [1, 2, 3, 4, 5, 6, 7]
}
df = pd.DataFrame(data)

# Create subplots
fig, axes = plt.subplots(1, 3, figsize=(10, 4))

# Create histograms on each subplot
sns.histplot(data=df[df['Category'] == 'A'], x='Value', kde=True, ax=axes[0])
sns.histplot(data=df[df['Category'] == 'B'], x='Value', kde=True, ax=axes[1])
sns.histplot(data=df[df['Category'] == 'C'], x='Value', kde=True, ax=axes[2])

# Set titles for each subplot
axes[0].set_title('Category A')
axes[1].set_title('Category B')
axes[2].set_title('Category C')

# Set individual legends for each subplot
axes[0].legend(['Category A'])
axes[1].legend(['Category B'])
axes[2].legend(['Category C'])

# Set individual x-axis limits for each subplot
axes[0].set_xlim(0, 5)
axes[1].set_xlim(0, 10)
axes[2].set_xlim(0, 10)

# Adjust spacing between subplots
plt.tight_layout()

# Display the plot
plt.show()

```

- Feature imp
```

# Load libraries
import pandas as pd
from sklearn.tree import DecisionTreeClassifier # Import Decision Tree Classifier
from sklearn.model_selection import train_test_split # Import train_test_split function
from sklearn import metrics #Import scikit-learn metrics module for accuracy calculation

import seaborn as sns
import matplotlib.pyplot as plt

# Get feature importances
importances = clf.feature_importances_

# Create a dataframe with feature names and importances
feature_importances = pd.DataFrame({'Feature': <Put cols>, 'Importance': importances})

# Sort the dataframe by importance in descending order
feature_importances = feature_importances.sort_values('Importance', ascending=False)

# Plot the feature importances using Seaborn
plt.figure(figsize=(10, 6))
sns.barplot(x='Importance', y='Feature', data=feature_importances, palette='viridis')
plt.xlabel('Importance')
plt.ylabel('Feature')
plt.title('Decision Tree - Feature Importances')
plt.show()
```

- subplots for all variables
```
import matplotlib.pyplot as plt
import seaborn as sns

variable_list = df0.columns.tolist()

# Calculate the number of rows and columns for subplots
num_variables = len(variable_list)
num_rows = (num_variables + 1) // 2
num_cols = min(2, num_variables)

# Create subplots with the specified number of rows and columns
fig, axes = plt.subplots(num_rows, num_cols, figsize=(12, 6))

# Flatten the axes array to make it easier to iterate over
axes = axes.flatten()

# Iterate over the variable list and create KDE plots in each subplot
for i, variable in enumerate(variable_list):
    # Select the appropriate subplot for the current variable
    ax = axes[i]
    
    # Plot the KDE plots for TARGET=0 and TARGET=1 on the selected subplot
    sns.kdeplot(df_transact[df_transact['TARGET'] == 0][variable], color="green", shade=True, cut=0, ax=ax)
    sns.kdeplot(df_transact[df_transact['TARGET'] == 1][variable], color="red", shade=True, cut=0, ax=ax)
    
    # Set the title of the subplot to the variable name
    ax.set_title(variable)
    
# Remove any empty subplots if the number of variables is not a multiple of 2
if num_variables % 2 != 0:
    fig.delaxes(axes[-1])

# Adjust the spacing between subplots
fig.tight_layout()

# Display the subplots
plt.show()

```
