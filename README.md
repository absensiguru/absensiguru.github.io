# Panduan Lengkap: Membuat https://absensiguru.github.io/

Panduan ini untuk membuat website PWA (bisa diinstall ke Android, fullscreen
tanpa address bar) dengan alamat **pendek dan tanpa nama akun pribadi Anda**
(`anton85-a1`) di dalamnya.

Hasil akhir: URL yang dikirim ke guru cukup:

    https://absensiguru.github.io/

Total waktu: ± 15-20 menit. Semua GRATIS, tidak perlu kartu kredit.

---

## DAFTAR ISI

1. Membuat GitHub Organization bernama "absensiguru"
2. Membuat repository dengan nama khusus
3. Upload file-file dari paket ini
4. Mengaktifkan GitHub Pages
5. Menguji alamat website
6. Menguji instalasi PWA di Android
7. Kalau nanti mau ganti URL GAS (redeploy Apps Script)
8. Troubleshooting (kalau ada yang error)

---

## BAGIAN 1 — Membuat GitHub Organization bernama "absensiguru"

Organization ini gratis dan tidak menggantikan akun pribadi Anda
(`anton85-a1`) — anggap seperti membuat "folder besar" baru yang
dimiliki oleh akun Anda, tapi punya nama sendiri.

1. Buka **github.com**, pastikan Anda sudah **login** dengan akun `anton85-a1`.
2. Klik **foto profil Anda** di pojok kanan atas.
3. Pada menu yang muncul, klik **"Your organizations"**.
4. Klik tombol hijau **"New organization"** (pojok kanan atas halaman).
5. Akan muncul pilihan paket. Pilih **"Free"** → klik **"Create a free organization"**.
6. Isi form:
   - **Organization account name**: ketik `absensiguru`
     - Kalau muncul tulisan merah "Name already taken" / nama sudah dipakai
       orang lain, coba variasi lain, misalnya:
       `absensi-guru`, `absensiguruku`, `guruabsensi`, `sistemabsensiguru`
     - **Catat nama yang berhasil Anda pakai**, karena URL akhir akan
       mengikuti nama ini persis (`https://NAMA-INI.github.io/`).
   - **Contact email**: isi email Anda.
   - **This organization belongs to**: pilih **"My personal account"**.
7. Klik **"Next"**.
8. Di halaman "Add organization members" — **lewati saja** (klik
   **"Complete setup"** atau **"Skip this step"**), tidak perlu invite
   siapa-siapa.
9. Halaman survey "About your team" boleh di-skip juga (klik "Skip").
10. Selesai — Anda sekarang punya Organization. Anda otomatis jadi **Owner**.

> Mulai bagian ini, saya akan pakai nama `absensiguru` sebagai contoh.
> Kalau nama Anda berbeda (misal `absensi-guru`), ganti semua penyebutan
> `absensiguru` di bawah dengan nama Anda.

---

## BAGIAN 2 — Membuat Repository dengan nama khusus

Ini bagian **PALING PENTING**: nama repository **harus persis sama**
dengan nama organization + `.github.io`, supaya GitHub otomatis
menjadikannya alamat utama (root), bukan alamat dengan folder tambahan.

1. Di halaman Organization `absensiguru` yang baru dibuat, klik tombol
   hijau **"New repository"** (atau ikon **+** di kanan atas → **"New repository"**,
   lalu pastikan **Owner** dipilih `absensiguru`, bukan `anton85-a1`).
2. Isi form **Create a new repository**:
   - **Repository name**: ketik persis →
     ```
     absensiguru.github.io
     ```
     (Kalau nama organization Anda `absensi-guru`, maka repo-nya
     `absensi-guru.github.io` — harus sama persis dengan nama org.)
   - **Description**: boleh kosong, atau isi "Website Sistem Absensi Guru".
   - Pilih **Public** (wajib Public untuk GitHub Pages gratis).
   - **JANGAN centang** "Add a README file" (biar tidak konflik nanti
     saat upload).
3. Klik **"Create repository"**.

Anda akan diarahkan ke halaman repo kosong.

---

## BAGIAN 3 — Upload file-file dari paket ini

Paket yang saya kirim (folder/zip `absensiguru-github-io`) isinya:

```
absensiguru-github-io/
├── index.html          <- halaman utama (wrapper PWA + iframe ke GAS)
├── manifest.json        <- identitas PWA (nama, ikon, mode standalone)
├── sw.js                 <- service worker (syarat wajib supaya bisa "Install")
├── icons/
│   ├── icon-192.png
│   ├── icon-512.png
│   └── icon-maskable-512.png
└── README.md              <- file panduan ini (tidak perlu diupload ke GitHub)
```

**PENTING:** Upload **ISI folder** (file-filenya langsung), **BUKAN**
folder `absensiguru-github-io` itu sendiri. Jadi di GitHub nanti,
`index.html` harus ada langsung di halaman utama repo (root), bukan
di dalam sub-folder.

### Langkah upload:

