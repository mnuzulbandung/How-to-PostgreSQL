## SELECT clause

1. **SELECT ALL Columns**, Mengambil semua kolom dari tabel customer.
    ```sql
    SELECT *
    FROM customer;
    ```
2. **SELECT Certain Columns**, Mengambil kolom name dan purchase_number dari tabel customer.
    ```sql
    SELECT name, purchase_number
    FROM customer;
    ```

3. **SELECT Certain Columns**, Mengambil kolom name (sebagai customer_name) dan purchase_number (sebagai quantity) dari tabel customer.
    ```sql
    SELECT name AS customer_name, purchase_number AS quantity
    FROM customer;
    ```

4. **Unique Value**

    * **DISTINCT**, Mengambil daftar kelompok umur dalam tabel customer. Dafter tersebut akan memiliki nilai yang unik atau tidak ada duplikat.
        ```sql
        SELECT DISTINCT age
        FROM customer;
        ```
    
    * **COUNT-DISTINCT**, Mengambil jumlah kelompok umur dalam tabel customer.
        ```sql
        SELECT COUNT(DISTINCT age)
        ```

5. **Aggregate**

    * **SUM**, Mengambil nilai jumlah purchase_number dari semua customer.
        ```sql
        SELECT SUM(purchase_number) AS Total_Purchase
        FROM customer;
        ```
    
    * **AVG**, Mengambil nilai rata-rata purchase_number dari semua customer.
        ```sql
        SELECT AVG(purchase_number) AS Averaged_Purchase
        ```
    
    * **MAX**, Mengambil nilai tertinggi purchase_number dari semua customer.
        ```sql
        SELECT MAX(purchase_number) AS Max_Purchase
        ```
    
    * **MIN**, Mengambil nilai terendah purchase_number dari semua customer.
        ```sql
        SELECT MIN(purchase_number) AS Min_Purchase
        ```
    
    * **COUNT**, Mengambil jumlah baris dari tabel customer.
        ```sql
        SELECT COUNT(*) AS Customer_Number
        ```

6. **Numeric Functions**

    * **ROUND**, Mengambil purchase_number dengan 2 nilai decimal.
        ```sql
        SELECT ROUND(purchase_number, 2)
        FROM customer;
        ```
    
    * **CEIL**, Mengambil purchase_number yang dibulatkan ke atas.
        ```sql
        SELECT CEIL(purchase_number)
        ```
    
    * **FLOOR**, Mengambil purchase_number yang dibulatkan ke bawah.
        ```sql
        SELECT FLOOR(purchase_number)
        ```
    
    * **MOD**, Mengambil sisa pembagian purchase_number dengan nilai 3.
        ```sql
        SELECT MOD(purchase_number, 3)
        ```

7. **String Functions**, Hanya berlaku untuk kolom dengan tipe string.

    * **UPPER**, Mengambil nama customer dari tabel customer dengan Uppercase.
        ```sql
        SELECT UPPER(name)
        FROM customer;
        ```
    
    * **LOWER**, Mengambil nama customer dari tabel customer dengan Lowercase.
        ```sql
        SELECT Lower(name)
        ```
    
    * **LENGTH**, Mengambil jumlah huruf dari nama setiap customer.
        ```sql
        SELECT LENGTH(name)
        ```
    
    * **SUBSTRING**, Mengambil tiga huruf pertama dari nama setiap customer.
        ```sql
        SELECT SUBSTRING(name, 1, 3)
        ```
    
    * **TRIM**, Menghilanhkan karakter ' ' yang ada di depan dan belakang nama. Juga dapat menghilangkan '  ' atau berjumlah banyak.
        ```sql
        SELECT TRIM(BOTH ' ' FROM name)
        ```
    
    * **REPLACE**, Mengambil semua nama customer dimana nama Adam diganti menjadi Ahmad.
        ```sql
        SELECT REPLACE(name, 'Adam', 'Ahmad')
        ```

8. **Date Functions**

    * **NOW**, Mengambil tanggal saat query dilakukan.
        ```sql
        SELECT NOW() AS current_time;
        ```

    * **DATE**, Mengambil tanggal pembelian dari kolom tanggal-waktu.
        ```sql
        SELECT DATE(purchase_date_time) AS purchase_date
        FROM customer;
        ```
    
    * **YEAR-MONTH-DAY**, Mengambil tahun, bulan, dan hari pembelian dari kolom tanggal-waktu ke tiga kolom yang berbeda.
        ```sql
        SELECT YEAR(purchase_date_time) AS purchase_year,
               MONTH(purchase_date_time) AS purchase_month,
               DAY(purchase_date_time) AS purchase_day
        ```
    
    * **DATEDIFF**, Mengambil perbedaan waktu dari pembelian hingga sekarang.
        ```sql
        SELECT DATEDIFF(NOW(), purchase_date_time) AS purchase_date_difference
        ```
    
    * **ADDDATE**, Mengambil waktu pembelian ditambah 1 tahun.
        ```sql
        SELECT ADDDATE(purchase_date_time, INTERVAL 1 YEAR) AS purchase_date_in_one_year
        ```

    
9. **Combining Multiple Columns**

    * **CONCAT**, Mengambil first_name dan last_name dari customer dimana keduanya dimasukkan ke dalam satu kolom yang sama sebagai full_name.
        ```sql
        SELECT CONCAT(first_name, " ", last_name) AS full_name
        FROM customer;
        ```
    
    * **Numerical Operator**, Mengambil jumlah dari kedua kolom untuk setiap customer.
        ```sql
        SELECT previous_purchase + current_purchase AS total_purchase
        FROM customer;
        ```

