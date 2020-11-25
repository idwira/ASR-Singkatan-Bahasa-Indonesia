## ASR-Singkatan-Bahasa-Indonesia
#### Automatic Speech Recognition (ASR) Bahasa Indonesia untuk pengucapan singkatan dan akronim. Singkatan dibaca huruf per huruf, contoh PSBB (Pembatasan Sosial Berskala Besar). Akronim adalah singkatan yang dibaca biasa, tidak huruf per-huruf contoh KOPASSUS (Komando Pasukan Khusus).

Platform: **Windows 10 (Nov 2020)**<br>
Langkah-langkah mengikuti [Tutorial: Create Acoustic Model - Manually](http://www.voxforge.org/home/dev/acousticmodels/windows/create/htkjulius/tutorial)<br>
### A. Persiapan Tools
1. Buat directory voxforge/bin, lokasi bisa di folder C: > Users > namauser > voxforge > bin<br><br>
2. Download dari [Software dan Guide](http://www.voxforge.org/home/dev/acousticmodels/windows/create/htkjulius/tutorial/download) (**angka versi terkini bisa berbeda**)
   - The Hidden Markov Model Toolkit (HTK), toolkit portabel untuk membangun dan memanipulasi hidden Markov models. HTK utamanya digunakan untuk *speech recognition* (htk-3.3-windows-binary), simpan di folder voxforge/bin diatas
   - htkbook_pdf (referensi toolkit commands), simpan di folder voxforge/bin diatas
   - *Large vocabulary continuous speech recognition (LVCSR) engine*: julius-4.3.1-win32bin [(*latest ver*)](http://julius.osdn.jp/en_index.php#latest_version), simpan di folder voxforge/bin diatas
   - Julia, bahasa scripting *high-level*, *high-performance* untuk *technical computing* (julia-1.5.3-win32, pilih yg 32-bit) [(*latest ver*)](https://julialang.org/downloads/), simpan di folder downloads (untuk eksekusi install kemudian)<br><br>
3. Instalasi
   - Untuk HTK dan Julius, file hasil download (pada langkah 2 diatas), cukup di-ekstrak di folder voxforge/bin tersebut.
   - Untuk htkbook_pdf, ekstrak juga filenya, di dalamnya dokumen panduan HTK (format pdf).
   - Untuk Julia, mesti dilakukan instalasi. Eksekusi file "julia-1.5.3-win32.exe" (installer)-nya.<br><br>
4. Catat *path* masing-masing aplikasi HTK, Julius dan Julia.
   - Untuk HTK, di PC saya lokasinya di (*path* persisnya akan berbeda di tiap PC, nama user PC saya 'Wira'):
         ```
         C:\Users\Wira\voxforge\bin\htk-3.3-windows-binary\htk
         ```
   - Untuk Julius, di PC saya lokasinya di:
         ```
         C:\Users\Wira\voxforge\bin\julius-4.3.1-win32bin\bin
         ```
   - Untuk Julia, bergantung apakah lokasi instalasinya di-*custom* atau mengikuti *default*. Saya mengikuti *default*, lokasinya di:
         ```
         C:\Users\Wira\AppData\Local\Programs\Julia 1.5.3\bin
         ```<br><br>
5. Konfigurasi *system environment variables* di Windows OS untuk ketiga *path* di langkah-4. Ini penting karena ketiga aplikasi diatas akan diakses melalui ***Command Prompt*** *Windows*. Kita ingin bisa mengeksekusi/membuka aplikasi-aplikasi tersebut tanpa mesti repot masuk ke lokasi folder aplikasi masing-masing.
   - Buka menu 'edit the system environment variables', bisa melalui menu search di Windows dengan kata kunci tersebut, atau
   - Melalui
         ```
         Control panel >> System and Security >> System >> Advanced System Settings >> Environment Variables
         ```
   - Akan ada dua bagian, *User Variables* atau *System Variables*, kita perlu tambahkan yang bagian ***User Variables***.
   - Klik tombol 'New' untuk memasukkan user variable yang baru, masukkan satu persatu.
      - *Variable name* 'HTK'; *Variable value* masukkan *path* htk yang sudah dicatat di langkah-4.
      - *Variable name* 'Julius'; *Variable value* masukkan *path* Julius yang sudah dicatat di langkah-4.
      - *Variable name* 'Julia'; *Variable value* masukkan *path* Julia yang sudah dicatat di langkah-4.<br><br>
6. Finalisasi *Environment Variables*
   - *Update Windows PATH environment variable* untuk HTK, Julius and Julia melalui *Command Prompt* Windows<br> (dengan perintah 'setx PATH'). Copy-paste lagi ketiga path yang sudah dilokasikan dilangkah-4. Contoh di PC saya (lakukan di ***Windows Command Prompt***):
     ``` cmd
     C:\>setx PATH "C:\Users\Wira\voxforge\bin\htk-3.3-windows-binary\htk;C:\Users\Wira\AppData\Local\Programs\Julia 1.5.3\bin;C:\Users\Wira\voxforge\bin\julius-4.3.1-win32bin\bin"
     ```
     Akan ditampilkan ```SUCCESS: Specified value was saved.``` jika updatenya berhasil.
   - Tutup *Command Prompt*-nya, lalu buka lagi baru. Finalisasi setx PATH di atas dengan perintah ```echo %PATH%```:
     ``` cmd
     C:\Users\Wira>echo %PATH%
     ```
7. Testing
   Uji apakah *path* sudah benar dan aplikasi bisa dijalankan, semua perintah dibawah dilakukan pada ***Windows Command Prompt***:
   - HTK
     ``` cmd
     C:\Users\Wira>HVite
     ```
     Akan ditampilkan list ```USAGE: HVite [options] VocabFile HMMList DataFiles...``` jika eksekusinya berhasil.
   - Julius (testing ini menggunakan Julius ver 4.3.1, sesuaikan dengan versi yang terinstall)
     ```
     C:\Users\Wira>julius-4.3.1
     ```
     Jika berhasil akan ditampilkan ```Julius rev.4.3.1 - based on JuliusLib rev.4.3.1 (fast)  built for i686-pc-cygwin```
   - Julia
     ```
     C:\Users\Wira>julia
     ```
     Jika berhasil akan ditampilkan logo 'Julia' dan *prompt* berubah menjadi 
     ``` julia
     julia>
     ```  
   **Catatan:**
   Dalam beberapa kasus, langkah 6 dan 7 diatas mesti diulang jika setelah restart PC ternyata testingnya gagal (tidak konsisten). Diulang saja, jika semua benar mestinya ini    permanen di Windows.

8. Instalasi Audacity<br>
   Audacity adalah *tool* perekam dan *editor* audio multi-track yang gratis serta mudah digunakan. Langsung saja download installernya dari situs resmi [Audacity](https://www.audacityteam.org/) dan jalankan instalasinya di PC.

### B. Persiapan Data (*Data Preparation*)
1. Test
