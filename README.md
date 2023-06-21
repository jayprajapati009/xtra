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
