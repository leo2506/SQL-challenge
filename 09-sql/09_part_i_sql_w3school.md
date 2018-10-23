# Challenge Set 9
## Part I: W3Schools SQL Lab 

*Introductory level SQL*

--

This challenge uses the [W3Schools SQL playground](http://www.w3schools.com/sql/trysql.asp?filename=trysql_select_all). Please add solutions to this markdown file and submit.

1. Which customers are from the UK?

### SQL Code

```sql
SELECT * FROM Customers
WHERE Country = "UK";
``` 
### Output

CustomerID	| CustomerName | ContactName | Address	| City |	PostalCode	| Country
----------  | ------------ | ----------- | -------- | ---- | ------------ | -------
4	 | Around the Horn	| Thomas Hardy |	120 Hanover Sq. |	London	| WA1 1DP |	UK
11 |	B's Beverages	| Victoria Ashworth |	Fauntleroy Circus |	London |	EC2 5NT |	UK
16 |	Consolidated Holdings |	Elizabeth Brown |	Berkeley Gardens 12 Brewery	| London |	WX1 6LT |	UK
19 |	Eastern Connection	| Ann Devon |	35 King George | London |	WX3 6FW	| UK
38 | 	Island Trading	| Helen Bennett	| Garden House Crowther Way |	Cowes	| PO31 7PJ |	UK
53 | North/South | Simon Crowther	| South House 300 Queensbridge | London |	SW7 1RZ |	UK
72 |	Seven Seas Imports |	Hari Kumar |	90 Wadhurst Rd. |	London |	OX15 4NB |	UK


2. What is the name of the customer who has the most orders?

### SQL Code

```sql
SELECT CustomerName, COUNT(OrderID) as TOTAL
FROM Customers c JOIN Orders o
ON c.CustomerID = o.CustomerID
GROUP BY CustomerName
ORDER BY 2 DESC 
LIMIT 1;
``` 
### Output

CustomerName | 	TOTAL
------------ | -------------
Ernst Handel | 	10

3. Which supplier has the highest average product price?
### SQL Code

```sql
SELECT SupplierName, AVG(Price) 
FROM Suppliers s JOIN Products p
ON s.SupplierID = p.SupplierID
GROUP BY SupplierName
ORDER BY 2 DESC LIMIT 1;
``` 
### Output


SupplierName | 		AVG(Price)
------------ | -------------
Aux joyeux ecclésiastiques | 	140.75

4. How many different countries are all the customers from? (*Hint:* consider [DISTINCT](http://www.w3schools.com/sql/sql_distinct.asp).)

### SQL Code

```sql
SELECT COUNT(DISTINCT Country) 
FROM Customers
``` 
### Output

COUNT(DISTINCT Country)
| -----
21

5. What category appears in the most orders?

```sql
SELECT CategoryName, COUNT(DISTINCT OrderID) total
FROM OrderDetails od JOIN Products p
USING (ProductID) JOIN Categories c
USING (CategoryID)
GROUP BY CategoryName
ORDER BY 2 DESC LIMIT 1;
``` 
### Output

CategoryName | 			total
------------ | -------------
Beverages | 	80

6. What was the total cost for each order?

```sql
SELECT OrderID, SUM(Price*Quantity) TotalCost FROM 
OrderDetails od JOIN Products p
USING(ProductID)
GROUP BY OrderID
ORDER BY 2 DESC;
``` 
### Output
|OrderID|TotalCost|
|--- |--- |
|10372|15353.6|
|10424|14366.5|
|10417|14104|
|10353|13427|
|10360|9244.250000000002|
|10324|7698.45|
|10440|7246.01|
|10430|7245|
|10351|7103.599999999999|
|10329|6025.12|
|10305|5197.25|
|10267|5040|
|10401|4837.02|
|10252|4662.5|
|10359|4572.2|
|10339|4330.4|
|10393|4135.6|
|10298|3909.5|
|10400|3829.59|
|10286|3772|
|10345|3662|
|10382|3628.76|
|10344|3570|
|10316|3547.5|
|10398|3420|
|10402|3393.5|
|10302|3388.8|
|10340|3205.8|
|10335|3181.5|
|10369|3159.8|
|10431|3155|
|10255|3115.75|
|10337|3087.52|
|10263|3086.4|
|10395|2920|
|10314|2910|
|10342|2876|
|10390|2845.2|
|10361|2842|
|10327|2828.65|
|10332|2792|
|10384|2778|
|10436|2763.5|
|10419|2760|
|10285|2726.8|
|10290|2713.8500000000004|
|10273|2679.5|
|10413|2656|
|10258|2529.75|
|10406|2527|
|10330|2431.5|
|10396|2380.8|
|10420|2372|
|10294|2359.5|
|10249|2329.25|
|10368|2294.05|
|10389|2292|
|10418|2268.5|
|10250|2267.25|
|10442|2246|
|10399|2207|
|10309|2202.5|
|10441|2195|
|10429|2186.5|
|10260|2183.9|
|10346|2164|
|10373|2135|
|10404|2096.9|
|10408|2030.2|
|10312|2019.9|
|10343|1982.5|
|10362|1938.8|
|10325|1873.25|
|10278|1862.4|
|10272|1821.1999999999998|
|10284|1816.95|
|10253|1806|
|10392|1800|
|10380|1776.02|
|10297|1776|
|10283|1770|
|10270|1720|
|10357|1701.68|
|10292|1620|
|10421|1595.6999999999998|
|10388|1594.5|
|10303|1555|
|10411|1514.25|
|10277|1503.6|
|10407|1492.5|
|10319|1490.4|
|10265|1470|
|10370|1467.5|
|10328|1462|
|10257|1400.5|
|10356|1383|
|10268|1377.1000000000001|
|10439|1348.7|
|10387|1323.6|
|10296|1315.5|
|10423|1275|
|10377|1272|
|10403|1258.95|
|10326|1227.5|
|10379|1200.6|
|10304|1193|
|10333|1192.5|
|10364|1187.5|
|10338|1168.35|
|10347|1160.1|
|10287|1158|
|10383|1123.75|
|10385|1080|
|10433|1064|
|10293|1061|
|10397|1054|
|10367|1044.85|
|10410|1002.5|
|10301|944|
|10264|906.25|
|10416|902|
|10350|891.75|
|10269|846|
|10251|839.5|
|10427|813.75|
|10435|790|
|10262|782.2|
|10254|781.5|
|10280|766.5|
|10300|760|
|10354|711.1600000000001|
|10438|710.5|
|10291|692.8|
|10274|673.5999999999999|
|10443|673.2|
|10256|648|
|10315|646|
|10320|645|
|10306|624.15|
|10432|610.3|
|10355|600|
|10425|600|
|10289|599.25|
|10279|585|
|10374|573.75|
|10248|566|
|10358|565|
|10261|560|
|10363|559|
|10394|553|
|10307|530.5|
|10276|525|
|10376|525|
|10341|515|
|10365|504|
|10405|500|
|10348|495|
|10437|491.99999999999994|
|10412|465|
|10266|456|
|10434|450|
|10299|438|
|10375|423.25|
|10426|422.75|
|10310|421|
|10409|399|
|10336|396|
|10275|384|
|10317|360|
|10311|336|
|10318|301|
|10414|290.6|
|10428|240|
|10313|228|
|10386|207.5|
|10323|205.5|
|10282|194.34|
|10352|194|
|10334|181|
|10321|180|
|10349|178.8|
|10366|170.25|
|10295|152|
|10322|140|
|10381|140|
|10378|129|
|10415|128|
|10259|126|
|10371|114|
|10288|112|
|10331|111.75|
|10308|111|
|10281|108.2|
|10391|108|
|10422|62.46|
|10271|60|



7. Which employee made the most sales (by total price)?

8. Which employees have BS degrees? (*Hint:* look at the [LIKE](http://www.w3schools.com/sql/sql_like.asp) operator.)

9. Which supplier of three or more products has the highest average product price? (*Hint:* look at the [HAVING](http://www.w3schools.com/sql/sql_having.asp) operator.)
