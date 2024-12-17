
# **PostgreSQL**

## **A. Fitur-fitur:**
PostgreSQL adalah Relational Database Management System (RDBMS) dengan beberapa fitur, antara lain:

* **SQL Compliance**: Menggunakan bahasa SQL untuk kebutuhan query data dari table, join beberapa table yang berbeda, atau agregasi nilai dari beberapa baris yang berbeda dalam satu tabel. 
* **Strong Data Integrity**: Menggunakan constraints (primary keys dan foreign keys).
* **Open Source**: Gratis untuk digunakan.
* **Cross-Platform**: Tersedia untuk platform Linux, macOS dan Windows. Bisa dihubungkan dengan tools seperti Python, R, dan cloud platforms (AWS RDS, Google Cloud SQL).
* **ACID Compliance**: Memastikan transaksi bersifat atomik, konsisten, terisolasi, dan tahan lama.
* **Data Types**: Hanya bisa menggunakan structured data.
* **Security**: Menggunakan metode otentikasi (kata sandi, Kerberos, LDAP, dll.) dan kontrol akses berbasis Role (RBAC) untuk mengelola izin.

## **B. Konsep:**
Istilah-istilah yang digunakan dalam PostgreSQL:

* **Schemas**: Container yang menampung objek-objek database.
* **Tables**: Bentuk structured data dalam baris dan kolom.
* **Indexes**: Nilai-nilai unik pada suatu kolom pada tabel yang digunakan untuk membedakan satu baris dengan baris yang lain.
* **Transactions**: Beberapa operasi berbeda yang dikelompokkan menjadi satu agar bisa dijalankan bersama.
* **Views**: Tabel virtual berdasarkan hasil query.
* **Functions**: Rangkuman logika yang dapat digunakan kembali.

**C. Penggunaan PostgreSQL dengan SQL**

Untuk menggunakan PostgreSQL, bahasa SQL dapat digunakan. Bahasa SQL dapat dibagi menjadi 5 jenis dengan perannya masing-masing.
* **Data Definition Language (DDL)**: Membuat atau mengubah database, schema, tables, indexes, atau constraints.
* **Data Manipulation Language (DML)**: Mengisi data ke dalam tabel yang sudah ada dalam database dan mengubahnya.
* **Transaction Control Language (TCL)**: Mengatur transaksi agar berjalan secara konsisten dan integritas.
* **Data Query Language (DQL)**: Meng-query atau mengambil data dari table.
* **Data Control Language (DCL)**: Mengontrol akses untuk database dan isinya.
