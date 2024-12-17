# **Data Control Language**

## **A. GRANT Clause**

1.  Memberikan Privilage SELECT dan INSERT untuk tabel table_1 dan table_2 pada user_1.
    ```sql
    GRANT SELECT, INSERT
    ON table_1, table_2
    TO user_1;
    ```

2.  Memberikan semua Privilage untuk tabel table_1 pada user_1.
    ```sql
    GRANT ALL PRIVILEGES ON table_1 TO user_1;
    ```

3.  Memberikan Privilage mengakses dan membuat object pada schema_1 pada user_1.
    ```sql
    GRANT USAGE ON SCHEMA schema_1 TO user_1;
    GRANT CREATE ON SCHEMA schema_1 TO user_1;
    ```

4.  Memberikan Privilage mengakses dan membuat tables (temporary) pada database_1 pada user_1.
    ```sql
    GRANT CONNECT ON DATABASE database_1 TO user_1;
    GRANT TEMP ON DATABASE database_1 TO user_1;
    ```

5.  Membuat role. Memberikan Provilage SELECT dan INSERT pada table_1 pada role_1. Memberikan role_1 pada user_1.
    ```sql
    CREATE ROLE role_1;
    GRANT SELECT, INSERT ON table_1 TO role_1;
    GRANT role_1 TO user_1;
    ```

## **B. REVOKE Clause**

1.  Menghilangkan Privilage tertentu dari user_1.
    ```sql
    REVOKE SELECT ON employees FROM user1;
    ```
