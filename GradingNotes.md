2017PurchasePricesDec.csv
BegInvFINAL12312016.csv
EndInvFINAL12312016.csv
InvoicePurchases12312016.csv
PurchasesFINAL12312016.csv
SalesFINAL12312016.csv

Sampled
BegInvFINAL12-31-16Sample.csv
EndInvFINAL12-31-16Sample.csv
InvoicePurchases12-31-16Sample.csv
PurchasesFINAL12-31-16Sample.csv
SalesFINAL12-31-16Sample.csv

2017PurchasePricesDecSample.csv

# Grading Notes

## Adam Acevedo **33**
* 2a. -0.5 pts: Wrong logic, used begInv instead of EndInv:
    ```python
    EndInv['InvCost12_31_2016'] = EndInv['12_31_2016_Qty'] * begInv['Price']
    -->EndInv['InvCost12_31_2016'] = EndInv['12_31_2016_Qty'] * EndInv['Price']
    ```
* 2b. -0.5 pts: Wrong logic, used begInv instead of EndInv:
    ```python
    EndInv['InvCost12_31_2016'] = EndInv['12_31_2016_Qty'] * begInv['Price']
    --> EndInv['InvCost12_31_2016'] = EndInv['12_31_2016_Qty'] * EndInv['Price']
    ```
* 3. -0.5 pts: Wrong logic, used begInv to multiply endInv quantity
    ```python
    endInv['InvCost12_31_2016'] = EndInv['12_31_2016_Qty'] * begInv['Price']
    -->endInv['InvCost12_31_2016'] = EndInv['12_31_2016_Qty'] * EndInv['Price']
    ```
* 4a. Used invoice data. Didn't filter, but can assume used receiving date (valid)
* 4b. Didn't filter for 2016 (ignored)
* 4c. -0.5 pts: Reorder aggregation before ratio freight/dollar
* 4d. Fix output line to match answer key (ignored)
    ```python
    HighestFreight[["Freight"]].head()
    -->HighestFreight.head()
    ```
* 5. This is taking the total dollar cost and subtracting it from a single cost of a SalesPrice

##  Armando Almazan **ERROR**
* Cannot grade, file is in HTML, not ipynb

## Tamara Alvarado **34.5**
* Reponses identical to answer key
* 5. =-0.5 pts: Broken logic, uses equal over subtraction symbol:
    ```python
    dfCM['Contribution Margin']=dfCM['SalesPrice']=dfCM['PurchasePrice']
    -->dfCM['Contribution Margin']=dfCM['SalesPrice']-dfCM['PurchasePrice']
    ```
  * No mention of attending Friday Session

## Ella AlvesdeLima **29.5**
* 1a. -0.5 pts: Missing sort_values
    ```python
    begInv_Store = begInv[['Store','01_01_2016_Qty','InvCost01_01_2016']].groupby('Store').sum()
    -->begInv_Store = begInv[['Store','01_01_2016_Qty','InvCost01_01_2016']].groupby('Store').sum().sort_values('InvCost01_01_2016', ascending = False)
    ```
    * 1b. Has the correct answer
* 1b. -1 pt: Responses from 1a are in 1b, missing 1b proper response. Didn't reuse the function to sort by Brand, just repeated the same Store function but sorted again
* 2ab. -2 pts: endInv_Store is not definied yet is used multiple times.
  * Both use double sorting when it should be grouping by brand or store instead of combining sorts twice.
        ```python
        endInv.sort_values(by='InvCost12_31_2016').tail(10).sort_values(by='InvCost12_31_2016', ascending = True)
        ```
* 4. No filtering for year (default is receivingdate which is 2016)
* 4c. Used Invoice data, logic looks right, but missing equality symbol in using '>' vs '>='
* 4d. -2 pts: Merges purchases with invoices then filters out freight and quantity
  * Dock point for merging with purchases
  * Takes too much effort to correct code
* 4e. Good enough

## Sarah Aufranc **35**
* Unsure why sorting isn't working unless it's appended to end of .sum().sort... 
* 4a. Used invoicepurchase data
* 4b. Used purchase data
* Full points

