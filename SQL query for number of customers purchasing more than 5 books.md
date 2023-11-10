SELECT c.name, COUNT(*) AS total_books
FROM customers c
JOIN invoices i ON c.id = i.customer_id 
JOIN invoice_lines il ON i.id = il.invoice_id
GROUP BY c.name
HAVING total_books > 5;
