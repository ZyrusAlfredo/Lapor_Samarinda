# Mini Project 1 (Pemograman Aplikasi Bergerak) - Lapor Samarinda

## Apa itu Lapor Samarinda?
Pernah kamu merasa bahwa ingin melaporkan fasilitas umum yang sudah tidak memadai atau bahkan rusak, tapi bingung mau melaporkan ke mana?

Nah, Lapor Samarinda hadir untuk menjawab permasalahan tersebut. Sekarang **kamu bisa melaporkan fasilitas umum yang kurang memadai atau bahkan rusak itu ke dalam aplikasi mobile kami yaitu Lapor Samarinda.**

```
Nama: Zyrus Alfredo Randan Malinggato
NIM: 2409116120
```

---

# Lapor Samarinda 📍📝

**Lapor Samarinda** adalah aplikasi mobile berbasis Flutter yang dirancang untuk memudahkan warga kota Samarinda dalam melaporkan kerusakan atau ketidaklayakan fasilitas umum di sekitar mereka. 

Seringkali masyarakat merasa bingung ke mana harus mengadu ketika menemukan fasilitas publik yang rusak (seperti lampu jalan mati, jalan berlubang, atau jembatan yang tidak memadai). **Lapor Samarinda** hadir sebagai platform solusi untuk mendata dan memantau laporan-laporan tersebut secara digital, terstruktur, dan transparan.

## Tampilan Aplikasi Mobile Lapor Samarinda
<img width="1080" height="1080" alt="1" src="https://github.com/user-attachments/assets/1d4aadff-e588-41b3-8166-26c559af1f14" />

---

# Fitur Utama📱
Aplikasi ini memiliki fitur **CRUD** (*Create, Read, Update, Delete*) lengkap yang memungkinkan pengelolaan data secara *real-time* di dalam aplikasi:

* **Tambah Laporan (Create):** Pengguna dapat menambahkan laporan baru dengan mengisi formulir yang terdiri dari Nama Infrastruktur, Lokasi, dan Deskripsi Kerusakan.
* **Daftar Laporan (Read):** Menampilkan seluruh laporan yang telah dibuat dalam bentuk *Card* yang rapi di halaman utama.
* **Edit Laporan (Update):** Pengguna dapat memperbarui informasi pada laporan yang sudah ada jika terdapat kesalahan atau perubahan status.
* **Hapus Laporan (Delete):** Menghapus data laporan dari daftar dengan fitur konfirmasi (Dialog) untuk mencegah penghapusan yang tidak sengaja.
* **Sistem Notifikasi (Feedback):** Memberikan respon visual berupa *SnackBar* setiap kali pengguna berhasil menambah, mengedit, atau menghapus data.

---

# Cara Penggunaan🤳

## 1. Create (Tambah Laporan)
Fitur ini memungkinkan pengguna untuk menginput laporan infrastruktur baru ke dalam sistem.\
**Cara Kerja:**\
a. **Navigasi:** Pengguna menekan *FloatingActionButton* di halaman utama yang memicu fungsi Navigator.push menuju halaman FormLaporan.\
b. **Input Data:** Pengguna mengisi tiga field utama: *Nama Infrastruktur*, *Lokasi*, dan *Deskripsi*. Data ini ditangkap secara *real-time* menggunakan TextEditingController.\
c. **Validasi & Objek:** Saat tombol "Simpan Laporan" ditekan, aplikasi membuat objek baru dari class LaporanInfrastruktur dengan ID unik berbasis *timestamp* (DateTime.now).\
d. **Data Passing:** Objek tersebut dikirim kembali ke halaman utama melalui Navigator.pop(context, laporanBaru).\
e. **State Management:** Di halaman utama, data yang diterima ditambahkan ke dalam List menggunakan fungsi setState(), sehingga tampilan otomatis diperbarui (Hot Reload secara lokal).\
f. **Feedback:** Muncul *SnackBar* berwarna hijau sebagai indikator bahwa data berhasil disimpan.

