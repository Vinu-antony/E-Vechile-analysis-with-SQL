# 🚗 E-Vehicle Data Analysis Using SQL

## 📌 Project Overview  
This project involves analyzing an **E-Vehicle dataset** using **SQL** to gain insights into electric vehicle trends, manufacturers, and performance metrics.

## 📂 Dataset Information  
- **Source**: CSV file containing E-Vehicle data  
- **Columns**:
  - `VIN` (Vehicle Identification Number)  
  - `Country`, `City`, `State`, `Postal Code`  
  - `Model Year`, `Make`, `Model`  
  - `Electric Vehicle Type`, `Electric Range`, `Base MSRP`  
  - `Legislative Code`, `DOL Vehicle ID`, `Electric Utility`, `Census Tract`  

## 🛠️ Tech Stack  
- **SQL (MySQL Workbench)**  
- **Git & GitHub for Version Control**  

## 📑 Steps to Implement  
### 1️⃣ Create a Database & Table  
```sql
CREATE DATABASE EvechileDB;
USE EvechileDB;

CREATE TABLE evechiles (
    VIN VARCHAR(20) PRIMARY KEY,
    COUNTRY VARCHAR(100),
    CITY VARCHAR(100),
    STATE VARCHAR(10),
    POSTAL_CODE INT,
    MODEL_YEAR INT,
    MAKE VARCHAR(50),
    MODEL VARCHAR(100),
    ELECTRIC_VEHICLE_TYPE VARCHAR(50),
    CLEAN_ALTERNATIVE_FUEL VARCHAR(50),
    ELECTRIC_RANGE INT,
    BASE_MSRP DECIMAL(10,2),
    Legislative INT,
    DOL_VEHICLE DECIMAL(10,2),
    VEHICLE_LOCATION VARCHAR(255),
    ELECTRIC_UTILITY VARCHAR(255),
    CENSUS_TRACT DECIMAL(15,2)
);
```

### 2️⃣ Import Data from CSV  
```sql
LOAD DATA LOCAL INFILE 'C:/Users/Vinusha/Desktop/vincent/E-vechicle data.csv' 
INTO TABLE evechiles 
FIELDS TERMINATED BY ',' 
ENCLOSED BY '"' 
LINES TERMINATED BY '\n' 
IGNORE 1 ROWS;
```

### 3️⃣ Verify Data Import  
```sql
SELECT * FROM evechiles;
```

### 4️⃣ Data Cleaning & Preparation  
- Check for missing values.
- Validate column structure and data types.

### 5️⃣ Perform SQL Analysis  
#### **Total Number of EVs in the Dataset**  
```sql
SELECT COUNT(*) AS Total_Vehicles FROM evechiles;
```

#### **Top 5 Most Common EV Models**  
```sql
SELECT Model, COUNT(*) AS Model_Count 
FROM evechiles 
GROUP BY Model 
ORDER BY Model_Count DESC 
LIMIT 5;
```

#### **Count Vehicles by Manufacturer**  
```sql
SELECT MAKE, COUNT(*) AS Total_Vehicles 
FROM evechiles 
GROUP BY MAKE 
ORDER BY Total_Vehicles DESC;
```

#### **Average Electric Range by Brand**  
```sql
SELECT MAKE, AVG(ELECTRIC_RANGE) AS Avg_Range 
FROM evechiles 
GROUP BY MAKE 
ORDER BY Avg_Range DESC;
```

#### **Find the Top Cities with the Most Electric Vehicles**  
```sql
SELECT CITY, COUNT(*) AS Total_Vehicles 
FROM evechiles 
GROUP BY CITY 
ORDER BY Total_Vehicles DESC 
LIMIT 10;
```

#### **Most Common EV Brands in a Specific County (e.g., King County)**  
```sql
SELECT MAKE, COUNT(*) AS Total_Vehicles 
FROM evechiles 
WHERE COUNTRY = 'KING' 
GROUP BY MAKE 
ORDER BY Total_Vehicles DESC;
```

#### **Optimize Query Execution with EXPLAIN**  
```sql
EXPLAIN SELECT * FROM evechiles WHERE MAKE = 'TESLA';
```

#### **EV Models with the Highest Electric Range**  
```sql
SELECT MAKE, MODEL, ELECTRIC_RANGE 
FROM evechiles 
ORDER BY ELECTRIC_RANGE DESC 
LIMIT 5;
```

## 🚀 How to Run the Project  
1. Clone this repository:  
```sh
git clone https://github.com/your-username/e-vehicle-sql.git
```

2. Open MySQL Workbench and execute the database creation script.

3. Import the dataset (CSV) into MySQL.

4. Run SQL queries to analyze the data!

## 📢 Future Enhancements  
- **Visualize data using Python (Pandas & Matplotlib)**  
- **Join with charging station data for location-based analysis**  
- **Predict EV adoption trends using ML models**  

## 🔗 Connect with Me  
📧 **Email**: vincentantony000@gmail.com 
🎓 **LinkedIn**: (https://www.linkedin.com/in/vincent-s-18a78316b/) 

