# Gauss-Jordan Eliminator

Aplikasi web kalkulator sistem persamaan linear menggunakan metode Gauss-Jordan untuk menghasilkan bentuk _Reduced Row Echelon Form_ (RREF) beserta himpunan penyelesaiannya.

---

## Deskripsi

Aplikasi ini membantu pengguna menyelesaikan sistem persamaan linear dalam bentuk matriks augmented. Pengguna memasukkan ukuran matriks, mengisi nilai koefisien, lalu aplikasi akan menampilkan setiap langkah eliminasi secara runtut hingga diperoleh solusi akhir berupa _Himpunan Penyelesaian (HP)_.

---

## Teknologi yang Digunakan

| Komponen         | Teknologi                             |
| ---------------- | ------------------------------------- |
| Struktur halaman | HTML5                                 |
| Logika aplikasi  | JavaScript (Vanilla, tanpa framework) |
| Styling          | Tailwind CSS (via CDN) + Custom CSS   |
| Tipografi        | Google Fonts — Poppins                |
| Ikon             | Inline SVG                            |

Tidak ada _backend_, _build tool_, atau _bundler_ yang digunakan. Aplikasi berjalan sepenuhnya di sisi klien (_client-side only_) dengan satu file HTML tunggal.

---

## Metode: Gauss-Jordan Elimination

### Konsep Dasar

Metode Gauss-Jordan adalah perluasan dari eliminasi Gauss yang mereduksi matriks augmented ke bentuk **Reduced Row Echelon Form (RREF)**. Pada RREF, setiap baris pivot bernilai 1, dan semua elemen di atas maupun di bawah pivot bernilai 0, sehingga solusi langsung dapat dibaca tanpa substitusi balik.

### Representasi Bilangan

Seluruh aritmetika dilakukan menggunakan **representasi pecahan eksak** (numerator/denominator) untuk menghindari kesalahan pembulatan bilangan desimal. Setiap bilangan disimpan sebagai objek `{ num, den }` dan disederhanakan menggunakan _Greatest Common Divisor_ (GCD) setiap kali operasi dilakukan.

### Langkah Algoritma

```
1. Tentukan kolom pivot (kolom paling kiri yang belum nol).
2. Jika elemen pivot = 0, tukar baris dengan baris di bawahnya (Row Swap).
3. Bagi seluruh elemen baris pivot dengan nilai pivot agar pivot = 1 (Row Scale).
4. Eliminasi semua elemen lain pada kolom pivot menjadi 0 (Row Reduction).
5. Ulangi untuk kolom pivot berikutnya hingga seluruh matriks dalam RREF.
6. Baca solusi dari baris RREF:
   - Jika ada baris 0 = c (c != 0), sistem tidak konsisten (tidak ada solusi).
   - Jika ada variabel bebas, nyatakan solusi dalam parameter.
   - Jika setiap variabel memiliki pivot, terdapat solusi unik.
```

### Operasi Baris Elementer yang Digunakan

| Notasi          | Keterangan                                        |
| --------------- | ------------------------------------------------- |
| `Ri <-> Rj`     | Tukar baris i dengan baris j                      |
| `Ri / k`        | Bagi baris i dengan skalar k (normalisasi pivot)  |
| `Ri - (f) * Rj` | Kurangi baris i dengan f kali baris j (eliminasi) |

---

## Cara Penggunaan

1. Buka file `OBE1.html` di browser.
2. Masukkan jumlah **Kolom** dan **Baris** pada input yang tersedia (rentang 1 sampai 50).
3. Klik tombol **Buat Matriks** untuk menampilkan grid input.
4. Isi setiap sel matriks augmented dengan nilai koefisien yang diinginkan.
5. Klik tombol **Hitung** untuk menjalankan eliminasi Gauss-Jordan.
6. Lihat proses langkah demi langkah pada bagian **Proses**, dan hasil akhir pada bagian **Penjabaran & HP**.
7. Klik **Refresh** untuk mengulang dari awal.

---
