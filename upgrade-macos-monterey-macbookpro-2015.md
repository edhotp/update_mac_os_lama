# Panduan Upgrade macOS: Yosemite → Monterey
## MacBook Pro Retina 13-inch Early 2015 (A1502 / EMC 2835)

> **Sumber resmi:** [Apple Support – macOS Monterey Compatibility](https://support.apple.com/en-us/102765)  
> **Versi target:** macOS 12 Monterey (versi resmi tertinggi yang didukung untuk model ini)  
> **Estimasi waktu total:** 3–5 jam (tergantung kecepatan internet dan kondisi perangkat)

---

## Daftar Isi
1. [Periksa Kondisi Perangkat](#1-periksa-kondisi-perangkat)
2. [Bebaskan Ruang Penyimpanan](#2-bebaskan-ruang-penyimpanan)
3. [Buat Cadangan (Backup) Data](#3-buat-cadangan-backup-data)
4. [Isi Daya Baterai](#4-isi-daya-baterai)
5. [Unduh macOS Monterey](#5-unduh-macos-monterey)
6. [Jalankan Instalasi](#6-jalankan-instalasi)
7. [Setelah Instalasi Selesai](#7-setelah-instalasi-selesai)
8. [Hal yang Perlu Diketahui Setelah Upgrade](#8-hal-yang-perlu-diketahui-setelah-upgrade)
9. [Langkah Darurat Jika Ada Masalah](#9-langkah-darurat-jika-ada-masalah)

---

## 1. Periksa Kondisi Perangkat

Sebelum mulai, pastikan perangkat siap untuk proses yang panjang.

### 1a. Cek Ruang Penyimpanan Tersedia
1. Klik logo **Apple (🍎)** di pojok kiri atas layar.
2. Pilih **About This Mac**.
3. Klik tab **Storage**.
4. Pastikan tersedia **minimal 25 GB ruang kosong**.
   - Jika kurang dari 25 GB, lanjutkan ke [Langkah 2](#2-bebaskan-ruang-penyimpanan) terlebih dahulu.

### 1b. Cek Kondisi RAM dan Prosesor
- RAM 8 GB dan prosesor 2.7 GHz Intel Core i5 sudah memenuhi syarat minimum Monterey.
- Tidak ada yang perlu diubah.

### 1c. Catat Versi macOS Saat Ini
- Pastikan Anda saat ini menjalankan **OS X Yosemite 10.10.5**.
- Untuk mengecek: **Apple (🍎) → About This Mac**.

---

## 2. Bebaskan Ruang Penyimpanan

> Lewati langkah ini jika ruang kosong sudah ≥ 25 GB.

### Yang Bisa Dihapus:
- **Sampah (Trash):** Buka Finder → klik kanan ikon Trash di Dock → **Empty Trash**.
- **File unduhan lama:** Buka Finder → **Go → Downloads** → hapus file yang tidak diperlukan.
- **Aplikasi yang tidak dipakai:** Buka **Launchpad** → tahan ikon aplikasi → klik **X** untuk menghapus.
- **Cache browser:** Jika menggunakan Safari, Chrome, atau Firefox, bersihkan cache dari pengaturan browser masing-masing.

---

## 3. Buat Cadangan (Backup) Data

> **Ini adalah langkah terpenting.** Jangan lewati. Backup melindungi semua file Anda jika terjadi hal yang tidak diinginkan selama instalasi.

### Pilihan A: Time Machine (Disarankan untuk Pemula)

**Yang Anda butuhkan:** Hard disk eksternal dengan kapasitas minimal sama dengan isi Mac Anda.

1. Sambungkan hard disk eksternal ke Mac.
2. Klik logo **Apple (🍎) → System Preferences → Time Machine**.
3. Klik **Select Backup Disk**.
4. Pilih hard disk eksternal Anda → klik **Use Disk**.
5. Klik **Back Up Now** dan tunggu hingga selesai.
6. Setelah selesai, indikator Time Machine akan menampilkan waktu backup terakhir.

### Pilihan B: Salin Manual ke Hard Disk Eksternal

Jika tidak punya hard disk eksternal, salin file-file penting ke:
- **Flash drive / USB** yang cukup besar, atau
- **Google Drive / iCloud / Dropbox** (pastikan file sudah terunggah sebelum mulai upgrade)

**File yang wajib disalin:**
- Folder Documents, Desktop, Downloads, Pictures, Music
- Kontak, Kalender (jika belum di iCloud)
- Password penting (catat manual di tempat aman)

---

## 4. Isi Daya Baterai

- Sambungkan adaptor daya ke Mac.
- Pastikan baterai terisi **minimal 50%** sebelum mulai, atau biarkan tersambung ke listrik selama proses berlangsung.
- **Jangan cabut adaptor** selama proses instalasi berlangsung.

---

## 5. Unduh macOS Monterey

> macOS Yosemite terlalu lama untuk langsung lompat ke Monterey melalui App Store biasa. Ikuti langkah berikut dengan tepat.

### 5a. Unduh macOS El Capitan Dulu (Batu Loncatan)

Karena Yosemite sudah sangat lama, App Store di Yosemite mungkin tidak bisa langsung mengunduh Monterey. Kita perlu upgrade bertahap atau menggunakan link langsung.

**Cara termudah – Gunakan link langsung dari Apple:**

1. Buka **Safari**.
2. Buka link unduhan resmi Apple untuk macOS Monterey:  
   `https://apps.apple.com/us/app/macos-monterey/id1576738294`
3. Jika App Store terbuka dan menunjukkan tombol **Download** atau **Get**, klik tombol tersebut.
4. Jika muncul pesan bahwa versi macOS Anda terlalu lama, ikuti langkah alternatif di bawah.

### 5b. Jika Link Di Atas Tidak Berhasil – Upgrade Bertahap

Anda perlu upgrade dua kali:

**Tahap 1: Yosemite → El Capitan (10.11)**
1. Buka Safari, kunjungi:  
   `https://support.apple.com/en-us/100100`
2. Scroll ke bawah, cari **macOS El Capitan** dan klik tombol unduhan.
3. Install El Capitan terlebih dahulu, tunggu sampai selesai dan Mac restart.

**Tahap 2: El Capitan → Monterey**
1. Setelah masuk ke El Capitan, ulangi langkah 5a.
2. Unduh dan install macOS Monterey.

---

## 6. Jalankan Instalasi

1. Setelah file installer selesai diunduh, akan muncul jendela instalasi otomatis.
   - Jika tidak muncul otomatis: buka **Launchpad → Install macOS Monterey**.
2. Klik **Continue**.
3. Baca dan klik **Agree** pada halaman lisensi.
4. Pilih disk tempat instalasi (biasanya sudah otomatis memilih disk utama Mac Anda).
5. Klik **Install**.
6. Masukkan password admin Mac Anda jika diminta.
7. Mac akan **restart sendiri** dan proses instalasi dimulai.

> ⚠️ **Penting:** Mac akan restart beberapa kali selama proses ini. Ini **normal**. Jangan matikan Mac secara paksa. Biarkan prosesnya selesai sendiri.

### Berapa Lama?
- Proses unduhan: 30–90 menit (tergantung kecepatan internet)
- Proses instalasi setelah restart: 30–60 menit
- Mac akan menampilkan loading bar dan persentase progres

---

## 7. Setelah Instalasi Selesai

Setelah Mac restart dan masuk ke tampilan baru, Anda akan diminta beberapa hal:

1. **Pilih bahasa** → pilih Bahasa Indonesia atau English sesuai preferensi.
2. **Sign in dengan Apple ID** → masukkan Apple ID Anda, atau pilih **Set Up Later** jika belum punya.
3. **Privacy settings** → ikuti panduan layar, klik Continue di setiap halaman.
4. **Time Zone** → pilih zona waktu Anda (misal: WIB / Jakarta).
5. **Transfer data** → pilih **Don't Transfer** jika tidak ingin memindahkan data lama. Pilih **From a Time Machine backup** jika Anda ingin memulihkan dari backup.

Setelah itu Anda akan masuk ke desktop macOS Monterey.

---

## 8. Hal yang Perlu Diketahui Setelah Upgrade

### Yang Berubah:
| Aspek | Yosemite (10.10) | Monterey (12) |
|---|---|---|
| Tampilan antarmuka | Flat, terang | Lebih modern, mendukung dark mode |
| Keamanan | Tidak menerima update keamanan | Mendapat update keamanan |
| Safari | Versi lama | Versi terbaru, lebih cepat |
| iMessage & FaceTime | Terbatas | Fitur lengkap |
| AirPlay | Terbatas | SharePlay tersedia |
| Notifikasi | Sederhana | Lebih terorganisir |

### Aplikasi yang Mungkin Tidak Kompatibel:
- Aplikasi 32-bit **tidak bisa berjalan** di Monterey. Mulai macOS Catalina, Apple sudah menghapus dukungan 32-bit.
- Untuk mengecek aplikasi 32-bit di Mac Anda sebelum upgrade:
  1. Klik **Apple (🍎) → About This Mac → System Report**.
  2. Di panel kiri, klik **Software → Applications**.
  3. Cari kolom "64-Bit" yang bertanda **No** — itu adalah aplikasi yang tidak akan berjalan setelah upgrade.

### Update Setelah Masuk Monterey:
1. Klik **Apple (🍎) → System Preferences → Software Update**.
2. Install semua update yang tersedia agar Anda mendapatkan versi Monterey terbaru (12.7.x).

---

## 9. Langkah Darurat Jika Ada Masalah

### Masalah: Mac Tidak Bisa Boot Setelah Instalasi
1. Tahan tombol **Command (⌘) + R** saat Mac dinyalakan hingga muncul logo Apple.
2. Pilih **Reinstall macOS** dari macOS Recovery.
3. Ikuti panduan di layar.

### Masalah: Instalasi Terhenti di Tengah Jalan
1. Tunggu minimal 1 jam — kadang proses instalasi memang tampak berhenti tapi masih berjalan.
2. Jika benar-benar stuck (lebih dari 2 jam tanpa perubahan), restart Mac dengan menahan tombol power selama 5 detik.
3. Mac akan mencoba melanjutkan instalasi secara otomatis.

### Masalah: File Hilang Setelah Upgrade
1. Cek folder **Documents, Desktop, Downloads** — biasanya file masih ada di sini.
2. Cek **Trash** — kadang file dipindahkan ke sana.
3. Jika sudah membuat Time Machine backup, pulihkan data melalui **Time Machine** dari Finder.

### Masalah: Ingin Kembali ke Yosemite
Sangat disarankan **tidak** kembali ke Yosemite karena tidak mendapatkan update keamanan sejak 2017. Namun jika benar-benar perlu:
1. Anda harus memformat ulang Mac dan reinstall dari zero menggunakan installer Yosemite yang sudah didownload sebelumnya, atau dari Time Machine backup Yosemite.

---

## Ringkasan Langkah Cepat

```
[1] Cek ruang penyimpanan ≥ 25 GB
[2] Backup data ke Time Machine atau hard disk eksternal
[3] Sambungkan adaptor daya
[4] Unduh macOS Monterey dari App Store atau link resmi Apple
[5] Jalankan installer → Continue → Agree → Install
[6] Tunggu Mac restart (beberapa kali) – jangan dimatikan
[7] Selesai setup awal Monterey
[8] Jalankan Software Update untuk update terakhir
```

---

## Referensi Resmi Apple

| Halaman | URL |
|---|---|
| Kompatibilitas macOS Monterey | https://support.apple.com/en-us/102765 |
| Spesifikasi MacBook Pro Early 2015 | https://support.apple.com/en-us/111959 |
| Cara upgrade ke macOS terbaru | https://support.apple.com/en-us/105113 |
| Cara membuat backup Time Machine | https://support.apple.com/en-us/104984 |
| macOS Recovery (jika ada masalah) | https://support.apple.com/en-us/102603 |

---

> **Catatan:** macOS Monterey adalah versi **resmi tertinggi** yang didukung Apple untuk MacBook Pro Retina 13-inch Early 2015. Versi di atasnya (Ventura, Sonoma, Sequoia) tidak dapat diinstall secara resmi pada model ini.
