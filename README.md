# Investigate Hotel Business using Data Visualization
Project ini merupakan project yang bertujuan untuk melakukan investigasi terhadap suatu hotel (dalam kasus ini Hotel Business). Project ini dibuat menggunakan bahasa pemrograman Python

## Daftar Isi
- Data Preprocessing
- Analisis Pemesanan Hotel Bulanan Berdasarkan Jenis Hotel
- Analisis Dampak Durasi Menginap pada Tingkat Pembatalan Pemesanan Hotel
- Analisis Dampak _Lead Time_ terhadap Tingkat Pembatalan Pemesanan Hotel

## Bagian 0: Pendahuluan
Sangat penting bagi suatu perusahaan untuk selalu menganalisa performa bisnisnya. Pada kesempatan kali ini, akan didalami bisnis dalam bidang perhotelan. Fokus yang dituju adalah untuk mengetahui bagaimana perilaku pelanggan dalam melakukan pemesanan hotel, dan hubungannya terhadap tingkat pembatalan pemesanan hotel. Hasil dari insight yang ditemukan akan disajikan dalam bentuk visualisasi data agar lebih mudah dipahami dan bersifat lebih persuasif. Dari latar belakang tersebut, didapat tiga tujuan penelitian yakni sebagai berikut
1. Mengidentifikasi jenis hotel apa yang paling sering dikunjungi oleh pelanggan
2. Mengetahui pengaruh durasi menginap terhadap tingkat pembatalan pemesanan hotel
3. Mengetahui pengaruh jarak waktu antara pemesanan hotel dan hari kedatangan tamu terhadap tingkat pembatalan pemesanan hotel

## Bagian 1: Data Preprocessing
|     Asesmen Data         |     Temuan                                                                                                                                         |     Penyelesaian                                                                                                                                                                                                                                                                                                                                                                               |
|--------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     Null Values          |     Terdapat   null value pada kolom     `company`, `city`, `children`,   dan `agent`                                                              | 1. Kolom `company` diisi dengan 0 yang mengindikasikan tamu tidak berasal dari company<br> 2. Kolom `city` diisi dengan 0 yang mengindikasikan tamu melakukan reservasi mandiri atau tidak melalui agen 3. Kolom `children` diisi dengan 0 yang mengindikasikan tamu tidak membawa anak-anak<br> 4. Kolom `agent` diisi dengan `undefined` dikarenakan kota nya tak diketahui dengan pasti |
|     Konsistensi Nilai    |     Terdapat makna “Undefined” pada kolom `meal`                                                                                                   | Mengkategorikan nilai kolom `meal` menjadi 2                                                                                                                                                                                                                                                                                                                                                   |
| Nilai Anomali            | 1. Terdapat nilai negatif dan outlier yang sangat jauh dari distribusi data pada kolom `adr` 2. Terdapat 180 data booking yang tidak memiliki tamu |                                                                                                                                                                                                                                                                                                                                                                                                |
