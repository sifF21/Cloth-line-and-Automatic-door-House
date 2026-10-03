# Automation Jemuran Rumah dan Pintu Otomatis

Proyek Arduino untuk otomatisasi jemuran rumah dan pintu otomatis berbasis sensor hujan dan sensor jarak.

## Deskripsi

Sistem ini dirancang untuk membantu mengangkat jemuran secara otomatis saat hujan mulai turun dan membuka pintu otomatis ketika ada objek yang mendekat. Proyek ini menggunakan:

- Sensor kelembapan/air (analog input)
- Sensor ultrasonik HC-SR04
- 2 buah servo motor
- LED indikator
- Buzzer
- Arduino

## Fitur

- Jemuran otomatis naik saat ketinggian air sensor melebihi ambang tertentu
- Jemuran turun kembali saat kondisi tidak hujan
- Pintu terbuka otomatis bila objek terdeteksi dalam jarak <= 6 cm
- Pintu akan menutup kembali setelah 3 detik
- LED dan buzzer digunakan sebagai indikator status

## Komponen yang Digunakan

- Arduino Uno (atau board kompatibel)
- Servo motor untuk jemuran
- Servo motor untuk pintu
- Sensor air analog
- Sensor ultrasonik HC-SR04
- LED 5V
- Buzzer
- Kabel jumper dan breadboard

## Pin Wiring

| Komponen | Pin Arduino |
| --- | --- |
| Sensor Air | A0 |
| Servo Jemuran | 9 |
| Servo Pintu | 6 |
| Buzzer | 8 |
| LED | 7 |
| Trigger HC-SR04 | 10 |
| Echo HC-SR04 | 11 |

## Prinsip Kerja

### 1. Jemuran otomatis
- Nilai sensor air diukur setiap loop.
- Jika sensor air >= 300, sistem menganggap hujan dan mengangkat jemuran.
- Jika tidak hujan, jemuran berada pada posisi turun.

### 2. Pintu otomatis
- Sensor HC-SR04 memantau jarak objek.
- Jika jarak <= 6 cm, pintu membuka sebesar 90°.
- Setelah 3 detik, pintu menutup kembali.

### 3. Indikator
- LED menyala saat pintu terbuka.
- Buzzer menandakan kondisi hujan dan chime saat pintu membuka.

## Struktur File

- `Kode Arduino` — file kode program utama Arduino
- `README.md` — dokumentasi proyek

## Cara Menjalankan

1. Buka file `Kode Arduino` di Arduino IDE.
2. Pastikan board dan port serial sudah benar.
3. Upload program ke Arduino.
4. Hubungkan semua komponen sesuai pin wiring.
5. Jalankan sistem dan amati respons otomatis.

## Catatan

- Nilai ambang `batasAir` dan `batasJarak` dapat diubah sesuai kebutuhan.
- Gunakan power supply yang stabil agar servo dan komponen bekerja dengan baik.
- Untuk penggunaan di lingkungan nyata, disarankan menambahkan penguatan casing dan proteksi kabel.

## Lisensi

Proyek ini dibuat untuk kebutuhan pembelajaran dan pengembangan sistem otomatisasi rumah sederhana.

## Penulis

Dibuat oleh `sifF21`.
