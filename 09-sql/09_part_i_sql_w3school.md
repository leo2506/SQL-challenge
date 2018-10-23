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

<tbody><tr><th>OrderID</th><th>TotalCost</th></tr><tr><td>10372</td><td>15353.6</td></tr><tr><td>10424</td><td>14366.5</td></tr><tr><td>10417</td><td>14104</td></tr><tr><td>10353</td><td>13427</td></tr><tr><td>10360</td><td>9244.250000000002</td></tr><tr><td>10324</td><td>7698.45</td></tr><tr><td>10440</td><td>7246.01</td></tr><tr><td>10430</td><td>7245</td></tr><tr><td>10351</td><td>7103.599999999999</td></tr><tr><td>10329</td><td>6025.12</td></tr><tr><td>10305</td><td>5197.25</td></tr><tr><td>10267</td><td>5040</td></tr><tr><td>10401</td><td>4837.02</td></tr><tr><td>10252</td><td>4662.5</td></tr><tr><td>10359</td><td>4572.2</td></tr><tr><td>10339</td><td>4330.4</td></tr><tr><td>10393</td><td>4135.6</td></tr><tr><td>10298</td><td>3909.5</td></tr><tr><td>10400</td><td>3829.59</td></tr><tr><td>10286</td><td>3772</td></tr><tr><td>10345</td><td>3662</td></tr><tr><td>10382</td><td>3628.76</td></tr><tr><td>10344</td><td>3570</td></tr><tr><td>10316</td><td>3547.5</td></tr><tr><td>10398</td><td>3420</td></tr><tr><td>10402</td><td>3393.5</td></tr><tr><td>10302</td><td>3388.8</td></tr><tr><td>10340</td><td>3205.8</td></tr><tr><td>10335</td><td>3181.5</td></tr><tr><td>10369</td><td>3159.8</td></tr><tr><td>10431</td><td>3155</td></tr><tr><td>10255</td><td>3115.75</td></tr><tr><td>10337</td><td>3087.52</td></tr><tr><td>10263</td><td>3086.4</td></tr><tr><td>10395</td><td>2920</td></tr><tr><td>10314</td><td>2910</td></tr><tr><td>10342</td><td>2876</td></tr><tr><td>10390</td><td>2845.2</td></tr><tr><td>10361</td><td>2842</td></tr><tr><td>10327</td><td>2828.65</td></tr><tr><td>10332</td><td>2792</td></tr><tr><td>10384</td><td>2778</td></tr><tr><td>10436</td><td>2763.5</td></tr><tr><td>10419</td><td>2760</td></tr><tr><td>10285</td><td>2726.8</td></tr><tr><td>10290</td><td>2713.8500000000004</td></tr><tr><td>10273</td><td>2679.5</td></tr><tr><td>10413</td><td>2656</td></tr><tr><td>10258</td><td>2529.75</td></tr><tr><td>10406</td><td>2527</td></tr><tr><td>10330</td><td>2431.5</td></tr><tr><td>10396</td><td>2380.8</td></tr><tr><td>10420</td><td>2372</td></tr><tr><td>10294</td><td>2359.5</td></tr><tr><td>10249</td><td>2329.25</td></tr><tr><td>10368</td><td>2294.05</td></tr><tr><td>10389</td><td>2292</td></tr><tr><td>10418</td><td>2268.5</td></tr><tr><td>10250</td><td>2267.25</td></tr><tr><td>10442</td><td>2246</td></tr><tr><td>10399</td><td>2207</td></tr><tr><td>10309</td><td>2202.5</td></tr><tr><td>10441</td><td>2195</td></tr><tr><td>10429</td><td>2186.5</td></tr><tr><td>10260</td><td>2183.9</td></tr><tr><td>10346</td><td>2164</td></tr><tr><td>10373</td><td>2135</td></tr><tr><td>10404</td><td>2096.9</td></tr><tr><td>10408</td><td>2030.2</td></tr><tr><td>10312</td><td>2019.9</td></tr><tr><td>10343</td><td>1982.5</td></tr><tr><td>10362</td><td>1938.8</td></tr><tr><td>10325</td><td>1873.25</td></tr><tr><td>10278</td><td>1862.4</td></tr><tr><td>10272</td><td>1821.1999999999998</td></tr><tr><td>10284</td><td>1816.95</td></tr><tr><td>10253</td><td>1806</td></tr><tr><td>10392</td><td>1800</td></tr><tr><td>10380</td><td>1776.02</td></tr><tr><td>10297</td><td>1776</td></tr><tr><td>10283</td><td>1770</td></tr><tr><td>10270</td><td>1720</td></tr><tr><td>10357</td><td>1701.68</td></tr><tr><td>10292</td><td>1620</td></tr><tr><td>10421</td><td>1595.6999999999998</td></tr><tr><td>10388</td><td>1594.5</td></tr><tr><td>10303</td><td>1555</td></tr><tr><td>10411</td><td>1514.25</td></tr><tr><td>10277</td><td>1503.6</td></tr><tr><td>10407</td><td>1492.5</td></tr><tr><td>10319</td><td>1490.4</td></tr><tr><td>10265</td><td>1470</td></tr><tr><td>10370</td><td>1467.5</td></tr><tr><td>10328</td><td>1462</td></tr><tr><td>10257</td><td>1400.5</td></tr><tr><td>10356</td><td>1383</td></tr><tr><td>10268</td><td>1377.1000000000001</td></tr><tr><td>10439</td><td>1348.7</td></tr><tr><td>10387</td><td>1323.6</td></tr><tr><td>10296</td><td>1315.5</td></tr><tr><td>10423</td><td>1275</td></tr><tr><td>10377</td><td>1272</td></tr><tr><td>10403</td><td>1258.95</td></tr><tr><td>10326</td><td>1227.5</td></tr><tr><td>10379</td><td>1200.6</td></tr><tr><td>10304</td><td>1193</td></tr><tr><td>10333</td><td>1192.5</td></tr><tr><td>10364</td><td>1187.5</td></tr><tr><td>10338</td><td>1168.35</td></tr><tr><td>10347</td><td>1160.1</td></tr><tr><td>10287</td><td>1158</td></tr><tr><td>10383</td><td>1123.75</td></tr><tr><td>10385</td><td>1080</td></tr><tr><td>10433</td><td>1064</td></tr><tr><td>10293</td><td>1061</td></tr><tr><td>10397</td><td>1054</td></tr><tr><td>10367</td><td>1044.85</td></tr><tr><td>10410</td><td>1002.5</td></tr><tr><td>10301</td><td>944</td></tr><tr><td>10264</td><td>906.25</td></tr><tr><td>10416</td><td>902</td></tr><tr><td>10350</td><td>891.75</td></tr><tr><td>10269</td><td>846</td></tr><tr><td>10251</td><td>839.5</td></tr><tr><td>10427</td><td>813.75</td></tr><tr><td>10435</td><td>790</td></tr><tr><td>10262</td><td>782.2</td></tr><tr><td>10254</td><td>781.5</td></tr><tr><td>10280</td><td>766.5</td></tr><tr><td>10300</td><td>760</td></tr><tr><td>10354</td><td>711.1600000000001</td></tr><tr><td>10438</td><td>710.5</td></tr><tr><td>10291</td><td>692.8</td></tr><tr><td>10274</td><td>673.5999999999999</td></tr><tr><td>10443</td><td>673.2</td></tr><tr><td>10256</td><td>648</td></tr><tr><td>10315</td><td>646</td></tr><tr><td>10320</td><td>645</td></tr><tr><td>10306</td><td>624.15</td></tr><tr><td>10432</td><td>610.3</td></tr><tr><td>10355</td><td>600</td></tr><tr><td>10425</td><td>600</td></tr><tr><td>10289</td><td>599.25</td></tr><tr><td>10279</td><td>585</td></tr><tr><td>10374</td><td>573.75</td></tr><tr><td>10248</td><td>566</td></tr><tr><td>10358</td><td>565</td></tr><tr><td>10261</td><td>560</td></tr><tr><td>10363</td><td>559</td></tr><tr><td>10394</td><td>553</td></tr><tr><td>10307</td><td>530.5</td></tr><tr><td>10276</td><td>525</td></tr><tr><td>10376</td><td>525</td></tr><tr><td>10341</td><td>515</td></tr><tr><td>10365</td><td>504</td></tr><tr><td>10405</td><td>500</td></tr><tr><td>10348</td><td>495</td></tr><tr><td>10437</td><td>491.99999999999994</td></tr><tr><td>10412</td><td>465</td></tr><tr><td>10266</td><td>456</td></tr><tr><td>10434</td><td>450</td></tr><tr><td>10299</td><td>438</td></tr><tr><td>10375</td><td>423.25</td></tr><tr><td>10426</td><td>422.75</td></tr><tr><td>10310</td><td>421</td></tr><tr><td>10409</td><td>399</td></tr><tr><td>10336</td><td>396</td></tr><tr><td>10275</td><td>384</td></tr><tr><td>10317</td><td>360</td></tr><tr><td>10311</td><td>336</td></tr><tr><td>10318</td><td>301</td></tr><tr><td>10414</td><td>290.6</td></tr><tr><td>10428</td><td>240</td></tr><tr><td>10313</td><td>228</td></tr><tr><td>10386</td><td>207.5</td></tr><tr><td>10323</td><td>205.5</td></tr><tr><td>10282</td><td>194.34</td></tr><tr><td>10352</td><td>194</td></tr><tr><td>10334</td><td>181</td></tr><tr><td>10321</td><td>180</td></tr><tr><td>10349</td><td>178.8</td></tr><tr><td>10366</td><td>170.25</td></tr><tr><td>10295</td><td>152</td></tr><tr><td>10322</td><td>140</td></tr><tr><td>10381</td><td>140</td></tr><tr><td>10378</td><td>129</td></tr><tr><td>10415</td><td>128</td></tr><tr><td>10259</td><td>126</td></tr><tr><td>10371</td><td>114</td></tr><tr><td>10288</td><td>112</td></tr><tr><td>10331</td><td>111.75</td></tr><tr><td>10308</td><td>111</td></tr><tr><td>10281</td><td>108.2</td></tr><tr><td>10391</td><td>108</td></tr><tr><td>10422</td><td>62.46</td></tr><tr><td>10271</td><td>60</td></tr></tbody>

7. Which employee made the most sales (by total price)?

8. Which employees have BS degrees? (*Hint:* look at the [LIKE](http://www.w3schools.com/sql/sql_like.asp) operator.)

9. Which supplier of three or more products has the highest average product price? (*Hint:* look at the [HAVING](http://www.w3schools.com/sql/sql_having.asp) operator.)
