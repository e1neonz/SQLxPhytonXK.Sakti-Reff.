import pandas as pd

customers = pd.read_csv('customers.csv')
invoices = pd.read_csv('invoices.csv') 
invoice_lines = pd.read_csv('invoice_lines.csv')

# b. Customers with > 5 books
cust_books = customers.merge(invoices).merge(invoice_lines)
cust_books = cust_books.groupby('id_x')['id_y'].count().reset_index(name='book_count')
print(cust_books[cust_books['book_count'] > 5][['id_x', 'name']])

# c. Customers with no purchases  
no_purchases = customers.merge(invoices, how='left')
print(no_purchases[no_purchases['id_y'].isnull()][['id_x', 'name']])

# d. Book purchases per user
user_books = customers.merge(invoices).merge(invoice_lines)
print(user_books[['name', 'description']])# test