1. Di halaman repo `absensiguru.github.io` yang masih kosong, cari
   tulisan link **"uploading an existing file"** (biasanya ada di
   tengah halaman) → klik.
   - Kalau tidak muncul link itu, klik tombol **"Add file"** (pojok
     kanan atas daftar file) → pilih **"Upload files"**.
2. Akan muncul kotak area upload bertuliskan
   *"Drag files here to add them to your repository"*.
3. Buka folder `absensiguru-github-io` di komputer Anda (hasil ekstrak
   zip yang saya kirim).
4. **Blok/select semua isi di dalamnya** (index.html, manifest.json,
   sw.js, dan folder icons) — jangan blok folder `absensiguru-github-io`-nya,
   cukup ISI-nya saja.
5. **Drag** (seret) semua yang terblok tadi ke kotak upload di GitHub.
   - Kalau drag folder `icons` tidak bisa (browser tertentu tidak
     mendukung drag folder), lakukan 2 kali upload terpisah:
     - Upload dulu: `index.html`, `manifest.json`, `sw.js`
     - Lalu klik "Add file" → "Upload files" lagi, kali ini masuk dulu
       ke folder icons di komputer, blok 3 file png-nya, drag ke GitHub.
       GitHub otomatis membuat folder `icons/` kalau nama filenya
       ditulis dengan path (lihat catatan di bawah).
   - **Alternatif paling aman kalau drag folder gagal:** gunakan cara
     di Bagian 3B (GitHub Desktop) di bawah.
6. Tunggu sampai semua file selesai ter-upload (progress bar hijau).
7. Scroll ke bawah, di kotak **"Commit changes"**:
   - Judul commit boleh dibiarkan default, atau ganti jadi:
     `Tambah PWA Absensi Guru`
   - Pilih **"Commit directly to the main branch"**.
8. Klik tombol hijau **"Commit changes"**.

Setelah ini, halaman repo Anda seharusnya menampilkan daftar file:
`icons/`, `index.html`, `manifest.json`, `sw.js`.

### BAGIAN 3B — Kalau upload drag-and-drop folder icons bermasalah

Cara termudah kalau ragu dengan drag-and-drop folder lewat browser:

1. Install **GitHub Desktop** (gratis): https://desktop.github.com/
2. Buka GitHub Desktop → login dengan akun GitHub Anda (`anton85-a1`).
3. **File → Clone repository** → pilih tab **"GitHub.com"** → cari dan
   pilih `absensiguru/absensiguru.github.io` → klik **Clone**.
4. Pilih folder di komputer untuk menyimpan hasil clone (misalnya
   Documents), klik **Clone**.
5. Buka folder hasil clone tadi lewat File Explorer/Finder.
6. **Copy-paste** semua isi folder `absensiguru-github-io` (index.html,
   manifest.json, sw.js, folder icons) ke DALAM folder hasil clone tadi.
7. Kembali ke aplikasi GitHub Desktop — akan terlihat daftar file baru
   di kolom kiri (Changes).
8. Isi kolom **"Summary"** di kiri bawah: `Tambah PWA Absensi Guru`.
9. Klik **"Commit to main"**.
10. Klik **"Push origin"** (tombol biru di atas).

Selesai, file sudah ada di GitHub.

---

## BAGIAN 4 — Mengaktifkan GitHub Pages

Untuk repo yang namanya `<nama>.github.io`, GitHub Pages **biasanya
otomatis aktif**. Tapi tetap cek supaya yakin:

1. Di halaman repo `absensiguru.github.io`, klik tab **"Settings"**
   (ikon gerigi, di deretan atas: Code, Issues, Pull requests, ... Settings).
2. Di sidebar kiri, cari dan klik **"Pages"** (di bagian "Code and automation").
3. Pastikan:
   - **Source**: "Deploy from a branch"
   - **Branch**: `main` dan folder `/ (root)` → kalau belum, ubah lalu
     klik **Save**.
4. Kalau sudah aktif, di bagian atas halaman ini akan muncul kotak hijau:
   *"Your site is live at https://absensiguru.github.io/"*
5. Kalau baru saja diaktifkan/disimpan, **tunggu 1–3 menit** sebelum
   dicoba buka (GitHub perlu waktu build & deploy).

---

## BAGIAN 5 — Menguji alamat website

1. Buka browser (Chrome, di HP atau laptop, **bukan mode Incognito**).
2. Ketik alamat:
   ```
   https://absensiguru.github.io/
   ```
3. Yang seharusnya terjadi:
   - Muncul sebentar layar loading "Memuat Sistem Absensi Guru…"
   - Lalu muncul halaman login aplikasi GAS Anda di dalam layar penuh.
4. Kalau yang muncul halaman GitHub 404 ("There isn't a GitHub Pages site here"):
   - Kemungkinan besar Pages belum selesai deploy → tunggu beberapa
     menit lagi, refresh.
   - Atau nama repo belum persis `absensiguru.github.io` → cek lagi
     Bagian 2.
