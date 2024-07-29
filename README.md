![3c  Tren Pembatalan Pemesanan Berdasarkan Durasi](https://github.com/user-attachments/assets/ea2b175e-edeb-438b-9258-687ea26c8515)# Investigate Hotel Business using Data Visualization
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
Pada proses ini dilakukan pemrosesan data sekaligus pembersihan data, yang terdiri dari:
1. Pemeriksaan _null_ / _missing value_ pada data
2. Pemeriksaan duplikasi data
3. Pemeriksaan tipe data dan konsistensi nilai, serta
4. Pemeriksaan _outlier_ atau data yang tidak biasa<br>
Hasilnya tertera pada tabel dibawah.

| Asesmen Data      | Temuan                                                                                                                                                 | Penyelesaian                                                                                                                                                                                                                                                                                                                                                                                   |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Null Values       | Terdapat null value pada kolom `company`, `city`, `children`,   dan `agent`                                                                            | 1. Kolom `company` diisi dengan 0 yang mengindikasikan tamu tidak berasal dari company<br> 2. Kolom `city` diisi dengan 0 yang mengindikasikan tamu melakukan reservasi mandiri atau tidak melalui agen<br> 3. Kolom `children` diisi dengan 0 yang mengindikasikan tamu tidak membawa anak-anak<br> 4. Kolom `agent` diisi dengan `undefined` dikarenakan kota nya tak diketahui dengan pasti |
| Konsistensi Nilai | Terdapat makna “Undefined” pada kolom `meal`                                                                                                           | Mengkategorikan nilai kolom `meal` menjadi 2, yaitu:<br> 1. `With Meal` (_Breakfast, Full Board, Dinner_)<br> 2. `No Meal` (_No Meal, Undefined_)                                                                                                                                                                                                                                              |
| Nilai Anomali     | 1. Terdapat nilai negatif dan outlier yang sangat jauh dari distribusi data pada kolom `adr`<br> 2. Terdapat 180 data booking yang tidak memiliki tamu | Melakukan _drop_ pada baris data tersebut                                                                                                                                                                                                                                                                                                                                                      |
## Bagian 2: Analisis Pemesanan Hotel Bulanan Berdasarkan Jenis Hotel
Analisis ini difokuskan untuk melihat tren dari pemesanan hotel untuk tiap jenis hotel.
![2a  Ratio Total Booking](https://github.com/user-attachments/assets/14d90a41-a95c-45cc-8c10-30e1e35be5ce)<br>
Dari grafik diatas, didapatkan bahwa City Hotel 66.41%, lebih banyak dipesan dibanding Resort Hotel yang memiliki persentase 33.59%.<br>
**Mengapa hal tersebut dapat terjadi?**
Diduga bahwa mayoritas pelanggan yang memesan Hotel City ini merupakan pelancong yang memiliki aktivitas utama disekitar tempat mereka menginap, bukan tujuan utama mereka untuk melakukan aktivitas di hotel.
Selain itu, City hotel biasanya terletak di pusat kota atau daerah perkotaan, dekat dengan tempat-tempat wisata dan bisnis. Mereka biasanya dirancang untuk memberikan kenyamanan dan kemudahan akses ke fasilitas dan aktivitas di kota, seperti restoran, pusat perbelanjaan, dan tempat wisata.<br>
Sedangkan, Pelanggan yang memesan Resort Hotel diduga memang memiliki tujuan untuk berlibur dan bersantai di tempat ini karena Resort hotel biasanya terletak di tempat-tempat yang indah seperti tepi pantai, pegunungan, atau daerah pedesaan yang tenang dan terdapat fasilitas yang lengkap.<br><br>
Jika dilihat secara bulanan, dapat dilihat pada grafik dibawah ini
![2b  Ratio Total Booking jpg](https://github.com/user-attachments/assets/f0444e8c-0fe1-4584-b6c8-90c188b9efdf)<br>
Dari grafik tersebut, dapat dibuat kesimpulan sebagai berikut.
1. Tingkat pemesanan pada periode Januari – Maret merupakan tingkat pemesanan terendah. Hal ini dapat dikarenakan sedikit sekali hari libur nasional. Selain itu, bulan tersebut merupakan awal tahun ajaran baru bagi pelajar. Oleh karena itu, memiliki aktivitas perjalanan bisnis pada bulan tersebut tidak sesibuk bulan-bulan lainnya dikarenakan masih awal tahun.
2. Pemesanan kedua tipe hotel pada perode bulan Mei - Agustus memiliki nilai tertinggi (terutama untuk City Hotel), serta mengalami peningkatan yang signifikan pada periode waktu tersebut. Hal ini dapat dikarenakan selain adanya liburan sekolah pada bulan tersebut, juga bertepatan dengan banyaknya hari libur nasional seperti cuti bersama dan acara keagamaan seperti bulan Ramadhan dan Idul Fitri. Oleh karena itu, banyak orang yang mengambil kesempatan ini untuk menfaatkan waktunya dengan berlibur, seperti berkunjung ke luar kota, dan melakukan pemesanan hotel.
3. Sedangkan pada musim liburan Oktober - Desember bertepatan depan dengan natal dan tahun baru, yang menyebabkan tingkat pemesanan pada bulan tersebut kembali meninggi.

## Bagian 3: Analisis Dampak Durasi Menginap pada Tingkat Pembatalan Pemesanan Hotel
Analisis ini berfokus untuk melihat tren antara durasi menginap dengan tingkat pembatalan pemesanan hotel. 
![3 0  Impact Analysis of Stay Duration on Hotel Bookings Cancellation Rates](https://github.com/user-attachments/assets/5f97150e-66c5-4004-966c-4fa8d771a7b9)
Walaupun Hotel City memiliki tingkat pemesanan yang lebih tinggi daripada Hotel Resort, akan tetapi hal tersbut berbanding lurus dengan tingkat pembatalannya. Hal ini menunjukkan bahwa banyak pelanggan yang memesan City Hotel cenderung lebih sering membatalkan pesanannya. Dikarenakan Hotel City banyak berpusat di daerah perkotaan dengan berkawasan bisnis, maka terkadang banyak kegiatan bisnis yang harus diatur, serta pengaruh faktor lain. Oleh karena itulah banyak pelanggan yang membatalkan pesanan mereka.<br>
**Namun apakah hal tersebut berpengaruh terhadap durasi menginapnya?**
![3c  Tren Pembatalan Pemesanan Berdasarkan Durasi](https://github.com/user-attachments/assets/9a0c1dc8-91b1-45b3-afd2-da1fdc9f0438)
Dapat dilihat bahwa tingkat pembatalan akan semakin tinggi seiring dengan lama durasi menginap yang dipesan pada kedua tipe hotel. Pada City Hotel untuk durasi menginap >2 minggu memiliki Cancelation Rate >50%, apalagi untuk durasi menginap >1 bulan hanya 1 dari 10 orang yang tidak membatalkan pesanannya.

## Bagian 4: Analisis Dampak _Lead Time_ terhadap Tingkat Pembatalan Pemesanan Hotel
![4a  Tingkat Pembatalan Pemesanan Hotel Berdasarkan Masa Tunggu (Lead Time)](https://github.com/user-attachments/assets/63ae8400-92bc-4161-95b1-4670ab31d25e)
Dari grafik diatas, didapatkan bahwa tingkat pembatalan berdasarkan masa tunggu masih didominasi oleh City Hotel, dengan tingkat Cancelation Rate cenderung tinggi ketika masa tunggu hampir satu tahun.
