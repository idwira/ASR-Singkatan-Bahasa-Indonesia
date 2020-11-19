## ASR-Singkatan-Bahasa-Indonesia
#### Automatic Speech Recognition (ASR) Bahasa Indonesia untuk pengucapan singkatan dan akronim. Singkatan dibaca huruf per huruf, contoh PSBB (Pembatasan Sosial Berskala Besar). Akronim adalah singkatan yang dibaca biasa, tidak huruf per-huruf contoh KOPASSUS (Komando Pasukan Khusus).

Platform: **Windows 10 (Nov 2020)**<br>
Langkah-langkah mengikuti [Tutorial: Create Acoustic Model - Manually](http://www.voxforge.org/home/dev/acousticmodels/windows/create/htkjulius/tutorial)<br><br>
1. Buat directory voxforge/bin, lokasi bisa di folder C: > Users > namauser > voxforge > bin<br><br>
2. Download dari [Software dan Guide](http://www.voxforge.org/home/dev/acousticmodels/windows/create/htkjulius/tutorial/download) (**angka versi terkini bisa berbeda**)
   - The Hidden Markov Model Toolkit (HTK), toolkit portabel untuk membangun dan memanipulasi hidden Markov models. HTK utamanya digunakan untuk *speech recognition* (htk-3.3-windows-binary), simpan di folder voxforge/bin diatas
   - htkbook_pdf (referensi toolkit commands), simpan di folder voxforge/bin diatas
   - *Large vocabulary continuous speech recognition (LVCSR) engine*: julius-4.3.1-win32bin [(*latest ver*)](http://julius.osdn.jp/en_index.php#latest_version), simpan di folder voxforge/bin diatas
   - Julia, bahasa scripting *high-level*, *high-performance* untuk *technical computing* (julia-1.5.3-win32, pilih yg 32-bit) [(*latest ver*)](https://julialang.org/downloads/), simpan di folder downloads (untuk eksekusi install kemudian)<br><br>
3. Instalasi
   - Untuk HTK dan Julius, file hasil download (pada langkah 2 diatas), cukup di-ekstrak di folder voxforge/bin tersebut.
   - Untuk htkbook_pdf, ekstrak juga filenya, di dalamnya dokumen panduan HTK (format pdf).
   - Untuk Julia, mesti dilakukan instalasi. Eksekusi file "julia-1.5.3-win32.exe" (installer)-nya.