10. **Combining Multiple Rows**

    employee table
    | employee_ID | name  | department | salary |
    |-------------|-------|------------|--------|
    | 1           | Adi   | HR         | 7000   |
    | 2           | Budi  | IT         | 8500   |
    | 3           | Cindi | IT         | 8500   |
    | 4           | Edi   | HR         | 6000   |

    <br>

    * **GROUP_CONCAT**, Mengelompokkan nama-nama employee di satu baris berdasarkan department.
        ```sql
        SELECT department, GROUP_CONCAT(name) AS employee_names
        FROM employees
        GROUP BY department;
        ```
        **Result**:
        | department  | employee_names |
        |-------------|----------------|
        | HR          | Adi,Edi        |
        | IT          | Budi,Cindi     |
        
        <br>

    * **GROUP_CONCAT with IF**, Mengelompokkan nama-nama employee di satu baris berdasarkan department, namun hanya memperlihatkan nama dengan awalan huruf A dan B.
        ```sql
        SELECT
            department,
            GROUP_CONCAT(IF(name LIKE 'A%' OR name LIKE 'B%', name, NULL)) AS employee_names
        FROM employees
        GROUP BY department;
        ```
        **Result**:
        | department  | employee_names |
        |-------------|----------------|
        | HR          | Adi            |
        | IT          | Budi           |

        <br>
    
    * **GROUP_CONCAT with ORDER BY**, Mengelompokkan nama-nama employee di satu baris berdasarkan department dengan urutan descending.
        ```sql
        SELECT department, GROUP_CONCAT(name ORDER BY name DESC) AS employee_names
        FROM employees
        GROUP BY department;
        ```
        **Result**:
        | department  | employee_names |
        |-------------|----------------|
        | HR          | Edi,Adi        |
        | IT          | Cindi,Budi     |

        <br>
    
    * **GROUP_CONCAT with SEPARATOR**, Mengelompokkan nama-nama employee di satu baris berdasarkan department sengan separator '; '.
        ```sql
        SELECT department, GROUP_CONCAT(name SEPARATOR '; ') AS employee_names
        FROM employees
        GROUP BY department;
        ```
        **Result**:
        | department  | employee_names |
        |-------------|----------------|
        | HR          | Adi; Edi       |
        | IT          | Budi; Cindi    |

        <br>

11. **Classifity Output with CASE**, Mengambil purchase_number yang diklasifikasikan sebagai High(>100), Medium(100-51), dan Low(<51).
    ```sql
    SELECT CASE 
            WHEN purchase_number > 100 THEN 'High'
            WHEN purchase_number > 50 THEN 'Medium'
            ELSE 'Low'
        END AS purchase_number_classification
    FROM customer;
    ```

12. **Replace NULL Values**, Mengambil purchase_number, jika terdapat nilai NULL maka akan diganti dengan nilai 0.
    ```sql
    SELECT COALESCE(purchase_number, 0) AS purchase_number
    FROM customer;
    ```

13. **Ranking**

    employee table
    | employee_ID | name  | department | salary |
    |-------------|-------|------------|--------|
    | 1           | Adi   | HR         | 7000   |
    | 2           | Budi  | IT         | 8500   |
    | 3           | Cindi | IT         | 8500   |
    | 4           | Edi   | HR         | 6000   |

    <br>

    * **RANK**, Membuat kolom rank (baru) berdasarkan urutan kolom salary. Jika ada dua baris dengan nilai yang kembar, maka rank keduanya sama. Lalu, rank baris selanjutnya dilewat satu.
        ```sql
        SELECT 
            name, 
            salary, 
            RANK() OVER (ORDER BY salary DESC) AS rank
        FROM 
            employees;
        ```
        **Result**:
        | name  | salary | rank |
        |-------|--------|------|
        | Adi   | 7000   | 3    |
        | Budi  | 8500   | 1    |
        | Cindi | 8500   | 1    |
        | Edi   | 6000   | 4    |

        <br>

    * **DENSE_RANK**, Membuat kolom rank (baru) berdasarkan urutan kolom salary. Jika ada dua baris dengan nilai yang kembar, maka rank keduanya sama. Lalu, rank baris selanjutnya TIDAK dilewat satu.
        ```sql
        SELECT 
            name,
            department, 
            salary, 
            DENSE_RANK() OVER (ORDER BY salary DESC) AS rank
        FROM 
            employees;
        ```
        **Result**:
        | name  | salary | rank |
        |-------|--------|------|
        | Adi   | 7000   | 2    |
        | Budi  | 8500   | 1    |
        | Cindi | 8500   | 1    |
        | Edi   | 6000   | 3    |

        <br>

    * **RANK-PARTITION**, Membuat kolom rank (baru) berdasarkan urutan kolom salary per kelompok department. Jika ada dua baris dengan nilai yang kembar, maka rank keduanya sama. Lalu, rank baris selanjutnya dilewat satu.
        ```sql
        SELECT 
            name, 
            salary, 
            RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS rank
        FROM 
            employees;
        ```
        **Result**:
        | name  | department | salary | rank |
        |-------|------------|--------|------|
        | Adi   | HR         | 7000   | 1    |
        | Budi  | IT         | 8500   | 1    |
        | Cindi | IT         | 8500   | 1    |
        | Edi   | HR         | 6000   | 2    |

        <br>
