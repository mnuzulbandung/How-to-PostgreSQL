# **Data Definition Language**

## **A. CREATE Clause**

1. **CREATE DATABASE**, Membuat Database.
    ```sql
    CREATE DATABASE new_database
    WITH 
        OWNER = postgres
        ENCODING = 'UTF8'
        CONNECTION LIMIT = 50;
    ```
    *   `new_database`: Nama Database
    *   `OWNER = postgres`: Pemilik Database
    *   `ENCODING = 'UTF8'`: Sistem penulisan karakter (Encoding)
    *   `CONNECTION LIMIT = 50`: Maksimal koneksi

2. **CREATE SCHEMA**, Membuat Schema.
    ```sql
    CREATE SCHEMA new_schema AUTHORIZATION postgres;
    ```
    *   `new_schema`: Nama Schema
    *   `AUTHORIZATION postgres`: Pemilik Schema

3. **CREATE TABLE**, Membuat Table.
    ```sql
    CREATE TABLE new_table (
        column_numeric_1 SERIAL PRIMARY KEY,
        column_categoric_1 VARCHAR(100) NOT NULL,
        column_categoric_1 VARCHAR(50) UNIQUE,
        column_numeric_2 NUMERIC(10, 2),
        column_date DATE DEFAULT CURRENT_DATE
    );
    ```
    *   `new_table`: Nama Table
    *   `column_numeric_1`: Nama Column
    *   `SERIAL`: Mengisi nilai secara otomatis untuk Primary Key
    *   `PRIMARY KEY`: Menjadikan column sebagai primary key
    *   `VARCHAR(100)`: Column bertipe text dengan panjang 100 karakter
    *   `NOT NULL`: Memastikan kolumn tidak berisi NULL
    *   `UNIQUE`: Memastikan kolumn bersifat unik
    *   `NUMERIC(10, 2)`: Column bertipe number dengan panjang 10 digit di depan 0 dan 2 digit di belakang 0
    *   `DATE`: Column bertipe date
    *   `DEFAULT CURRENT_DATE`: Mengisi nilai secara otomatis berdasarkan tanggal sekarang

3. **CREATE INDEX**, Membuat kolom baru dari tabel yang sudah ada yang bisa digunakan sebagai index (memiliki nilai yang unik tiap baris).
    ```sql
    CREATE INDEX new_index ON old_table(old_colummn);
    ```
    *   `new_index`: Nama Index
    *   `old_table`: Nama tabel
    *   `old_colummn`: Nama column

4. **CREATE USER**, Membuat database user.
    ```sql
    CREATE USER new_user WITH PASSWORD 'new_password';
    ```
    *   `new_user`: Username
    *   `new_password`: Password

5. **CREATE ROLE**, Membuat role.
    ```sql
    CREATE ROLE manager 
    WITH 
        LOGIN 
        PASSWORD 'managerpassword'
        CREATEDB;
    ```
    *   `LOGIN`: Username
    *   `CREATEDB`: Dibolehkan untuk membuat database

## **B. DROP Clause**

1. Menghapus tabel.
    ```sql
    DROP TABLE IF EXISTS old_table;
    ```

2. Menghapus schema.
    ```sql
    DROP SCHEMA IF EXISTS old_schema CASCADE;
    ```

3. Menghapus database.
    ```sql
    DROP DATABASE IF EXISTS old_database;
    ```

4. Menghapus role.
    ```sql
    DROP ROLE IF EXISTS old_role;
    ```

5. Menghapus index.
    ```sql
    DROP INDEX IF EXISTS old_index;
    ```

6. Menghapus column dalam tabel.
    ```sql
    ALTER TABLE old_table DROP COLUMN IF EXISTS old_column;
    ```

7. Menghapus constraints dalam column dalam tabel.
    ```sql
    ALTER TABLE old_table DROP CONSTRAINT old_column;
    ```

## **C. ALTER Clause**

1. Merubah Table.

    *   Menambah Column baru pada table
        ```sql
        ALTER TABLE old_table ADD COLUMN new_column INT;
        ```
    *   Menghapus column lama pada table
        ```sql
        ALTER TABLE old_table DROP COLUMN old_column;
        ```
    *   Merubah nama column pada table
        ```sql
        ALTER TABLE old_table RENAME COLUMN old_column_name TO new_column_name;
        ```
    *   Merubah tipe column pada table
        ```sql
        ALTER TABLE old_table ALTER COLUMN old_column TYPE NUMERIC(10, 2);
        ```
    *   Memasukkan default value pada column. Ubah `SET` menjadi `DROP` dan hapus `5000` untuk menghilangkannya.
        ```sql
        ALTER TABLE old_table ALTER COLUMN old_column SET DEFAULT 5000;
        ```
    *   Memperbolehkan nilai NULL pada column. Ubah `DROP` menjadi `SET` untuk tidak memperbolehkan nilai NULL.
        ```sql
        ALTER TABLE old_table ALTER COLUMN old_column DROP NOT NULL;
        ```

2. Merubah Schema.

    *   Merubah nama schema
        ```sql
        ALTER SCHEMA old_schema_name RENAME TO new_schema_name;
        ```
    
    *   Merubah pemilik schema
        ```sql
        ALTER SCHEMA old_schema_name OWNER TO new_owner;
        ```

3. Merubah Role.

    *   Merubah nama Role
        ```sql
        ALTER ROLE app_user RENAME TO app_user_1;
        ```
    
    *   Merubah Role Password
        ```sql
        ALTER ROLE app_user WITH PASSWORD 'newpassword';
        ```
    
    *   Menambah Privilage dari Role.
        ```sql
        ALTER ROLE app_user WITH CREATEDB;
        ```

4. Merubah Databae.

    *   Merubah nama database
        ```sql
        ALTER DATABASE new123 RENAME TO production_db;
        ```
    
    *   Merubah connection limit
        ```sql
        ALTER DATABASE production_db WITH CONNECTION LIMIT 50;
        ```
    
    *   Menambah owner.
        ```sql
        ALTER DATABASE production_db OWNER TO admin_user;
        ```
    
  ## **D. TRUNCATE Clause**

1.  Menghapus baris pada tabel. Kolom masih ada.
    ```sql
    TRUNCATE TABLE old_table_1, old_table_2;
    ```

2.  Menghapus baris pada tabel. Jika ada column dengan auto-increment sequence.
    ```sql
    TRUNCATE TABLE old_table_1 RESTART IDENTITY;
    ```

3.  Menghapus baris pada tabel. Jika ada column dengan foreign key dependencies.
    ```sql
    TRUNCATE TABLE old_table_1 CASCADE;
    ```
