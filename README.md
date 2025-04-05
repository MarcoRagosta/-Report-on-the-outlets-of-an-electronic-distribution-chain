# TechMarket S.p.A. - Sales Report

## Project Description

This project involves creating a Power BI report for TechMarket S.p.A., a retail chain of electronic products. The report was designed to analyze product sales in stores across Italy during 2014.

### Objectives:

- Visualize sales for each month, considering discounts, units, and prices.
- Visualize the units sold for each city.
- Display all information related to each product.
- Display information for each store, combining sales data and store information.
- Create navigation between different pages using buttons.
- Implement a bookmark to save an important view.

**Bonus Point**: Create a page that calculates sales excluding returns for the months of January and February.

---

## Data Structure

The data used in the project is contained in several CSV files:

1. **Folder "DATI"**: Contains sales data for various stores.
   - The files are separated by month (e.g., `January.csv`, `February.csv`, etc.).
   - Each file contains information on Products, Quantity Sold, Price, Discount, and Sale Date.

2. **Folder "DATI NEGOZI"**: Contains data related to stores, products, and Italian provinces.
   - Includes information on stores (ID, name, city, province).
   - Includes information on products (Product ID, product description, unit price).

3. **"RESI" file (bonus point)**: Contains data on returns made for products in January and February.
   - Includes product ID, store ID, returned quantity, and return date.

---

## Data Cleaning and Transformation Steps

### 1. Data Loading:

- The data was loaded into Power BI using the **File** > **Load Data** menu.
- The CSV files were imported into their respective tables: `Sales`, `Stores`, `Products`, `Provinces`, `Returns`.


### 2. Data Cleaning:

- **Handling null values**:  
  Some files had rows with null values (e.g., in the Discount or Quantity columns). These were handled by removing incomplete rows or replacing null values with `0`.

  ```m
  #"Removed Null Values" = Table.SelectRows(#"Previous Step", each ([Sconto] <> null and [Quantita] <> null))

- **Date formatting**:
  The dates in the sales files were correctly formatted to be used in time-based visualizations (e.g., month and year).

  ```m
  #"Changed Type" = Table.TransformColumnTypes(#"Previous Step",{{"Data", type date}})

- **Removing duplicates**:
  Duplicates were removed where there was duplication in the sales rows.

  ```m
  #"Removed Duplicates" = Table.Distinct(#"Previous Step")


### 3. Data Transformation:

- **Merging tables**:  
  Using the Merge function in Power Query, the Sales and Products tables were joined by the Product_ID field to include the product description and unit price in the sales data.
  
  ```m
  #"Merged Queries" = Table.NestedJoin(#"Vendite", "Prodotto_ID", #"Prodotti", "Prodotto_ID", "Prodotti", JoinKind.Inner)

- **Merging with the stores file**:
  The Stores file was also merged with the Sales table by store ID, including all store information (name, city, province).
  
  ```m
  #"Merged with Negozi" = Table.NestedJoin(#"Vendite", "Negozi_ID", #"Negozi", "Negozi_ID", "Negozi", JoinKind.Inner)

- **Creating calculated columns**:
  A calculated column was created to calculate Total Sales as the product of Quantity and Price (taking discounts into account).

  ```m
  #"Aggiunto Totale Vendite" = Table.AddColumn(#"Previous Step", "TotaleVendite", each [Prezzo] * [Quantita] * (1 - [Sconto]), type number)

- **Creating relationships**:
  Relationships between tables were created using the product IDs, store IDs, and sales IDs. The key relationships are:
  
  - Sales[Product_ID] → Products[Product_ID]

  - Sales[Store_ID] → Stores[Store_ID]

  - Stores[Province_ID] → Provinces[Province_ID]
    

### 4. Report Creation:

- **Page 1 (Sales by month)**:  
  A time-based visualization was created to show total sales per month. Discounts and the number of units sold are also considered.

- **Page 2 (Units Sold by city)**:
 A map-based visualization was created to show units sold by city, based on the relationship with provinces.

- **Page 3 (Product Information)**:
  A table was created to display all information about products, including description, unit price, and units sold.

- **Page 4 (Store Information and Sales)**:
  A unified table shows store information along with sales, including discounts, quantity, and total sales per store.


### 5. Bonus Functionality:

- A page was created that displays sales excluding returns for the months of January and February, using the Returns file to subtract returns from total sales.

  #"Sales Without Returns" = Table.AddColumn(#"Sales", "SalesWithoutReturns", each [TotalSales] - [Returns], type number)
  

### 6. Interactivity and Navigation:

- Bookmarks were created to allow the user to save and navigate between the most relevant visualizations.
- Navigation buttons were configured to allow users to move between the different pages of the report.
  
---

## Instructions for Using the Report

- **Page 1 (Sales by month)**: Displays total sales by month, considering discounts and units sold.

- **Page 2 (Units Sold by city)**: Shows units sold by each city.

- **Page 3 (Product Information)**: Details for each product, including description, price, and units sold.

- **Page 4 (Store Information and Sales)**: Shows information for each store, combining sales data and store information.


  
