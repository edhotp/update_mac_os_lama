# Panduan Install macOS Monterey dari Offline Package (USB Installer)
## MacBook Pro Retina 13-inch Early 2015 (A1502 / EMC 2835)

> **Sumber resmi Apple:**
> - [Cara membuat bootable installer macOS](https://support.apple.com/en-us/101578)
> - [Cara download dan install macOS](https://support.apple.com/en-us/102662)
> - [Cara reinstall macOS](https://support.apple.com/en-us/102655)
> - [Cara start up dari macOS Recovery](https://support.apple.com/en-us/102518)
> - [Kompatibilitas macOS Monterey](https://support.apple.com/en-us/103260)
>
> **File installer yang sudah didownload:**
> `Install macOS Monterey.app` (12 GB, versi 12.7.6, Build 21H1320)
>
> **Lokasi file:** `/Users/edhotpurwoko/Documents/myCodes/common/Install macOS Monterey.app`

---

## Daftar Isi

1. [Persiapan Sebelum Install](#1-persiapan-sebelum-install)
2. [Metode A: Install Langsung dari Installer App](#2-metode-a-install-langsung-dari-installer-app)
3. [Metode B: Buat Bootable USB Installer (Disarankan)](#3-metode-b-buat-bootable-usb-installer-disarankan)
4. [Metode C: Install via macOS Recovery + USB](#4-metode-c-install-via-macos-recovery--usb)
5. [Setup Awal Setelah Instalasi](#5-setup-awal-setelah-instalasi)
6. [Verifikasi dan Update Pasca-Instalasi](#6-verifikasi-dan-update-pasca-instalasi)
7. [Troubleshooting (Penanganan Masalah)](#7-troubleshooting-penanganan-masalah)
8. [FAQ (Pertanyaan Umum)](#8-faq-pertanyaan-umum)

---

## 1. Persiapan Sebelum Install

### 1a. Pastikan Perangkat Kompatibel

MacBook Pro Retina 13-inch Early 2015 (A1502) **kompatibel** dengan macOS Monterey 12.
Ini adalah versi **tertinggi** yang didukung secara resmi oleh Apple untuk model ini.

Untuk memastikan model Mac Anda:
1. Klik **Apple (🍎)** di pojok kiri atas → **About This Mac**
2. Lihat baris **Model Identifier** — harus tertulis **MacBookPro12,1**

### 1b. Cek Ruang Penyimpanan

Anda membutuhkan **minimal 35 GB ruang kosong** pada disk internal:
- ~12 GB untuk file installer
- ~20 GB untuk proses instalasi dan file sistem baru
- ~3 GB ruang cadangan

Cara cek:
1. **Apple (🍎)** → **About This Mac** → tab **Storage**
2. Lihat ruang kosong yang tersedia

Jika kurang, hapus file yang tidak diperlukan (lihat panduan utama bagian "Bebaskan Ruang Penyimpanan").

### 1c. Backup Data (WAJIB!)

> ⚠️ **PENTING:** Selalu backup data sebelum install/upgrade OS. Meskipun upgrade biasanya mempertahankan data, ada risiko kecil kehilangan data.

**Pilihan backup:**

| Metode | Yang Dibutuhkan | Kelebihan |
|---|---|---|
| **Time Machine** | Hard disk eksternal | Backup lengkap, bisa restore seluruh sistem |
| **Copy manual** | USB / hard disk eksternal | Mudah, pilih file sendiri |
| **Cloud** | Akun Google Drive / iCloud | Tidak perlu perangkat tambahan |

**File yang wajib di-backup:**
- Folder `Documents`, `Desktop`, `Downloads`, `Pictures`, `Music`
- Bookmark browser (Safari, Chrome, Firefox)
- Password dan catatan penting
- File project / pekerjaan

### 1d. Sambungkan Adaptor Daya

- **Wajib:** Pastikan MacBook tersambung ke charger selama proses instalasi.
- Baterai harus terisi **minimal 50%** sebelum memulai.
- **Jangan cabut adaptor daya** sampai instalasi selesai dan Mac sudah masuk desktop.

### 1e. Pindahkan Installer ke Folder Applications

Installer harus berada di folder `/Applications` agar bisa digunakan untuk membuat bootable USB dan untuk instalasi langsung.

Buka Terminal dan jalankan:

```bash
sudo cp -R "/Users/edhotpurwoko/Documents/myCodes/common/Install macOS Monterey.app" /Applications/
```

Verifikasi:
```bash
ls -la "/Applications/Install macOS Monterey.app"
```

Anda harus melihat folder `Install macOS Monterey.app` di dalam `/Applications`.

---

## 2. Metode A: Install Langsung dari Installer App

> **Metode ini paling mudah** — langsung jalankan installer dari Mac yang sedang aktif.
> Cocok untuk upgrade dari macOS versi sebelumnya (El Capitan, Sierra, High Sierra, Catalina, Big Sur).

### Langkah-langkah:

#### Langkah 1: Buka Installer
1. Buka **Finder** → navigasi ke **Applications** (atau tekan `Cmd + Shift + A`)
2. Double-click **Install macOS Monterey**
3. Jendela installer akan terbuka

#### Langkah 2: Mulai Instalasi
1. Klik **Continue**
2. Baca dan klik **Agree** pada Software License Agreement
3. Klik **Agree** lagi pada popup konfirmasi
4. Pilih disk tujuan instalasi — biasanya **Macintosh HD** (disk utama Mac)
5. Klik **Install**

#### Langkah 3: Masukkan Password
- Masukkan **password admin Mac** Anda saat diminta
- Klik **OK** atau tekan Enter

#### Langkah 4: Tunggu Proses Instalasi
- Mac akan menyiapkan file instalasi (~5-10 menit)
- Mac akan **restart otomatis**
- Setelah restart, akan muncul logo Apple dengan progress bar
- Proses instalasi memakan waktu **30-60 menit**
- Mac mungkin **restart beberapa kali** — ini **normal**

> ⚠️ **JANGAN:**
> - Menutup penutup (lid) MacBook
> - Mencabut adaptor daya
> - Mematikan Mac secara paksa
> - Menekan tombol apa pun selama proses berlangsung

#### Langkah 5: Selesai
Setelah instalasi berhasil, Mac akan boot ke layar login atau setup awal macOS Monterey.
Lanjut ke [Setup Awal Setelah Instalasi](#5-setup-awal-setelah-instalasi).

---

## 3. Metode B: Buat Bootable USB Installer (Disarankan)

> **Metode ini disarankan** karena:
> - Bisa dipakai untuk install ulang kapan saja tanpa perlu download ulang
> - Bisa dipakai di beberapa Mac sekaligus
> - Berguna jika Mac tidak bisa boot ke OS yang ada
>
> **Sumber resmi:** [Apple Support – Create a bootable installer for macOS](https://support.apple.com/en-us/101578)

### Yang Dibutuhkan:
- USB flash drive **minimal 16 GB** (32 GB lebih aman)
- File `Install macOS Monterey.app` sudah ada di `/Applications`

### Langkah-langkah:

#### Langkah 1: Siapkan USB Flash Drive

> ⚠️ **PERINGATAN:** Semua data di USB akan **dihapus**. Pastikan tidak ada file penting di dalamnya.

1. Colokkan USB flash drive ke Mac
2. Buka **Disk Utility** (Finder → Applications → Utilities → Disk Utility, atau tekan `Cmd + Space` lalu ketik "Disk Utility")
3. Di sidebar kiri, pilih USB flash drive Anda (pastikan pilih **disk**, bukan partisi)
4. Klik **Erase** di toolbar atas
5. Isi pengaturan:
   - **Name:** `MyVolume`
   - **Format:** `Mac OS Extended (Journaled)`
   - **Scheme:** `GUID Partition Map`
6. Klik **Erase** dan tunggu selesai
7. Klik **Done**

**Alternatif via Terminal:**
```bash
# Ganti "disk#" dengan nomor disk USB Anda (cek dulu dengan diskutil list)
diskutil eraseDisk JHFS+ MyVolume GPT /dev/disk#
```

> 💡 **Tip:** Untuk mengetahui nomor disk USB, jalankan `diskutil list` dan cari USB Anda berdasarkan ukurannya.

#### Langkah 2: Buat Bootable Installer

Buka **Terminal** dan jalankan command berikut:

```bash
sudo /Applications/Install\ macOS\ Monterey.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
```

Terminal akan meminta:
1. **Password admin** — ketik password Anda (karakter tidak akan muncul di layar, ini normal)
2. **Konfirmasi hapus volume** — ketik `Y` lalu tekan Enter

Tunggu prosesnya selesai. Anda akan melihat output seperti ini:

```
Erasing disk: 0%... 10%... 20%... 30%... 100%
Copying to disk: 0%... 10%... 20%... 30%... 40%... 50%... 60%... 70%... 80%... 90%... 100%
Making disk bootable...
Install media now available at "/Volumes/Install macOS Monterey"
```

Proses ini memakan waktu **15-30 menit** tergantung kecepatan USB.

#### Langkah 3: Boot dari USB Installer

Karena MacBook Pro Early 2015 adalah **Intel-based Mac**, ikuti langkah berikut:

1. **Matikan Mac** sepenuhnya (Apple → Shut Down)
2. Pastikan USB installer masih **terhubung** ke Mac
3. **Nyalakan Mac** dengan menekan tombol power
4. **Segera tahan tombol Option (⌥/Alt)** setelah menekan tombol power
5. Tahan terus sampai muncul **layar pemilihan disk boot** (Startup Manager)
6. Anda akan melihat disk-disk yang tersedia, termasuk **Install macOS Monterey**
7. Pilih **Install macOS Monterey** (ikon berwarna oranye/kuning)
8. Klik **panah ke atas** atau tekan **Enter**

> ⚠️ **Catatan:** Mac harus terhubung ke internet saat instalasi agar bisa mendapatkan firmware dan informasi spesifik untuk model Mac Anda.
> — [Sumber: Apple Support](https://support.apple.com/en-us/101578)

#### Langkah 4: Pilih Bahasa
- Pilih bahasa yang diinginkan (English atau Bahasa Indonesia jika tersedia)
- Klik **panah** untuk melanjutkan

#### Langkah 5: Pilih Install macOS Monterey
Setelah muncul jendela **macOS Utilities**, pilih:
- **Install macOS Monterey** (atau **Install macOS**)
- Klik **Continue**

#### Langkah 6: Ikuti Proses Instalasi
1. Klik **Continue** pada layar perkenalan
2. Klik **Agree** untuk License Agreement, lalu **Agree** lagi untuk konfirmasi
3. Pilih disk tujuan: **Macintosh HD**
4. Klik **Install**
5. Tunggu proses selesai (30-60 menit, Mac akan restart beberapa kali)

#### Langkah 7: Selesai
Setelah instalasi selesai, cabut USB flash drive saat Mac sudah masuk ke layar setup atau login.
Lanjut ke [Setup Awal Setelah Instalasi](#5-setup-awal-setelah-instalasi).

---

## 4. Metode C: Install via macOS Recovery + USB

> Metode ini berguna jika:
> - Mac tidak bisa boot ke OS yang ada (stuck, error, layar hitam)
> - Ingin melakukan **clean install** (hapus semua data dan install dari nol)
>
> **Sumber resmi:** [Apple Support – Start up from macOS Recovery](https://support.apple.com/en-us/102518)

### Langkah-langkah:

#### Langkah 1: Masuk ke macOS Recovery

Untuk Intel-based Mac (MacBook Pro 2015):

| Kombinasi Tombol | Fungsi |
|---|---|
| **⌘ + R** | Reinstall macOS versi terakhir yang terinstall |
| **⌥ + ⌘ + R** | Upgrade ke macOS terbaru yang kompatibel |
| **⇧ + ⌥ + ⌘ + R** | Reinstall macOS bawaan Mac (atau versi terdekat) |

1. **Matikan Mac** sepenuhnya
2. **Nyalakan Mac** sambil **langsung tahan** tombol `Command (⌘) + R`
3. Tahan terus sampai muncul **logo Apple** atau **globe berputar**
4. Jika diminta, pilih **jaringan Wi-Fi** dan masukkan password Wi-Fi
5. Jika diminta, pilih **user** dan masukkan **password login Mac**
6. Tunggu sampai muncul jendela **macOS Utilities**

#### Langkah 2: (Opsional) Format Disk untuk Clean Install

> ⚠️ **PERINGATAN:** Langkah ini **menghapus semua data** di disk utama. Hanya lakukan jika Anda ingin install dari nol dan sudah backup semua data.

1. Pada jendela macOS Utilities, pilih **Disk Utility** → klik **Continue**
2. Di sidebar kiri, pilih **Macintosh HD** (atau disk internal utama)
3. Klik **Erase** di toolbar
4. Isi pengaturan:
   - **Name:** `Macintosh HD`
   - **Format:** `APFS` (jika tersedia) atau `Mac OS Extended (Journaled)`
   - **Scheme:** `GUID Partition Map`
5. Klik **Erase** dan tunggu selesai
6. Tutup Disk Utility untuk kembali ke jendela macOS Utilities

#### Langkah 3: Install dari USB

1. Pastikan USB bootable installer sudah terhubung ke Mac
2. Pada jendela macOS Utilities, pilih **Install macOS Monterey**
3. Klik **Continue**
4. Pilih disk tujuan: **Macintosh HD**
5. Klik **Install**
6. Tunggu proses selesai

#### Langkah 4: Selesai
Mac akan restart ke layar setup awal macOS Monterey.
Lanjut ke [Setup Awal Setelah Instalasi](#5-setup-awal-setelah-instalasi).

---

## 5. Setup Awal Setelah Instalasi

Setelah macOS Monterey berhasil terinstall, Anda akan melewati setup wizard:

### Langkah Setup:

| No | Layar | Yang Harus Dilakukan |
|---|---|---|
| 1 | **Select Your Country or Region** | Pilih **Indonesia** atau negara Anda |
| 2 | **Written and Spoken Languages** | Pilih bahasa, klik **Continue** |
| 3 | **Accessibility** | Klik **Not Now** (bisa diatur nanti) |
| 4 | **Select Your Wi-Fi Network** | Pilih jaringan Wi-Fi, masukkan password |
| 5 | **Data & Privacy** | Baca info privasi, klik **Continue** |
| 6 | **Migration Assistant** | Pilih **Not Now** jika tidak ingin transfer data dari Mac/backup lain |
| 7 | **Sign In with Your Apple ID** | Masukkan Apple ID atau klik **Set Up Later** → **Skip** |
| 8 | **Terms and Conditions** | Klik **Agree** → **Agree** |
| 9 | **Create a Computer Account** | Isi nama lengkap, nama akun, dan password baru |
| 10 | **Enable Location Services** | Pilih sesuai preferensi |
| 11 | **Select Your Time Zone** | Pilih zona waktu (WIB: Jakarta) |
| 12 | **Analytics** | Pilih sesuai preferensi, klik **Continue** |
| 13 | **Screen Time** | Klik **Set Up Later** |
| 14 | **Choose Your Look** | Pilih **Light**, **Dark**, atau **Auto** |

> 💡 **Tip:** Anda **tidak wajib** login Apple ID saat setup. Pilih "Set Up Later" jika belum punya atau belum ingin login. App Store dan iCloud tidak akan berfungsi tanpa Apple ID, tapi Mac tetap bisa dipakai normal.

---

## 6. Verifikasi dan Update Pasca-Instalasi

### 6a. Verifikasi Versi macOS
1. Klik **Apple (🍎)** → **About This Mac**
2. Pastikan tertulis **macOS Monterey** dan versi **12.7.6** (atau versi terbaru)

### 6b. Jalankan Software Update
1. Klik **Apple (🍎)** → **System Preferences** → **Software Update**
2. Tunggu Mac mencari update yang tersedia
3. Jika ada update, klik **Update Now** atau **Upgrade Now**
4. Restart Mac jika diminta

### 6c. Cek Kesehatan Disk
1. Buka **Disk Utility** (Finder → Applications → Utilities → Disk Utility)
2. Pilih **Macintosh HD** di sidebar kiri
3. Klik **First Aid** → **Run**
4. Tunggu proses verifikasi selesai

### 6d. Reset SMC dan NVRAM (Opsional, Disarankan)

Setelah upgrade OS besar, reset SMC dan NVRAM bisa membantu stabilitas:

**Reset NVRAM:**
1. Matikan Mac
2. Nyalakan sambil langsung tahan `Option + Command + P + R`
3. Tahan selama ~20 detik (Mac akan restart, tahan terus)
4. Lepaskan setelah mendengar suara startup kedua atau logo Apple muncul dan hilang dua kali

**Reset SMC (MacBook Pro 2015 — tanpa T2 chip):**
1. Matikan Mac
2. Sambungkan adaptor daya (MagSafe)
3. Tahan `Shift (kiri) + Control (kiri) + Option (kiri)` + **tombol power** secara bersamaan selama **10 detik**
4. Lepaskan semua tombol
5. Nyalakan Mac seperti biasa

### 6e. Install Aplikasi yang Dibutuhkan

Setelah macOS Monterey terinstall, install kembali aplikasi:

| Aplikasi | Cara Install |
|---|---|
| **Homebrew** | `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"` |
| **Google Chrome** | Download dari `google.com/chrome` |
| **Visual Studio Code** | Download dari `code.visualstudio.com` |
| **Aplikasi lain** | Via App Store (perlu Apple ID) atau download dari situs resmi |

---

## 7. Troubleshooting (Penanganan Masalah)

### Masalah 1: Installer Bilang "This copy of the Install macOS Monterey application is damaged"

**Penyebab:** Tanggal dan waktu Mac tidak benar (sering terjadi pada Mac lama).

**Solusi:**
1. Saat di layar installer, buka **Utilities → Terminal** dari menu bar atas
2. Jalankan command untuk memperbaiki tanggal:
   ```bash
   date 0417120026
   ```
   Format: `MMDDhhmmYY` (bulan-tanggal-jam-menit-tahun)
3. Tutup Terminal dan coba install lagi

### Masalah 2: Mac Tidak Bisa Boot dari USB

**Solusi:**
- Pastikan USB tercolok langsung ke Mac, bukan lewat hub/adapter
- Coba port USB yang berbeda
- Pastikan tahan **tombol Option (⌥)** segera setelah menekan tombol power
- Jika USB tidak muncul, buat ulang bootable installer

### Masalah 3: Mac Stuck di Logo Apple / Progress Bar Tidak Bergerak

**Solusi:**
1. **Tunggu minimal 1 jam** — proses instalasi kadang terlihat stuck tapi masih berjalan
2. Jika benar-benar stuck (>2 jam tanpa perubahan):
   - Tahan tombol **power selama 10 detik** untuk mematikan paksa
   - Nyalakan kembali — Mac biasanya akan melanjutkan instalasi
3. Jika masih gagal:
   - Boot ke Recovery Mode (`⌘ + R`)
   - Pilih **Reinstall macOS**

### Masalah 4: "An error occurred while installing the selected updates"

**Solusi:**
- Pastikan Mac terhubung ke internet (Wi-Fi atau Ethernet)
- Coba ulangi instalasi
- Jika pakai USB installer, buat ulang bootable USB

### Masalah 5: Installer Tidak Melihat Disk / Disk Tidak Muncul

**Solusi:**
1. Dari jendela installer, buka **Disk Utility** (menu bar → Utilities → Disk Utility)
2. Pilih disk internal di sidebar
3. Klik **Erase** dengan pengaturan:
   - Format: **APFS** atau **Mac OS Extended (Journaled)**
   - Scheme: **GUID Partition Map**
4. Tutup Disk Utility dan coba install lagi

> **Sumber:** [Apple Support – If an error occurred while installing macOS](https://support.apple.com/en-us/102531)

### Masalah 6: Mac Tidak Start Up Setelah Install

**Solusi:**
1. Coba **Safe Mode**: Nyalakan Mac sambil tahan **tombol Shift**
2. Jika Safe Mode berhasil, restart normal
3. Jika tidak berhasil, masuk **Recovery Mode** (`⌘ + R`) dan pilih **Reinstall macOS**
4. Jika Recovery Mode tidak tersedia, gunakan **Internet Recovery** (`⌥ + ⌘ + R`)

> **Sumber:** [Apple Support – If your Mac doesn't start up all the way](https://support.apple.com/en-us/102675)

### Masalah 7: Ingin Kembali ke OS Sebelumnya

Jika sudah membuat **Time Machine backup** sebelum upgrade:
1. Boot ke Recovery Mode (`⌘ + R`)
2. Pilih **Restore from Time Machine Backup**
3. Pilih backup yang dibuat sebelum upgrade
4. Ikuti petunjuk di layar

---

## 8. FAQ (Pertanyaan Umum)

### Q: Apakah data saya hilang setelah upgrade?
**A:** Tidak, jika menggunakan Metode A (install langsung) atau Metode B (boot USB lalu install), data Anda tetap ada. Data hanya hilang jika Anda memformat disk di Metode C (clean install).

### Q: Apakah perlu Apple ID?
**A:** Tidak wajib. Mac bisa dipakai tanpa Apple ID. Tapi Anda tidak bisa mengakses App Store, iCloud, iMessage, dan FaceTime tanpa Apple ID.

### Q: Berapa lama proses instalasi?
**A:** Biasanya 30-60 menit setelah restart pertama. Total proses (termasuk persiapan) sekitar 1-2 jam.

### Q: Apakah bisa downgrade kembali?
**A:** Bisa, tapi harus format ulang disk dan install OS lama dari awal (atau restore dari Time Machine backup).

### Q: USB bootable bisa dipakai di Mac lain?
**A:** Ya, selama Mac tersebut kompatibel dengan macOS Monterey. Lihat daftar kompatibilitas di [Apple Support](https://support.apple.com/en-us/103260).

### Q: Apakah macOS Monterey masih mendapat security update?
**A:** Apple secara berkala merilis security update untuk macOS Monterey. Cek [Apple Security Releases](https://support.apple.com/en-us/100100) untuk informasi terbaru.

### Q: Kenapa Metode B (USB) lebih disarankan daripada Metode A?
**A:** Karena USB bootable bisa dipakai berulang kali, berguna jika Mac bermasalah dan tidak bisa boot, serta bisa dipakai di Mac lain. Metode A lebih mudah tapi hanya bisa dipakai jika Mac sudah berjalan normal.

---

## Ringkasan Perbandingan Metode

| Aspek | Metode A (Langsung) | Metode B (USB Bootable) | Metode C (Recovery + USB) |
|---|---|---|---|
| **Kesulitan** | Mudah | Sedang | Sedang-Sulit |
| **Butuh USB** | Tidak | Ya (16GB+) | Ya (16GB+) |
| **Butuh Internet** | Tidak* | Saat install saja | Saat Recovery |
| **Bisa clean install** | Tidak | Ya | Ya |
| **Bisa dipakai ulang** | Tidak | Ya | Ya |
| **Cocok untuk** | Upgrade dari OS lama | Install ulang / multi-Mac | Mac tidak bisa boot |

*) Installer sudah offline, tapi Mac mungkin perlu internet untuk firmware update.

---

## Referensi Resmi Apple

| Halaman | URL |
|---|---|
| Membuat bootable installer macOS | https://support.apple.com/en-us/101578 |
| Cara download dan install macOS | https://support.apple.com/en-us/102662 |
| Cara reinstall macOS | https://support.apple.com/en-us/102655 |
| Start up dari macOS Recovery | https://support.apple.com/en-us/102518 |
| Kompatibilitas macOS Monterey | https://support.apple.com/en-us/103260 |
| Error saat install macOS | https://support.apple.com/en-us/102531 |
| Mac tidak bisa start up | https://support.apple.com/en-us/102675 |
| Erase dan reformat disk | https://support.apple.com/en-us/102506 |

---

> **Catatan:** Tutorial ini dibuat berdasarkan file installer `Install macOS Monterey.app` versi 12.7.6 (Build 21H1320) yang sudah didownload menggunakan tool `mist-cli` pada 17 April 2026. Semua referensi merujuk ke sumber resmi Apple Support.
