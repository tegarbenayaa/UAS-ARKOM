# Smart Alarm System for Home Berbasis Arduino

Proyek ini merupakan sistem keamanan rumah pintar (Smart Home Security) berbasis mikrokrontroler Arduino Uno. Sistem ini dirancang untuk mendeteksi berbagai jenis gangguan di area rumah serta menerapkan konsep logika digital dasar seperti gerbang OR, AND, dan SR Flip-Flop untuk mengunci status alarm.

---

## 👥 Nama Penyusun Proyek
[cite_start]S-1 Kecerdasan Artifisial, Fakultas Matematika dan Ilmu Pengetahuan Alam, Universitas Negeri Surabaya [cite: 8, 9, 10]
* [cite_start]**Ghazanfar Abdillah** (25032014089) [cite: 3]
* [cite_start]**Nabil Ramadhan Istighfarin** (25032014064) [cite: 4]
* [cite_start]**Tegar Benaya Chrismanuel S.** (25032014089) [cite: 5]

[cite_start]**Dosen Pengampu:** Harmon Prayogi, M.Sc. [cite: 6, 7]

---

## 📝 Deskripsi Proyek & Fitur

[cite_start]Sistem ini mengintegrasikan berbagai sensor perimeter dan gerak untuk melindungi aset rumah dari tindakan pencurian atau gangguan[cite: 12, 13]. [cite_start]Dengan memanfaatkan logika **SR Flip-Flop**, alarm yang telah terpicu akan tetap mengunci statusnya (*latch/memori*) dan terus berbunyi meskipun pelaku atau gangguan sudah tidak terdeteksi lagi, hingga pemilik rumah menekan tombol reset secara manual[cite: 20, 21, 78].

### Fitur Utama:
* [cite_start]**Multi-Sensor Detection:** Mendeteksi pembukaan pintu, jendela 1, jendela 2, dan pergerakan manusia di dalam ruangan[cite: 16, 23, 24, 25, 26, 27].
* [cite_start]**Visual & Audio Alert:** Menggunakan kombinasi LED Merah dan Buzzer berkekuatan tinggi saat terjadi indikasi bahaya[cite: 17, 28].
* [cite_start]**Sistem Latching (SR Flip-Flop Logic):** Status alarm terkunci aman (TRUE) dan tidak akan mati otomatis sebelum di-reset[cite: 20, 21, 75, 76, 78].
* [cite_start]**Real-time Status Monitoring:** Dilengkapi dengan LCD 16x2 I2C untuk menampilkan status sistem (Armed/Standby) dan menunjukkan zona sensor mana yang sedang terganggu[cite: 65].
* **Indikator LED Tiga Warna:**
  * [cite_start]**LED Hijau:** Sistem aktif / terjaga (*Armed*)[cite: 29, 49].
  * [cite_start]**LED Kuning:** Sistem nonaktif / bersiap (*Standby*)[cite: 29, 53].
  * [cite_start]**LED Merah:** Terjadi pelanggaran keamanan (*Alarm Triggered*)[cite: 28, 61].

### Daftar Pin Input & Output (Arduino Uno):

| Jenis | Komponen | Pin Arduino | Fungsi |
| :--- | :--- | :--- | :--- |
| **Input** | Sakelar Utama | D2 | [cite_start]Mengaktifkan/Armed sistem [cite: 32] |
| **Input** | Sensor Pintu | D3 | [cite_start]Mendeteksi pintu terbuka [cite: 32] |
| **Input** | Sensor Jendela 1 | D4 | [cite_start]Mendeteksi jendela 1 terbuka [cite: 32, 33] |
| **Input** | Sensor Jendela 2 | D5 | [cite_start]Mendeteksi jendela 2 terbuka [cite: 35, 36, 37] |
| **Input** | Tombol Reset | D6 | [cite_start]Mematikan/Reset status alarm [cite: 39, 40, 41] |
| **Input** | PIR Sensor | D7 | [cite_start]Mendeteksi gerakan manusia [cite: 43, 44, 45] |
| **Output** | LED Hijau | D10 | [cite_start]Indikator sistem aktif (Armed) [cite: 47, 48, 49] |
| **Output** | LED Kuning | D11 | [cite_start]Indikator sistem standby (Off) [cite: 51, 52, 53] |
| **Output** | Buzzer | D12 | [cite_start]Alarm suara peringatan [cite: 55, 56, 57] |
| **Output** | LED Merah | D13 | [cite_start]Alarm visual peringatan [cite: 59, 60, 61] |
| **Output** | LCD 16x2 I2C | SDA (A4), SCL (A5) | [cite_start]Menampilkan status & lokasi zona gangguan [cite: 63, 64, 65] |

