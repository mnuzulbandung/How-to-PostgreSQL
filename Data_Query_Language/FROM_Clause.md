## FROM clause

1. **FROM**, Mengambil baris dari tabel customer dengan kolom id, name, purchase_number.
    ```sql
    SELECT id, name, purchase_number
    FROM customer;
    ```

2. **FROM**, Mengambil baris dari tabel customer dengan kolom id, name, purchase_number. Menggunakan alias untuk nama tabel customer sebagai c.
    ```sql
    SELECT c.name, p.purchase_number 
    FROM customer AS c
    JOIN purchase AS p ON c.id = p.customer_id;
    ```

3. **Subqueries**, Mencari kelompok umur dengan total_purchase di atas 1000.
    ```sql
    SELECT age, total_purchase
    FROM (
        SELECT age, SUM(purchase_number) AS total_purchase
        FROM customer
        GROUP BY age)
    WHERE total_purchase > 1000;
    ```
