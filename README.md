# 🚦 Road Accident Analysis: SQL & Power BI

![Road Accident Analysis Dashboard](![Dashboard Preview](https://github.com/bhavishgupta/ROAD-ACCIDENT-ANALYSIS/blob/main/roadaccidentsdashboard.png))

---

## 📋 Project Overview

This project demonstrates data-driven analysis of road accident data using SQL for querying and Power BI for interactive visualization.  
The goal is to uncover patterns, highlight risks, and provide actionable insights for road safety improvements.

---

## 🗂️ Dataset Structure

The analysis is performed on a dataset with the following columns:

- **Accident_Index**
- **Accident Date**
- **Day_of_Week**
- **Junction_Control**
- **Junction_Detail**
- **Accident_Severity**
- **Latitude**
- **Light_Conditions**
- **Local_Authority_(District)**
- **Carriageway_Hazards**
- **Longitude**
- **Number_of_Casualties**
- **Number_of_Vehicles**
- **Police_Force**
- **Road_Surface_Conditions**
- **Road_Type**
- **Speed_limit**
- **Time**
- **Urban_or_Rural_Area**
- **Weather_Conditions**
- **Vehicle_Type**

---

## 📊 Power BI Dashboard

The Power BI dashboard visualizes accident statistics and patterns:

- **Total Casualties & Accidents:** Key metrics and % change.
- **CY & PY Comparison:** Monthly trends.
- **Breakdowns:** By vehicle type, road type, light condition, urban/rural, and districts.
- **Geospatial Mapping:** Accident locations across UK.
- **Interactive Filtering:** By road surface and weather conditions.

**Sample Dashboard:**  
![Road Accident Analysis Dashboard](https://github.com/bhavishgupta/ROAD-ACCIDENT-ANALYSIS/blob/main/roadaccidentsdashboard.png)

---

## 🛠️ SQL Queries

Below are some advanced SQL queries used in the analysis, each with a problem statement:

### 1. **Severity Distribution by District**
```sql
SELECT Local_Authority_(District), Accident_Severity, COUNT(*) AS accident_count
FROM accidents
GROUP BY Local_Authority_(District), Accident_Severity
ORDER BY Local_Authority_(District), Accident_Severity;
```

### 2. **Top Districts by Casualties**
```sql
SELECT Local_Authority_(District), SUM(Number_of_Casualties) AS total_casualties
FROM accidents
GROUP BY Local_Authority_(District)
ORDER BY total_casualties DESC LIMIT 5;
```

### 3. **Daywise Accident Occurrences**
```sql
SELECT Day_of_Week, COUNT(*) AS accidents_per_day
FROM accidents
GROUP BY Day_of_Week
ORDER BY accidents_per_day DESC;
```

### 4. **Speed Limit vs Severity**
```sql
SELECT Speed_limit, AVG(CASE WHEN Accident_Severity = 'Fatal' THEN 1 ELSE 0 END) AS fatal_ratio, COUNT(*) AS total_accidents
FROM accidents
GROUP BY Speed_limit
ORDER BY fatal_ratio DESC;
```

### 5. **Top Junctions for Serious Accidents**
```sql
SELECT Junction_Detail, COUNT(*) AS serious_accidents
FROM accidents
WHERE Accident_Severity = 'Serious'
GROUP BY Junction_Detail
ORDER BY serious_accidents DESC LIMIT 5;
```

### 6. **Effect of Light Conditions**
```sql
SELECT Light_Conditions, Accident_Severity, COUNT(*) AS accident_count
FROM accidents
GROUP BY Light_Conditions, Accident_Severity
ORDER BY Light_Conditions, Accident_Severity;
```

### 7. **Multi-Vehicle Accidents**
```sql
SELECT * FROM accidents WHERE Number_of_Vehicles > 2;
```

### 8. **Weather in Fatal Accidents**
```sql
SELECT Weather_Conditions, COUNT(*) AS fatal_accidents
FROM accidents
WHERE Accident_Severity = 'Fatal'
GROUP BY Weather_Conditions
ORDER BY fatal_accidents DESC;
```

### 9. **Urban vs Rural Analysis**
```sql
SELECT Urban_or_Rural_Area, Accident_Severity, COUNT(*) AS accident_count
FROM accidents
GROUP BY Urban_or_Rural_Area, Accident_Severity
ORDER BY Urban_or_Rural_Area, Accident_Severity;
```

### 10. **Hourly Serious Accidents**
```sql
SELECT EXTRACT(HOUR FROM Time) AS hour_of_day, COUNT(*) AS serious_accidents
FROM accidents
WHERE Accident_Severity = 'Serious'
GROUP BY hour_of_day
ORDER BY serious_accidents DESC;
```

---

## 📈 Insights & Use Cases

- Identify accident hotspots and casualty-prone districts.
- Discover risky road types, junctions, or weather/light conditions.
- Compare accident frequency between urban and rural areas.
- Allocate resources and plan interventions to improve road safety.

---

## 🚀 How to Use

1. **SQL Analysis:**  
   Load the dataset into a SQL-supported database. Run the provided queries to extract insights.

2. **Power BI Visualization:**  
   Import the dataset and build interactive dashboards using visuals as shown.

3. **Customize:**  
   Modify the queries/visuals for your specific data structure or region.

---

## 🙌 Credits

- Dataset provided for educational analysis.
- SQL queries and dashboard designed for practical road safety insights.

