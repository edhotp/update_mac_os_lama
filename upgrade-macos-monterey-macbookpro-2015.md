# Panduan Upgrade macOS: Yosemite → Monterey (Bertahap & Aman)
## MacBook Pro Retina 13-inch Early 2015 (A1502 / EMC 2835)

> **Metode:** Upgrade bertahap (Yosemite → El Capitan → Monterey) — jalur paling aman  
> **Versi target:** macOS 12 Monterey 12.7.6 (versi resmi tertinggi yang didukung untuk model ini)  
> **Estimasi waktu total:** 2–4 jam (tergantung kecepatan perangkat)
>
> **Sumber resmi Apple:**
> | Topik | URL |
> |---|---|
> | Kompatibilitas macOS Monterey | https://support.apple.com/en-us/103260 |
> | Cara download dan install macOS | https://support.apple.com/en-us/102662 |
> | Membuat bootable installer macOS | https://support.apple.com/en-us/101578 |
> | Start up dari macOS Recovery | https://support.apple.com/en-us/102518 |
> | Error saat install macOS | https://support.apple.com/en-us/102531 |
> | Cara reinstall macOS | https://support.apple.com/en-us/102655 |
>
> **File installer yang sudah tersedia (offline):**
> | File | Ukuran | Lokasi |
> |---|---|---|
> | `InstallMacOSX.dmg` (El Capitan 10.11) | 5.8 GB | `el-capitan-installer/` |
> | `Install macOS Monterey.app` (12.7.6) | 12 GB | root folder |

---

## Mengapa Harus Bertahap?

OS X Yosemite (10.10, tahun 2014) dan macOS Monterey (12, tahun 2021) terpisah **7 generasi**. Lompatan langsung berisiko karena:

1. **Framework tidak kompatibel** — Installer Monterey adalah aplikasi modern yang mungkin tidak bisa berjalan di Yosemite
2. **Sertifikat keamanan expired** — Yosemite tidak lagi menerima update sertifikat dari Apple sejak 2017
3. **Perubahan file system** — Upgrade melewati konversi HFS+ → APFS (terjadi di era High Sierra 10.13)

**Jalur upgrade bertahap yang aman:**
```
Yosemite 10.10 ──→ El Capitan 10.11 ──→ Monterey 12.7.6
                   (batu loncatan)        (tujuan akhir)
```

