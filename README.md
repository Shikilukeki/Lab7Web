# Praktikum 1

- Nama: Rifqi Maulana
- NIM: 312410529
- Kelas: I241E
---

### 🎯 Tujuan Praktikum
Berdasarkan modul, praktikum ini bertujuan untuk:
1. Memahami konsep dasar framework
2. Memahami konsep MVC (Model-View-Controller)
3. Membuat aplikasi sederhana menggunakan CodeIgniter 4

---

### 🛠️ Persiapan
Sebelum mulai, dilakukan beberapa konfigurasi:
- Menggunakan XAMPP sebagai web server
- Mengaktifkan ekstensi PHP:
  - php-json
  - php-mysqlnd
  - php-xml
  - php-intl
  - libcurl (opsional)

📸 Screenshot: (Konfigurasi PHP.ini)

---

### 📦 Instalasi CodeIgniter 4
Langkah-langkah:
1. Download CodeIgniter dari website resmi
2. Extract ke folder:
```
htdocs/lab11_ci
```
4. Rename folder menjadi:
```
ci4
```
4. Akses di browser:
```
http://localhost/lab11_ci/ci4/public/
```
📸 Screenshot: (Halaman awal CI4)

---

## ⚙️ Menjalankan CLI
Masuk ke folder project:
```bash
cd C:\xampp\htdocs\lab11_ci\ci4
```
Jalankan:
```
php spark
```
Untuk menjalankan server:
```
php spark serve
```
Akses:
```
http://localhost:8080
```
📸 Screenshot: (CLI berjalan)

---

🐞 Mengaktifkan Debugging

Langkah:

Rename file:
```
env → .env
```
Ubah:
```
CI_ENVIRONMENT = development
```
Tujuan: agar error lebih jelas saat debugging

📸 Screenshot: (Error tampil detail)

---

📂 Struktur Direktori

Penjelasan singkat:

app/ → tempat coding utama
public/ → file yang bisa diakses (CSS, JS, index.php)
system/ → core CodeIgniter
writable/ → file log, cache, dll

---
🧠 Konsep MVC
```
Model → mengelola data
View → tampilan (HTML, CSS)
Controller → penghubung antara model dan view
```
Jadi alurnya:
```
User → Controller → Model → View
```

---

🔀 Routing

File:
```
app/Config/Routes.php
```
Menambahkan route:
```
$routes->get('/about', 'Page::about');
$routes->get('/contact', 'Page::contact');
$routes->get('/faqs', 'Page::faqs');
```
📸 Screenshot: (Routes.php)
---
🎮 Membuat Controller

File:
```
app/Controllers/Page.php
```
Contoh:
```
<?php

namespace App\Controllers;

class Page extends BaseController
{
    public function about()
    {
        echo "Ini halaman About";
    }

    public function contact()
    {
        echo "Ini halaman Contact";
    }

    public function faqs()
    {
        echo "Ini halaman FAQ";
    }
}
```
📸 Screenshot: (Halaman About tampil)
---
🖼️ Membuat View

File:
```
app/Views/about.php
```
Isi:
```
<!DOCTYPE html>
<html>
<head>
    <title><?= $title; ?></title>
</head>
<body>
    <h1><?= $title; ?></h1>
    <p><?= $content; ?></p>
</body>
</html>

Controller diubah:

public function about()
{
    return view('about', [
        'title' => 'Halaman About',
        'content' => 'Ini adalah halaman about'
    ]);
}
```
📸 Screenshot: (View tampil)
---

🎨 Membuat Layout dengan CSS

Langkah:

Buat file:
```
public/style.css
```
Buat folder:
```
app/Views/template/
```
File:
```
header.php
footer.php
```
Header
```
<link rel="stylesheet" href="<?= base_url('/style.css');?>">
About.php
<?= $this->include('template/header'); ?>

<h1><?= $title; ?></h1>
<p><?= $content; ?></p>

<?= $this->include('template/footer'); ?>
```

📸 Screenshot: (Tampilan dengan CSS)
---

### ⚠️ Kendala yang Dialami

Beberapa kendala saat praktikum:

CSS tidak terbaca karena file tidak berada di folder public
URL berbeda antara:
```
XAMPP → /public
CLI → :8080
Error ERR_CONNECTION_REFUSED
```
karena server belum dijalankan
---
### Solusi:

-Memastikan file CSS di public
-Menggunakan php spark serve
-Mengecek base_url di config
---
### ✅ Kesimpulan

Dari praktikum ini dapat disimpulkan:

Framework mempermudah pengembangan web
Konsep MVC membantu memisahkan logic, tampilan, dan data
CodeIgniter 4 cukup ringan dan mudah dipahami untuk pemula
Penggunaan routing dan controller sangat penting dalam pengelolaan halaman
