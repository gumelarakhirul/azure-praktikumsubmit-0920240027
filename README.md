# PraktikumSubmit - Azure Cloud Service Project

PraktikumSubmit adalah aplikasi web sederhana berbasis **Node.js + Express** yang digunakan untuk pengumpulan tugas praktikum mahasiswa.  
Aplikasi ini terintegrasi dengan beberapa layanan Azure:

- Azure App Service → Hosting aplikasi web
- Azure Database for MySQL → Penyimpanan data pengumpulan tugas
- Azure Blob Storage → Penyimpanan file tugas
- Azure Functions → Proses otomatis saat file diupload
- Azure Virtual Machine → Backup database dan maintenance

---

## Fitur Utama

### Mahasiswa
- Upload file tugas
- Input data mahasiswa:
  - NIM
  - Nama
  - Kelas
  - Mata Kuliah
- Data otomatis tersimpan ke Azure Database
- File otomatis tersimpan ke Azure Blob Storage

### Admin
- Login admin sederhana
- Dashboard daftar pengumpulan tugas
- Melihat detail pengumpulan tugas
- Download file tugas mahasiswa

### Sistem
- Blob Trigger menggunakan Azure Function
- Validasi file otomatis (.pdf, .docx, .zip)
- Logging file upload
- Backup database menggunakan Azure VM

---

## Tech Stack

- Node.js 22 LTS
- Express.js
- EJS
- MySQL
- Multer
- Azure Blob Storage SDK
- Azure App Service
- Azure Functions
- Azure Database for MySQL
- Azure Virtual Machine

---

## Struktur Project

```bash
PraktikumSubmit/
│── app.js
│── package.json
│── .env
│── views/
│   │── index.ejs
│   │── task-list.ejs
│   │── task-detail.ejs
│   │── admin-login.ejs
│── public/
│── uploads/
