# Codes

```

# Write the output to a file
with open('output.txt', 'w') as file:
    # Convert DataFrame to string row-wise
    df_str = iv.apply(lambda row: row.astype(str).str.cat(sep=' '), axis=1)
    
    # Print the string representation of each row
    for row_str in df_str:
        file.write(row_str)
```

```
import pandas as pd

# Convert DataFrame to string row-wise
df_str = iv.apply(lambda row: row.astype(str).str.cat(sep=' '), axis=1)

# Create a DataFrame with the row-wise strings
output_df = pd.DataFrame(df_str, columns=['Row Strings'])

# Write the DataFrame to an Excel file
output_df.to_excel('output.xlsx', index=False)


```
