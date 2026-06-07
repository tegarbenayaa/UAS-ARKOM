# Smart Alarm System for Home Berbasis Arduino

Proyek ini merupakan sistem keamanan rumah pintar (Smart Home Security) berbasis mikrokontroler Arduino Uno. Sistem ini dirancang untuk mendeteksi berbagai jenis gangguan di area rumah serta menerapkan konsep logika digital dasar seperti gerbang OR, AND, dan SR Flip-Flop untuk mengunci status alarm.

Detail lengkap mengenai arsitektur logika dan skema rangkaian proyek ini dirujuk secara penuh dari dokumen SMART ALARM SYSTEM FOR HOME BERBASIS ARDUINO.docx.

---

## Nama Penyusun Proyek
**Program Studi S-1 Kecerdasan Artifisial**  
**Fakultas Matematika dan Ilmu Pengetahuan Alam, Universitas Negeri Surabaya**

* **Ghazanfar Abdillah** (25032014089)
* **Nabil Ramadhan Istighfarin** (25032014064)
* **Tegar Benaya Chrismanuel S.** (25032014089)

**Dosen Pengampu:** Harmon Prayogi, M.Sc. (0026069206)

---

## Deskripsi Proyek & Fitur

Sistem ini mengintegrasikan berbagai sensor perimeter dan gerak untuk melindungi aset rumah dari tindakan pencurian atau gangguan yang tidak diinginkan. Dengan memanfaatkan logika **SR Flip-Flop**, alarm yang telah terpicu akan tetap mengunci statusnya (*latch/memori*) dan terus berbunyi meskipun pelaku atau gangguan sudah tidak berada di area sensor, hingga pemilik rumah menekan tombol reset secara manual.

### Fitur Utama:
* **Multi-Sensor Detection:** Mampu mendeteksi pembukaan pintu, jendela 1, jendela 2, serta pergerakan manusia secara aktual.
* **Visual & Audio Alert:** Menggunakan kombinasi LED Merah dan Buzzer sebagai indikator utama saat terjadi indikasi bahaya.
* **Sistem Latching (SR Flip-Flop Logic):** Status alarm otomatis terkunci (TRUE) ketika ada gangguan dan tidak akan mati sendiri meskipun kondisi sensor kembali normal.
* **Real-time Status Monitoring:** Dilengkapi dengan LCD 16x2 I2C untuk menampilkan status keamanan sistem secara langsung dan menginformasikan zona sensor yang sedang terganggu.
* **Indikator Status LED:**
  * **LED Hijau:** Indikator bahwa sistem sedang aktif menjaga rumah (*Armed*).
  * **LED Kuning:** Indikator bahwa sistem dalam kondisi bersiap (*Standby / Off*).
  * **LED Merah:** Indikator bahwa terjadi pelanggaran keamanan (*Alarm Aktif*).

### Daftar Pin Input & Output (Arduino Uno):

| Jenis | Komponen | Pin Arduino | Fungsi |
| :--- | :--- | :--- | :--- |
| **Input** | Sakelar Utama | D2 | Mengaktifkan sistem |
| **Input** | Sensor Pintu | D3 | Mendeteksi pintu terbuka |
| **Input** | Sensor Jendela 1 | D4 | Mendeteksi jendela 1 terbuka |
| **Input** | Sensor Jendela 2 | D5 | Mendeteksi jendela 2 terbuka |
| **Input** | Tombol Reset | D6 | Mematikan alarm |
| **Input** | PIR Sensor | D7 | Mendeteksi gerakan manusia |
| **Output** | LED Hijau | D10 | Indikator sistem aktif |
| **Output** | LED Kuning | D11 | Indikator sistem standby |
| **Output** | Buzzer | D12 | Alarm suara |
| **Output** | LED Merah | D13 | Alarm visual |
| **Output** | LCD 16x2 I2C | SDA (A4), SCL (A5) | Menampilkan status sistem dan zona gangguan |

---

## Langkah-Langkah Cara Menjalankan / Simulasi

Proyek ini dapat disimulasikan secara fisik maupun melalui platform simulator digital (seperti Wokwi / Proteus). Ikuti langkah berikut untuk mengoperasikannya sesuai skenario logika:

1. **Persiapan Rangkaian:**
   * Sambungkan seluruh komponen input dan output ke pin Arduino Uno sesuai dengan tabel spesifikasi pin di atas.
2. **Unggah Program:**
   * Buka file kode program utama (`.ino`) pada Arduino IDE.
   * Pastikan Anda sudah memasukkan library untuk LCD I2C.
   * Lakukan *Compile* dan *Upload* program ke papan Arduino Anda.
3. **Kondisi Standby (Awal):**
   * Saat pertama kali dinyalakan, posisikan **Sakelar Utama (D2)** pada logika `LOW` (Mati). 
   * **LED Kuning** akan menyala, menandakan sistem berada dalam kondisi stanby. Pada kondisi ini, sensor tidak akan memicu alarm.
4. **Mengaktifkan Sistem (Arming):**
   * Ubah posisi **Sakelar Utama (D2)** ke logika `HIGH` (Aktif).
   * **LED Kuning** akan mati dan berganti menjadi **LED Hijau** yang menyala. Sistem kini siap mendeteksi ancaman.
5. **Simulasi Deteksi Gangguan:**
   * Berikan trigger atau simulasikan gangguan pada salah satu sensor (misal: aktifkan Sensor Pintu di D3 atau PIR Sensor di D7).
   * Melalui kombinasi logika gerbang OR dan AND pada program, sistem mendeteksi adanya intrusi.
   * Logika SR Flip-Flop akan mengubah status menjadi `Set`, menyebabkan **LED Merah** dan **Buzzer** langsung aktif berbunyi, serta LCD menampilkan zona gangguan.
6. **Menguji Fungsi Memori (Latch):**
   * Kembalikan sensor ke kondisi normal (misal: pintu ditutup kembali atau sensor gerak kembali mati).
   * Perhatikan bahwa **LED Merah dan Buzzer tetap menyala**. Hal ini membuktikan sistem pengunci memori bekerja agar pelaku tidak bisa menghilangkan jejak alarm.
7. **Mereset Alarm:**
   * Tekan **Tombol Reset (D6)** satu kali untuk mengaktifkan fungsi `Reset` pada logika Flip-Flop.
   * Status alarm kembali menjadi `FALSE`, LED Merah dan Buzzer akan mati, dan sistem kembali ke mode penjagaan awal (LED Hijau kembali menyala).

---

## Link Video Penjelasan Proyek
Untuk melihat demonstrasi alat secara detail, penjelasan *flowchart*, serta visualisasi penerapan gerbang logikanya, silakan tonton video presentasi kami melalui tautan berikut:

🔗 **[Tonton Video Penjelasan Smart Alarm System di YouTube]()**
*(Link akan diperbarui setelah video diunggah)*
