# Indian-Election-results

# Indian Election SQL Project

## Overview
This project analyzes the **2024 Indian General Election results** using SQL. It includes queries for constituency-wise and party-wise results, total seat calculations, and state-wise breakdowns.

## Database Structure
The database is named **`Indian_election_results`** and contains the following tables:

1. **`constituencywise_details`** - Detailed results for each constituency.
2. **`partywise_results`** - Aggregated party results.
3. **`constituencywise_results`** - Seat-wise election results.
4. **`states`** - List of states and their IDs.
5. **`statewise_results`** - State-wise seat distribution.

## SQL Queries

### 1. Create and Select Database
```sql
CREATE DATABASE Indian_election_results;
USE Indian_election_results;
```

### 2. Fetch All Data from Tables
```sql
SELECT * FROM constituencywise_details;
SELECT * FROM partywise_results;
SELECT * FROM constituencywise_results;
SELECT * FROM states;
SELECT * FROM statewise_results;
```

### 3. Total Number of Seats in Election
```sql
SELECT COUNT(DISTINCT Parliament_Constituency) AS Total_Seats
FROM constituencywise_results;
```

### 4. Total Seats Available in Each State
```sql
SELECT 
    s.State AS State_Name,
    COUNT(DISTINCT cr.Constituency_ID) AS Total_Seats_Available
FROM constituencywise_results cr
JOIN statewise_results sr ON cr.Parliament_Constituency = sr.Parliament_Constituency
JOIN states s ON sr.State_ID = s.State_ID
GROUP BY s.State
ORDER BY s.State;
```

### 5. Total Seats Won by NDA Alliance
```sql
SELECT 
    COUNT(*) AS NDA_Total_Seats
FROM constituencywise_results
WHERE party IN (
    'Bharatiya Janata Party - BJP', 
    'Telugu Desam - TDP',
    'Janata Dal (United) - JD(U)',
    'Shiv Sena - SS',
    'Lok Janshakti Party - LJP'
);
```

## Usage Instructions
1. Import the SQL file into your database management system (MySQL, PostgreSQL, etc.).
2. Run the queries provided above to analyze election results.
3. Modify queries as needed for deeper insights.

## Future Enhancements
- Add visualization using Python (Pandas, Matplotlib, Seaborn).
- Implement interactive dashboards using Power BI or Tableau.
- Expand dataset with voter demographics and turnout analysis.

## Contributors
- **[Your Name]** - SQL Queries & Analysis
- **[Other Contributors]** - Data Collection & Validation

---
*For any questions or improvements, feel free to contribute!* 🚀
