## GROUP BY clause

customer table

| customer_ID | name      | location | age         |
|-------------|-----------|----------|-------------|
| 1           | Alice     | Jakarta  | adult       |
| 2           | Bob       | Bandung  | teenager    |
| 3           | Charlie   | Jakarta  | young_adult |
| 4           | Dimas     | Jakarta  | young_adult |

<br>

1. **GROUP BY and Aggregate**, Mencari tahu jumlah customer per lokasi.
    ```sql
    SELECT location, COUNT(*) AS customer_count
    FROM customer
    GROUP BY location;
    ```
    **Result**:
    | location | customer_count |
    |----------|----------------|
    | Jakarta  | 3              |
    | Bandung  | 1              |

    <br>

2. **Multiple GROUP BY and Aggregate**, Mencari tahu jumlah customer per lokasi dan kelompok umur.
    ```sql
    SELECT location, age, COUNT(*) AS customer_count
    FROM customer
    GROUP BY location, age;
    ```
    **Result**:
    | location | age         | customer_count | 
    |----------|-------------|----------------|
    | Jakarta  | adult       | 1              |
    | Jakarta  | young_adult | 2              |
    | Bandung  | teenager    | 1              |

    <br>

3. **GROUP BY, Having and Aggregate**, Mencari tahu jumlah customer per lokasi. Hanya memperlihatkan location dengan jumlah customer lebih dari 1.
    ```sql
    SELECT location, age, COUNT(*) AS customer_count
    FROM customer
    GROUP BY location
    HAVING COUNT(*) > 1;
    ```
    **Result**:
    | location | customer_count | 
    |----------|----------------|
    | Jakarta  | 3              |
