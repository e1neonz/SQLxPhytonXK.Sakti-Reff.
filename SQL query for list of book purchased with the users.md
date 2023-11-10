SELECT c.name, il.description
FROM customers c
JOIN invoices i ON c.id = i.customer_id 
JOIN invoice_lines il ON i.id = il.invoice_id;
