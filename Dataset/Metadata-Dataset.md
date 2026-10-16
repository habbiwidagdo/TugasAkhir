### Hydroponics datasets  
Baris: 50,570  
Kolom: 13  

Deskripsi:  
Dataset ini memuat data telemetri deret waktu mentah dari sistem hidroponik berskala kecil. Data tersebut mencakup pembacaan sensor kimia air dan lingkungan (pH, TDS, suhu, kelembapan, ketinggian air) serta status aktuator (pompa penurun pH, pompa penambah air, penambah nutrisi, pelembap udara, dan kipas pembuangan). Tujuannya adalah untuk mendukung penelitian mengenai peramalan, pengendalian, deteksi anomali, dan penginderaan yang efisien dalam penggunaan sumber daya pada pertanian dalam ruangan.  

Konteks:  
Data dikumpulkan dari node IoT berbasis Arduino/ESP yang terhubung ke sensor pH, TDS, ketinggian air, dan DHT, serta aktuator yang dikendalikan oleh relai untuk menjaga kondisi pertumbuhan yang optimal. Penanda waktu dicatat oleh perangkat pada interval yang bervariasi selama operasional harian.  

Waktu Pengambilan:  
2023-11-26 10:57:52 sampai 2023-12-26 21:36:40  

Granularitas (tingkat detail):  
Tidak teratur (berbasis peristiwa/log)  

Pra-pemrosesan:  
Tidak ada (raw export)  

Atribut Kolom:
* id (int) - Pengidentifikasi baris.
* timestamp (string ISO 8601) - Stempel waktu perangkat local dari catatan
* pH (float) - Keasaman/alkalinitas larutan nutrisi (biasanya 5.5-6.8, untuk sayuran berdaun hijau).
* TDS (float, ppm) - Total padatan terlarut dari larutan (proksi untuk konsentrasi nutrisi).
* water\_level (int, 0-3) - Indikator level diskrit (0 = kosong/rendah ... 3 = tinggi).
* DHT\_temp (°C) - Suhu lingkungan/Udara yang diukur di dekat reservoir.
* DHT\_humidity (%RH) - Kelembaban relative lingkungan.
* water\_temp (°C) - Suhu air reservoir.
* pH\_reducer (ON/OFF) - Status pompa pengisian ulang.
* add\_water (ON/OFF) - Status pompa pengisian ulang.
* nutrients\_adder (ON/OFF) - Status pompa dosis nutrisi.
* humidifier (ON/OFF) - Status actuator ultrasonic/kabut dingin.
* ex\_fan (ON/OFF) - Status kipas pembuangan.

Statistik Dasar:
* pH: rata-rata ≈ 6.00, min = 0.27, maks = 11.57
* TDS (ppm): rata-rata ≈ 1154.1, min = -283.91, maks = 2278.35
* DHT\_temp (­°C): rata-rata ≈ 24.32, rentang 12.3 - 70.0
* DHT\_humidity (­°C): rata-rata ≈ 71.71, rentang 25.0 - 3312.6

Actuator Sparsity (jumlah ON):
* pH\_reducer: 652
* add\_water: 2.260
* nutrients\_adder: 3.057
* humidifier: 2.458
* ex\_fan: 52

Masalah yang Diketahui \& Catatan:
* Data mentah: Ekspor tanpa penyaringan yang ditujukan untuk keperluan penelitian; terdapat nilai-nilai yang tidak wajar (misalnya, TDS negatif, kelembapan DHT yang sangat tinggi). Harap lakukan pemotongan atau penyaringan pencilan (\*outlier\*) sebagaimana mestinya.
* Pengambilan sampel tidak teratur: Interval antar-rekaman tidak seragam; pengambilan sampel ulang (\*resampling\*) mungkin diperlukan untuk model deret waktu (\*time-series\*).
* Ketidakseimbangan aktuator: Status aktuator sangat condong ke arah OFF; hal ini perlu diperhatikan untuk tugas klasifikasi atau prediksi kejadian.
* Satuan: TDS dalam ppm; suhu dalam °C; kelembapan dalam %RH; tingkat air bersifat diskret (0–3).

Potensi Penggunaan:
* Prakiraan pH/TDS dan pemberian dosis secara proaktif
* Pembelajaran kebijakan kendali untuk aktuator (berbasis aturan atau RL)
* Deteksi anomali/pencilan dalam jaringan sensor
* Optimalisasi masa pakai sensor (misalnya, memprediksi waktu pengukuran)