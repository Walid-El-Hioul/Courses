
### **1. Basic Query: Retrieve Specific Columns**

**Query:**
```sql
SELECT customerid, city, country
FROM customers;
```

**Description:** This query retrieves the `customerid`, `city`, and `country` columns from the `customers` table.

**Result (Sample):**
| CustomerId | City    | Country |
|------------|---------|---------|
| 1          | City A  | Country X |
| 2          | City B  | Country Y |
| ...        | ...     | ...     |

---

### **2. Retrieve All Columns**

**Query:**
```sql
SELECT * 
FROM customers;
```

**Description:** This query retrieves all columns from the `customers` table.

**Result (Sample):**
| CustomerId | FirstName | LastName | City   | Country |
|------------|-----------|----------|--------|---------|
| 1          | John      | Doe      | City A | Country X |
| 2          | Jane      | Smith    | City B | Country Y |
| ...        | ...       | ...      | ...    | ...     |

---

### **3. Sort Results in Ascending Order**

**Query:**
```sql
SELECT customerid, city, country
FROM customers
ORDER BY city;
```

**Description:** This query retrieves `customerid`, `city`, and `country` columns from the `customers` table and sorts the results in ascending alphabetical order based on the `city` column.

**Result (Sample):**
| CustomerId | City    | Country |
|------------|---------|---------|
| 1          | Amsterdam | Netherlands |
| 2          | Berlin    | Germany |
| ...        | ...     | ...     |

---

### **4. Sort Results in Descending Order**

**Query:**
```sql
SELECT customerid, city, country
FROM customers
ORDER BY city DESC;
```

**Description:** This query retrieves `customerid`, `city`, and `country` columns from the `customers` table and sorts the results in descending alphabetical order based on the `city` column.

**Result (Sample):**
| CustomerId | City      | Country |
|------------|-----------|---------|
| 1          | Yellowknife | Canada |
| 2          | Winnipeg   | Canada |
| ...        | ...       | ...     |

---

### **5. Sort Results by Multiple Columns**

**Query:**
```sql
SELECT customerid, city, country
FROM customers
ORDER BY country, city;
```

**Description:** This query retrieves `customerid`, `city`, and `country` columns from the `customers` table, sorting first by `country` in ascending order and then by `city` in ascending order within each country.

**Result (Sample):**
| CustomerId | City          | Country |
|------------|---------------|---------|
| 1          | Buenos Aires  | Argentina |
| 2          | Santiago      | Chile    |
| ...        | ...           | ...     |
