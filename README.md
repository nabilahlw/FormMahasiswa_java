# 🎓 Form Data Mahasiswa Berbasis Java 

Aplikasi desktop berbasis **Java Swing** untuk mengelola data mahasiswa. Dibuat menggunakan NetBeans IDE dengan koneksi ke database **MySQL** via XAMPP. Mendukung operasi CRUD lengkap: Tambah, Edit, Hapus, dan Cetak data.

## ✨ Fitur

- **Tambah** data mahasiswa baru
- **Edit** data mahasiswa yang sudah ada
- **Hapus** data mahasiswa
- **Cetak** tabel data mahasiswa
- Tampilan tabel data real-time
- Validasi input data sebelum disimpan

## 🗂️ Data yang Dikelola

| Field | Keterangan |
|-------|------------|
| NIM | Nomor Induk Mahasiswa (Primary Key) |
| Nama Lengkap | Nama mahasiswa |
| Program Studi | Sistem Informasi / Teknik Informatika / Manajemen Informatika |
| Kelas | Kelas mahasiswa |

## 📁 Struktur File

```
FormMahasiswa_java-main/
├── Formmhs.java          ← Form utama (GUI + logika CRUD)
├── Formmhs.form          ← File desain form NetBeans
└── KoneksiDatabase.java  ← Konfigurasi koneksi MySQL
```

---

## ⚙️ Cara Menjalankan

### Prasyarat

Pastikan sudah terinstall:
- [NetBeans IDE](https://netbeans.apache.org/front/main/index.html) (versi 12 ke atas)
- [Java JDK 8+](https://www.oracle.com/java/technologies/downloads/)
- [XAMPP](https://www.apachefriends.org/) (untuk MySQL)
- [MySQL Connector/J](https://dev.mysql.com/downloads/connector/j/) (driver JDBC)

### Step 1 — Jalankan XAMPP

1. Buka **XAMPP Control Panel**
2. Klik **Start** pada **Apache** dan **MySQL**
3. Pastikan keduanya berstatus **hijau / Running**

### Step 2 — Buat Database & Tabel

1. Buka browser → akses `http://localhost/phpmyadmin`
2. Klik **New** → buat database bernama `kampusmhs1` → klik **Create**
3. Klik tab **SQL** → paste perintah berikut → klik **Go**:

```sql
CREATE DATABASE IF NOT EXISTS kampusmhs1;
USE kampusmhs1;

CREATE TABLE mhs (
    nim VARCHAR(20) PRIMARY KEY,
    nama_mhs VARCHAR(100) NOT NULL,
    prodi VARCHAR(50) NOT NULL,
    kelas VARCHAR(10) NOT NULL
);
```

### Step 3 — Buka Project di NetBeans

1. Buka **NetBeans IDE**
2. Klik **File → Open Project**
3. Arahkan ke folder `FormMahasiswa_java-main` → klik **Open**

### Step 4 — Tambahkan MySQL Connector (Driver JDBC)

> Langkah ini wajib agar program bisa terhubung ke MySQL!

1. Download **MySQL Connector/J** di [dev.mysql.com/downloads/connector/j](https://dev.mysql.com/downloads/connector/j/)
2. Di NetBeans, klik kanan nama project → pilih **Properties**
3. Pilih **Libraries** → klik **Add JAR/Folder**
4. Cari dan pilih file `mysql-connector-java-x.x.x.jar`
5. Klik **OK**

### Step 5 — Cek Konfigurasi Koneksi

Buka file `KoneksiDatabase.java`, pastikan isinya sesuai:

```java
Connection cn = DriverManager.getConnection(
    "jdbc:mysql://localhost/kampusmhs1", // nama database
    "root",   // username MySQL
    ""        // password MySQL (kosong jika tidak ada)
);
```

> Jika password MySQL kamu bukan kosong, isi bagian `""` dengan password kamu.

### Step 6 — Jalankan Program

1. Klik kanan file `Formmhs.java` → pilih **Run File**, ATAU
2. Tekan **Shift + F6**
3. Jendela aplikasi akan terbuka

---
