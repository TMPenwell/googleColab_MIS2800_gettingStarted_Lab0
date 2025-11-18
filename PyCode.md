Note:  This is a markdown file which supports visual differences in content.  You can learn more at https://www.markdownguide.org/basic-syntax/#overview.


# Instructions

Insert the code snippets when prompted. 


## Step 1: Insert Python code to prepare Colab to work with SQL. 
<code>!pip install pandasql
import pandas as pd
from pandasql import sqldf</code>


## Step 2: Create a Pandas Dataframe
This will be the "table" you query
<code>
data = {'id': [1, 2, 3], 
        'product': ['Laptop', 'Monitor', 'Keyboard'], 
        'price': [1200.00, 350.50, 75.00]}
df_products = pd.DataFrame(data)
print("Original DataFrame:")
print(df_products)
</code>



## Step 3: Run SQL queries on the DataFrame
<code>
# SQL query to select products priced over 100
query = """
SELECT 
    product, 
    price 
FROM 
    df_products 
WHERE 
    price > 100 
ORDER BY 
    price DESC;
"""

### Execute the query
result_df = sqldf(query, globals())

### The result is a new Pandas DataFrame
print("\nSQL Query Result:")
print(result_df)
</code>

import pandas as pd
from google.colab import files

# --- 1. Create the Excel file in the Colab session storage ---

## Assuming 'df' is your final DataFrame
# If you don't have a DataFrame, you can create one for testing:
data = {'Name': ['Alice', 'Bob'], 'Score': [95, 88]}
df = pd.DataFrame(data)

## Save the DataFrame to a local Excel file named 'Colab_Output.xlsx'
## Set index=False to prevent the DataFrame's row numbers from being written to the file
file_name = 'Colab_Output.xlsx'
df.to_excel(file_name, index=False, sheet_name='Summary_Data') 

print(f"File '{file_name}' created successfully in Colab storage.")

## --- 2. Trigger the download to your local machine ---

files.download(file_name) 

## Note: The download prompt/process may vary slightly depending on your browser.
