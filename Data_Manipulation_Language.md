# **Data Manipulation Language**

## **A. INSERT Clause**

1.  **INSERT**, Memasukkan data ke dalam tabel yang sudah ada. Nilai default dari kolom tertentu bisa dimasukkan dengan menggunakan nilai `DEFAULT`. Nilai kosong bisa dimasukkan dengan menggunakan nilai `NULL`. 
    ```sql
    INSERT INTO employees (employee_id, name, department, salary)
    VALUES 
        (2, 'Bob', 'Finance', 60000),
        (3, 'Charlie', 'Engineering', 70000);
    ```

2. **INSERT froma other table**, Memasukkan data dari tabel lain.
    ```sql
    INSERT INTO employees (employee_id, name, department, salary)
    SELECT id, full_name, division, income
    FROM candidates
    WHERE division = 'Engineering';
    ```

## **B. UPDATE Clause**

1.  **UPDATE**, Mengubah data pada beberapa column.
    ```sql
    UPDATE employees
    SET name = 'Alice Johnson', department = 'Finance'
    WHERE employee_id = 1;
    ```

2.  **UPDATE using Subqueries**, Mengubah data pada column dengan nilai hasil query.
    ```sql
    UPDATE employees
    SET salary = (
        SELECT MAX(expected_salary)
        FROM candidates
        WHERE candidates.department = employees.department
    )
    WHERE department = 'Engineering';
    ```

3.  **UPDATE using CASE**, Mengubah data pada column dengan beberapa kondisi.
    ```sql
    UPDATE employees
    SET salary = CASE
        WHEN department = 'HR' THEN salary * 1.05
        WHEN department = 'Engineering' THEN salary * 1.10
        ELSE salary * 1.02
    END;
    ```

4. **UPDATE with JOIN**, Mengubah data berdasarkan join.
    ```sql
    UPDATE employees
    SET salary = candidates.expected_salary
    FROM candidates
    WHERE employees.employee_id = candidates.id;
    ```

5.  **UPDATE NULL value**, Mengubah data dengan nilai NULL.
    ```sql
    UPDATE employees
    SET salary = 50000
    WHERE salary IS NULL;
    ```

## **C. DELETE Clause**

1.  **DELETE**, Menghapus data dengan kondisi tertentu.
    ```sql
    DELETE FROM employees
    WHERE employee_id = 1;
    ```

2.  **DELETE with JOIN**, Menghapus data dengan JOIN.
    ```sql
    DELETE FROM employees
    USING departments
    WHERE employees.department_id = departments.department_id
    AND departments.department_name = 'Finance';
    ```