---

## Langkah-Langkah Cara Menjalankan / Simulasi

Proyek ini dapat disimulasikan secara fisik menggunakan komponen riil atau secara digital melalui platform simulasi (seperti Wokwi / Proteus). Berikut adalah langkah-langkah pengoperasiannya:

1. **Persiapan Rangkaian:**
   * [cite_start]Hubungkan seluruh sensor input (Sakelar, Sensor Pintu/Magnetic Switch, PIR, Tombol Reset) dan komponen output (LED, Buzzer, LCD I2C) ke pin Arduino Uno sesuai dengan tabel *Input dan Output Sistem* di atas[cite: 31, 32, 63, 64].
2. **Unggah Program:**
   * Buka file kode program (`.ino`) di Arduino IDE atau editor simulasi Anda.
   * Pastikan library untuk LCD I2C (`LiquidCrystal_I2C.h`) telah terinstal.
   * Lakukan *Compile* dan *Upload* program ke papan Arduino Uno.
3. **Kondisi Standby (Awal):**
   * [cite_start]Saat pertama kali dinyalakan, jika **Sakelar Utama (D2)** berada di posisi `LOW` (Mati), maka **LED Kuning** akan menyala[cite: 20, 29]. [cite_start]Sistem berada dalam mode *Standby* dan tidak akan merespons gangguan sensor[cite: 20, 53, 71, 72].
4. **Mengaktifkan Sistem (Arming):**
   * [cite_start]Ubah posisi **Sakelar Utama (D2)** ke posisi `HIGH` (Aktif)[cite: 32].
   * [cite_start]**LED Kuning** akan mati, dan **LED Hijau** akan menyala[cite: 29]. [cite_start]LCD akan menampilkan status bahwa sistem keamanan rumah sekarang telah aktif (*Armed*)[cite: 65].
5. **Simulasi Deteksi Gangguan:**
   * [cite_start]Berikan trigger `HIGH` pada salah satu atau beberapa sensor (Pintu, Jendela 1, Jendela 2, atau PIR)[cite: 23, 69].
   * [cite_start]Melalui gerbang logika OR dan AND di dalam program, sistem akan langsung mengenali adanya intrusi[cite: 68, 71, 72].
   * [cite_start]Variabel `statusAlarm` akan berubah menjadi `TRUE` (Set pada konsep SR Flip-Flop)[cite: 75, 76].
   * [cite_start]**LED Merah** dan **Buzzer** langsung aktif berbunyi[cite: 28]. [cite_start]LCD akan memunculkan informasi zona spesifik yang mendeteksi gangguan[cite: 65].
6. **Menguji Fitur Memori (Latch):**
   * [cite_start]Kembalikan sensor gangguan ke kondisi normal (misal: pintu ditutup kembali / sensor PIR kembali `LOW`)[cite: 78].
   * [cite_start]Perhatikan bahwa **LED Merah dan Buzzer tetap aktif menyala**[cite: 21, 28]. [cite_start]Ini membuktikan fungsi memori flip-flop bekerja dengan baik demi keamanan[cite: 20, 78].
7. **Mereset Alarm:**
   * [cite_start]Tekan **Tombol Reset (D6)** satu kali[cite: 40, 77].
   * [cite_start]Status `statusAlarm` akan kembali menjadi `FALSE` (Reset)[cite: 77].
   * [cite_start]LED Merah dan Buzzer akan mati, dan sistem kembali ke mode penjagaan normal (LED Hijau aktif) jika sakelar utama masih menyala[cite: 29].

---

## Link Video Penjelasan Proyek
Untuk melihat demonstrasi alat secara detail, penjelasan *flowchart*, serta visualisasi penerapan gerbang logikanya, silakan tonton video presentasi kami melalui tautan berikut:

🔗 **[Tonton Video Penjelasan Smart Alarm System di YouTube]()**
