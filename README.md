#  Market Analysis Report for National Clothing Chain

## Introduction

An online national clothing chain is facing flat sales and aims to re-engage lost customers through a targeted marketing campaign. The goal is to identify the best product (Shirt: $25, Sweater: $100, Leather Bag: $1,000) to advertise to specific customers in specific locations. This project involves analyzing various data sources to understand customer income, product performance, and potential correlations to drive effective targeting.

## Project Instructions

This project requires analyzing several datasets to provide actionable insights for the marketing campaign. You will leverage population statistics from the US Census Bureau to understand income distribution across the country and explore the correlation between sales and income. By comparing customer purchase history and locations with census data, you will develop a method to predict customer income. Furthermore, an analysis of product inventory, focusing on customer ratings and return rates, will determine any existing correlations.

## Analysis Questions:

This project aims to answer the following key business questions:

1.  **What is the correlation (R² value) between sales and income?**
2.  **What is the correlation (R² value) between customer ratings and product return rate?**
3.  **What are the linear regression formulas to predict customer income from customer sales?**
4.  **Which customer do you predict has the highest income?** (Based on the analysis)
5.  **Which product will be advertised the most?** (Based on the analysis and recommendations)

## Data Sourcing

The project utilizes a variety of data sources:

* **US Census Bureau:**
    * Average income
    * Location
    * Population
    * Industry
* **Business Data:**
    * Product inventory
    * Product prices
    * Customer rating
    * Product return rate
* **Customer Data:**
    * Customer ID
    * Names
    * Location
    * Date of birth
    * Purchase history
### Power Query M Code: Transform Product Inventory

This M code in Power Query transforms the "Product Inventory" sheet from `customer-list.xlsx`.

**Steps:**

1.  **Connect to Excel:** Reads the specified Excel file.
2.  **Navigate to Sheet:** Select the "Product Inventory" sheet data.
3.  **Remove Header Row:** Filters out the initial header row.
4.  **Split Column:** Splits the first column into multiple columns by space.
5.  **Set Data Types:** Assign appropriate data types to the split columns.
6.  **Merge Product Name:** Combines split parts of the product name.
7.  **Rename Columns:** Gives meaningful names to the columns.

**Output:**

A clean table with columns: "Product ID", "Product Name", "Current Price", "Number in Stock", "Customer Rating (stars)", and "Return Rate".
### Power Query M Code: Transform Customer Purchase History

This M code in Power Query restructures customer purchase data from `purchase-list.xlsx` to create a clear list of individual purchases.

**Steps:**

1.  **Connect to Excel:** Opens the specified Excel file.
2.  **Navigate to Sheet:** Selects the data from "Sheet1".
3.  **Use Dates as Headers:** Promotes the first row (containing dates) to be the column headers.
4.  **Transform Layout (Unpivot):** Converts the table from a wide format (each date as a column) to a long format (each purchase on its own row). The dates become a single "Date" column, and the purchase amounts become a single "Value" column.
5.  **Filter Out Zero Purchases:** Removes rows where the purchase value is zero.
6.  **Rename Columns:** Renames the "Attribute" column (containing the dates) to "Purchase Date" and the "Value" column to "Purchase Value".
7.  **Set Data Types:** Ensures "Customer ID" is text, "Purchase Date" is text initially for splitting, and "Purchase Value" is a number.
8.  **Clean Up Purchase Date:** Splits and merges the "Purchase Date" column to convert it into a proper date format.

**Output:**

A clean table with columns: "Customer ID", "Purchase Date" (in date format), and "Purchase Value", representing each individual customer purchase. This format is suitable for analyzing purchase trends over time.
