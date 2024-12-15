## JOIN clause

order table

| order_ID | product_bought | customer_ID |
|----------|----------------|-------------|
| 1        | Apple          | 1           |
| 2        | Blueberry      | 2           |
| 3        | Cherry         | 3           |

customer table

| ID | name      | location |
|----|-----------|----------|
| 1  | Alice     | Jakarta  |
| 2  | Bob       | Bandung  |
| 4  | Dimas     | Jakarta  |

1. **JOIN**

    * **INNER JOIN**, Menggabungkan dua tabel berdasarkan nilai kolom customer_ID. Baris yang muncul jika ada di kedua tabel.
        ```sql
        SELECT o.product_bought, c.name
        FROM order AS o
        INNER JOIN customer AS c
        ON o.customer_ID = c.ID;
        ```
        **Result**:
        | product_bought | name      |
        |----------------|-----------|
        | Apple          | Alice     |
        | Blueberry      | Bob       |

        <br>

    * **LEFT JOIN**, Menggabungkan dua tabel berdasarkan nilai kolom customer_ID di tabel order.
        ```sql
        SELECT o.product_bought, c.name
        FROM order AS o
        LEFT JOIN customer AS c
        ON o.customer_ID = c.ID;
        ```
        **Result**:
        | product_bought | name      |
        |----------------|-----------|
        | Apple          | Alice     |
        | Blueberry      | Bob       |
        | Cherry         | NULL      |

        <br>
    
    * **RIGHT JOIN**, Menggabungkan dua tabel berdasarkan nilai kolom ID di tabel customer.
        ```sql
        SELECT o.product_bought, c.name
        FROM order AS o
        RIGHT JOIN customer AS c
        ON o.customer_ID = c.ID;
        ```
        **Result**:
        | product_bought | name      |
        |----------------|-----------|
        | Apple          | Alice     |
        | Blueberry      | Bob       |
        | NULL           | Dimas     |

        <br>
    
    * **FULL JOIN**, Menggabungkan dua tabel berdasarkan nilai kolom customer_ID di tabel order dan customer.
        ```sql
        SELECT o.product_bought, c.name
        FROM order AS o
        FULL JOIN customer AS c
        ON o.customer_ID = c.ID;
        ```
        **Result**:
        | product_bought | name      |
        |----------------|-----------|
        | Apple          | Alice     |
        | Blueberry      | Bob       |
        | Cherry         | NULL      |
        | NULL           | Dimas     |

        <br>
    
2. **CROSS JOIN**, Menggabungkan semua baris dari beberapa kolom yang ada di dua tabel.
    ```sql
    SELECT o.name, c.product_bought
    FROM order AS o
    CROSS JOIN customer AS c;
    ```
    **Result**:
    | product_bought | name      |
    |----------------|-----------|
    | Apple          | Alice     |
    | Apple          | Bob       |
    | Apple          | Dimas     |
    | Blueberry      | Alice     |
    | Blueberry      | Bob       |
    | Blueberry      | Dimas     |
    | Cherry         | Alice     |
    | Cherry         | Bob       |
    | Cherry         | Dimas     |

    <br>
    
