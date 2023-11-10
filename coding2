import pandas as pd
from sqlalchemy import create_engine

# Step 1: Extract - Load data from CSV files into Pandas DataFrames
customers_df = pd.read_csv('customers.csv')
invoices_df = pd.read_csv('invoices.csv')
invoice_lines_df = pd.read_csv('invoice_lines.csv')

# Step 2: Transform - Perform data manipulations (e.g., SQL-like queries)
# b. SQL query for the number of customers purchasing more than 5 books
customers_purchasing_more_than_5_books = pd.read_sql_query("""
    SELECT customers.id, customers.name
    FROM customers
    JOIN invoices ON customers.id = invoices.customer_id
    JOIN invoice_lines ON invoices.id = invoice_lines.invoice_id
    GROUP BY customers.id
    HAVING COUNT(DISTINCT invoice_lines.id) > 5;
""", create_engine('sqlite:///:memory:'))

# c. SQL query for a list of customers who never purchased anything
customers_never_purchased = pd.read_sql_query("""
    SELECT customers.id, customers.name
    FROM customers
    LEFT JOIN invoices ON customers.id = invoices.customer_id
    WHERE invoices.id IS NULL;
""", create_engine('sqlite:///:memory:'))

# d. SQL query for a list of books purchased with the users
books_purchased_with_users = pd.read_sql_query("""
    SELECT customers.name, invoice_lines.description
    FROM customers
    JOIN invoices ON customers.id = invoices.customer_id
    JOIN invoice_lines ON invoices.id = invoice_lines.invoice_id;
""", create_engine('sqlite:///:memory:'))

# Step 3: Load - Store the transformed data back into the database or another destination
# (This is a simplified example, in a real scenario, you might want to store the results in a new table or a separate database)

# Display the results
print("Customers purchasing more than 5 books:")
print(customers_purchasing_more_than_5_books)

print("\nCustomers who never purchased anything:")
print(customers_never_purchased)

print("\nBooks purchased with users:")
print(books_purchased_with_users)
