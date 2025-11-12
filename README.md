# PROJEK_OS_KHANZA
Tugas Proyek : Langkah Implementasi

# LANGKAH 1 BUAT STRUKTUR DIREKTORI
Berikut cara membuat struktur direktori Project_Manajemen_File: 
[Deskripsi gambar] : ( https://drive.google.com/file/d/1pO1Rtliq6PD3oCToHWo2kqO2_Oec2IRU/view?usp=drivesdk )

~~~~
khanzak@khanza~virtualbox:~$ mkdir project_manajemen_file
~~~~
penjelasan: 

mkdir project_manajemen_file
artinya kamu membuat folder baru bernama project_manajemen_file di direktori home (~).


Cara berpindah direktori ke Project_Manajement_File dan Membuat folder document images archives logs:
[Deskripsi gambar] : ( https://drive.google.com/file/d/16Grlf5pktd5BUahh79U6iBcrVSIRpBWA/view?usp=drivesdk )

~~~~
cd project_manajemen_organisasi
~~~~
~~~~
mkdir documents images archives logs
~~~~

penjelasan:
1. cd project_manajemen_organisasi

➡️ Artinya: masuk ke dalam folder bernama project_manajemen_organisasi.

2. mkdir documents images archives logs

➡️ Artinya: membuat empat folder sekaligus di dalam direktori tersebut, yaitu:

Perintah membuat 20 contoh file dan memasukkan sebuah text ke dalam masing-masing file:

[Deskripsi gambar] ( https://drive.google.com/file/d/1HecELSIRX-Gnd_BrTP2NpAb-pHe1X-px/view?usp=drivesdk )

~~~~
touch file{1..10}.txt file{11..15}.jpg file{16..18}.pdf file{19..20}.log
ls
echo "ini adalah dokumen contoh:" > file1.txt
echo "Data gambar" > file11.jpg
echo "log sistem contoh" > log
~~~~

penjelasan:
1. touch file{1..10}.txt file{11..15}.jpg file{16..18}.pdf file{19..20}.log
Artinya:

Membuat file file1.txt sampai file10.txt

Membuat file file11.jpg sampai file15.jpg

Membuat file file16.pdf sampai file18.pdf

Membuat file file19.log sampai file20.log

2. ls
 Menampilkan daftar semua file dan folder di direktori kamu sekarang.
Jadi kamu bisa cek apakah file-file tadi sudah berhasil dibuat.

3. echo "ini adalah dokumen contoh:" > file1.txt
 Artinya: Menulis teks "ini adalah dokumen contoh:" ke dalam file1.txt.
Tanda > akan menimpa isi file (kalau sudah ada sebelumnya).


# LANGKAH 2 SKRIP FILE ORGANISASI
Script organisasi file di dalam direktori proyek:

~~~~
nano organisasi_file.sh
~~~~

SCRIPT ISI
[deskripsi gambar] ()

~~~~
#!/bin/bash
# Script untuk mengorganisasi file berdasarkan ekstensi

# Pastikan berada di direktori proyek
cd ~/project_manajemen_file

# Pindahkan file sesuai ekstensi
find . -maxdepth 1 -type f -name "*.txt" -exec mv {} documents/ \;
find . -maxdepth 1 -type f -name "*.jpg" -exec mv {} images/ \;
find . -maxdepth 1 -type f -name "*.pdf" -exec mv {} archives/ \;
find . -maxdepth 1 -type f -name "*.log" -exec mv {} logs/ \;

# Konfirmasi hasil
echo "File berhasil dipindahkan ke folder sesuai ekstensi!"
ls documents images archives logs
~~~~

penjelasan:
1. #!/bin/bash
→ Menandakan ini adalah script Bash.

2. cd ~/project_manajemen_file
→ Masuk ke folder proyek utama.

3. find . -maxdepth 1 -type f -name "*.txt" -exec mv {} documents/ \;
→ Cari semua file .txt di folder ini, lalu pindahkan ke folder documents/.
(Pernyataan berikutnya melakukan hal sama untuk .jpg, .pdf, dan .log.)

4. echo "File berhasil dipindahkan ke folder sesuai ekstensi!"
ls documents images archives logs
→ Tampilkan pesan konfirmasi dan daftar isi dari tiap folder hasil pemindahan.


Memberi Hak Eksekusi
~~~~
chmod +x organisasi_file.sh
~~~~

penjelasan :
chmod +x organisasi_file.sh
→ Memberi izin eksekusi agar script bisa dijalankan.
Eksekusi naskah yang telah di buat

~~~~
./organisasi_file.sh
~~~~
penjelasan:
./organisasi_file.sh
→ Menjalankan script yang sudah dibuat.


# LANGKAH 3 FUNGSI PENCARIAN
Buat file search_file.sh

[Deskripsi gambar] ()

~~~~
 #!/bin/bash
# Script: search_files.sh
# Fungsi: Mencari file berdasarkan nama, ukuran, atau konten

cd ~/project_file_management

echo "=== PENCARIAN FILE ==="
echo "1. Cari berdasarkan nama"
echo "2. Cari berdasarkan ukuran"
echo "3. Cari berdasarkan isi konten"
read -p "Pilih opsi (1/2/3): " opsi

case $opsi in
  1)
    read -p "Masukkan nama atau pola file (contoh: *.txt): " nama
    echo "Hasil pencarian:"
    find . -type f -name "$nama"
    ;;
  2)
    read -p "Masukkan batas ukuran (contoh: +1M untuk lebih dari 1MB, -500k untuk kurang dari 500KB): " ukuran
    echo "Hasil pencarian:"
    find . -type f -size "$ukuran"
    ;;
  3)
    read -p "Masukkan kata kunci yang ingin dicari dalam file: " keyword
    echo "Hasil pencarian:"
    grep -r "$keyword" .
    ;;
  *)
    echo "Opsi tidak valid."
    ;;
