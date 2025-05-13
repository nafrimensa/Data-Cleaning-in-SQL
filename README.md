# 🧹 **Data Cleaning Process – Nashville Housing Dataset**

This project involved cleaning a real-world housing dataset using SQL. Below is a breakdown of the cleaning and transformation steps I performed to prepare the data for analysis.

---

## 🔍 1. Initial Data Exploration

I began by inspecting the raw dataset to understand its structure, identify inconsistencies, missing values, and determine which columns needed cleaning or transformation.

---

## 📅 2. Standardizing the Date Format

The `SaleDate` column originally included both date and time information. To simplify analysis, I converted this column to contain only the date in a standard format (YYYY-MM-DD). Since direct modification wasn't ideal due to data type constraints, I created a new column to store the cleaned date values, ensuring data integrity while maintaining clarity.

---

## 🏠 3. Populating Missing Property Addresses

Some records had missing property addresses. To resolve this, I used a self-join on the `ParcelID`, a unique identifier for properties. This allowed me to find other entries with the same `ParcelID` that had valid address information. I then updated the missing values by borrowing the correct address from the matching entries.

---

## 🧩 4. Splitting Property Address into Separate Columns

The `PropertyAddress` field contained both the street address and city in a single string. For better usability, I split this field into two new columns:

* **Street Address**
* **City**

This made the data more structured and easier to query or analyze by geographic location.

---

## 🧩 5. Splitting Owner Address into Separate Components

Similar to property addresses, the `OwnerAddress` field included the full address in one line (street, city, and state). I separated this into three distinct columns:

* **Owner Street Address**
* **Owner City**
* **Owner State**

This separation was achieved by using a delimiter to extract each component, improving the granularity and readability of the data.

---

## ✅ 6. Standardizing "Sold As Vacant" Field

The `SoldAsVacant` column had inconsistent values such as `'Y'`, `'N'`, `'Yes'`, and `'No'`. I standardized these to `'Yes'` and `'No'` across the entire dataset, ensuring consistency for accurate filtering and analysis.

---

## 🧹 7. Removing Duplicate Records

To eliminate duplicate entries, I used a technique that identifies rows with the same key property information (such as `ParcelID`, `SalePrice`, `SaleDate`, etc.). I assigned row numbers to these duplicates and filtered out all but the first occurrence, resulting in a clean, duplicate-free dataset.

---

## 🧯 8. Dropping Unnecessary Columns

After completing the transformations, several columns became redundant or obsolete, such as the original address fields or the unconverted date column. I dropped these columns to streamline the dataset and improve performance during analysis.

---

## ✅ Final Outcome

At the end of the cleaning process, the dataset was:

* **Standardized:** Consistent formats across date and text fields
* **Complete:** Missing values were intelligently populated
* **Structured:** Address data was parsed into discrete components
* **Clean:** Free from duplicates and inconsistencies
* **Optimized:** Unused columns removed for efficiency

This transformation laid a solid foundation for future analysis, visualization, and reporting tasks.

---
🧰 Technologies Used

SQL (Structured Query Language)
Used to query, clean, and transform the Nashville Housing dataset using complex joins, conditional logic, string functions, and window functions.

Microsoft SQL Server
Relational database system used to host and manage the dataset. Queries were executed via SQL Server Management Studio (SSMS) or Azure Data Studio.

Relational Database Concepts
Leveraged best practices in schema design, normalization, and data integrity throughout the data cleaning process.

✅ Skills Demonstrated
Data cleaning and transformation using SQL

Parsing and standardizing address fields

Handling missing values with joins and conditional logic

Removing duplicates using ROW_NUMBER() and CTEs

Optimizing data by dropping unused or redundant columns

Working with real-world messy datasets to prepare for analysis
