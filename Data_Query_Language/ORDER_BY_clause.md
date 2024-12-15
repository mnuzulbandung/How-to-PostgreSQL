## ORDER BY clause

1. **Sorting**,

    *   **ASC**, Mengambil baris dari tabel customer dengan kolom id, name, purchase_number yang **diurutkan** berdasarkan kolom purchase_number, dari nilai terkecil ke terbesar.
        ```sql
        SELECT id, name, purchase_number
        FROM customer
        ORDER BY purchase_number;
        ```

    *   **DESC**, Mengambil baris dari tabel customer dengan kolom id, name, purchase_number yang **diurutkan** berdasarkan kolom purchase_number, dari nilai terbesar ke terkecil.
        ```sql
        ORDER BY purchase_number DESC;
        ```

2. **Sorting by Multiple Columns**, Mengambil baris dari tabel customer dengan kolom id, name, purchase_number yang **diurutkan** berdasarkan kolom purchase_number (Ascending), lalu berdasarkan kolom name (Descending).
    ```sql
    SELECT id, name, purchase_number
    FROM customer
    ORDER BY purchase_number ASC, name DESC;
    ```

3. **Sorting based on Alias**, Mengambil baris dari tabel customer dengan kolom id, name, purchase_number yang **diurutkan** berdasarkan kolom alias dari purchase_number, number.
    ```sql
    SELECT id, name, purchase_number AS quantity
    FROM customer
    ORDER BY quantity;
    ```

4. **LIMIT**, Mengambil baris dari tabel customer dengan kolom id, name, purchase_number yang **diurutkan** berdasarkan kolom purchase_number (Ascending). Namun, hanya mengambil 5 baris teratas.
    ```sql
    SELECT id, name, purchase_number
    FROM customer
    ORDER BY purchase_number
    LIMIT 5;
    ```

5. **NULL Position**

    * **NULLS LAST**, Mengambil baris dari tabel customer dengan kolom id, name, purchase_number yang **diurutkan** berdasarkan kolom purchase_number (Ascending). Lalu, menaruh baris dengan nilai NULL di paling bawah.
        ```sql
        SELECT id, name, purchase_number
        FROM customer
        ORDER BY purchase_number ASC NULLS LAST;
        ```
    
    * **NULLS FIRST**, Mengambil baris dari tabel customer dengan kolom id, name, purchase_number yang **diurutkan** berdasarkan kolom purchase_number (Ascending). Lalu, menaruh baris dengan nilai NULL di paling atas.
        ```sql
        ORDER BY purchase_number ASC NULLS FIRST;
        ```

6. **RANDOM**

    * MySQL, Mengambil baris dari tabel customer dengan kolom id, name, purchase_number yang **diurutkan** berdasarkan random.
        ```sql
        SELECT id, name, purchase_number
        FROM customer
        ORDER BY RAND();
        ```
    
    * PostgreSQL, Mengambil baris dari tabel customer dengan kolom id, name, purchase_number yang **diurutkan** berdasarkan random.
        ```sql
        ORDER BY RANDOM();
        ```
