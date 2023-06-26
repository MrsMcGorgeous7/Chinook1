# Chinook1

#This is a Final Project in my SQL project with Charlotte Chaze.

1./Show all customers full name,customer ID and country who are in the USA. 
  SELECT FirstName, LastName, CustomerID,country 
  FROM chinook.customers
  WHERE country = 'USA'

2./Show all the customers from Canada
  SELECT * FROM chinook.customers 
  WHERE country = 'Canada'

3./Find the invoices of customers who are from USA. The resulting table should show the customers full name,Invoie ID, Date of the invoice. 
  SELECT cust. FirstName,cust.LastName,inv.InvoiceID,inv.InvoiceDate
  FROM chinook.invoices AS inv
  LEFT JOIN chinook.customers as cust
  ON inv.customerID = cust.customerID
  WHERE inv.BillingCountry = 'USA';

4./How many employees live in the same city Calgary?
  SELECT * FROM chinook.employees
  WHERE city = 'Calgary';

5./Provide a query that shows all the tracks, and include the album name, media type, and genre. 
  SELECT ar.name AS artist, t.name AS t.InvoiceLineID
  FROM chinook.Invoice_items i
  Left Join chinook. tracks t
  ON i.TrackID = t.TrackID
  INNER JOIN chinook.albums a
  ON a.albumID =t.AlbumID
  LEFT JOIN chinook.artists ar
  ON ar.ArtistID = a.ArtistID;

6./Provide a query that shows the invoices associated with each sales agent. The resulting table should included the Sales Agents full name. 
  SELECT emp. LastName, emp. FirstName, inv.InvoiceID 
  FROM chinook. employee emp
  JOIN chinook.customers cust ON cust.SupportRepID = emp.EmployeeID 
  JOIN chinook.Invoices Inv ON Inv. customerID = cust.customerID;

7./Write a query that includes the purchased track name with each Invoiceline ID.
  SELECT t.name,InvoiceLineID
  FROM chinook.invoice_items i
  JOIN chinook.tracks t
  ON I. trackID = t.trackID

8./Create a query that includes the playlist with all the tracks with there IDs limit to 100.
  SELECT t.name, playlistID
  FROM chinook.playlist_track p
  JOIN chinook.tracks t
  ON p.TrackID = t.TrackID
  Limit to 100


9./Find a unique/distinct list of billing countries from the Invoice tables and include the customers full name
  SELECT DISTINCT Billing Country,c.FirstName, c.LastName
  FROM chinook. invoices i
  JOIN chinook.customers c
  ON i.customerID = c.customerID

10./Show the invoice Total, customer name, and Sales Agent name for all invoices and customers.
  SELECT emp.LastName,emp.FirstName,cust.FirstName,cust.LastName,inv.total
  FROM chinook.customers cust ON cust. SupportRepID = emp. EmployeeID
  JOIN chinook.invoices inv ON Inv.customerID = cust.customerID

11./What are the total sales for 2010?
  SELECT SUM (total)
  FROM chinook.invoices
  WHERE InvoiceDate BETWEEN '2010-01-01' AND '2010-12-31';

12./Which sales agent made the most dollars in sales in 2009?
  SELECT emp.FirstName,emp.LastName,
  ROUND (SUM(Inv.total), 2) 'Total Sales'
  FROM chinook.Employees emp

  JOIN chinook.Invoices inv
  ON Inv.customerID = cust.customerID

  WHERE emp.Title = 'Sales Support Agent'
  AND inv.InvoiceDate LIKE '2009%'
  GROUP BY (round(sum(Invoice.total), 2))DESC Limit 1;

13./Show the total sales made by each sales agent. 
  SELECT emp.FirstName, emp.LastName,
  ROUND (SUM(Inv.total), 2) AS 'Total Sales'
  FROM chinook.employees emp

  JOIN chinook.customer cust
  ON cust.SupportRepID = emp.employeeID

  JOIN chinook.invoices inc
  ON inv.CustomerID =  cust.CustomerID

  WHERE emp. Title = 'Sales Support Agent'
  GROUP BY emp.FirstName;
    
