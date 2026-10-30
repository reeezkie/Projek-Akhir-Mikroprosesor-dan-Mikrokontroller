# 🔥 Sistem Deteksi Kebakaran & Suhu Berbasis Arduino Uno
> Proyek Akhir Praktikum Mikroprosesor dan Mikrokontroler

[![Status Project](https://img.shields.io/badge/Status-Completed-success.svg)]()
[![C Language](https://img.shields.io/badge/Language-Embedded%20C-blue.svg)]()
[![Institution](https://img.shields.io/badge/Universitas-Brawijaya-red.svg)]()

Repositori ini berisi kode sumber (*source code*), dokumentasi laporan akhir, dan file pendukung untuk **Proyek Akhir Mikroprosesor dan Mikrokontroler**. Proyek ini merancang dan mengimplementasikan sistem deteksi dini kebakaran berbasis *embedded system* menggunakan mikrokontroler Arduino Uno, multisensor, serta antarmuka visual-audio untuk memantau kondisi lingkungan secara *real-time*.

---

## 🏛️ Informasi Akademik
* **Mata Kuliah:** Praktikum Mikroprosesor dan Mikrokontroler
* **Dosen Pengampu:** Agung Setia Budi, S.T., M.T., M.Eng., Ph.D.
* **Institusi:** Fakultas Ilmu Komputer, Universitas Brawijaya (FILKOM UB)

### 👥 Tim Penyusun (Kelompok)
1. **Rezky Auliasarie** (245150300111014)
2. **Agatha Triotama** (245150300111020)
3. **Afifah Zuriah Mindarini** (245150301111001)
4. **Adinda Eka Suja Pertiwi** (245150307111014)
5. **Delvin Nhean Olamina** (245150307111032)

---

## 💡 Latar Belakang & Tujuan
Kebakaran merupakan bencana yang sering kali menimbulkan kerugian besar akibat kurangnya sistem deteksi dini. Proyek ini bertujuan untuk membangun sistem pemantauan suhu dan deteksi api secara *real-time* yang responsif, terjangkau, dan andal.

Sistem ini dirancang untuk:
1. Mendeteksi adanya nyala api secara langsung menggunakan sensor Flame IR (jalur analog dan digital).
2. Memonitor suhu dan kelembapan ruangan menggunakan sensor DHT22.
3. Memberikan peringatan dini secara visual (LED Merah/Hijau) dan audio (Buzzer dengan modulasi PWM).
4. Menampilkan informasi status lingkungan secara *real-time* melalui LCD 16x2 I2C.
5. Menyediakan fitur *manual override* melalui *push button* untuk mematikan alarm secara manual saat situasi ditangani.

---

## ⚙️ Komponen & Perangkat Keras (Hardware)
* **Mikrokontroler:** Arduino Uno R3
* **Sensor Suhu & Kelembapan:** DHT22 (Pin Digital D2)
* **Sensor Api (Flame IR):** Analog Output (Pin A0) & Digital Output (Pin D8)
* **Display:** LCD 16x2 I2C (Modul PCF8574, Pin A4 & A5)
* **Indikator & Alarm:** 
  * LED Merah (Indikator Bahaya/Panas/Api pada Pin D5)
  * LED Hijau (Indikator Aman/Normal pada Pin D6)
  * Buzzer Pasif (Pin D9 dengan PWM)
* **Input Kontrol:** Push Button (Pin D3 dengan internal *pull-up*)

---

## 📊 Klasifikasi Status Sistem
Sistem membagi kondisi lingkungan ke dalam 4 kategori utama berdasarkan pembacaan sensor:
* **NORMAL:** Suhu $<30^\circ\text{C}$, tidak ada api $\rightarrow$ LED Hijau Nyala, Buzzer Mati.
* **HANGAT:** Suhu $30^\circ\text{C} - 39^\circ\text{C}$ $\rightarrow$ LED Hijau Nyala, Buzzer Mati (Waspada ringan).
* **PANAS:** Suhu $\ge 40^\circ\text{C}$ $\rightarrow$ LED Merah Nyala, Buzzer Aktif (Frekuensi 1000 Hz).
* **API:** Terdeteksi nyala api (Flame analog $<300$ atau digital LOW) $\rightarrow$ LED Merah Nyala, Buzzer Aktif (Frekuensi 1200 Hz), LCD menampilkan `"API!"`.

---

## 📂 Struktur Repositori
```text
├── LAPORAN AKHIR MM (1).pdf    # Dokumen laporan resmi lengkap (analisis, skematik, & pengujian)
├── kodeprogram.c               # Kode sumber utama program Arduino (Embedded C)
└── README.md                   # Dokumentasi proyek