El Capitan adalah "batu loncatan" resmi yang disediakan Apple untuk upgrade dari versi-versi lama.  
**Sumber:** [Apple Support – How to download and install macOS](https://support.apple.com/en-us/102662)

---

## Daftar Isi

1. [Periksa Kondisi Perangkat](#1-periksa-kondisi-perangkat)
2. [Bebaskan Ruang Penyimpanan](#2-bebaskan-ruang-penyimpanan)
3. [Buat Cadangan (Backup) Data](#3-buat-cadangan-backup-data)
4. [Isi Daya Baterai dan Persiapan Terakhir](#4-isi-daya-baterai-dan-persiapan-terakhir)
5. [TAHAP 1: Upgrade Yosemite → El Capitan](#5-tahap-1-upgrade-yosemite--el-capitan)
6. [TAHAP 2: Upgrade El Capitan → Monterey](#6-tahap-2-upgrade-el-capitan--monterey)
7. [Metode Alternatif: Bootable USB (Jika Bertahap Gagal)](#7-metode-alternatif-bootable-usb-jika-bertahap-gagal)
8. [Setup Awal macOS Monterey](#8-setup-awal-macos-monterey)
9. [Pasca-Instalasi: Verifikasi dan Optimasi](#9-pasca-instalasi-verifikasi-dan-optimasi)
10. [Hal yang Perlu Diketahui Setelah Upgrade](#10-hal-yang-perlu-diketahui-setelah-upgrade)
11. [Troubleshooting Lengkap](#11-troubleshooting-lengkap)

---

## 1. Periksa Kondisi Perangkat

Sebelum mulai, pastikan perangkat siap untuk proses yang panjang.

### 1a. Cek Ruang Penyimpanan Tersedia
1. Klik logo **Apple (🍎)** di pojok kiri atas layar.
2. Pilih **About This Mac**.
3. Klik tab **Storage**.
4. Pastikan tersedia **minimal 35 GB ruang kosong**.
   - ~6 GB untuk installer El Capitan
   - ~12 GB untuk installer Monterey
   - ~15 GB untuk proses instalasi dan file sistem baru
   - ~2 GB ruang cadangan
   - Jika kurang dari 35 GB, lanjutkan ke [Langkah 2](#2-bebaskan-ruang-penyimpanan) terlebih dahulu.

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

## 4. Isi Daya Baterai dan Persiapan Terakhir

- Sambungkan adaptor daya (MagSafe) ke Mac.
- Pastikan baterai terisi **minimal 50%** sebelum mulai, atau biarkan tersambung ke listrik selama proses berlangsung.
- **Jangan cabut adaptor** selama proses instalasi berlangsung.

### Catat Informasi Penting di Kertas/HP

Sebelum mulai upgrade, catat hal berikut di **kertas atau HP** (bukan di Mac):

```
□ Password login Mac: ______________
□ Apple ID (jika ada): ______________
□ Password Wi-Fi: ______________
□ Nama jaringan Wi-Fi: ______________
```

### Cek Daftar Aplikasi 32-bit

Aplikasi 32-bit **tidak akan berjalan** setelah upgrade ke Monterey (sejak macOS Catalina, Apple menghapus dukungan 32-bit).

Cara cek di Yosemite:
1. Klik **Apple (🍎) → About This Mac → System Report**
2. Di panel kiri: **Software → Applications**
3. Cari kolom **64-Bit (Intel)** — aplikasi bertanda **No** tidak akan berjalan setelah upgrade

> Catat aplikasi 32-bit yang masih dibutuhkan. Cari alternatif 64-bit sebelum upgrade.

### Transfer File Installer ke Media Penyimpanan

File installer sudah tersedia secara offline di repo ini. Transfer ke **USB flash drive** atau **hard disk eksternal** untuk dibawa ke MacBook target:

| File | Ukuran | Lokasi di Repo |
|---|---|---|
| `InstallMacOSX.dmg` | 5.8 GB | `el-capitan-installer/InstallMacOSX.dmg` |
| `Install macOS Monterey.app` | 12 GB | `Install macOS Monterey.app` |

> **Sumber file:**
> - El Capitan: Link resmi Apple CDN — [Apple Support](https://support.apple.com/en-us/102662)
> - Monterey: Didownload via `mist-cli` dari Apple Software Update catalog

---

## 5. TAHAP 1: Upgrade Yosemite → El Capitan

> **Estimasi waktu:** 30–60 menit
>
> El Capitan (10.11) adalah "batu loncatan" resmi Apple untuk upgrade dari macOS versi lama. Apple menyediakan file `.dmg` langsung untuk El Capitan di halaman [How to download and install macOS](https://support.apple.com/en-us/102662).

### 5a. Siapkan File Installer El Capitan

Jika file `InstallMacOSX.dmg` sudah ada di USB/hard disk eksternal:
1. Colokkan USB/hard disk ke MacBook target
2. Copy file `InstallMacOSX.dmg` ke folder **Downloads** di Mac

Jika **belum punya file** dan Mac bisa online, download langsung dari Safari:
```
http://updates-http.cdn-apple.com/2019/cert/061-41424-20191024-218af9ec-cf50-4516-9011-228c78eda3d2/InstallMacOSX.dmg
```
> Ini adalah link resmi dari halaman [Apple Support – How to download and install macOS](https://support.apple.com/en-us/102662), bagian "Use a web browser for older versions".

### 5b. Buka dan Install El Capitan

1. **Double-click** file `InstallMacOSX.dmg` di Finder
   - Sebuah volume baru akan muncul (mounted disk image)
2. Di dalam volume tersebut, **double-click** file `InstallMacOSX.pkg`
3. Installer package akan terbuka — ikuti instruksi di layar:
   - Klik **Continue**
   - Klik **Agree** pada License Agreement
   - Klik **Install**
   - Masukkan **password admin** saat diminta
4. Proses ini akan meng-install **installer El Capitan** ke folder `/Applications`
   - Hasilnya: file `Install OS X El Capitan.app` akan muncul di folder Applications

> **Referensi Apple:** "Double-click the .dmg file to open it and see the package (.pkg) file within. Double-click the .pkg file, then follow the onscreen instructions to install the macOS installer into the Applications folder." — [Apple Support](https://support.apple.com/en-us/102662)

### 5c. Jalankan Installer El Capitan

1. Buka **Finder → Applications** (atau tekan `Cmd + Shift + A`)
2. Double-click **Install OS X El Capitan**
3. Jendela installer akan terbuka
4. Klik **Continue**
5. Klik **Agree** pada License Agreement → **Agree** lagi pada popup konfirmasi
6. Pilih disk tujuan: **Macintosh HD** (biasanya sudah terpilih otomatis)
7. Klik **Install**
8. Masukkan **password admin** saat diminta
9. Mac akan mulai menyiapkan instalasi, lalu **restart otomatis**

### 5d. Tunggu Proses Instalasi El Capitan

- Setelah restart, muncul **logo Apple dengan progress bar**
- Proses memakan waktu **15–30 menit**
- Mac mungkin restart **1–2 kali** — ini **normal**
- Layar mungkin gelap beberapa saat — **jangan matikan Mac**

> ⚠️ **JANGAN:**
> - Mematikan Mac secara paksa
> - Menutup lid MacBook
> - Mencabut adaptor daya
> - Menekan tombol apapun

### 5e. Verifikasi El Capitan Berhasil

Setelah Mac boot ke desktop:
1. Klik **Apple (🍎) → About This Mac**
2. Pastikan tertulis **OS X El Capitan Version 10.11.x**
3. **Update El Capitan ke versi terbaru:**
   - Buka **App Store → Updates**
   - Install **semua** update yang tersedia
   - Restart jika diminta
   - Ulangi sampai tidak ada update lagi
   - Pastikan versi akhir **10.11.6**

> 💡 **Penting:** Update ke 10.11.6 memastikan semua framework, sertifikat keamanan, dan driver terbaru tersedia sebelum lanjut ke Monterey. Jangan lewati langkah ini.

### 5f. (Opsional) Bersihkan Installer El Capitan

Setelah berhasil upgrade, hapus installer untuk membebaskan ruang (~6 GB):
1. Buka **Finder → Applications**
2. Cari **Install OS X El Capitan** → klik kanan → **Move to Trash**
3. Kosongkan Trash

---

## 6. TAHAP 2: Upgrade El Capitan → Monterey

> **Estimasi waktu:** 45–90 menit
>
> Sekarang Mac sudah menjalankan El Capitan (10.11.6), installer Monterey akan berjalan jauh lebih baik karena framework dan sertifikat keamanan sudah lebih baru.

### 6a. Pindahkan Installer Monterey ke Mac

**Jika file `Install macOS Monterey.app` ada di USB/hard disk eksternal:**
1. Colokkan USB/hard disk ke Mac
2. Buka Finder → navigasi ke USB
3. **Copy** folder `Install macOS Monterey.app` ke folder **Applications**:
   - Drag & drop ke Applications di sidebar Finder, atau
   - Via Terminal:
     ```bash
     sudo cp -R "/Volumes/NamaUSB/Install macOS Monterey.app" /Applications/
     ```

**Jika file ada di lokasi lain di Mac:**
```bash
sudo cp -R "/path/ke/Install macOS Monterey.app" /Applications/
```

**Verifikasi:**
```bash
ls -la "/Applications/Install macOS Monterey.app"
```
Harus muncul folder `Install macOS Monterey.app`.

### 6b. Perbaiki Tanggal/Waktu Sistem (Pencegahan Error)

Sebelum menjalankan installer, pastikan tanggal dan waktu benar untuk menghindari error sertifikat:

1. Buka **Apple (🍎) → System Preferences → Date & Time**
2. Klik ikon gembok di kiri bawah → masukkan password
3. Centang **Set date and time automatically**
4. Pastikan server: `time.apple.com`

Jika tidak bisa otomatis, set manual via Terminal:
```bash
sudo ntpdate -u time.apple.com
```

### 6c. Jalankan Installer Monterey

1. Buka **Finder → Applications** (atau tekan `Cmd + Shift + A`)
2. Double-click **Install macOS Monterey**
3. Jendela installer akan terbuka

   > Jika muncul error "damaged" atau "cannot be verified", lihat [Troubleshooting #1](#masalah-1-installer-bilang-damaged-atau-cannot-be-verified).

4. Klik **Continue**
5. Klik **Agree** pada Software License Agreement → **Agree** lagi
6. Pilih disk tujuan: **Macintosh HD**
7. Klik **Install**
8. Masukkan **password admin** saat diminta

### 6d. Tunggu Proses Instalasi Monterey

- Mac menyiapkan instalasi (~5–10 menit)
- Mac **restart otomatis**
- Muncul logo Apple dengan progress bar
- Proses memakan waktu **30–60 menit**
- Mac mungkin restart **2–3 kali**
- Disk akan dikonversi otomatis dari **HFS+ → APFS** (aman dan otomatis)

> ⚠️ **PENTING:**
> - Mac akan restart beberapa kali — ini **normal**
> - Layar mungkin gelap beberapa menit — **normal**
> - **Jangan** matikan Mac, tutup lid, atau cabut charger
> - Jika progress bar tidak bergerak, **tunggu minimal 2 jam** sebelum bertindak

### 6e. Selesai!

Setelah proses selesai, Mac akan boot ke layar setup macOS Monterey.
Lanjut ke [Setup Awal macOS Monterey](#8-setup-awal-macos-monterey).

---

## 7. Metode Alternatif: Bootable USB (Jika Bertahap Gagal)

> Gunakan metode ini jika:
> - Installer Monterey tidak bisa dibuka dari El Capitan
> - Instalasi gagal di tengah jalan
> - Mac tidak bisa boot ke OS apapun
>
> **Sumber resmi:** [Apple Support – Create a bootable installer for macOS](https://support.apple.com/en-us/101578)

### Yang Dibutuhkan
- USB flash drive **16 GB** atau lebih
- File `Install macOS Monterey.app` sudah ada di `/Applications`

### Langkah 1: Format USB Flash Drive

1. Colokkan USB ke Mac
2. Buka **Disk Utility** (`Cmd + Space` → ketik "Disk Utility")
3. Pilih USB di sidebar kiri (pilih **disk**, bukan partisi)
4. Klik **Erase**:
   - **Name:** `MyVolume`
   - **Format:** `Mac OS Extended (Journaled)`
   - **Scheme:** `GUID Partition Map`
5. Klik **Erase** → tunggu selesai

### Langkah 2: Buat Bootable Installer

Buka Terminal dan jalankan:

```bash
sudo /Applications/Install\ macOS\ Monterey.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
```

> **Catatan Apple:** Jika Mac menjalankan macOS Sierra 10.12.6 atau lebih lama (termasuk El Capitan), tambahkan `--applicationpath`:
> ```bash
> sudo /Applications/Install\ macOS\ Monterey.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume --applicationpath /Applications/Install\ macOS\ Monterey.app
> ```
> — [Apple Support](https://support.apple.com/en-us/101578)

Saat diminta:
1. Ketik **password admin** (karakter tidak muncul di layar — normal)
2. Ketik **Y** lalu Enter untuk konfirmasi

Tunggu **15–30 menit**. Selesai saat muncul:
```
Install media now available at "/Volumes/Install macOS Monterey"
```

### Langkah 3: Boot dari USB

MacBook Pro 2015 adalah Intel-based Mac:

1. **Matikan Mac** sepenuhnya (Apple → Shut Down)
2. Pastikan USB **terhubung** ke Mac
3. **Nyalakan Mac** sambil **segera tahan tombol Option (⌥/Alt)**
4. Tahan sampai muncul **Startup Manager** (layar pilihan disk boot)
5. Pilih **Install macOS Monterey** (ikon berwarna oranye)
6. Klik panah atau tekan **Enter**

> **Apple:** "Your Mac must be connected to the internet so that the installer can get firmware and other information specific to this Mac model." — [Apple Support](https://support.apple.com/en-us/101578)

### Langkah 4: Install dari USB

1. Pilih bahasa → klik panah
2. Pada jendela **macOS Utilities**: pilih **Install macOS Monterey** → **Continue**
3. **Continue** → **Agree** → **Agree**
4. Pilih disk: **Macintosh HD**
5. Klik **Install**
6. Tunggu 30–60 menit (Mac restart beberapa kali)

Setelah selesai, cabut USB. Lanjut ke [Setup Awal](#8-setup-awal-macos-monterey).

---

## 8. Setup Awal macOS Monterey

Setelah instalasi berhasil, Anda akan melewati setup wizard:

| No | Layar | Tindakan | Catatan |
|---|---|---|---|
| 1 | **Country or Region** | Pilih **Indonesia** | |
| 2 | **Written and Spoken Languages** | Pilih bahasa | Bisa tambah Bahasa Indonesia |
| 3 | **Accessibility** | Klik **Not Now** | Bisa diatur nanti |
| 4 | **Wi-Fi Network** | Pilih jaringan, masukkan password | **Wajib** untuk aktivasi |
| 5 | **Data & Privacy** | Klik **Continue** | |
| 6 | **Migration Assistant** | **Not Now** | Kecuali ingin restore dari Time Machine |
| 7 | **Apple ID** | Masukkan Apple ID atau **Set Up Later → Skip** | Tidak wajib |
| 8 | **Terms and Conditions** | **Agree → Agree** | |
| 9 | **Computer Account** | Isi nama dan password | Bisa pakai password lama |
| 10 | **Location Services** | Sesuai preferensi | |
| 11 | **Time Zone** | Jakarta (WIB) / Makassar (WITA) / Jayapura (WIT) | |
| 12 | **Analytics** | Sesuai preferensi, klik **Continue** | |
| 13 | **Screen Time** | **Set Up Later** | |
| 14 | **Appearance** | Pilih **Light** / **Dark** / **Auto** | |

> 💡 Mac bisa digunakan **tanpa Apple ID**. Pilih "Set Up Later" jika belum punya. App Store, iCloud, dan iMessage tidak aktif tanpa Apple ID, tapi semua fungsi dasar Mac tetap berjalan normal.

---

## 9. Pasca-Instalasi: Verifikasi dan Optimasi

### 9a. Verifikasi Versi macOS
1. Klik **Apple (🍎) → About This Mac**
2. Pastikan tertulis **macOS Monterey Version 12.7.6**

### 9b. Jalankan Software Update
1. **Apple (🍎) → System Preferences → Software Update**
2. Install **semua** update yang tersedia
3. Restart jika diminta
4. Ulangi sampai "Your Mac is up to date"

### 9c. Verifikasi Kesehatan Disk
1. Buka **Disk Utility** (Finder → Applications → Utilities → Disk Utility)
2. Pilih **Macintosh HD** di sidebar
3. Klik **First Aid → Run**
4. Pastikan tidak ada error

### 9d. Reset NVRAM (Disarankan Setelah Upgrade Besar)
1. Matikan Mac
2. Nyalakan sambil langsung tahan **Option + Command + P + R**
3. Tahan selama **~20 detik**
4. Lepaskan setelah bunyi startup kedua atau logo Apple muncul dan hilang dua kali

### 9e. Reset SMC (MacBook Pro 2015 — Tanpa T2 Chip)
1. Matikan Mac
2. Sambungkan adaptor MagSafe
3. Tahan **Shift (kiri) + Control (kiri) + Option (kiri) + tombol power** bersamaan selama **10 detik**
4. Lepaskan semua tombol
5. Nyalakan Mac seperti biasa

### 9f. Tunggu Spotlight Indexing

Setelah upgrade besar, Mac mungkin terasa lambat selama **24–48 jam pertama** karena Spotlight mengindeks ulang seluruh disk. Ini **normal** dan akan membaik sendiri.

---

## 10. Hal yang Perlu Diketahui Setelah Upgrade

### Yang Berubah:
| Aspek | Yosemite (10.10) | Monterey (12) |
|---|---|---|
| Tampilan antarmuka | Flat, terang | Lebih modern, mendukung dark mode |
| Keamanan | Tidak menerima update keamanan sejak 2017 | Mendapat update keamanan aktif |
| Safari | Versi lama, banyak situs tidak support | Versi terbaru, lebih cepat & aman |
| File System | HFS+ | APFS (lebih cepat, lebih aman) |
| iMessage & FaceTime | Terbatas | Fitur lengkap, SharePlay |
| AirPlay | Terbatas | AirPlay to Mac tersedia |
| Notifikasi | Sederhana | Focus mode, terorganisir |
| Shortcuts | Tidak ada | Tersedia |
| Aplikasi 32-bit | Didukung | **Tidak didukung** |

### Aplikasi yang Mungkin Tidak Kompatibel:
- Aplikasi 32-bit **tidak bisa berjalan** di Monterey. Mulai macOS Catalina (10.15), Apple sudah menghapus dukungan 32-bit.
- Untuk mengecek aplikasi 32-bit di Mac Anda (sebaiknya dicek **sebelum** upgrade):
  1. Klik **Apple (🍎) → About This Mac → System Report**.
  2. Di panel kiri, klik **Software → Applications**.
  3. Cari kolom "64-Bit" yang bertanda **No** — itu adalah aplikasi yang tidak akan berjalan setelah upgrade.

---

## 11. Troubleshooting Lengkap

### Masalah 1: Installer Bilang "Damaged" atau "Cannot Be Verified"

**Penyebab:** Tanggal/waktu sistem tidak benar, atau sertifikat keamanan expired.

**Solusi A — Perbaiki tanggal:**
1. **Apple → System Preferences → Date & Time**
2. Centang **Set date and time automatically**

**Solusi B — Via Terminal:**
```bash
sudo ntpdate -u time.apple.com
# Atau set manual (format MMDDhhmmYY):
sudo date 0417120026
```

**Solusi C — Hapus quarantine flag:**
```bash
sudo xattr -rd com.apple.quarantine "/Applications/Install macOS Monterey.app"
```

**Sumber:** [Apple Support – If an error occurred while updating or installing macOS](https://support.apple.com/en-us/102531)

### Masalah 2: Mac Tidak Bisa Boot Setelah Instalasi

1. Tahan tombol **Command (⌘) + R** saat Mac dinyalakan → masuk **macOS Recovery**
2. Pilih **Reinstall macOS** dari daftar utilitas
3. Ikuti panduan di layar

Jika Recovery lokal tidak tersedia:
- Gunakan **Internet Recovery**: nyalakan sambil tahan **⌥ + ⌘ + R**
- Mac akan download recovery dari internet dan install macOS terbaru yang kompatibel

**Sumber:** [Apple Support – How to start up from macOS Recovery](https://support.apple.com/en-us/102518)

### Masalah 3: Instalasi Terhenti / Stuck di Progress Bar

1. **Tunggu minimal 2 jam** — proses mungkin masih berjalan di background
2. Jika benar-benar stuck (>2 jam tanpa perubahan):
   - Tahan tombol **power selama 10 detik** untuk mematikan paksa
   - Nyalakan kembali — Mac biasanya melanjutkan instalasi otomatis
3. Jika masih gagal:
   - Boot **Safe Mode**: nyalakan sambil tahan **tombol Shift**
   - Boot **Recovery**: nyalakan sambil tahan **⌘ + R**
   - Pilih **Reinstall macOS**

**Sumber:** [Apple Support – If your Mac doesn't start up all the way](https://support.apple.com/en-us/102675)

### Masalah 4: Disk Tidak Muncul Saat Install

1. Dari installer, buka menu: **Utilities → Disk Utility**
2. Pilih disk internal → klik **First Aid → Run**
3. Jika tetap tidak muncul, klik **Erase**:
   - Format: **APFS** (atau Mac OS Extended jika APFS tidak tersedia)
   - Scheme: **GUID Partition Map**
4. Tutup Disk Utility → coba install lagi

> ⚠️ Erase menghapus semua data. Hanya lakukan jika sudah backup.

### Masalah 5: File Hilang Setelah Upgrade

1. Cek folder **Documents, Desktop, Downloads** — biasanya file masih ada
2. Cek **Trash** — file kadang dipindahkan ke sana
3. Jika sudah membuat Time Machine backup, pulihkan via **Time Machine** dari Finder

### Masalah 6: USB Bootable Tidak Muncul di Startup Manager

- Pastikan USB tercolok **langsung** ke Mac (bukan lewat hub)
- Coba **port USB yang berbeda**
- Pastikan tahan **Option (⌥)** segera setelah menekan power
- Buat ulang bootable installer jika perlu

### Masalah 7: Performa Lambat Setelah Upgrade

**Penyebab:** Spotlight indexing (normal, 24–48 jam)

**Solusi:**
- Tunggu sampai indexing selesai
- Cek di **System Preferences → Spotlight** (ada progress bar jika masih berjalan)
- Jika masih lambat setelah 48 jam: Reset NVRAM dan SMC (lihat bagian 9d & 9e)

### Masalah 8: Ingin Kembali ke OS Sebelumnya

**Jika punya Time Machine backup:**
1. Boot Recovery Mode (`⌘ + R`)
2. Pilih **Restore from Time Machine Backup**
3. Pilih backup sebelum upgrade → ikuti instruksi

**Jika tidak punya backup:**
- Perlu download installer OS lama dan format ulang disk
- El Capitan tersedia di: [Apple Support](https://support.apple.com/en-us/102662)

> ⚠️ Sangat disarankan **tidak** kembali ke Yosemite — sudah tidak menerima update keamanan sejak 2017.

---

## Ringkasan Langkah Cepat

```
═══════════════════════════════════════════════════════
  PERSIAPAN
═══════════════════════════════════════════════════════
[1] Cek ruang penyimpanan ≥ 35 GB
[2] Backup data ke Time Machine / hard disk / cloud
[3] Catat password, Apple ID, Wi-Fi di kertas/HP
[4] Sambungkan adaptor daya (jangan cabut sampai selesai)

═══════════════════════════════════════════════════════
  TAHAP 1: Yosemite → El Capitan
═══════════════════════════════════════════════════════
[5] Copy InstallMacOSX.dmg ke Mac
[6] Double-click .dmg → double-click .pkg → install
[7] Buka Applications → Install OS X El Capitan → Install
[8] Tunggu restart + instalasi (~30 menit)
[9] Verifikasi: About This Mac = El Capitan 10.11.x
[10] Update El Capitan ke 10.11.6 via App Store

═══════════════════════════════════════════════════════
  TAHAP 2: El Capitan → Monterey
═══════════════════════════════════════════════════════
[11] Copy Install macOS Monterey.app ke /Applications
[12] Perbaiki tanggal/waktu (Date & Time → automatic)
[13] Buka Applications → Install macOS Monterey → Install
[14] Tunggu restart + instalasi (~45-60 menit)

═══════════════════════════════════════════════════════
  PASCA-INSTALASI
═══════════════════════════════════════════════════════
[15] Selesai setup awal (bahasa, Wi-Fi, akun)
[16] Jalankan Software Update
[17] Reset NVRAM + SMC (opsional, disarankan)
[18] Tunggu Spotlight indexing (24-48 jam)
```

---

## Referensi Resmi Apple

| Topik | URL |
|---|---|
| Kompatibilitas macOS Monterey | https://support.apple.com/en-us/103260 |
| Cara download dan install macOS | https://support.apple.com/en-us/102662 |
| Membuat bootable installer macOS | https://support.apple.com/en-us/101578 |
| Cara reinstall macOS | https://support.apple.com/en-us/102655 |
| Start up dari macOS Recovery | https://support.apple.com/en-us/102518 |
| Update macOS di Mac | https://support.apple.com/en-us/108382 |
| Error saat install macOS | https://support.apple.com/en-us/102531 |
| Mac tidak start up | https://support.apple.com/en-us/102675 |
| Spesifikasi MacBook Pro Early 2015 | https://support.apple.com/en-us/111959 |
| Cara membuat backup Time Machine | https://support.apple.com/en-us/104984 |

---

> **Catatan:** macOS Monterey 12 adalah versi **resmi tertinggi** yang didukung Apple untuk MacBook Pro Retina 13-inch Early 2015. Versi di atasnya (Ventura, Sonoma, Sequoia, Tahoe) tidak dapat diinstall secara resmi pada model ini.
>
> Tutorial ini dibuat pada 17 April 2026. File installer El Capitan didownload dari Apple CDN dan Monterey didownload via `mist-cli` dari Apple Software Update catalog. Semua referensi merujuk ke sumber resmi Apple Support.