## Emily Beaton **34.5**
* 4d. -0.5 pts: Logic error, used OR instead of AND:
  ```python
  Invoices_100 = Invoices4d[Invoices4d["Freight"]>100 | (Invoices4d["Quantity"]<=1000)]
  ```
  * Overall unsure why this is broken/numbers wrong
  * 5. Formula is missing salesquantity, this is profit per unit, but ill pass it

## Jack Bennison **34**
* 4c used > over >=
* 4d. -1 pt: Filtered for freight and quantity, but didn't aggregate and groupby 

## Macy Boell **22**
* 4a. -0.5 pt: Wrong order, max num was 31k:
```python
purchases_vendors = purchases_vendors[['VendorNumber','VendorName','Dollars']].groupby('Dollars').sum()
-->purchases_vendors = purchases_vendors.groupby(['VendorNumber','VendorName'])[['Dollars']].sum()
```
* 4b. -0.5 pt: Wrong order, same as 4a issue
* 4c. -3 pts: No answer
* 4d. -3 pts: N/A
* 4e. -3 pts: N/A
* 5. -3 pts: N/A

## Eric Bonomo **34.5**
* 2a. -0.5 pts: Copy and pasted code for 1b, but forgot to change the variables to output the sorted 2a.
  ```python
  begInv_Store.sort_values(by='InvCost01_01_2016',ascending=False).head(10)
  -->endInv_Store.sort_values(by='InvCost12_31_2016',ascending=False).head(10)
  ```
* 5. Unable to run, requires 34 GiB to allocate, code seems fine, missing an explanantion tho

## Cameron Branch **34**
* 4d. -1 pt: Missing groupby and aggregation, only filtered and sorted the data.
```python
sort_sample[['VendorNumber', 'VendorName','Quantity','Freight']].sort_values(by='Freight',ascending=False).head()
-->sort_sample.groupby(["VendorNumber", "VendorName", ])[['Quantity','Freight']].sum().sort_values(by='Freight',ascending=False).head()
```

## Jayden Brewer **27.5**
* 4c. -2 pts: Missing per $ freight, no calculation, only filtered for 250k, only showed filtered head
* 4d. -0.5 pt: Misunderstanding dollars as freight cost, also missing sorting for highest
* 4e. -2 pt: This is just dividing 4d in dollars/quantity twice, the same variables used again below?
* 5. -3 pts: Missing, no Friday note

## Riley Buckley **35**
* Identical to answer key aside from not filtering for 2016
* Told to skip #5
  
## WIlliam Cannon **34**
* 4c. -1 pt: Faulty logic, also need to aggregate before calculating ratios
```python
top_purchases = purchases_4c[['VendorNumber','VendorName','Freightper$%','FreightperUnit']].groupby('VendorNumber').sum()
```

## Faith Carroll **35**
* 4e. Similar to key, but broken apart

## Jialin Chen **35**

## Keith Chen **34**
* 4d. -0.5 pts: Unknown to the issue. DF not correct, but misunderstanding that dollars is freight.
* 4e. -0.5 pts: No explanation, idk what I'm looking at because all unsure if this code pertains to #4d, nothing from #4c
* 5. (ignored) Unsure what is the analysis, created a cost formula from freight then subtracted it from dfs without merging.

## Kennedy Cole **34.5**
* 4e. -0.5 pts: Logic error in using 4c to subtract from 4d.
```python
VendorsD['FreightPerDollarPercent'] = (VendorsD['Freight'] / Vendor_over_250['Dollars']) * 100
--> VendorsD['FreightPerDollarPercent'] = (VendorsD['Freight'] / VendorsD['Dollars']) * 100
```

## David Combs
* 4c. He said he couldnt get groupby working

## Aaron Cote
* 3. Broken code
  ```python
  Inventory = merge3[["InventoryId", "01_01_2016_Qty_x", "InvCost01_01_2016_x", "01_01_2016_Qty_y", "InvCost01_01_2016_y"]]
  --> Inventory = merge3[["InventoryId", "01_01_2016_Qty", "InvCost01_01_2016"]]
  ```