5. Kalau halaman muncul tapi **layarnya putih/blank** (loading tidak
   pernah selesai): lihat bagian **Troubleshooting** di bawah.

---

## BAGIAN 6 — Menguji instalasi PWA di Android

1. Di HP Android, buka **Chrome** (bukan browser bawaan HP lain, harus
   Chrome), buka:
   ```
   https://absensiguru.github.io/
   ```
2. Tunggu halaman dan aplikasi GAS-nya termuat sempurna.
3. Cara install (salah satu akan muncul):
   - **Otomatis**: banner kecil muncul di bawah bertuliskan
     "Tambahkan Sistem Absensi Guru ke layar utama" / "Install app" →
     tap **"Install"** atau **"Tambahkan"**.
   - **Manual**: kalau banner tidak muncul, tap tombol hijau bulat
     **"📲 Install App"** yang ada di pojok kanan bawah halaman.
   - **Lewat menu Chrome**: tap ikon titik tiga (⋮) di kanan atas
     Chrome → cari **"Install app"** atau **"Tambahkan ke Layar Utama"**.
4. Konfirmasi install → tunggu beberapa detik.
5. Buka ikon aplikasi dari **layar utama HP** (bukan dari Chrome lagi).
6. Hasilnya: aplikasi terbuka **fullscreen**, **tanpa address bar**,
   seperti aplikasi native.

---

## BAGIAN 7 — Kalau nanti URL GAS berganti (redeploy Apps Script)

Kalau suatu saat Anda deploy ulang GAS dan dapat URL `/exec` yang baru:

1. Buka repo `absensiguru.github.io` di GitHub → klik file `index.html`.
2. Klik ikon **pensil (Edit)** di kanan atas file.
3. Cari baris (sekitar tengah file):
   ```html
   src="https://script.google.com/macros/s/AKfycbwB1O84zB2mga8ujkKSXqrGI3UHJnsb9JZTU9wH2kz5cBQSR5BLc0W2Tb7KYSW8dcLY/exec"
   ```
4. Ganti bagian URL-nya saja dengan URL `/exec` yang baru.
5. Scroll bawah → **"Commit changes"** → **"Commit directly to the main branch"** → **Commit changes**.
6. Tunggu 1-2 menit, lalu buka lagi `https://absensiguru.github.io/`
   untuk memastikan sudah terhubung ke deployment baru.

---

## BAGIAN 8 — Troubleshooting

**A. Halaman GitHub Pages 404 ("There isn't a GitHub Pages site here")**
- Cek nama repo harus PERSIS `absensiguru.github.io` (tanpa spasi, huruf kecil semua).
- Cek Settings → Pages, pastikan branch `main` / folder `root` sudah di-Save.
- Tunggu lagi 2-3 menit, GitHub Pages kadang butuh waktu build ulang.

**B. Halaman terbuka tapi kosong/putih, loading tidak selesai**
- Kemungkinan `index.html` gagal memuat iframe. Buka halaman itu di
  laptop, tekan **F12** (buka DevTools) → tab **Console** → lihat pesan
  error berwarna merah, screenshot dan kirim ke saya.
- Pastikan URL GAS di dalam `index.html` masih aktif (coba buka URL
  `/exec` itu langsung di tab baru, harus tampil halaman login GAS).

**C. Tombol "Install App" tidak pernah muncul**
- Pastikan pakai **Chrome**, bukan Samsung Internet/Firefox/browser lain
  (dukungan PWA install paling stabil di Chrome/Edge).
- Pastikan alamat pakai **https://** (GitHub Pages otomatis https, ini
  seharusnya aman).
- Coba refresh halaman 1-2 kali, kadang butuh reload agar service worker
  selesai terdaftar sebelum tombol muncul.
- Cek juga: HP yang sama pernah membuka halaman ini lalu klik
  "tidak, terima kasih" pada banner sebelumnya bisa membuat Chrome
  tidak menawarkan lagi selama beberapa waktu — tetap bisa install
  manual lewat menu ⋮ → "Install app".

**D. Nama organization "absensiguru" ternyata sudah dipakai orang lain**
- Ganti dengan variasi lain (lihat daftar contoh di Bagian 1), lalu
  ulangi Bagian 1 dan 2 dengan nama barunya. Semua file di paket ini
  TIDAK perlu diubah (tidak menyebut nama domain di dalamnya).

**E. Ingin pindah ke domain sendiri nanti (mis. absensiguru.my.id)**
- Tidak perlu ubah file apa pun di paket ini.
- Beli domain → arahkan DNS (CNAME) ke `absensiguru.github.io` →
  tambahkan file bernama `CNAME` (isi: nama domain Anda) ke root repo
  ini → beri tahu saya kalau butuh langkah detailnya nanti.

---

Kalau ada langkah yang macet atau muncul pesan error yang tidak ada di
daftar Troubleshooting, screenshot saja dan kirim ke saya — saya bantu
lacak masalahnya.