esac
~~~~
penjelasan: 
1. echo ➡️ Menampilkan menu pilihan ke pengguna, lalu menyimpan pilihan ke variabel opsi.

2. case digunakan untuk mengeksekusi perintah berdasarkan pilihan yang dimasukkan.

3. find -name ➡️ Cari file berdasarkan nama	
4. find -size ➡️ Cari file berdasarkan ukuran	
5. grep -r ➡️ Cari isi teks dalam file
   
Beri Hak Eksekusi
~~~~
chmod +x search_file.sh
~~~~

Eksekusi File Yang Telah Dibuat
~~~~
./search_file.sh
~~~~

penjelasan:
1. chmod +x search_file.sh
→ Memberi izin eksekusi agar script bisa dijalankan.
Eksekusi naskah yang telah di buat

2. ./search_file.sh
→ Menjalankan script yang sudah dibuat.


# LANGKAH 4 HASILKAN SISTEM FILE LAPORAN
Buat File Report.sh

~~~~
nano report.sh
~~~~

[Deskripsi_gambar] ()

~~~~
#!/bin/bash
# Script: generate_report.sh
# Fungsi: Membuat laporan statistik file sistem

cd ~/project_file_management

echo "=== LAPORAN FILE SISTEM ===" > report.txt
echo "Tanggal: $(date)" >> report.txt
echo "" >> report.txt

echo "--- Jumlah File dan Folder ---" >> report.txt
ls -lR | wc -l >> report.txt
echo "" >> report.txt

echo "--- Ukuran Total Folder ---" >> report.txt
du -sh . >> report.txt
echo "" >> report.txt

echo "--- Daftar 10 File Terbesar ---" >> report.txt
find . -type f -exec du -h {} + | sort -rh | head -10 >> report.txt
echo "" >> report.txt

echo "--- Statistik Berdasarkan Ekstensi ---" >> report.txt
echo "TXT: $(find . -type f -name '*.txt' | wc -l)" >> report.txt
echo "JPG: $(find . -type f -name '*.jpg' | wc -l)" >> report.txt
echo "PDF: $(find . -type f -name '*.pdf' | wc -l)" >> report.txt
echo "LOG: $(find . -type f -name '*.log' | wc -l)" >> report.txt

echo "" >> report.txt
echo "=== Selesai! Laporan disimpan di report.txt ==="
~~~~

penjelasan
1. echo untuk menampilkan teks atau hasil variabel ke layar — atau untuk menulis teks ke file.
2. ls -lR menampilkan semua isi folder secara rekursif,
3. wc -l menghitung jumlah baris = total file & folder.
4. du -sh . menampilkan ukuran total direktori saat ini dalam format mudah dibaca
5. find mencari semua file,
6. sort -rh mengurutkan dari yang terbesar,
7. head -10 menampilkan 10 teratas.

Beri hak Akses Eksekusi
~~~~
chmod +x report.sh
~~~~
penjelasan:
 chmod +x report.sh
→ Memberi izin eksekusi agar script bisa dijalankan.
Eksekusi naskah yang telah di buat

~~~~
./report.sh
~~~~

Melihat Isi Laporan
~~~~
cat report.sh
~~~~
