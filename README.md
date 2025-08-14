# Sales-insight
 TO show all customer records :-
SELECT * FROM customers;

Show total number of customers :-
SELECT count(*) FROM customers;

To show transactions for any particular market place :-
SELECT * FROM transactions where market_code='Mark001';

 To show distrinct product codes that were sold in particular region :-
SELECT distinct product_code FROM transactions where market_code='Mark001';

To show transactions in 2020 join by date table :-
SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;

TO Show total revenue in year 2020 :-
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";

To show total revenue in year 2020, January Month :-
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");

Show total revenue in year 2020 in a any particular place :-
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";

Data Analysis Using Power BI
Formula to create norm_amount column :-
= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*87 else [sales_amount], type any)