<img width="1920" height="1080" alt="Tambah Laporan" src="https://github.com/user-attachments/assets/376e101b-79a8-444a-b60d-e6e920ad84ec" />

## 2. Read (Melihat Laporan)
Fitur ini bertanggung jawab untuk menyajikan data laporan yang tersimpan agar dapat dibaca oleh pengguna secara terorganisir.\
**Penjelasan Singkat:**\
a. **Penyimpanan Data:** Seluruh laporan disimpan di dalam sebuah variabel List<LaporanInfrastruktur> bernama daftarLaporan.\
b. **Kondisi Data Kosong:** Aplikasi melakukan pengecekan kondisi. Jika daftarLaporan.isEmpty, maka aplikasi akan menampilkan widget Center dengan teks "Belum Ada Laporan" sebagai informasi kepada pengguna.\
c. **Rendering List:** Jika data tersedia, aplikasi menggunakan widget ListView.builder. Widget ini sangat efisien karena hanya merender item yang terlihat di layar saja.\
d. **Komponen Visual:** Setiap data diubah menjadi widget Card yang berisi ListTile.\
   - **Leading:** Menampilkan ikon catatan untuk memberikan konteks visual.\
   - **Title:** Menampilkan nama infrastruktur yang dilaporkan.\
   - **Subtitle:** Menampilkan lokasi kerusakan.\
e. **Dinamis:** Setiap kali ada penambahan atau perubahan data melalui setState(), ListView akan otomatis membangun ulang (rebuild) tampilannya sehingga data terbaru langsung muncul tanpa perlu memuat ulang halaman.

<img width="1920" height="1080" alt="Lihat Laporan" src="https://github.com/user-attachments/assets/daf2a69b-5309-49c0-9326-46ecdbb242c0" />

## 3. Update (Memperbarui/Mengubah Laporan)
Fitur ini memungkinkan pengguna untuk memperbaiki atau memperbarui informasi pada laporan yang sudah dibuat sebelumnya.\
**Cara Kerja:**\
a. **Pengiriman Data:** Saat pengguna menekan ikon edit atau baris laporan, aplikasi membawa objek laporan yang dipilih menuju halaman Form Laporan.\
b. **Auto-Fill:** Di halaman form, fungsi initState akan mendeteksi kiriman data tersebut dan secara otomatis mengisi (pre-fill) semua kotak input dengan data lama.\
c. **Identifikasi:** Aplikasi menggunakan ID unik yang sudah ada agar sistem tahu bahwa ini adalah proses pembaruan data, bukan pembuatan data baru.\
d. **Sinkronisasi:** Setelah tombol simpan ditekan, data hasil edit dikirim kembali ke Halaman Utama dan memperbarui posisi list yang sesuai menggunakan setState.\
e. **Feedback:** Muncul SnackBar berwarna biru sebagai tanda bahwa pembaruan data telah berhasil.

<img width="1920" height="1080" alt="Update Laporan" src="https://github.com/user-attachments/assets/cbd44912-24cc-4045-86f6-7496a07dc424" />

## 4. Delete (Menghapus Laporan)
Fitur ini berfungsi untuk menghapus laporan yang sudah tidak relevan/tidak penting/tidak perlu/salah dari daftar.\
**Cara Kerja:**\
a. **Konfirmasi:** Saat tombol ikon tempat sampah ditekan, aplikasi tidak langsung menghapus data, melainkan menampilkan Dialog Konfirmasi (Alert Dialog). Ini bertujuan untuk mencegah penghapusan yang tidak disengaja.\
b. **Eksekusi:** Jika pengguna memilih "Hapus", aplikasi menjalankan perintah removeAt berdasarkan indeks laporan tersebut di dalam daftar.\
c. **Penyegaran Tampilan:** Melalui setState, item tersebut akan langsung hilang dari tampilan ListView secara real-time.\
d. **Feedback:** Notifikasi SnackBar akan muncul untuk memberi tahu pengguna bahwa data telah terhapus secara permanen dari memori.

