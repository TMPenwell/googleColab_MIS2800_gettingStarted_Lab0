Note:  This is a markdown file which supports visual differences in content.  You can learn more at https://www.markdownguide.org/basic-syntax/#overview.


#Instructions

Insert the code snippets when prompted. 


##Step 1: Insert Python code to prepare Colab to work with SQL. 
<code>!pip install pandasql
import pandas as pd
from pandasql import sqldf</code>


##Step 2: Create a Pandas Dataframe
This will be the "table" you query
<code>
data = {'id': [1, 2, 3], 
        'product': ['Laptop', 'Monitor', 'Keyboard'], 
        'price': [1200.00, 350.50, 75.00]}
df_products = pd.DataFrame(data)
print("Original DataFrame:")
print(df_products)
</code>



##Step 3: Run SQL queries on the DataFrame
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

# Execute the query
result_df = sqldf(query, globals())

# The result is a new Pandas DataFrame
print("\nSQL Query Result:")
print(result_df)
</code>