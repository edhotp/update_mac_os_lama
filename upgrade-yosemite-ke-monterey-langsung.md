# Panduan Upgrade macOS Yosemite → Monterey (Jalur Langsung via Installer)
## MacBook Pro Retina 13-inch Early 2015 (A1502 / EMC 2835)

> **Fokus:** Menjalankan installer macOS Monterey langsung dari OS X Yosemite 10.10.5 dengan risiko rendah
>
> **File installer tersedia:** `Install macOS Monterey.app` (12 GB, versi 12.7.6, Build 21H1320)
>
> **Referensi resmi Apple:**
> | Topik | URL |
> |---|---|
> | Cara download dan install macOS | https://support.apple.com/en-us/102662 |
> | Kompatibilitas macOS Monterey | https://support.apple.com/en-us/103260 |
> | Membuat bootable installer macOS | https://support.apple.com/en-us/101578 |
> | Reinstall macOS dari Recovery | https://support.apple.com/en-us/102655 |
> | Start up dari macOS Recovery | https://support.apple.com/en-us/102518 |
> | Error saat install macOS | https://support.apple.com/en-us/102531 |
> | Mac tidak start up | https://support.apple.com/en-us/102675 |

---

## Daftar Isi

1. [Analisis Risiko: Yosemite → Monterey](#1-analisis-risiko-yosemite--monterey)
2. [Strategi Upgrade: 3 Opsi dari Paling Aman](#2-strategi-upgrade-3-opsi-dari-paling-aman)
3. [Persiapan Wajib Sebelum Memulai](#3-persiapan-wajib-sebelum-memulai)
4. [OPSI A: Upgrade Bertahap Yosemite → El Capitan → Monterey (Paling Aman)](#4-opsi-a-upgrade-bertahap-yosemite--el-capitan--monterey-paling-aman)
5. [OPSI B: Langsung via Bootable USB (Aman, Tanpa Upgrade Bertahap)](#5-opsi-b-langsung-via-bootable-usb-aman-tanpa-upgrade-bertahap)
6. [OPSI C: Jalankan Installer Langsung dari Yosemite (Berisiko)](#6-opsi-c-jalankan-installer-langsung-dari-yosemite-berisiko)
7. [Setup Awal macOS Monterey](#7-setup-awal-macos-monterey)
8. [Pasca-Instalasi: Verifikasi dan Optimasi](#8-pasca-instalasi-verifikasi-dan-optimasi)
9. [Troubleshooting Lengkap](#9-troubleshooting-lengkap)
10. [Perbandingan dan Rekomendasi Final](#10-perbandingan-dan-rekomendasi-final)

---

## 1. Analisis Risiko: Yosemite → Monterey

### Mengapa Ini Perlu Perhatian Khusus?

OS X Yosemite (10.10) dirilis tahun 2014, sementara macOS Monterey (12) dirilis tahun 2021. Ini adalah **lompatan 7 generasi macOS**:

```
Yosemite 10.10 (2014)
    ↓
El Capitan 10.11 (2015)
    ↓
Sierra 10.12 (2016)
    ↓
High Sierra 10.13 (2017)  ← perubahan file system ke APFS
    ↓
Mojave 10.14 (2018)       ← akhir support 32-bit
    ↓
Catalina 10.15 (2019)     ← hapus semua 32-bit
    ↓
Big Sur 11 (2020)          ← perubahan besar arsitektur
    ↓
Monterey 12 (2021)        ← TARGET
```

### Perubahan Teknis Penting

| Perubahan | Dampak pada Upgrade |
|---|---|
| **File system: HFS+ → APFS** | Disk akan dikonversi otomatis saat upgrade. Proses ini aman tapi irreversible |
| **Penghapusan dukungan 32-bit** | Aplikasi 32-bit tidak akan berjalan setelah upgrade |
| **Perubahan framework sistem** | Installer Monterey mungkin membutuhkan framework yang tidak ada di Yosemite |
| **Firmware update** | Mac perlu internet untuk update firmware saat upgrade |
| **Security framework** | Sertifikat keamanan di Yosemite sudah expired, bisa menyebabkan error verifikasi |

### Tabel Risiko per Metode

| Metode | Tingkat Risiko | Alasan |
|---|---|---|
| **Opsi A:** Bertahap via El Capitan | 🟢 **Rendah** | Jalur upgrade bertahap yang diuji Apple |
| **Opsi B:** Bootable USB | 🟢 **Rendah** | Installer berjalan di environment sendiri, bypass Yosemite |
| **Opsi C:** Langsung dari Yosemite | 🟡 **Sedang-Tinggi** | Framework Yosemite mungkin tidak support installer Monterey |

---

## 2. Strategi Upgrade: 3 Opsi dari Paling Aman

### Rekomendasi Berdasarkan Situasi

| Situasi Anda | Opsi Terbaik |
|---|---|
| Punya USB 16GB+ dan waktu cukup | **Opsi B** (Bootable USB) |
| Tidak punya USB, Mac bisa online | **Opsi A** (Bertahap via El Capitan) |
| Tidak punya USB, Mac offline, hanya punya installer | **Opsi C** (Langsung) — ikuti mitigasi risiko |
| Mac tidak bisa boot sama sekali | **Opsi B** (Bootable USB) + format disk |

---

## 3. Persiapan Wajib Sebelum Memulai

> ⚠️ **KRITIS:** Langkah ini WAJIB dilakukan sebelum memilih opsi manapun. Jangan lewati.

### 3a. Backup Seluruh Data

**Ini langkah terpenting.** Upgrade besar dari Yosemite ke Monterey melibatkan konversi file system (HFS+ → APFS) yang tidak bisa di-undo.

#### Pilihan Backup:

**Time Machine (Disarankan):**
1. Sambungkan hard disk eksternal ke Mac
2. Buka **Apple (🍎) → System Preferences → Time Machine**
3. Klik **Select Backup Disk** → pilih hard disk eksternal
4. Klik **Back Up Now** dan tunggu selesai
5. **Jangan cabut hard disk** sampai proses selesai 100%

**Copy Manual:**
1. Buka Finder → `Go → Home` (atau tekan `Cmd + Shift + H`)
2. Copy folder-folder berikut ke hard disk eksternal atau USB:
   - `Documents`
   - `Desktop`
   - `Downloads`
   - `Pictures`
   - `Music`
   - `Movies`
   - `Library/Keychains` (password tersimpan)
   - `Library/Mail` (jika pakai Apple Mail)
   - `Library/Safari` (bookmark)

**Cloud:**
- Upload file penting ke Google Drive, Dropbox, atau iCloud
- Pastikan upload selesai sebelum mulai upgrade

### 3b. Catat Informasi Penting

Sebelum upgrade, catat hal berikut di **kertas atau HP** (bukan di Mac):

```
□ Password login Mac: ______________
□ Apple ID (jika ada): ______________
□ Password Wi-Fi: ______________
□ Nama jaringan Wi-Fi: ______________
□ Daftar aplikasi penting yang terinstall
□ Nomor seri Mac (Apple → About This Mac)
```

### 3c. Cek Daftar Aplikasi 32-bit

Aplikasi 32-bit **tidak akan berjalan** setelah upgrade ke Monterey.

Cara cek di Yosemite:
1. Klik **Apple (🍎) → About This Mac → System Report**
2. Di panel kiri: **Software → Applications**
3. Cari kolom **64-Bit (Intel)** — aplikasi yang bertanda **No** tidak akan berjalan

> Catat aplikasi 32-bit yang masih Anda butuhkan. Cari alternatif 64-bit sebelum upgrade.

### 3d. Pastikan Adaptor Daya Tersambung

- **Wajib** sambungkan MagSafe charger
- Baterai minimal **50%** terisi
- **Jangan cabut** adaptor daya selama seluruh proses upgrade

### 3e. Cek Ruang Penyimpanan

Pastikan tersedia **minimal 35 GB** ruang kosong:
1. **Apple (🍎) → About This Mac → Storage**
2. Jika kurang, hapus file tidak penting, kosongkan Trash, hapus cache browser

### 3f. Pastikan Koneksi Internet Aktif

- Semua metode upgrade membutuhkan internet (minimal saat awal install) untuk firmware update
- Gunakan Wi-Fi yang stabil atau Ethernet adapter
- **Sumber:** Apple menyatakan "The installer needs a stable internet connection to download macOS and get firmware and other information specific to your Mac model" — [Apple Support](https://support.apple.com/en-us/102531)

---

## 4. OPSI A: Upgrade Bertahap Yosemite → El Capitan → Monterey (Paling Aman)

> **Tingkat risiko:** 🟢 RENDAH
>
> **Waktu estimasi:** 2-4 jam
>
> **Kebutuhan:** Koneksi internet, tidak perlu USB
>
> **Mengapa paling aman:** El Capitan adalah "batu loncatan" resmi yang direkomendasikan Apple untuk upgrade dari versi lama. Installer Monterey berjalan jauh lebih baik dari El Capitan dibanding dari Yosemite.

### Tahap 1: Upgrade Yosemite → El Capitan (10.11)

#### Langkah 1: Download El Capitan

Apple menyediakan file `.dmg` resmi untuk El Capitan yang bisa didownload langsung dari browser:

**Sumber resmi:** [Apple Support – How to download and install macOS](https://support.apple.com/en-us/102662)

1. Buka **Safari** di Mac yang menjalankan Yosemite
2. Kunjungi URL berikut:
   ```
   http://updates-http.cdn-apple.com/2019/cert/061-41424-20191024-218af9ec-cf50-4516-9011-228c78eda3d2/InstallMacOSX.dmg
   ```
   > Ini adalah link resmi dari Apple Support halaman "How to download and install macOS"
3. File `InstallMacOSX.dmg` (~6 GB) akan mulai didownload ke folder Downloads
4. Tunggu sampai download selesai

#### Langkah 2: Install El Capitan

1. Buka Finder → **Downloads** → double-click file `InstallMacOSX.dmg`
2. Sebuah volume akan muncul — double-click file `InstallMacOSX.pkg` di dalamnya
3. Ikuti instruksi di layar untuk menginstall **installer** El Capitan ke folder Applications
4. Setelah selesai, buka **Finder → Applications** → double-click **Install OS X El Capitan**
5. Klik **Continue** → **Agree** → pilih disk **Macintosh HD** → klik **Install**
6. Masukkan password admin → Mac akan restart
7. Tunggu proses instalasi (15-30 menit, Mac restart beberapa kali)

#### Langkah 3: Verifikasi El Capitan

Setelah Mac boot ke desktop:
1. Klik **Apple (🍎) → About This Mac**
2. Pastikan tertulis **OS X El Capitan Version 10.11.x**
3. Buka **App Store → Updates** dan install semua update El Capitan yang tersedia
4. Pastikan versi akhir **10.11.6** sebelum lanjut

### Tahap 2: Upgrade El Capitan → Monterey

#### Langkah 4: Pindahkan Installer Monterey ke Applications

Installer Monterey yang sudah didownload perlu dipindahkan ke Mac target. Ada beberapa cara:

**Cara A — Transfer via USB/Hard Disk Eksternal:**
1. Copy `Install macOS Monterey.app` dari Mac ini ke USB/hard disk eksternal
2. Colokkan ke MacBook target yang sudah menjalankan El Capitan
3. Copy ke folder `/Applications`:
   ```bash
   sudo cp -R "/Volumes/NamaUSB/Install macOS Monterey.app" /Applications/
   ```

**Cara B — Jika installer sudah ada di Mac target:**
```bash
sudo cp -R "/Users/edhotpurwoko/Documents/myCodes/common/Install macOS Monterey.app" /Applications/
```

**Cara C — Download ulang dari El Capitan:**
1. Buka Safari di El Capitan
2. Kunjungi App Store link: `https://apps.apple.com/us/app/macos-monterey/id1576738294`
3. Klik **Get** → download installer (~12 GB)

#### Langkah 5: Jalankan Installer Monterey

1. Buka **Finder → Applications**
2. Double-click **Install macOS Monterey**
3. Klik **Continue**
4. Klik **Agree** pada License Agreement → **Agree** lagi untuk konfirmasi
5. Pilih disk: **Macintosh HD**
6. Klik **Install**
7. Masukkan password admin saat diminta

#### Langkah 6: Tunggu Proses Instalasi

- Mac akan menyiapkan instalasi (~5-10 menit)
- Mac restart otomatis
- Muncul logo Apple dengan progress bar
- Proses berlangsung **30-60 menit**
- Mac mungkin restart **2-3 kali** — ini normal

> ⚠️ **JANGAN:**
> - Mematikan Mac secara paksa
> - Menutup lid MacBook
> - Mencabut adaptor daya
> - Menekan tombol apapun

#### Langkah 7: Selesai

Mac boot ke macOS Monterey. Lanjut ke [Setup Awal](#7-setup-awal-macos-monterey).

---

## 5. OPSI B: Langsung via Bootable USB (Aman, Tanpa Upgrade Bertahap)

> **Tingkat risiko:** 🟢 RENDAH
>
> **Waktu estimasi:** 1-2 jam
>
> **Kebutuhan:** USB flash drive 16 GB+, koneksi internet saat install
>
> **Mengapa aman:** Installer Monterey pada USB memiliki environment sendiri yang lengkap. Tidak bergantung pada framework Yosemite karena Mac boot langsung dari USB, bukan dari Yosemite.
>
> **Sumber resmi:** [Apple Support – Create a bootable installer for macOS](https://support.apple.com/en-us/101578)

### Langkah 1: Pindahkan Installer ke /Applications

```bash
sudo cp -R "/Users/edhotpurwoko/Documents/myCodes/common/Install macOS Monterey.app" /Applications/
```

### Langkah 2: Siapkan USB Flash Drive

> ⚠️ **Semua data di USB akan dihapus.** Pastikan tidak ada file penting.

1. Colokkan USB flash drive (16 GB+) ke Mac
2. Buka **Disk Utility** (`Cmd + Space` → ketik "Disk Utility")
3. Pilih USB di sidebar kiri (pilih **disk**, bukan partisi)
4. Klik **Erase**:
   - **Name:** `MyVolume`
   - **Format:** `Mac OS Extended (Journaled)`
   - **Scheme:** `GUID Partition Map`
5. Klik **Erase** → tunggu selesai → klik **Done**

### Langkah 3: Buat Bootable Installer

Buka Terminal dan jalankan:

```bash
sudo /Applications/Install\ macOS\ Monterey.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
```

> **Catatan penting dari Apple:** Jika membuat bootable installer pada Mac yang menjalankan macOS Sierra 10.12.6 atau lebih lama (termasuk Yosemite), **tambahkan `--applicationpath`:**
> ```bash
> sudo /Applications/Install\ macOS\ Monterey.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume --applicationpath /Applications/Install\ macOS\ Monterey.app
> ```
> — [Apple Support](https://support.apple.com/en-us/101578)

Saat diminta:
1. Ketik **password admin** (karakter tidak muncul — normal)
2. Ketik **Y** lalu Enter untuk konfirmasi hapus volume

Tunggu 15-30 menit. Output akhir yang diharapkan:
```
Install media now available at "/Volumes/Install macOS Monterey"
```

### Langkah 4: Boot dari USB

MacBook Pro 2015 adalah Intel-based Mac:

1. **Matikan Mac** sepenuhnya (Apple → Shut Down)
2. Pastikan USB **masih terhubung**
3. **Nyalakan Mac** sambil **langsung tahan tombol Option (⌥/Alt)**
4. Tahan sampai muncul **Startup Manager** (layar pilihan disk)
5. Pilih **Install macOS Monterey** (ikon berwarna oranye)
6. Klik **panah** atau tekan **Enter**

> **Apple:** "Your Mac must be connected to the internet so that the installer can get firmware and other information specific to this Mac model." — [Apple Support](https://support.apple.com/en-us/101578)

### Langkah 5: Install Monterey

1. Pilih bahasa → klik panah
2. Pada jendela **macOS Utilities**: pilih **Install macOS Monterey** → klik **Continue**
3. Klik **Continue** → **Agree** → **Agree**
4. Pilih disk: **Macintosh HD**
5. Klik **Install**
6. Tunggu 30-60 menit (Mac restart beberapa kali)

### Langkah 6: Selesai

Cabut USB setelah Mac masuk layar setup. Lanjut ke [Setup Awal](#7-setup-awal-macos-monterey).

---

## 6. OPSI C: Jalankan Installer Langsung dari Yosemite (Berisiko)

> **Tingkat risiko:** 🟡 SEDANG-TINGGI
>
> **Waktu estimasi:** 1-2 jam (jika berhasil)
>
> **Kebutuhan:** Tidak perlu USB, tidak perlu upgrade bertahap
>
> **Mengapa berisiko:** Installer `Install macOS Monterey.app` adalah aplikasi macOS modern yang mungkin membutuhkan framework, library, atau API yang tidak tersedia di Yosemite. Apple tidak secara eksplisit mendokumentasikan dukungan menjalankan installer Monterey dari Yosemite.

### Risiko yang Mungkin Terjadi

| Risiko | Kemungkinan | Dampak | Mitigasi |
|---|---|---|---|
| Installer tidak bisa dibuka | Tinggi | Proses gagal di awal | Coba Opsi A atau B |
| Error "damaged" / sertifikat expired | Sedang | Proses gagal | Perbaiki tanggal sistem |
| Installer crash di tengah jalan | Rendah | Mac stuck, perlu Recovery | Boot ke Recovery Mode |
| Konversi file system gagal | Sangat rendah | Data hilang | Sudah backup di Langkah 3 |

### Langkah Mitigasi Risiko (WAJIB Sebelum Mencoba)

#### Mitigasi 1: Pastikan Backup Sudah Dibuat
- Verifikasi backup di Langkah 3a sudah selesai 100%
- Pastikan bisa mengakses backup dari perangkat lain

#### Mitigasi 2: Siapkan Rencana Cadangan
- Pastikan Anda tahu cara masuk **Recovery Mode** (`⌘ + R` saat startup)
- Pastikan Anda punya akses ke **Internet Recovery** (`⌥ + ⌘ + R` saat startup)
- Jika memungkinkan, siapkan USB flash drive sebagai backup plan (Opsi B)

#### Mitigasi 3: Perbaiki Tanggal dan Waktu Sistem
Sertifikat di Yosemite mungkin sudah expired. Perbaiki tanggal:
1. Buka **Apple (🍎) → System Preferences → Date & Time**
2. Centang **Set date and time automatically**
3. Pastikan menggunakan server `time.apple.com`
4. Jika tidak bisa otomatis, set manual ke tanggal hari ini

Alternatif via Terminal:
```bash
sudo ntpdate -u time.apple.com
```

#### Mitigasi 4: Update Sertifikat Keamanan
Download dan install update sertifikat terbaru untuk Yosemite (jika tersedia):
1. Buka **App Store → Updates**
2. Install semua update yang tersedia
3. Restart Mac setelah update

### Langkah-langkah Instalasi

#### Langkah 1: Pindahkan Installer ke /Applications

```bash
sudo cp -R "/Users/edhotpurwoko/Documents/myCodes/common/Install macOS Monterey.app" /Applications/
```

Verifikasi:
```bash
ls -la "/Applications/Install macOS Monterey.app"
```

#### Langkah 2: Verifikasi Integritas Installer

```bash
# Cek bahwa installer valid
codesign -dv --verbose=4 "/Applications/Install macOS Monterey.app" 2>&1 | head -5
```

Jika output menunjukkan `Authority=Apple` dan tidak ada error, installer valid.

#### Langkah 3: Coba Jalankan Installer

1. Buka **Finder → Applications**
2. Double-click **Install macOS Monterey**

**Kemungkinan hasil:**

| Hasil | Apa yang Terjadi | Langkah Selanjutnya |
|---|---|---|
| ✅ Installer terbuka normal | Jendela installer muncul | Lanjut ke Langkah 4 |
| ❌ "This application requires macOS X.X or later" | OS terlalu lama | Gunakan **Opsi A** atau **Opsi B** |
| ❌ "This copy is damaged" | Sertifikat/tanggal bermasalah | Lihat [Troubleshooting #1](#masalah-1-installer-bilang-damaged-atau-cannot-be-verified) |
| ❌ Installer crash / tidak responsif | Framework tidak kompatibel | Gunakan **Opsi A** atau **Opsi B** |
| ❌ "Cannot be verified" | Sertifikat expired | Perbaiki tanggal, lihat Mitigasi 3 |

#### Langkah 4: Jalankan Instalasi (Jika Installer Berhasil Terbuka)

1. Klik **Continue**
2. Klik **Agree** pada License Agreement → **Agree** lagi
3. Pilih disk: **Macintosh HD**
4. Klik **Install**
5. Masukkan **password admin** saat diminta
6. Mac mulai menyiapkan instalasi (~5-10 menit)
7. Mac restart otomatis

#### Langkah 5: Monitoring Proses Instalasi

Setelah restart:
- Logo Apple muncul dengan progress bar
- Proses memakan waktu **30-90 menit** (lebih lama dari biasa karena lompatan besar)
- Mac mungkin restart **3-4 kali**
- Layar mungkin gelap beberapa menit — **ini normal**
- Proses konversi HFS+ → APFS terjadi otomatis

> ⚠️ **PERINGATAN KRITIS:**
> - **Jangan matikan Mac** selama proses ini
> - **Jangan cabut adaptor daya**
> - **Jangan tutup lid** MacBook
> - Jika progress bar tidak bergerak, **tunggu minimal 2 jam** sebelum mengambil tindakan

#### Langkah 6: Jika Gagal — Rencana Darurat

Jika Mac stuck atau error setelah restart:

**Skenario A: Mac menampilkan error dan kembali ke Yosemite**
- Bagus — Mac Anda aman, data masih ada
- Gunakan **Opsi A** (upgrade via El Capitan) atau **Opsi B** (USB bootable)

**Skenario B: Mac stuck di logo Apple > 2 jam**
1. Tahan tombol **power selama 10 detik** untuk mematikan paksa
2. Nyalakan Mac — biasanya proses akan dilanjutkan
3. Jika tetap stuck, boot ke **Recovery Mode** (`⌘ + R`)
4. Pilih **Reinstall macOS** atau gunakan **Disk Utility** untuk repair disk

**Skenario C: Mac tidak bisa boot sama sekali**
1. Coba **Internet Recovery**: nyalakan sambil tahan `⌥ + ⌘ + R`
2. Mac akan download recovery dari internet
3. Pilih **Reinstall macOS** — akan install macOS terbaru yang kompatibel (Monterey)

**Sumber:** [Apple Support – How to start up from macOS Recovery](https://support.apple.com/en-us/102518)

#### Langkah 7: Selesai

Jika berhasil, Mac boot ke macOS Monterey. Lanjut ke [Setup Awal](#7-setup-awal-macos-monterey).

---

## 7. Setup Awal macOS Monterey

Setelah instalasi berhasil dari opsi manapun:

### Wizard Setup (Langkah demi Langkah)

| No | Layar | Tindakan | Catatan |
|---|---|---|---|
| 1 | **Country or Region** | Pilih **Indonesia** | |
| 2 | **Written and Spoken Languages** | Pilih bahasa | Bisa tambah Bahasa Indonesia |
| 3 | **Accessibility** | Klik **Not Now** | Bisa diatur nanti |
| 4 | **Wi-Fi Network** | Pilih jaringan, masukkan password | **Wajib** untuk aktivasi |
| 5 | **Data & Privacy** | Klik **Continue** | |
| 6 | **Migration Assistant** | Pilih **Not Now** | Kecuali ingin restore dari Time Machine |
| 7 | **Apple ID** | Masukkan Apple ID atau **Set Up Later → Skip** | Tidak wajib |
| 8 | **Terms and Conditions** | **Agree → Agree** | |
| 9 | **Computer Account** | Isi nama dan password baru | Bisa pakai password yang sama dengan sebelumnya |
| 10 | **Location Services** | Sesuai preferensi | |
| 11 | **Time Zone** | Jakarta (WIB) / Makassar (WITA) / Jayapura (WIT) | |
| 12 | **Analytics** | Sesuai preferensi | |
| 13 | **Screen Time** | **Set Up Later** | |
| 14 | **Appearance** | Pilih **Light** / **Dark** / **Auto** | |

> 💡 **Tentang Apple ID:** Mac bisa digunakan tanpa Apple ID. Pilih "Set Up Later" jika belum punya. App Store, iCloud, dan iMessage tidak aktif tanpa Apple ID, tapi semua fungsi dasar Mac tetap berjalan.

---

## 8. Pasca-Instalasi: Verifikasi dan Optimasi

### 8a. Verifikasi Versi macOS

```
Apple (🍎) → About This Mac
```
Harus tertulis: **macOS Monterey Version 12.7.6**

### 8b. Jalankan Software Update

```
Apple (🍎) → System Preferences → Software Update
```
Install semua update yang tersedia.

### 8c. Verifikasi Kesehatan Disk

Buka Disk Utility → pilih Macintosh HD → klik **First Aid → Run**

Pastikan tidak ada error. Jika ada, jalankan First Aid sekali lagi.

### 8d. Reset NVRAM (Disarankan Setelah Upgrade Besar)

Reset NVRAM untuk memastikan parameter hardware optimal setelah upgrade:

1. Matikan Mac
2. Nyalakan sambil langsung tahan **Option + Command + P + R**
3. Tahan selama **~20 detik**
4. Mac akan restart — lepaskan setelah bunyi startup kedua atau logo Apple muncul dan hilang dua kali

### 8e. Reset SMC (MacBook Pro 2015 — Tanpa T2 Chip)

1. Matikan Mac
2. Sambungkan adaptor MagSafe
3. Tahan **Shift (kiri) + Control (kiri) + Option (kiri) + tombol power** bersamaan selama **10 detik**
4. Lepaskan semua tombol
5. Nyalakan Mac seperti biasa

### 8f. Cek Performa

Setelah upgrade besar, Mac mungkin terasa lambat selama **24-48 jam pertama** karena:
- Spotlight sedang mengindeks ulang seluruh disk
- Proses background (mds, mds_stores) sedang berjalan

Ini **normal** dan akan membaik sendiri setelah indexing selesai.

Untuk memonitor:
```bash
# Cek proses yang menggunakan CPU tinggi
top -l 1 -s 0 | head -20
```

---

## 9. Troubleshooting Lengkap

### Masalah 1: Installer Bilang "Damaged" atau "Cannot Be Verified"

**Penyebab:** Tanggal/waktu sistem tidak benar, atau sertifikat keamanan sudah expired.

**Solusi A — Perbaiki tanggal via System Preferences:**
1. **Apple → System Preferences → Date & Time**
2. Centang **Set date and time automatically**
3. Coba jalankan installer lagi

**Solusi B — Perbaiki tanggal via Terminal:**
```bash
# Sync dari NTP server
sudo ntpdate -u time.apple.com

# Atau set manual (format: MMDDhhmmYY)
sudo date 0417120026
```

**Solusi C — Bypass Gatekeeper (jika solusi di atas tidak berhasil):**
```bash
sudo xattr -rd com.apple.quarantine "/Applications/Install macOS Monterey.app"
```

**Sumber:** [Apple Support – If an error occurred while updating or installing macOS](https://support.apple.com/en-us/102531)

### Masalah 2: "This application requires macOS X.X or later"

**Penyebab:** Installer Monterey membutuhkan versi macOS minimum yang lebih tinggi dari Yosemite.

**Solusi:** Ini menandakan Opsi C tidak bisa digunakan. Gunakan:
- **Opsi A** — Upgrade ke El Capitan dulu
- **Opsi B** — Gunakan bootable USB (bypass Yosemite sepenuhnya)

### Masalah 3: Mac Stuck di Logo Apple / Progress Bar

**Solusi bertahap:**
1. **Tunggu minimal 2 jam** — proses mungkin masih berjalan
2. Jika stuck > 2 jam, **tahan power 10 detik** → nyalakan ulang
3. Jika masih stuck:
   - Boot **Safe Mode**: nyalakan sambil tahan **Shift**
   - Jika Safe Mode berhasil, restart normal
4. Jika masih gagal:
   - Boot **Recovery**: nyalakan sambil tahan **⌘ + R**
   - Pilih **Reinstall macOS**
5. Jika Recovery tidak tersedia:
   - Boot **Internet Recovery**: nyalakan sambil tahan **⌥ + ⌘ + R**

**Sumber:** [Apple Support – If your Mac doesn't start up all the way](https://support.apple.com/en-us/102675)

### Masalah 4: Disk Tidak Muncul Saat Install

**Solusi:**
1. Dari installer, buka menu bar: **Utilities → Disk Utility**
2. Pilih disk internal di sidebar
3. Klik **First Aid → Run** (repair terlebih dahulu)
4. Jika tetap tidak muncul, klik **Erase**:
   - Format: **APFS** (atau Mac OS Extended jika APFS tidak tersedia)
   - Scheme: **GUID Partition Map**
5. Tutup Disk Utility → coba install lagi

> ⚠️ Erase akan **menghapus semua data**. Hanya lakukan jika sudah ada backup.

### Masalah 5: USB Bootable Tidak Muncul di Startup Manager

**Solusi:**
- Pastikan USB tercolok **langsung** ke Mac (bukan lewat hub)
- Coba **port USB yang berbeda**
- Pastikan tahan tombol **Option (⌥)** **segera** setelah menekan power
- Buat ulang bootable USB — mungkin proses sebelumnya tidak sempurna

### Masalah 6: Error "An error occurred while preparing the installation"

**Solusi:**
1. Restart Mac dan coba lagi
2. Pastikan koneksi internet stabil
3. Jika error berlanjut, boot ke Recovery Mode dan install dari sana
4. Pastikan disk tidak bermasalah (jalankan First Aid di Disk Utility)

**Sumber:** [Apple Support – If an error occurred while updating or installing macOS](https://support.apple.com/en-us/102531)

### Masalah 7: Ingin Kembali ke Yosemite/El Capitan

**Jika punya Time Machine backup:**
1. Boot ke Recovery Mode (`⌘ + R`)
2. Pilih **Restore from Time Machine Backup**
3. Pilih backup yang dibuat sebelum upgrade
4. Ikuti instruksi di layar

**Jika tidak punya backup:**
- Anda perlu installer Yosemite/El Capitan dan harus **format ulang disk** + install dari nol
- El Capitan tersedia di: https://support.apple.com/en-us/102662

### Masalah 8: Performa Lambat Setelah Upgrade

**Penyebab:** Spotlight indexing (normal, berlangsung 24-48 jam)

**Solusi:**
- Tunggu sampai indexing selesai
- Cek di **System Preferences → Spotlight** — jika ada progress bar, indexing masih berjalan
- Jika masih lambat setelah 48 jam:
  1. Restart Mac
  2. Reset NVRAM (lihat bagian 8d)
  3. Reset SMC (lihat bagian 8e)
  4. Buka **Activity Monitor** untuk cek proses yang menggunakan CPU/RAM tinggi

---

## 10. Perbandingan dan Rekomendasi Final

### Perbandingan Lengkap

| Aspek | Opsi A (Bertahap) | Opsi B (USB Bootable) | Opsi C (Langsung) |
|---|---|---|---|
| **Risiko** | 🟢 Rendah | 🟢 Rendah | 🟡 Sedang-Tinggi |
| **Butuh USB** | Tidak | Ya (16GB+) | Tidak |
| **Butuh internet** | Ya (download El Capitan ~6GB) | Ya (saat install) | Ya (saat install) |
| **Waktu total** | 2-4 jam | 1-2 jam | 1-2 jam (jika berhasil) |
| **Tingkat kemudahan** | Mudah | Sedang | Mudah (jika berhasil) |
| **Butuh upgrade dua kali** | Ya | Tidak | Tidak |
| **Bisa clean install** | Tidak | Ya | Tidak |
| **Bisa pakai ulang** | Tidak | Ya (USB bisa dipakai lagi) | Tidak |
| **Kemungkinan berhasil** | ✅ Sangat tinggi | ✅ Sangat tinggi | ⚠️ Sedang |
| **Jika gagal, dampak** | Kecil, tetap di Yosemite | Kecil, tetap di Yosemite | Kecil-Sedang |

### Rekomendasi Final

```
┌─────────────────────────────────────────────────────┐
│           URUTAN REKOMENDASI (PALING AMAN)          │
│                                                     │
│  1. OPSI B — Bootable USB (jika punya USB 16GB+)   │
│  2. OPSI A — Bertahap via El Capitan                │
│  3. OPSI C — Langsung dari Yosemite (plan terakhir) │
└─────────────────────────────────────────────────────┘
```

**Untuk MacBook Pro Retina 13-inch Early 2015 Anda:**

- Jika punya **USB flash drive 16GB+** → pilih **Opsi B** (paling cepat dan aman)
- Jika **tidak punya USB** → pilih **Opsi A** (upgrade via El Capitan dulu)
- Jika **tidak punya USB DAN tidak ada internet untuk download El Capitan** → coba **Opsi C** dengan semua mitigasi risiko yang sudah disiapkan

---

## Referensi Resmi Apple

| Topik | URL | Terakhir Diperbarui |
|---|---|---|
| Cara download dan install macOS | https://support.apple.com/en-us/102662 | 4 Mar 2026 |
| Kompatibilitas macOS Monterey | https://support.apple.com/en-us/103260 | 5 Jun 2025 |
| Membuat bootable installer macOS | https://support.apple.com/en-us/101578 | 15 Okt 2025 |
| Cara reinstall macOS | https://support.apple.com/en-us/102655 | 19 Feb 2026 |
| Start up dari macOS Recovery | https://support.apple.com/en-us/102518 | 4 Feb 2026 |
| Error saat install macOS | https://support.apple.com/en-us/102531 | 29 Apr 2025 |
| Mac tidak start up | https://support.apple.com/en-us/102675 | — |
| Update macOS di Mac | https://support.apple.com/en-us/108382 | 16 Apr 2026 |

---

> **Catatan:** Tutorial ini dibuat pada 17 April 2026 berdasarkan file installer `Install macOS Monterey.app` versi 12.7.6 (Build 21H1320). Semua referensi merujuk ke sumber resmi Apple Support. Informasi upgrade path didasarkan pada dokumentasi resmi Apple dan pengalaman komunitas.
