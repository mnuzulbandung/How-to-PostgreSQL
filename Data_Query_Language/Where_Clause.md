## WHERE clause

1. **Basic Condition**, Mengambil baris dengan customer dengan purchase_number di atas 5
    ```sql
    SELECT * 
    FROM customer
    WHERE purchase_number > 5;
    ```

2. **Multiple Conditions On Multiple Columns**,

    *   **AND**, Mengambil baris dengan customer dengan purchase_number di atas 5 dan berumur sebagai Teen. Kedua kondisi harus terpenuhi.
        ```sql
        SELECT * 
        FROM customer
        WHERE purchase_number > 5 AND age = 'Teen';
        ```

    *   **OR**, Mengambil baris dengan customer dengan purchase_number di atas 5 atau berumur sebagai Teen. Salah satu kondisi harus terpenuhi.
        ```sql
        WHERE purchase_number > 5 OR age = 'Teen';
        ```

    *   **AND-OR Combination**, Mengambil baris dengan customer dengan purchase_number di atas 5 dan berumur sebagai Teen atau Young Adult. Kondisi "purchase_number di atas 5" harus terpenuhi. Kondisi "berumur sebagai Teen atau Young Adult" harus terpenuhi salah satu.
        ```sql
        WHERE purchase_number > 5 AND (age = 'Teen' OR age = 'Young Adult');
        ```

3. **Multiple Conditions On Categorical Columns**, **IN**, Mengambil baris dengan customer yang berumur sebagai Teen, Young Adult, atau Adult. Salah satu kondisi harus terpenuhi
    ```sql
    SELECT * 
    FROM customer
    WHERE age IN ('Teen', 'Young Adult', 'Adult');
    ```

4. **Multiple Conditions On Numerical Columns**, **BETWEEN**, Mengambil baris dengan customer dengan purchase_number 4 hingga 6. Jumlah 4 dan 6 termasuk.
    ```sql
    SELECT * 
    FROM customer
    WHERE purchase_number BETWEEN 4 AND 6;
    ```

5. **Patterns in Text Columns**,

    *   **Huruf/Kata Depan**, Mengambil baris dengan customer bernama berawalan huruf "A".
        ```sql
        SELECT * 
        FROM customer
        WHERE name LIKE 'A%';
        ```
    *   **Huruf/Kata Belakang**, Mengambil baris dengan customer bernama berakhiran huruf "Z".
        ```sql
        WHERE name LIKE '%A';
        ```
    *   **Huruf/Kata Tengah**, Mengambil baris dengan customer bernama yang memiliki kata "AA".
        ```sql
        WHERE name LIKE '%AA%';
        ```
    *   **Huruf/Kata Depan di huruf Kedua**, Mengambil baris dengan customer bernama dengan huruf kedua huruf "a".
        ```sql
        WHERE name LIKE '_a%';
        ```

6. **NULL Values**, **IS NULL**, Mengambil baris dengan customer dengan purchase_number yang tidak memiliki nilai.
    ```sql
    SELECT * 
    FROM customer
    WHERE purchase_number IS NULL;
    ```

7. **The Opposite of the Condition**,

    *   **NOT IN**, Mengambil baris dengan customer yang BUKAN berumur sebagai Teen, Young Adult, atau Adult.
        ```sql
        SELECT * 
        FROM customer
        WHERE age NOT IN ('Teen', 'Young Adult', 'Adult');
        ```
    *   **NOT BETWEEN**, Mengambil baris dengan customer dengan purchase_number BUKAN 4 hingga 6.
        ```sql
        SELECT * 
        FROM customer
        WHERE purchase_number BETWEEN 4 AND 6;
        ```

8. **Subqueries**, Mengambil baris dengan customer dengan purchase_number di atas rata-rata.
    ```sql
    SELECT * 
    FROM customer
    WHERE purchase_number >
        (SELECT AVG(purchase_number) FROM customer);
    ```

9. **Subqueries with EXISTS**, Mengambil baris jika "customer dengan purchase_number di atas 5" berjumlah 10 atau lebih. Jika tidak, tidak akan mengambil apa-apa
    ```sql
    SELECT * 
    FROM customer AS c
    WHERE EXISTS (
        SELECT 10
        FROM purchase AS p
        WHERE c.ID = p.Customer_ID AND p.purchase_number > 5
    );
