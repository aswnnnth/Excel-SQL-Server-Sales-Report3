# 📊 Excel Sales Report with SQL Server & Power Query

This project demonstrates how to connect **Microsoft Excel** with **Microsoft SQL Server**, import and transform data using **Power Query**, build an interactive **Pivot Table Report**, and refresh the report automatically when the source data changes.

---

# 🛠 Tools Used

* Microsoft Excel
* Microsoft SQL Server (SSMS)
* Power Query
* Pivot Tables
* Slicers

---

# 📂 Dataset

The dataset contains the following columns:

| Column          |
| --------------- |
| TransactionID   |
| CustomerName    |
| TextileType     |
| Category        |
| Region          |
| SalespersonName |
| OrderDate       |
| Quantity        |
| PricePerUnit    |
| TotalAmount     |
| PaymentMethod   |

---

# 🚀 Project Workflow

## Step 1: Load Data into Microsoft SQL Server

First, a new database was created in SQL Server.

```sql
CREATE DATABASE TextileDB;

USE TextileDB;
```

The dataset was imported into SQL Server using the **SQL Server Import and Export Wizard**.

**Import Process**

* Open SQL Server Management Studio (SSMS).
* Create a new database.
* Right-click the database → **Tasks → Import Data**.
* Select **Flat File Source** and choose the CSV file.
* Select the SQL Server database as the destination.
* Verify the column mappings.
* Complete the import.

After importing, the data was verified using:

```sql
SELECT * FROM [dbo].[Textile+Dataset];
```

---

## Step 2: Import SQL Server Data into Excel

The SQL Server table was connected to Excel using **Power Query**.

**Steps**

* Open Excel.
* Go to **Data → Get Data → From Database → From SQL Server Database**.
* Enter the Server Name and Database Name.
* In **Advanced Options**, enter the SQL query:

```sql
SELECT * FROM [dbo].[Textile+Dataset];
```

* Click **Transform Data** to open **Power Query**.
* Reviewed the dataset and verified data quality before loading it into Excel.

---

## Step 3: Create the Pivot Table Report

After loading the data from Power Query:

* Close & Load To → PivotTable

Configured the Pivot Table as follows:

**Values**

* TotalAmount

**Rows**

* OrderDate

**Columns**

* PaymentMethod

Added interactive slicers for:

* Category
* Customer Name
* Month
* Region
* Textile Type

(Textile Types include Cotton Fabric, Silk Fabric, Woolen Fabric, and Denim.)

The slicers and Pivot Table were formatted to create an interactive sales report.

---

## Step 4: Refresh Data from SQL Server

To demonstrate dynamic data refresh, I deleted all records where the **TextileType** was **Denim** directly in SQL Server.

```sql
DELETE FROM [dbo].[Textile+Dataset]
WHERE TextileType = 'Denim';
```

### Before Refresh

Before refreshing the Excel report, the Power Query connection contained **2,000 records**.

**Screenshot:**

<img width="1600" height="713" alt="Image" src="https://github.com/user-attachments/assets/6631d6cd-ab4a-4944-94a1-536f3d6f64cb" />

---

### Refresh the Report

In Excel:

**Data → Refresh All**

Excel refreshed the Power Query connection and updated the Pivot Table automatically.

---

### After Refresh

After refreshing, the deleted **Denim** records were removed from the report, and the total number of records decreased from **2,000** to **1,636**.

**Screenshot:**

<img width="1917" height="977" alt="Image" src="https://github.com/user-attachments/assets/d4845d92-55ab-4d84-9023-8224c525c961" />

This demonstrates how Excel stays synchronized with the SQL Server database, ensuring reports always reflect the latest data without manually re-importing the dataset.


---

# 🎯 Skills Demonstrated

* SQL Server Database Management
* SQL Import & Export Wizard
* SQL Queries
* Excel Power Query
* Data Transformation
* Database Connectivity
* Pivot Tables
* Interactive Slicers
* Data Refresh from SQL Server
* Business Reporting


