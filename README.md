# 🚀 Praktikum Pemrograman Web 2  
## 🌐 CodeIgniter 4 – Routing & Auto Routing

<p align="center">
  <img src="https://img.shields.io/badge/PHP-8.x-blue?logo=php" />
  <img src="https://img.shields.io/badge/CodeIgniter-4-red?logo=codeigniter" />
  <img src="https://img.shields.io/badge/XAMPP-Localhost-orange" />
  <img src="https://img.shields.io/badge/Status-Praktikum%20Selesai-brightgreen" />
</p>

---

## 👤 Identitas Mahasiswa
| Keterangan | Isi |
|-----------|-----|
| Nama | Fathan Atallah Rasya Nugraha |
| NIM | 312410425 |
| Kelas | I241C |
| Mata Kuliah | Pemrograman Web 2 |

---

## 📌 Deskripsi Praktikum
Praktikum ini bertujuan untuk memahami penggunaan dasar **Framework CodeIgniter 4**, meliputi proses instalasi, konfigurasi environment, pembuatan routing manual, penerapan auto routing, serta pengujian controller melalui browser.

---

## 🛠️ Tools & Software
- XAMPP  
- PHP 8.x  
- CodeIgniter 4  
- Visual Studio Code  
- Web Browser  
- Git & GitHub  

---

## ⚙️ Langkah-Langkah Praktikum

### 1️⃣ Instalasi CodeIgniter 4
1. Mengunduh CodeIgniter 4 dari situs resmi.  
2. Mengekstrak file ke folder:
   `htdocs/lab11_ci/ci4`
3. Menjalankan melalui browser: `http://localhost/lab11_ci/ci4/public`
Jika berhasil, akan muncul halaman **Welcome to CodeIgniter 4**.

![img](img/welcome.png)

---

### 2️⃣ Menjalankan Server CodeIgniter
Server dijalankan menggunakan perintah:
```bash
php spark serve
```

Server aktif pada alamat: `http://localhost:8080`

![img](img/spark_serve.png)

### 3️⃣ Konfigurasi Environment
Mengubah nama file env menjadi .env

Mengatur environment menjadi development:
```bash
CI_ENVIRONMENT = development
```

```bash
#--------------------------------------------------------------------
# Example Environment Configuration file
#
# This file can be used as a starting point for your own
# custom .env files, and contains most of the possible settings
# available in a default install.
#
# By default, all of the settings are commented out. If you want
# to override the setting, you must un-comment it by removing the '#'
# at the beginning of the line.
#--------------------------------------------------------------------

#--------------------------------------------------------------------
# ENVIRONMENT
#--------------------------------------------------------------------

# CI_ENVIRONMENT = development

#--------------------------------------------------------------------
# APP
#--------------------------------------------------------------------

# app.baseURL = ''
# If you have trouble with `.`, you could also use `_`.
# app_baseURL = ''
# app.forceGlobalSecureRequests = false
# app.CSPEnabled = false

#--------------------------------------------------------------------
# DATABASE
#--------------------------------------------------------------------

# database.default.hostname = localhost
# database.default.database = ci4
# database.default.username = root
# database.default.password = root
# database.default.DBDriver = MySQLi
# database.default.DBPrefix =
# database.default.port = 3306

# If you use MySQLi as tests, first update the values of Config\Database::$tests.
# database.tests.hostname = localhost
# database.tests.database = ci4_test
# database.tests.username = root
# database.tests.password = root
# database.tests.DBDriver = MySQLi
# database.tests.DBPrefix =
# database.tests.charset = utf8mb4
# database.tests.DBCollat = utf8mb4_general_ci
# database.tests.port = 3306

#--------------------------------------------------------------------
# ENCRYPTION
#--------------------------------------------------------------------

# encryption.key =

#--------------------------------------------------------------------
# SESSION
#--------------------------------------------------------------------

# session.driver = 'CodeIgniter\Session\Handlers\FileHandler'
# session.savePath = null

#--------------------------------------------------------------------
# LOGGER
#--------------------------------------------------------------------

# logger.threshold = 4
```

### 4️⃣ Routing Manual
Konfigurasi routing manual dilakukan pada file app/Config/Routes.php:
```php
<?php

use CodeIgniter\Router\RouteCollection;

/**
 * @var RouteCollection $routes
 */

$routes->setAutoRoute(true);

$routes->get('/', 'Home::index');
$routes->get('/about', 'Page::about');
$routes->get('/contact', 'Page::contact');
$routes->get('/faqs', 'Page::faqs');
```
![img](img/about.png)

### 5️⃣ Membuat Controller
Controller dibuat pada file `app/Controllers/Page.php`:
```php
<?php
namespace App\Controllers;

use App\Controllers\BaseController;

class Page extends BaseController
{
    public function about()
    {
        return view('about', [
            'title' => 'Halaman About',
            'content' => 'Ini adalah halaman about'
        ]);
    }

    public function contact()
    {
        echo "Ini halaman Contact";
    }

    public function faqs()
    {
        echo "Ini halaman FAQ";
    }

    public function tos()
    {
        echo "Ini halaman Term of Services";
    }
}
```

### 6️⃣ Mengaktifkan Auto Routing
Auto Routing diaktifkan dengan menambahkan konfigurasi berikut pada Routes.php:
```php
$routes->setAutoRoute(true);
```

Pada CodeIgniter 4 versi terbaru, perlu menonaktifkan Improved Auto Routing melalui file:
```php
app/Config/Feature.php
```
```php
public bool $autoRoutesImproved = false;
```

### 7️⃣ Pengujian Auto Routing
Pengujian dilakukan dengan mengakses URL:
`http://localhost:8080/page/tos`
Jika berhasil, akan tampil:
```bash
Ini halaman Term of Services
```
![img](img/tos.png)

### 📂 Struktur Direktori Project
![img](img/folder.png)

### ❗ Kendala yang Dihadapi
Auto Routing menampilkan error 404 pada CodeIgniter 4 versi terbaru.

#### ✅ Solusi
Menonaktifkan fitur Improved Auto Routing pada file Feature.php agar Auto Routing lama dapat digunakan sesuai modul praktikum.

### 📊 Hasil Praktikum
- Routing manual berhasil dijalankan
- Auto Routing berhasil digunakan
- Controller dapat diakses melalui browser
- Tidak ditemukan error setelah konfigurasi diperbaiki

### ✅ Kesimpulan
Dari praktikum ini dapat disimpulkan bahwa CodeIgniter 4 menyediakan fitur routing manual dan auto routing. Auto Routing mempermudah pemanggilan method controller, namun pada versi terbaru diperlukan konfigurasi tambahan agar sesuai dengan modul praktikum.