<img width="1920" height="1080" alt="Hapus Laporan" src="https://github.com/user-attachments/assets/5a0a2e38-ff94-41b3-b15c-d9c92d40c30d" />

---

# Widget yang Digunakan📲
Dalam pengembangan aplikasi ini, digunakan berbagai jenis widget bawaan Flutter untuk menyusun antarmuka dan logika aplikasi:

**1. Widget Utama (Struktur & Navigasi)**
a. StatefulWidget: Digunakan pada halaman utama dan form agar aplikasi dapat memperbarui tampilan secara dinamis saat data laporan berubah.\
b. Scaffold: Merupakan struktur dasar halaman yang menyediakan komponen penting seperti AppBar, Body, dan FloatingActionButton.\
c. Navigator: Digunakan untuk mengelola perpindahan antar halaman (Halaman Utama ke Halaman Form) dengan sistem tumpukan (stack).

**2. Layout & List**\
a. ListView.builder: Digunakan untuk menampilkan daftar laporan secara efisien. Widget ini sangat bertenaga karena hanya merender item yang muncul di layar saja.\
b. Card & ListTile: Kombinasi widget untuk membungkus data laporan agar terlihat rapi dengan susunan ikon, judul, dan subjudul.\
c. Row & Column: Widget layout utama untuk menyusun elemen secara horizontal (seperti tombol edit dan hapus) serta vertikal (seperti susunan input field).\
d. Padding & SizedBox: Digunakan untuk mengatur jarak antar elemen agar antarmuka tidak terlihat rapat dan lebih nyaman dipandang.

**3. Komponen Input & Interaksi**\
a. TextField: Komponen utama untuk menerima input teks dari pengguna (Nama, Lokasi, Deskripsi).\
b. TextEditingController: Berfungsi untuk mengontrol, mengambil, dan memanipulasi teks yang diketikkan pengguna di dalam TextField.\
c. IconButton & TextButton: Widget interaktif yang digunakan untuk memicu aksi seperti menyimpan, mengedit, membatalkan, atau menghapus data.\
d. FloatingActionButton: Tombol melayang di pojok kanan bawah yang berfungsi sebagai akses cepat untuk menambah laporan baru.

**4. Feedback & Dialog**\
a. AlertDialog: Jendela pop-up yang muncul untuk meminta konfirmasi pengguna sebelum melakukan penghapusan data.\
b. SnackBar: Notifikasi singkat di bagian bawah layar untuk memberikan informasi keberhasilan sebuah aksi (Tambah/Edit/Hapus).

---

# Kekurangan & Rencana Pengembangan🚨💡

**1. Kekurangan Saat Ini**\
a. **Penyimpanan Data Sementara:** Data laporan saat ini hanya disimpan di dalam memori variabel (RAM). Artinya, jika aplikasi ditutup atau di-restart, seluruh data laporan akan hilang.\
b. **Belum Ada Validasi Input:** Pengguna masih dapat menyimpan laporan meskipun kolom input (seperti nama atau lokasi) masih kosong atau tidak diisi.\
c. **Media Laporan Terbatas:** Laporan saat ini hanya berbasis teks, sehingga pengguna belum bisa melampirkan foto bukti kerusakan infrastruktur secara langsung.

**2. Rencana Pengembangan**\
a. **Implementasi Local Database:** Agar data tetap tersimpan secara permanen di perangkat pengguna meskipun aplikasi ditutup.
b. **Integrasi Kamera:** Menambahkan fitur unggah foto agar laporan menjadi lebih valid dan informatif bagi pihak terkait.
c. **Fitur Pencarian & Filter:** Memudahkan pengguna untuk mencari laporan spesifik berdasarkan nama infrastruktur atau wilayah lokasi tertentu.
d. **Validasi Form:** Menambahkan logika pengecekan agar tombol simpan hanya bisa ditekan jika semua data sudah terisi dengan benar.
