# IoT Real-time Campus Weather Monitoring System in Prasetiya Mulya 

Sistem stasiun cuaca IoT ini dirancang untuk pemantauan lingkungan kampus secara real-time. Mengumpulkan data seperti suhu, kelembapan, kecepatan angin, dan curah hujan menggunakan mikrokontroler ESP32 dan berbagai sensor. Data ditransmisikan melalui protokol MQTT dan divisualisasikan pada dashboard Node-RED yang interaktif, serta disimpan untuk analisis lebih lanjut.

## Tentang Proyek Ini

Dalam proyek ini, saya berperan sebagai **Software Developer** dengan fokus utama pada:
*   Pengambilan data dari berbagai sensor lingkungan.
*   Implementasi komunikasi data menggunakan protokol MQTT.
*   Pengembangan dashboard visualisasi data menggunakan Node-RED. Dashboard ini dirancang agar pengguna dapat dengan mudah membaca dan memahami data sensor secara real-time.
*   Desain UI/UX untuk dashboard, menggunakan *function template* di Node-RED dan mengimplementasikan kode HTML, CSS, dan JavaScript kustom untuk tampilan yang optimal dan fungsional.

Saya juga terlibat dalam perancangan arsitektur sistem end-to-end awal dan sebagai Project Manager, memastikan proyek berjalan sesuai jadwal. Arsitektur yang diimplementasikan meliputi konfigurasi sensor (DHT22, Anemometer, dll.) melalui Arduino IDE, komunikasi MQTT (dengan broker Mosquitto yang berjalan di Raspberry Pi), dan perancangan alur (flows) Node-RED untuk visualisasi dashboard secara real-time dan penyimpanan data ke SQLite.

## Fitur Utama
*   Pemantauan real-time untuk:
    *   Suhu
    *   Kelembapan
    *   Kecepatan Angin
    *   Curah Hujan
*   Visualisasi data interaktif melalui dashboard Node-RED.
*   Komunikasi data yang efisien menggunakan MQTT.
*   Penyimpanan data historis (misalnya menggunakan SQLite melalui Node-RED).

## Arsitektur Sistem (Gambaran Umum)
1.  **Sensor:** DHT22 (suhu & kelembapan), Anemometer (kecepatan angin), Sensor Curah Hujan.
2.  **Mikrokontroler:** ESP32 (diprogram menggunakan C++ di Arduino IDE).
3.  **Komunikasi:**
    *   Sensor ke ESP32: Sesuai protokol sensor masing-masing.
    *   ESP32 ke Broker: MQTT.
4.  **MQTT Broker:** Mosquitto (dapat di-host di Raspberry Pi, server lokal, atau cloud).
5.  **Pemrosesan & Visualisasi Data:** Node-RED.
    *   Menerima data dari MQTT broker.
    *   Memproses data.
    *   Menampilkan data pada dashboard.
    *   Menyimpan data ke database (misalnya SQLite).
6.  **Dashboard UI:** Dibuat dengan Node-RED Dashboard nodes, dikustomisasi dengan HTML, CSS, dan JavaScript melalui node `template`.

## Prasyarat
Sebelum memulai, pastikan Anda telah menginstal:
*   [Node.js dan NPM](https://nodejs.org/)
*   [Node-RED](https://nodered.org/docs/getting-started/local) (dapat diinstal secara global melalui npm: `sudo npm install -g --unsafe-perm node-red`)
*   (Opsional, jika Anda ingin menjalankan sistem end-to-end) Sebuah MQTT Broker yang aktif dan dapat diakses (misalnya, [Mosquitto](https://mosquitto.org/)). ESP32 dan sensor juga harus dikonfigurasi untuk mengirim data ke broker ini.

## Menjalankan Dashboard Node-RED

Untuk melihat visualisasi data pada dashboard Node-RED:

1.  **Unduh File `flows.json`**
    Pastikan Anda memiliki file `flows.json` dari repositori ini. File ini berisi konfigurasi alur Node-RED untuk dashboard.

2.  **Jalankan Node-RED**
    Buka terminal atau command prompt Anda dan ketik perintah berikut:
    ```bash
    node-red
    ```
    Node-RED akan mulai berjalan. Biasanya, Anda akan melihat output yang menunjukkan alamat editor, umumnya `http://127.0.0.1:1880` atau `http://localhost:1880`.

3.  **Akses Editor Node-RED**
    Buka browser web Anda dan navigasikan ke alamat yang ditampilkan saat Node-RED dimulai (misalnya, `http://localhost:1880`).

4.  **Impor Alur (Flows)**
    *   Di antarmuka editor Node-RED, klik ikon menu hamburger (☰) di pojok kanan atas.
    *   Pilih **"Import"**.
    *   Di dialog Impor:
        *   Pilih tab **"Clipboard"** (jika Anda ingin menyalin-tempel isi file JSON) atau **"Select a file to import"** (untuk mengunggah file `flows.json` secara langsung).
        *   **Jika menyalin-tempel:** Buka file `flows.json` di editor teks, salin seluruh isinya, dan tempel ke area teks di bawah tab "Clipboard".
        *   **Jika mengunggah file:** Klik tombol "select a file to import" dan pilih file `flows.json` yang telah Anda unduh.
    *   Setelah konten JSON dimuat atau file dipilih, klik tombol merah **"Import"**. Anda mungkin perlu memilih apakah akan mengimpor ke alur baru atau alur saat ini.

5.  **Deploy Alur**
    Setelah alur berhasil diimpor, Anda akan melihat node-node dan koneksinya di editor. Klik tombol merah **"Deploy"** di pojok kanan atas untuk mengaktifkan perubahan.

6.  **Lihat Dashboard Visualisasi**
    *   Dashboard Node-RED biasanya dapat diakses dengan menambahkan `/ui` ke URL editor Node-RED.
    *   Contoh: Jika editor Anda di `http://localhost:1880`, maka dashboard akan berada di `http://localhost:1880/ui`.
    *   Buka URL dashboard di tab browser baru untuk melihat visualisasi data sensor.

## Struktur Proyek (Contoh)