* 4c. Unfinished code, uses field name as a variable
  ```python
  Freight_per_dollar = VendorInfo['Freight'] / VendorInfo['Dollars']
  sorted_vendors = VendorInfo.sort_values(by='Freight_per_dollar', ascending=False)
  --> VendorInfo['Freight_per_dollar'] = VendorInfo['Freight'] / VendorInfo['Dollars']
  ```
* 4d. Has some unnecessary code, but overall missing groupby vendorname and num, also sorting it for freight.
* 4e. Added fields for per dollar and unit, but no response recorded.

## Lauren Crane
* 4c. Made the field, but didn't it in the sort after copying previous code.
  * Forgot to change Purchase[] to Purchases_250000
* 4d. Missing groupby, missing sort, did filter for quan and freight.
* 4e. After running .mean() on 4d and 4c, analysis is not proven to be true.

## Andrew Czernik
* 4c. Used purchases, then merged purchases with vendors (shouldve just used vendors/invoices)
* 4d. Merged invoices and purchases again
* Will likely just dock for improper merging, logic is there, some tables are iffy

## Nathan Dahlman
* 2ab: Used endinv * beginv causing variance
* 4e. Sus, similar to answerkey
* 5. Faulty logic, used dollars - purchaseprice, but that's subtracting a total value from a single item? 

## Austin Deardorff
* 4e. Weak analysis, but ok

## Dallas Dethlefs **35**

## Christopher diazdiaz
* 4e. Logic error in code due to not multiplying by 100 in 4e, but did in 4c.
* 5. copy of key without explanation of the code

## Tyler Du **35**
* 5. Also didn't multiplty by SalesQuantity for profit, but close enough

## Garrett Edward
* After running .mean() on 4d and 4c, analysis is not proven to be true. D is more expensive than C
* 5. Unanswered

## Tyler Ellertson
* 4d. Said 4d was wrong
  * Found error to be in missing groupby
* 4e. Faulty response "The cost of freight per unit is a lot higher than the cost of freight per dollar spent. "
  * Also missing clauclation of per dollar for 4d/4e so not possible to make statement

## Ethan Fergerson
* 4a. Didn't sum for dollars here, but did in 4b.
* 4d. Missing sort for highest freight vendor
* 4e. Missing response explaining the comparison/analysis, just a dataframe

## Morgan Gerhart
* 4c. Filtered, but didn't use the variable they just made to show the above250 orders 
* 4e. Technically right due to flow-through error. Pass

## Anna Gallego
* 4c. Unsure why the Rates are so low, code logic appears correct, dataset issues?
  * The chaining of variables is likely the issue, too long to debug
* 4e. Taking mean of vendourpurchases1 and 2, this is untrue, on average, 4c is alot less than 4e

## Morgan Gerhart **35**
* 4e. Similar to answer key
* 5. Noted skipped by Pesch Day

## Parker Goodloe
* 1b. Missing groupby for Brand, there is only 1a
* 4b. Used Dollars over Freight in calculation, swapping with freight fixes DF
* 4e. Iffy response, says per dollar and per unit have no relationship. pass?
* 5. Cannot run due to the merging sales with purchases requires 43 GiB. 
  * Parker noted computer crashes when run

## Grace Gordon
* 4c. Used > over >=
* 4d. Missing aggregation of fields, only filtered for frieght and quantity and sorted, no groupby or sum.
* 4e. Based on current work, analysis holds true.

## Jennifer Hafley
* 4c. Values slightly off, unable to confirm

## Matthew Hainley
* 1b. Missing sort by highest cost and displayed 2
* 2b. Missing sort by highest cost and displayed 2

## Emma Hall
* 4c. Missing Quantity field when initially filtering from invoice table into freight causing variance
* 4e. Claims all are experiencing similar fright costs which is untrue
* 5. Odd analysis to use beginning inventory and merge with year end sales then divide sales by cost, no reponse explaining purpose

## Suzanne Harrell
* 2a. Missing formula to generate InvCost01_01_2016 field
  * head has .head(206530) error
  * Had to add rename for onHand and calcualte invCost
* 4c. Missing filtering for >=250000
* 4d. Filtered for quantity and freight, but did nothing else for the question
* 4e. Missing
* 5. Missing
  

