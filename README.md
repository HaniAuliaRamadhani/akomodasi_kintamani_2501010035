# Akuisisi Data Akomodasi Kecamatan Kintamani

Repositori ini dikembangkan untuk menyelesaikan tugas praktikum mata kuliah **BIFP-243 Akuisisi dan Manajemen Data** dengan studi kasus ekstraksi, pembersihan, dan analisis data spasial akomodasi pariwisata di Kecamatan Kintamani, Kabupaten Bangli, Bali.

## Identitas Mahasiswa
* **Nama:** Hanifah Aulia Ramadhani
* **NIM:** 2501010035
* **Mata Kuliah:** BIFP-243 Akuisisi dan Manajemen Data
* **Institusi:** Institut Bisnis dan Teknologi Indonesia (INSTIKI)

## Tujuan
Memahami proses pengambilan data geospasial menggunakan API, mengolah data mentah bertingkat menjadi format tabular DataFrame, memeriksa kualitas dan kelengkapan data (*completeness rate*), serta menyusun laporan analisis spasial persebaran akomodasi di Kecamatan Kintamani.

## Sumber Data & Tanggal Akses
1. **OpenStreetMap (OSM)** melalui **Overpass API** (Data spasial primer titik dan area pariwisata).
2. **Badan Pusat Statistik (BPS) Kabupaten Bangli** melalui publikasi *Kecamatan Kintamani Dalam Angka 2025* (Data pembanding statistik resmi).
* **Tanggal Akses Data:** November 2026.

## Metode Akuisisi
Proses ekstraksi dan pemrosesan data dilakukan melalui tahapan berikut:
1. Mengambil data spasial akomodasi menggunakan kueri Overpass API.
2. Menerapkan mekanisme tangguh (*retry* / penanganan pengecualian) apabila permintaan API mengalami kendala jaringan.
3. Menyimpan data mentah hasil respons API dalam format JSON ke direktori `data/raw/`.
4. Menerapkan fungsi transformasi kustom (`ratakan()`) untuk mengubah struktur JSON bertingkat (`node` dan `way`) menjadi tabel tabular menggunakan Pandas.
5. Memeriksa kualitas data, nilai kosong (*missing values*), serta melakukan uji kelengkapan (*completeness analysis*) terhadap data acuan BPS.
6. Melakukan verifikasi acak terhadap sampel data (*ground truthing audit*).
7. Membuat visualisasi grafik persebaran akomodasi di Kecamatan Kintamani.

## Batasan dan Etika Data
- Menggunakan sumber data terbuka (*open data*).
- Tidak melakukan *scraping* ilegal dari platform pihak ketiga tertutup seperti Online Travel Agent (OTA) maupun Google Maps.
- Menerapkan prinsip **Minimalisasi Data**: tidak mengambil, menyimpan, atau memproses data kontak pribadi seperti nomor telepon atau alamat email pengelola.
- Mematahi batasan teknis penggunaan API (*rate limiting*) untuk menghindari beban berlebih pada peladen OSM.
- Tetap mencantumkan atribusi kepemilikan data secara transparan.

*Atribusi: © OpenStreetMap contributors. Lisensi Open Database License (ODbL).*

## Cara Menjalankan Ulang
1. Instal pustaka (*libraries*) yang diperlukan:
   ```bash
   pip install requests pandas matplotlib jupyter
   ```