## Victoria Hildebrandt
* 2b. Fixed errors: Missing sort, improper field placmeent
    ```python
    endInv_Brand = endinv[['Brand','01_01_2016_Qty','InvCost01_01_2016']].groupby('Brand').sum()
    endInv_Brand.head(10)
    -->endInv_Brand = endinv[['01_01_2016_Qty','InvCost01_01_2016']].groupby('Brand').sum().sort_values('InvCost01_01_2016',ascending=False)
    endInv_Brand.head(10)
    ```
* 3. Only tried merging and is broken, give 25% credit


## Victoria Hildebrandt
* 4c. Syntax error, missing brackets on:
    ```python
    dfLargeVendors = df2016Invoices.groupby(['VendorNumber', 'VendorName'])(['Freight', 'Dollars', 'Quantity']).sum()
    -->dfLargeVendors = df2016Invoices.groupby(['VendorNumber', 'VendorName'])[['Freight', 'Dollars', 'Quantity']].sum()
* 4d. Unanswered. Said unable to open file (incorrect filename and likely not in the same local folder)
* 4e. Unanswered due to 4d.
* 5. This is literally 1b but sorted ascending now...

## Peyton Hogan
* 4c. Sorted by wrong order, used ascending over descending order
* 4d. Missing aggregation of data, no groupby or sum
* 4e. copy of answer key
* 5. Blank

## Devan Hunsaker
* 1b. Missing groupby brand, no dataframe or code to support
* 2b. Missing groupby brand, no dataframe or code to support
* 3. None of these have 250k records
* 4a. Missing aggregation that wasn't done to 'merge2' also not the right variable to use, should be PurchaseInvoice data
* 4b. Missing aggregation in groupby and sum, also supposed to sort by Freight
* 4c. Minor variance, reason unknown
* 4d. Missing aggregation in groupby and sum
* 4e. Explanation not provided. Unknown if truly similar, no per unit or per dollar actually calculated in the two tables
* 5. Sorted sales by sales ascending for analysis.
    ```python
    merge4.sort_values(by='Sales',ascending=False).head(10)
    ```

## Ryle Hurley
* 3. Merged on inner not outer, rows = 175k =/= 256k
* 5. Similar logic to key, but merges on InventoryID and no explanation or sorting, just calculates CM for everything

## Gayatri Jog
* 4d. Unable to confirm issue, but this is just outputting 4b. One confirmed issue Logic Error: Used OR instead of AND. 
* 5. Iffy cause SalesPrice - PurchasePrice is per item profit, not total profit since SalesQuantity is also in here
  * No explanation

## Ciera Johnson **35**
  
## Carly Kaster
* 1-2. Rename functions out of order, need to be placed prior to called renamed field names.
* 3. Missing merge, turned in with error since beginning inventory fields were unmerged and nonexistent to filter
  * Give 75%?
* 4abced. only filtered purchases, but also error in using "pd.to_datetime()" (correct) vs "pd.to.datetime()" (wrong)
* 5. Blank

## Liam Kiger
* 4d. Wrong syntax, extra bracket causing errors:
    ```python
    largevendorsA = purchases[purchases[('PurchasePrice')]>100][['Quantity']<=1000]]
    -->largevendorsA = purchases[(purchases[('PurchasePrice')]>100) & (purchases['Quantity']<=1000)]
    ```
* 4e. Missing, noted "wasn't able to completely get a match because I wasn't able to pull in the freight data"
* 5. Tried to merge sales with purchases, wrote an explanantion of end goal since it couldn't run
  * "My computer was having trouble recognizing predefined DF's and I ran out of time to completely fix this. I wanted to create an analysis where I could compare sales dollars coming in vs purchase price for vendors. I wanted a single table that would have very important information clearly depicted for quick access."

## Riley Kruel
* 4d. Unable to confirm issue, but Edrington Americas is not properly summed

## Xinrui Liu
* 4d. Logic error, used OR instead of AND
* 4e. Running mean function, analysis is questionable, both 4d and 4c shouldn't have such similar per dollar values
* 5. Tried to merge Sales and Purchases (can't due to file size)
  * Put aribitrary code under the unrunnable code. 

## Jacob Luty
* 4c. Logic error: Used Dollars/Freight instead of Freight/Dollars
  * Additional error in not summing fields before dividing (reordered code)
* 4e. No explanation, only created fields for 4d in DF
* 5. Wrote two lines. Missing use of Sales data. Takes beg and end inventory to get total change in inventory. This doesn't use any Sales data.

## Alexandra Magana
* 4e. Error in logic, didn't use data from 4d, instead used entire invoice dataset.

## Stephen McKay
* 3. Several errors. Does not run. 
  * Due to logic, missing df = pd.DataFrame(begInv) since this is pulling the previous code (endInv)
  * 'df' is constantly redefined, there doesn't exist a TotalValue in begInv or endInv
* 4b. Missing
* 4c. ? Calculates individual fields then merges them, but none of the result is correct?
* 5. Only used Sales data

## Tyler Miller
* 1b. Missing sort
* 2b. Missing sort
* 4c. Unable to confirm number variance.
  * Reordering and revising aggregation code fixes most of the issues, but the vendors aren't right
* 4d. Missing sort
* 4e. Finale 4d table is here, but not sorted and missing explanation
* 5. Used only sales data

## Zachary Mirek **35**
* 4e. no explanantion
* 5. Tried merging sales with purchases, was in friday help session

## Luna Moreno
* 4c. Missing per dollar formula (no code for it)
* 4d. Missing aggregation (output is missing edrington americas as high)
* 4e. Iffy analysis, sampled the first 5 numbers then averaged it.
* 5. Given full point
  * Multplies purchase price by quantity and same for sales price, then grabs the first one in the dataframe? All individually, none of it is related or merged.

## Carter Nelson
* 4a. Missing sum function, only sorted
* 4b. Missing sum function, only sorted
* 4c. Missing aggregation on groupby and sum, causing variance
* 4d. Does Freight * Quantity, not what is asked, then sorts in ascending order
* 4e. Only did per unit then sorted by Freight in ascending order
* 5. Only used purchases (where is sales?)

## Crystal Nguyen **35**
* Went to Friday help

## Austin Osborne **35**

## Parker Darren
* 3. Wrong merge type, used 'inner'
* 4c. Need to aggregate before Frieght/Dollars
* 4d. Edrington America not top, also used '<' instead of '<='
* 5. Only used Sales

## Abigail Parkin **35**

## Matthew Patchin
* 3. Left code missing closing brackets, also merged inner instead of outer.
* 4a. Error in understanding, used quantity*purchaseprice instead of dollars field, also didn't sort
* 4b. Missing sort
* 4c-5. Missing

## Garrett Plank
* 3. Merged on inner instead of outer
* 5. Only used sales to calculate the tax per unit

## Emily Plant **35**

## Javier Ruiz **35**

## Alejandro Sanchez Cuesta
* 1b. Missing
* 4e. Error, missing fields 'Freight/Dollar','Freight/Unit' since it pulls from purchases and formulas weren't made for the fields
  * Initial DF analysis is fine
* 5. Missing 

## Payge Sanderson **35**
* 4e. Only did analysis based on head values.

## Rhys Schluter
* 4c. Need to aggregate before getting ratio freight/dollar or else it's summing averages
  * Would've fixed the variance
* 4d. Work is all there, but wrong variables being used (rename 1 variable and delete one line fixes it)
```python
top_vendor_freight_cost = invoice_purchases[['VendorName','Freight',]].groupby('VendorName').sum()
--->top_vendor_freight_cost = above_100[['VendorName','Freight',]].groupby('VendorName').sum()
```
* 4e. Missing explanation and analysis of per dollar and per unit
  * This is a repeat of 4d with some groupby
* Only used Sales data.

## Rene Segura Ramos
* 4c. Reorder aggregation before freight/dollars 
* 4d. Missing aggregation for freight


## Dylan Shafer
* 5. Missing explanation of what's this analysis
  * Sums all the grouped SalesDollars which is iffy cause that's adding up one sale price per grouped row
  * Divides individual item price by the total purchase price from invoice?
  * Unsure what is the intent here
  
## Michael Siddel **35**

## James Smith
* 4c. Did aggregate before getting ratio, but didn't use the aggregrated variable nor the filtered dataset variable
  * Code's all there, but the variables aren't connected
* 4d. Missing aggregation for freight
* Only used sales data and just summed SalesDollars

## Dylan Spisla **35**

## Krista Suarez **35**

## Hannah Tallan
* 4d. Missing aggregation for freight

## Faith Thompson **35**

## Caleb Tremper
* 3. Didn't filter for the five columns
* 4a. Error: Missing purchases csv data variable (I added it in)
  ```python
  purchases = pd.read_csv("PurchasesFINAL12-31-16Sample.csv")
  ```
* 4b. Error: Missing invoices csv data variable and conversion to datetime (I added it in)
  ```python
  -->invoices = pd.read_csv("InvoicePurchases12-31-16Sample.csv")
  -->invoices['InvoiceDate'] = pd.to_datetime(invoices['InvoiceDate'])
  ```
* 4c. Missing filtering for 250k, missing per dollar calculation
* 4d. Used dollars instead of freight
* 4e. Error: per dollar field doesn't exist in this DF to filter
  * Missing explanantion
* 5. Only used sales data.

## Kenta Truong
* Uploaded wrong file type, had to add .ipynb
* 3. Wrong merge, used left instead of outer
* 4d. Missing explanantion
* 5. Only used sales data.

## Ryan Tsai **35**
* 4e. Noted that friday session so questions are excused because there's an error making 4e unrunnable
  * df2016invoices doesnt have a FreightRate% field to call

## Brendon Turnbaugh
* 4d. Missing aggregation of freight
* 5. Only used sales data.

## Peyton Vanhouten
* 5. Only used sales data.
  * Very similar to answers, maybe went to Friday session, but wasn't stated anywhere.

## Jordan Vogt
* 4e. Missing explanantion.
* 5. Only used sales data. 
  * Maybe went to Friday, similar to answer key content overall

## Riley Wall
* 5. Error, unsure what was in his invoices, but the merge can't work with those variables
  * Merging on nonexistent fields
  * Even if merge worked, based on the column outputs, there would be a suffix since everything is the same, but the suffix doesn't appear in use of 'SalesDate'?
  * It appears from his output before running, it's merging the same fields against themselves, so it must be two sales datas being merged?
  
## Alex Ward **35**
* 5. Attempted to merge december sales with all sales data. Requires 356GiB (happened at the end but commented not necessary)
  * However analysis is fine, individually compared two sorted datasets

## Kamila White
* 4a. Used Quantity instead of Dollars
* 4e. Iffy on the analysis. DF is correct, but the analysis is questionable.
  * "The per dollar prices are similar but the vendors are different. It makes sense, as the vendors in C might be purchasing more than $100 or 1,000 per transaction. "
  * If a .mean() was pulled it'd reveal they're not similar and the vendors in C can't purchase more than their limits since they've been filtered out


## Brett Wiebe **35**
* 4e. Final table anaylsis of vendors doesn't run (FreightRate is not defined in the field being called)
* 5. Went to Friday session

## Eedasso Wotcha
* 4d. Missing parenthsis on function call .sum()
  * Fixed shows correct output
* 4e. Missing
* 5. Missing

## Ross Yankowitz
* 4a. Missing aggregation, no groupby or summing found
* 4d. Missing aggregation for freight
* 4e. Missing explanation
* 5. Analysis is there, but could benefit from sorting to be more accurate. I'll take it.







2017PurchasePricesDec.csv
BegInvFINAL12312016.csv
EndInvFINAL12312016.csv
InvoicePurchases12312016.csv
PurchasesFINAL12312016.csv
SalesFINAL12312016.csv

Sampled
BegInvFINAL12-31-16Sample.csv
EndInvFINAL12-31-16Sample.csv
InvoicePurchases12-31-16Sample.csv
PurchasesFINAL12-31-16Sample.csv
SalesFINAL12-31-16Sample.csv

2017PurchasePricesDecSample.csv


